---
title: Serialización en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: eca4d0357977bc7ef21063718c738ae5bd8e7431
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372746"
---
# <a name="serialization-in-mfc"></a>Serialización en MFC

En este artículo se explica el mecanismo de serialización proporcionado en la biblioteca Microsoft Foundation Class (MFC) para permitir que los objetos persistan entre las ejecuciones del programa.

La serialización es el proceso de escribir o leer un objeto hacia o desde un medio de almacenamiento persistente, como un archivo de disco. La serialización es ideal para situaciones en las que se desea mantener el estado de los datos estructurados (como clases o estructuras C++) durante o después de la ejecución de un programa. El uso de los objetos de serialización proporcionados por MFC permite que esto se produzca de forma estándar y coherente, liberando al usuario de la necesidad de realizar operaciones de archivo a mano.

MFC proporciona compatibilidad integrada para la `CObject`serialización en la clase. Por lo tanto, `CObject` todas las `CObject`clases derivadas de pueden aprovechar el protocolo de serialización 's.

La idea básica de la serialización es que un objeto debe ser capaz de escribir su estado actual, normalmente indicado por el valor de sus variables miembro, en el almacenamiento persistente. Más adelante, el objeto se puede volver a crear leyendo o deserializando el estado del objeto desde el almacenamiento. La serialización controla todos los detalles de los punteros de objeto y las referencias circulares a los objetos que se utilizan al serializar un objeto. Un punto clave es que el propio objeto es responsable de leer y escribir su propio estado. Por lo tanto, para que una clase sea serializable, debe implementar las operaciones de serialización básicas. Como se muestra en el grupo de artículos Serialización, es fácil agregar esta funcionalidad a una clase.

MFC utiliza un `CArchive` objeto de la clase como intermediario entre el objeto que se va a serializar y el medio de almacenamiento. Este objeto siempre está `CFile` asociado a un objeto, del que obtiene la información necesaria para la serialización, incluido el nombre de archivo y si la operación solicitada es una lectura o escritura. El objeto que realiza una operación de serialización puede utilizar el `CArchive` objeto sin tener en cuenta la naturaleza del medio de almacenamiento.

Un `CArchive` objeto utiliza operadores de inserción sobrecargado (**<**) y extracción (**>>**) para realizar operaciones de escritura y lectura. Para obtener más información, consulte Almacenamiento y carga de [CObjects a través](../mfc/storing-and-loading-cobjects-via-an-archive.md) de un archivo en el artículo Serialización: serialización de un objeto.

> [!NOTE]
> No confunda `CArchive` la clase con clases iostream de uso general, que son solo para texto con formato. La `CArchive` clase es para objetos serializados de formato binario.

Si lo desea, puede omitir la serialización MFC para crear su propio mecanismo para el almacenamiento de datos persistente. Deberá invalidar las funciones miembro de clase que inician la serialización en el comando del usuario. Consulte la discusión en la [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md) de los comandos ID_FILE_OPEN, ID_FILE_SAVE y ID_FILE_SAVE_AS estándar.

Los siguientes artículos cubren las dos tareas principales necesarias para la serialización:

- [Serialization: Making a Serializable (Clase)](../mfc/serialization-making-a-serializable-class.md)

- [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

En el artículo [Serialización: serialización frente a entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md) de base de datos se describe cuándo la serialización es una técnica de entrada/salida adecuada en las aplicaciones de base de datos.

## <a name="see-also"></a>Consulte también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CArchive (clase)](../mfc/reference/carchive-class.md)<br/>
[Clase CObject](../mfc/reference/cobject-class.md)<br/>
[CDocument (clase)](../mfc/reference/cdocument-class.md)<br/>
[CFile (clase)](../mfc/reference/cfile-class.md)
