---
title: 'TN002: Formato de datos de objetos persistentes | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a23ade068fa0d71715a76d3a99a393cc5458947c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399969"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Formato de datos de objetos persistentes

Esta nota describe las rutinas MFC que admiten objetos persistentes de C++ y el formato de los datos del objeto cuando se almacena en un archivo. Esto se aplica únicamente a las clases con el [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) macros.

## <a name="the-problem"></a>El problema

La implementación de MFC para los datos persistentes almacena datos de muchos objetos en una única parte contigua de un archivo. El objeto `Serialize` método traduce los datos del objeto en un formato binario compacto.

La implementación garantiza que todos los datos se guarda en el mismo formato usando el [CArchive (clase)](../mfc/reference/carchive-class.md). Usa un `CArchive` objeto como un traductor. Conserva este objeto desde el momento en se crea hasta que llame a [CArchive::Close](../mfc/reference/carchive-class.md#close). Este método se puede llamar explícitamente por el programador o implícitamente el destructor cuando el programa sale del ámbito que contiene el `CArchive`.

Esta nota describe la implementación de la `CArchive` miembros [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) y [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Encontrará el código para estas funciones en Arcobj.cpp y la implementación principal para `CArchive` en Arccore.cpp. Código de usuario no llama a `ReadObject` y `WriteObject` directamente. En su lugar, se utilizan estos objetos específicos de la clase con seguridad de tipos de inserción y extracción de operadores que se generan automáticamente mediante las macros DECLARE_SERIAL y IMPLEMENT_SERIAL. El siguiente código muestra cómo `WriteObject` y `ReadObject` implícitamente se denominan:

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Guardado de objetos para el Store (CArchive::WriteObject)

El método `CArchive::WriteObject` escribe los datos de encabezado que se usan para reconstruir el objeto. Estos datos se compone de dos partes: el tipo del objeto y el estado del objeto. Este método también es responsable de mantener la identidad del objeto que se escribe, por lo que se guarda una sola copia, independientemente del número de punteros a ese objeto (incluidos los punteros circulares).

Guardar (inserción) y la restauración de objetos (extracción) se basa en varias "constantes de manifiesto." Estos son los valores que se almacenan en formato binario y proporcionan información importante para el archivo (tenga en cuenta el prefijo "w" indica las cantidades de 16 bits):

|Etiqueta|Descripción|
|---------|-----------------|
|wNullTag|Se usa para punteros a objetos NULL (0).|
|wNewClassTag|Indica la descripción de la clase que sigue es nueva en este contexto de archivo (-1).|
|wOldClassTag|Indica la clase del objeto que se está leyendo se ha visto en este contexto (0 x 8000).|

Al almacenar los objetos, el archivo mantiene un [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) (el *m_pStoreMap*) que es una asignación de un objeto almacenado en un identificador persistente (PID) de 32 bits. Un PID se asigna a cada objeto único y cada nombre de clase único que se guarda en el contexto del archivo. Estos PID se distribuyen secuencialmente, comenzando en 1. Estos PID no tener ningún significado fuera del ámbito del archivo y, en particular, no debe confundirse con los números de registros u otros elementos de la identidad.

En el `CArchive` (clase), PID es de 32 bits, pero éstas se escriben como de 16 bits a menos que sea mayor que 0x7FFE. PID grande se escribe como 0x7FFF seguido por el PID de 32 bits. Esto mantiene la compatibilidad con proyectos creados en versiones anteriores.

Cuando se realiza una solicitud para guardar un objeto en un archivo (normalmente mediante el operador de inserción globales), se realiza una comprobación para un valor NULL [CObject](../mfc/reference/cobject-class.md) puntero. Si el puntero es NULL, el *wNullTag* se inserta en la secuencia de archivo.

Si el puntero no es NULL y se puede serializar (la clase es un `DECLARE_SERIAL` clase), el código comprueba el *m_pStoreMap* para ver si ya se ha guardado el objeto. Si es así, el código inserta el PID de 32 bits asociado con ese objeto en la secuencia de archivo.

Si el objeto no se ha guardado antes, existen dos posibilidades que tener en cuenta: el objeto y el tipo exacto (es decir, (clase) del objeto están familiarizados con este contexto de archivo o el objeto es de un tipo exacto que ya se ha visto. Para determinar si el tipo se ha visto, el código consulta el *m_pStoreMap* para un [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objeto que coincide con el `CRuntimeClass` objeto asociado al objeto que se va a guardar. Si hay una coincidencia, `WriteObject` inserta una etiqueta que es el bit a bit `OR` de *wOldClassTag* y este índice. Si el `CRuntimeClass` es nueva en este contexto de archivo, `WriteObject` asigna un PID nuevo a esa clase y lo inserta en el archivo, precedido por el *wNewClassTag* valor.

El descriptor de esta clase, a continuación, se inserta en el archivo usando el `CRuntimeClass::Store` método. `CRuntimeClass::Store` Inserta el número de esquema de la clase (ver abajo) y el nombre de texto ASCII de la clase. Tenga en cuenta que el uso del nombre de texto ASCII no garantiza la unicidad del archivo en todas las aplicaciones. Por lo tanto, debe etiquetar los archivos de datos para evitar daños. Después de la inserción de la información de clase, el archivo coloca el objeto en el *m_pStoreMap* y, a continuación, llama a la `Serialize` método para insertar datos específicos de la clase. Colocar el objeto en el *m_pStoreMap* antes de llamar a `Serialize` impide que varias copias del objeto que se va a guardar en el almacén.

Cuando se devuelve al llamador inicial (la raíz de la red de objetos), debe llamar a [CArchive::Close](../mfc/reference/carchive-class.md#close). Si tiene previsto realizar otras [CFile](../mfc/reference/cfile-class.md)operaciones, debe llamar a la `CArchive` método [vaciar](../mfc/reference/carchive-class.md#flush) para evitar daños en el archivo.

> [!NOTE]
>  Esta implementación impone un límite máximo de índices de 0x3FFFFFFE por el contexto de archivo. Este número representa el número máximo de objetos únicos y las clases que pueden guardarse en un único archivo, pero un archivo de disco solo puede tener un número ilimitado de contextos de archivo.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Cargar objetos desde el Store (CArchive::ReadObject)

Cargando (extracción de) objetos utiliza la `CArchive::ReadObject` método y es el elemento opuesto de `WriteObject`. Igual que con `WriteObject`, `ReadObject` no llama directamente al código de usuario; código de usuario debe llamar el operador de extracción de la seguridad de tipos que se llama a `ReadObject` con el esperado `CRuntimeClass`. Esto garantiza la integridad del tipo de la operación de extracción.

Puesto que la `WriteObject` implementación asignado PID creciente, empezando por 1 (0 está predefinido como objeto nulo), el `ReadObject` implementación puede utilizar una matriz para mantener el estado del contexto del archivo. Cuando se lee un PID de la tienda, si el PID es mayor que el actual límite superior de la *m_pLoadArray*, `ReadObject` sabe que sigue un nuevo objeto (o la descripción de la clase).

## <a name="schema-numbers"></a>Números de esquema

El número de esquema, que se asigna a la clase cuando la `IMPLEMENT_SERIAL` método de la clase se encuentra, es la "versión" de la implementación de la clase. El esquema hace referencia a la implementación de la clase, no en el número de veces que un objeto determinado se ha realizado persistente (conoce normalmente como la versión del objeto).

Si piensa mantener varias implementaciones diferentes de la misma clase con el tiempo, incrementar el esquema según se revisa el objeto `Serialize` implementación del método, podrá escribir código que se puede cargar los objetos almacenados con versiones anteriores de la implementación.

El `CArchive::ReadObject` método producirá una [CArchiveException](../mfc/reference/carchiveexception-class.md) cuando encuentra un número de esquema en el almacén persistente que difiere del número de esquema de la descripción de la clase en la memoria. No es fácil para recuperarse de esta excepción.

Puede usar `VERSIONABLE_SCHEMA` combinada con (bit a bit **o**) su versión de esquema para mantener la que se produzca esta excepción. Mediante el uso de `VERSIONABLE_SCHEMA`, el código puede realizar la acción adecuada su `Serialize` función comprobando el valor devuelto de [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Llamar a serializar directamente

En muchos casos, la sobrecarga que supone el esquema de archivo de objeto general de `WriteObject` y `ReadObject` no es necesario. Este es el caso común de serializar los datos en un [CDocument](../mfc/reference/cdocument-class.md). En este caso, el `Serialize` método de la `CDocument` se llama directamente, no con los operadores de extracción o inserción. El contenido del documento a su vez puede usar el esquema de archivo de objeto más general.

Una llamada a `Serialize` directamente tiene las siguientes ventajas y desventajas:

- Ningún bytes adicionales se agregan al archivo antes o después de que el objeto se serializa. Esto no sólo hace que los datos guardados más pequeños, pero le permite implementar `Serialize` rutinas que pueden controlar cualquier formatos de archivo.

- La MFC se ajusta para que el `WriteObject` y `ReadObject` implementaciones y colecciones relacionadas no se vincularán a la aplicación a menos que necesite el esquema de archivo de objeto más general para cualquier otro propósito.

- El código no tiene que recuperarse los números de esquema anterior. Esto hace que el código de serialización de documentos que responsables por los números de esquema de codificación, números de versión del formato de archivo o números de identificación de cualquier usar al principio de los archivos de datos.

- Cualquier objeto que se serializa con una llamada directa a `Serialize` no deben usar `CArchive::GetObjectSchema` o debe identificador de valor devuelto de -1 (UINT) que indica que la versión era desconocida.

Dado que `Serialize` se denomina directamente en el documento, no es normalmente posible para los objetos secundarios del documento para archivar las referencias a su documento primario. Estos objetos deben tener un puntero a su documento de contenedor explícitamente o se debe usar [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) función para asignar el `CDocument` puntero a un PID antes de que estos punteros se archivan.

Como se indicó anteriormente, debe codificar la versión y clase información cuando se llama a `Serialize` directamente, lo que le permite cambiar el formato más adelante manteniendo la compatibilidad con versiones anteriores con los archivos antiguos. El `CArchive::SerializeClass` función se puede llamar explícitamente antes de serializar directamente un objeto o antes de llamar a una clase base.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

