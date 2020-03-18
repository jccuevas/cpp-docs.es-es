---
title: 'TN002: Formato de datos de objetos persistentes'
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 1880d5d43055966dea8ab16dc4f26bd4e4602ec5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447128"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Formato de datos de objetos persistentes

En esta nota se describen las rutinas de MFC C++ que admiten objetos persistentes y el formato de los datos de objeto cuando se almacenan en un archivo. Esto solo se aplica a las clases con las macros [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) .

## <a name="the-problem"></a>El problema

La implementación de MFC para datos persistentes almacena datos de muchos objetos en una única parte contigua de un archivo. El método `Serialize` del objeto traduce los datos del objeto a un formato binario compacto.

La implementación garantiza que todos los datos se guardan en el mismo formato mediante la [clase CArchive](../mfc/reference/carchive-class.md). Utiliza un objeto de `CArchive` como traductor. Este objeto se conserva desde el momento en que se crea hasta que se llama a [CArchive:: Close](../mfc/reference/carchive-class.md#close). Este método puede ser llamado explícitamente por el programador o implícitamente por el destructor cuando el programa sale del ámbito que contiene el `CArchive`.

En esta nota se describe la implementación de los miembros `CArchive` [CArchive:: ReadObject](../mfc/reference/carchive-class.md#readobject) y [CArchive:: writeObject](../mfc/reference/carchive-class.md#writeobject). Encontrará el código para estas funciones en Arcobj. cpp y la implementación principal de `CArchive` en Arccore. cpp. El código de usuario no llama a `ReadObject` y `WriteObject` directamente. En su lugar, estos objetos se usan en los operadores de inserción y extracción con seguridad de tipos específicos de la clase que se generan automáticamente mediante las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. En el código siguiente se muestra cómo se denominan implícitamente `WriteObject` y `ReadObject`:

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Guardar objetos en el almacén (CArchive:: WriteObject)

El método `CArchive::WriteObject` escribe los datos de encabezado que se usan para reconstruir el objeto. Estos datos se componen de dos partes: el tipo del objeto y el estado del objeto. Este método también es responsable de mantener la identidad del objeto que se va a escribir, de modo que solo se guarde una copia, independientemente del número de punteros a ese objeto (incluidos los punteros circulares).

Guardar (insertar) y restaurar (extraer) objetos se basa en varias "constantes del manifiesto". Estos son los valores que se almacenan en formato binario y proporcionan información importante al archivo (tenga en cuenta que el prefijo "w" indica las cantidades de 16 bits):

|Etiqueta|Descripción|
|---------|-----------------|
|wNullTag|Se utiliza para punteros de objeto NULL (0).|
|wNewClassTag|Indica que la descripción de la clase siguiente es nueva en este contexto de archivo (-1).|
|wOldClassTag|Indica que la clase del objeto que se está leyendo se ha detectado en este contexto (0x8000).|

Al almacenar objetos, el archivo mantiene un [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (el *m_pStoreMap*) que es una asignación de un objeto almacenado a un identificador persistente (PID) de 32 bits. Se asigna un PID a cada objeto único y a cada nombre de clase único que se guarda en el contexto del archivo. Estos PID se entregan secuencialmente a partir de 1. Estos PID no tienen importancia fuera del ámbito del archivo y, en particular, no se deben confundir con los números de registro u otros elementos de identidad.

En la clase `CArchive`, los PID son de 32 bits, pero se escriben como de 16 bits a menos que sean mayores que 0x7FFE. Los PID grandes se escriben como 0x7FFF seguido del PID de 32 bits. Esto mantiene la compatibilidad con los proyectos creados en versiones anteriores.

Cuando se realiza una solicitud para guardar un objeto en un archivo (normalmente mediante el operador de inserción global), se realiza una comprobación para un puntero [COBJECT](../mfc/reference/cobject-class.md) nulo. Si el puntero es NULL, el *wNullTag* se inserta en la secuencia de archivo.

Si el puntero no es NULL y se puede serializar (la clase es una clase `DECLARE_SERIAL`), el código comprueba el *m_pStoreMap* para ver si el objeto ya se ha guardado. Si es así, el código inserta el PID de 32 bits asociado a ese objeto en la secuencia de archivo.

Si el objeto no se ha guardado antes, hay dos posibilidades de considerar: tanto el objeto como el tipo exacto (es decir, la clase) del objeto son nuevos en este contexto de archivo o el objeto es de un tipo exacto ya detectado. Para determinar si se ha detectado el tipo, el código consulta el *m_pStoreMap* para un objeto [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) que coincida con el objeto `CRuntimeClass` asociado al objeto que se va a guardar. Si hay una coincidencia, `WriteObject` inserta una etiqueta que es el `OR` de bits de *wOldClassTag* y este índice. Si el `CRuntimeClass` es nuevo en este contexto de archivo, `WriteObject` asigna un nuevo PID a esa clase y lo inserta en el archivo, precedido por el valor de *wNewClassTag* .

A continuación, el descriptor de esta clase se inserta en el archivo mediante el método `CRuntimeClass::Store`. `CRuntimeClass::Store` inserta el número de esquema de la clase (vea más abajo) y el nombre de texto ASCII de la clase. Tenga en cuenta que el uso del nombre de texto ASCII no garantiza la exclusividad del archivo en todas las aplicaciones. Por lo tanto, debe etiquetar los archivos de datos para evitar daños. Después de la inserción de la información de la clase, el archivo coloca el objeto en el *m_pStoreMap* y, a continuación, llama al método `Serialize` para insertar datos específicos de la clase. Colocar el objeto en el *m_pStoreMap* antes de llamar a `Serialize` impide que se guarden varias copias del objeto en el almacén.

Al volver al llamador inicial (normalmente la raíz de la red de objetos), debe llamar a [CArchive:: Close](../mfc/reference/carchive-class.md#close). Si tiene previsto realizar otras operaciones de [CFile](../mfc/reference/cfile-class.md), debe llamar al método `CArchive` [Flush](../mfc/reference/carchive-class.md#flush) para evitar daños en el archivo.

> [!NOTE]
>  Esta implementación impone un límite estricto de índices de 0x3FFFFFFE por contexto de archivo. Este número representa el número máximo de objetos y clases únicos que se pueden guardar en un único archivo, pero un único archivo de disco puede tener un número ilimitado de contextos de archivo.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Cargar objetos de la tienda (CArchive:: ReadObject)

La carga (extracción) de objetos usa el método `CArchive::ReadObject` y es el opuesto de `WriteObject`. Como con `WriteObject`, el código de usuario no llama directamente a `ReadObject`. el código de usuario debe llamar al operador de extracción con seguridad de tipos que llama a `ReadObject` con el `CRuntimeClass`esperado. Esto garantiza la integridad de tipo de la operación de extracción.

Dado que la implementación de `WriteObject` ha asignado el aumento de los PID, empezando por 1 (0 está predefinido como el objeto NULL), la implementación de `ReadObject` puede usar una matriz para mantener el estado del contexto del archivo. Cuando se lee un PID del almacén, si el PID es mayor que el límite superior actual del *m_pLoadArray*, `ReadObject` sabe que sigue un nuevo objeto (o una descripción de clase).

## <a name="schema-numbers"></a>Números de esquema

El número de esquema, que se asigna a la clase cuando se encuentra el método de `IMPLEMENT_SERIAL` de la clase, es la "versión" de la implementación de la clase. El esquema hace referencia a la implementación de la clase, no al número de veces que un objeto determinado se ha convertido en persistente (lo que normalmente se conoce como la versión del objeto).

Si piensa mantener varias implementaciones diferentes de la misma clase a lo largo del tiempo, incrementar el esquema a medida que revise la implementación del método `Serialize` del objeto le permitirá escribir código que pueda cargar objetos almacenados mediante versiones anteriores de la implementación.

El método `CArchive::ReadObject` producirá una [CArchiveException](../mfc/reference/carchiveexception-class.md) cuando encuentre un número de esquema en el almacén persistente que difiere del número de esquema de la descripción de clase en la memoria. No es fácil recuperarse de esta excepción.

Puede usar `VERSIONABLE_SCHEMA` combinado con ( **OR bit a**bit) la versión del esquema para evitar que se produzca esta excepción. Mediante el uso de `VERSIONABLE_SCHEMA`, el código puede realizar la acción adecuada en su `Serialize` función comprobando el valor devuelto de [CArchive:: GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Llamar directamente a Serialize

En muchos casos, la sobrecarga del esquema de archivo de objeto general de `WriteObject` y `ReadObject` no es necesaria. Este es el caso común de serializar los datos en un [CDocument](../mfc/reference/cdocument-class.md). En este caso, se llama directamente al método `Serialize` del `CDocument`, no a los operadores Extract o INSERT. El contenido del documento puede usar a su vez el esquema de archivo de objeto más general.

Llamar a `Serialize` directamente presenta las siguientes ventajas y desventajas:

- No se agregan bytes adicionales al archivo antes o después de serializar el objeto. Esto no solo reduce el tamaño de los datos guardados, sino que permite implementar rutinas `Serialize` que pueden controlar cualquier formato de archivo.

- La MFC se optimiza para que las implementaciones de `WriteObject` y `ReadObject` y las colecciones relacionadas no se vinculen a la aplicación a menos que necesite el esquema de archivo de objeto más general para algún otro propósito.

- El código no tiene que recuperarse de los números de esquema antiguos. Esto hace que el código de serialización de documentos sea responsable de codificar los números de esquema, los números de versión de formato de archivo o cualquier número de identificación que se utilice al principio de los archivos de datos.

- Cualquier objeto que se serialice con una llamada directa a `Serialize` no debe utilizar `CArchive::GetObjectSchema` o debe controlar un valor devuelto de (UINT)-1, lo que indica que la versión era desconocida.

Dado que se llama a `Serialize` directamente en el documento, normalmente no es posible que los subobjetos del documento archiven las referencias a su documento primario. Estos objetos deben recibir explícitamente un puntero a su documento contenedor o debe usar la función [CArchive:: MapObject](../mfc/reference/carchive-class.md#mapobject) para asignar el puntero de `CDocument` a un PID antes de que se archiven estos punteros de retroceso.

Como se indicó anteriormente, debe codificar la información de la versión y de la clase cuando llame a `Serialize` directamente, lo que le permite cambiar el formato más adelante mientras sigue manteniendo la compatibilidad con versiones anteriores de los archivos más antiguos. Se puede llamar a la función `CArchive::SerializeClass` explícitamente antes de serializar directamente un objeto o antes de llamar a una clase base.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
