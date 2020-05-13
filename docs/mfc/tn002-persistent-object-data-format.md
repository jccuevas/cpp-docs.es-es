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
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370444"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Formato de datos de objetos persistentes

Esta nota describe las rutinas MFC que admiten objetos C++ persistentes y el formato de los datos de objeto cuando se almacenan en un archivo. Esto solo se aplica a las clases con las macros [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL.](../mfc/reference/run-time-object-model-services.md#implement_serial)

## <a name="the-problem"></a>El problema

La implementación de MFC para datos persistentes almacena datos para muchos objetos en una sola parte contigua de un archivo. El método `Serialize` del objeto traduce los datos del objeto en un formato binario compacto.

La implementación garantiza que todos los datos se guardan en el mismo formato mediante la [clase CArchive](../mfc/reference/carchive-class.md). Utiliza un `CArchive` objeto como traductor. Este objeto persiste desde el momento en que se crea hasta que se llama a [CArchive::Close](../mfc/reference/carchive-class.md#close). El programador puede llamar a este método explícitamente o implícitamente por el destructor `CArchive`cuando el programa sale del ámbito que contiene el archivo .

Esta nota describe la `CArchive` implementación de los miembros [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) y [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Encontrará el código para estas funciones en Arcobj.cpp `CArchive` y la implementación principal para Arccore.cpp. El código de `ReadObject` `WriteObject` usuario no llama y directamente. En su lugar, estos objetos se utilizan en los operadores de inserción y extracción de tipo seguro de clase específicos de clase generados automáticamente por las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. El código siguiente `WriteObject` `ReadObject` muestra cómo y se llama implícitamente:

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Guardar objetos en el almacén (CArchive::WriteObject)

El `CArchive::WriteObject` método escribe los datos de encabezado que se utilizan para reconstruir el objeto. Estos datos constan de dos partes: el tipo del objeto y el estado del objeto. Este método también es responsable de mantener la identidad del objeto que se está escribiendo, de modo que solo se guarde una sola copia, independientemente del número de punteros a ese objeto (incluidos los punteros circulares).

Guardar (insertar) y restaurar (extraer) objetos se basa en varias "constantes de manifiesto." Estos son valores que se almacenan en binario y proporcionan información importante al archivo (tenga en cuenta que el prefijo "w" indica cantidades de 16 bits):

|Etiqueta|Descripción|
|---------|-----------------|
|wNullTag|Se utiliza para punteros de objeto NULL (0).|
|wNewClassTag|Indica que la descripción de la clase que sigue es nueva en este contexto de archivado (-1).|
|wOldClassTag|Indica que la clase del objeto que se lee se ha visto en este contexto (0x8000).|

Al almacenar objetos, el archivo mantiene un [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (el *m_pStoreMap*) que es una asignación de un objeto almacenado a un identificador persistente de 32 bits (PID). Se asigna un PID a cada objeto único y a cada nombre de clase único que se guarda en el contexto del archivo. Estos PID se reparten secuencialmente a partir de 1. Estos PID no tienen importancia fuera del ámbito del archivo y, en particular, no deben confundirse con números de registro u otros elementos de identidad.

En `CArchive` la clase, los PID son de 32 bits, pero se escriben como de 16 bits a menos que sean mayores que 0x7FFE. Los PID grandes se escriben como 0x7FFF seguidos del PID de 32 bits. Esto mantiene la compatibilidad con los proyectos creados en versiones anteriores.

Cuando se realiza una solicitud para guardar un objeto en un archivo (normalmente mediante el operador de inserción global), se realiza una comprobación para un [NULL CObject](../mfc/reference/cobject-class.md) puntero. Si el puntero es NULL, *wNullTag* se inserta en la secuencia de archivado.

Si el puntero no es NULL y se `DECLARE_SERIAL` puede serializar (la clase es una clase), el código comprueba el *m_pStoreMap* para ver si el objeto ya se ha guardado. Si es así, el código inserta el PID de 32 bits asociado a ese objeto en la secuencia de archivado.

Si el objeto no se ha guardado antes, hay dos posibilidades a tener en cuenta: tanto el objeto como el tipo exacto (es decir, clase) del objeto son nuevos en este contexto de archivado, o el objeto es de un tipo exacto ya visto. Para determinar si se ha visto el tipo, el código consulta el `CRuntimeClass` *m_pStoreMap* para un [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objeto que coincide con el objeto asociado con el objeto que se está guardando. Si hay una `WriteObject` coincidencia, inserta una etiqueta que `OR` es bit a bit de *wOldClassTag* y este índice. Si `CRuntimeClass` es nuevo en este `WriteObject` contexto de archivado, asigna un nuevo PID a esa clase y lo inserta en el archivo, precedido por el valor *wNewClassTag.*

A continuación, el descriptor de esta clase `CRuntimeClass::Store` se inserta en el archivo mediante el método. `CRuntimeClass::Store`inserta el número de esquema de la clase (véase más adelante) y el nombre de texto ASCII de la clase. Tenga en cuenta que el uso del nombre de texto ASCII no garantiza la unicidad del archivo entre las aplicaciones. Por lo tanto, debe etiquetar los archivos de datos para evitar daños. Después de la inserción de la información de clase, `Serialize` el archivo coloca el objeto en el *m_pStoreMap y,* a continuación, llama al método para insertar datos específicos de la clase. Colocar el objeto *m_pStoreMap* en `Serialize` el m_pStoreMap antes de llamar impide que varias copias del objeto se guarden en el almacén.

Al volver al llamador inicial (normalmente la raíz de la red de objetos), debe llamar a [CArchive::Close](../mfc/reference/carchive-class.md#close). Si planea realizar otras operaciones [de CFile,](../mfc/reference/cfile-class.md)debe llamar al `CArchive` método [Flush](../mfc/reference/carchive-class.md#flush) para evitar daños en el archivo.

> [!NOTE]
> Esta implementación impone un límite duro de índices 0x3FFFFFFE por contexto de archivo. Este número representa el número máximo de objetos y clases únicos que se pueden guardar en un único archivo, pero un único archivo de disco puede tener un número ilimitado de contextos de archivado.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Carga de objetos desde el almacén (CArchive::ReadObject)

La carga (extracción) `CArchive::ReadObject` de objetos utiliza `WriteObject`el método y es la inversa de . Al `WriteObject`igual `ReadObject` que con , no se llama directamente por el código de usuario; código de usuario debe llamar al `ReadObject` operador de `CRuntimeClass`extracción con seguridad de tipos que llama con el esperado . Esto asegura la integridad del tipo de la operación de extracción.

Puesto `WriteObject` que la implementación asignada a los PID crecientes, empezando `ReadObject` por 1 (0 está predefinido como el objeto NULL), la implementación puede utilizar una matriz para mantener el estado del contexto de archivado. Cuando se lee un PID desde el almacén, si el *m_pLoadArray*PID `ReadObject` es mayor que el límite superior actual del m_pLoadArray , sabe que sigue un nuevo objeto (o descripción de clase).

## <a name="schema-numbers"></a>Números de esquema

El número de esquema, que se `IMPLEMENT_SERIAL` asigna a la clase cuando se encuentra el método de la clase, es la "versión" de la implementación de la clase. El esquema hace referencia a la implementación de la clase, no al número de veces que un objeto determinado se ha vuelto persistente (normalmente denominado la versión del objeto).

Si tiene la intención de mantener varias implementaciones diferentes de la misma clase `Serialize` a lo largo del tiempo, el incremento del esquema a medida que revise la implementación del método del objeto le permitirá escribir código que pueda cargar objetos almacenados mediante versiones anteriores de la implementación.

El `CArchive::ReadObject` método producirá un [CArchiveException](../mfc/reference/carchiveexception-class.md) cuando encuentra un número de esquema en el almacén persistente que difiere del número de esquema de la descripción de la clase en memoria. No es fácil recuperarse de esta excepción.

Puede usar `VERSIONABLE_SCHEMA` combined con (bitwise **OR**) la versión del esquema para evitar que se produzca esta excepción. Mediante `VERSIONABLE_SCHEMA`el uso de , el `Serialize` código puede realizar la acción adecuada en su función comprobando el valor devuelto de [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Llamar a Serialize directamente

En muchos casos, la sobrecarga del `WriteObject` `ReadObject` esquema de archivado de objetos general de y no es necesaria. Este es el caso común de serializar los datos en un [CDocument](../mfc/reference/cdocument-class.md). En este caso, `Serialize` el `CDocument` método de la se llama directamente, no con los operadores de extracto o inserción. El contenido del documento puede, a su vez, utilizar el esquema de archivo de objetos más general.

Llamar `Serialize` directamente tiene las siguientes ventajas y desventajas:

- No se agregan bytes adicionales al archivo antes o después de serializar el objeto. Esto no solo hace que los datos `Serialize` guardados sean más pequeños, sino que le permite implementar rutinas que pueden manejar cualquier formato de archivo.

- El MFC se `WriteObject` ajusta `ReadObject` para que las implementaciones y colecciones relacionadas no se vincularán a la aplicación a menos que necesite el esquema de archivado de objetos más general para algún otro propósito.

- El código no tiene que recuperarse de números de esquema antiguos. Esto hace que el código de serialización de documentos sea responsable de codificar números de esquema, números de versión de formato de archivo o los números de identificación que utilice al principio de los archivos de datos.

- Cualquier objeto serializado con una `Serialize` llamada directa `CArchive::GetObjectSchema` a no debe usar o debe controlar un valor devuelto de (UINT)-1 que indica que la versión era desconocida.

Dado `Serialize` que se llama directamente en el documento, normalmente no es posible que los subobjetos del documento archiven las referencias a su documento principal. Estos objetos deben tener un puntero a su documento contenedor explícitamente o debe `CDocument` usar [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) función para asignar el puntero a un PID antes de que se archiven estos punteros de retroceso.

Como se indicó anteriormente, debe codificar la información `Serialize` de la versión y la clase usted mismo cuando se llama directamente, lo que le permite cambiar el formato más adelante mientras mantiene la compatibilidad con versiones anteriores con archivos antiguos. Se `CArchive::SerializeClass` puede llamar a la función explícitamente antes de serializar directamente un objeto o antes de llamar a una clase base.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
