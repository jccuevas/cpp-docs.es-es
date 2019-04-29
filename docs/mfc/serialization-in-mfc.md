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
ms.openlocfilehash: 5c7dec140635b6d83bdae936d1bb0cef144f825b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308218"
---
# <a name="serialization-in-mfc"></a>Serialización en MFC

En este artículo se explica el mecanismo de serialización proporcionado en la base clase biblioteca MFC (Microsoft) para permitir que los objetos se conserven entre las ejecuciones del programa.

La serialización es el proceso de escritura o lectura de un objeto a o desde un medio de almacenamiento persistente, como un archivo de disco. La serialización es ideal para situaciones donde se desea mantener el estado de los datos estructurados (como las clases de C++ o estructuras) durante o después de la ejecución de un programa. Uso de los objetos de serialización proporcionados por MFC permite esto se produzca de manera coherente y estándar, lo cual elimina la necesidad de realizar operaciones de archivos de forma manual el usuario.

MFC proporciona compatibilidad integrada para la serialización en la clase `CObject`. Por lo tanto, todas las clases derivadas de `CObject` puede sacar partido de `CObject`del protocolo de serialización.

La idea básica de la serialización es que un objeto debe ser capaz de escribir su estado actual, que normalmente está indicado por el valor de sus variables miembro, en un almacenamiento persistente. Más adelante, el objeto se puede crear volver a leer o deserializar, el estado del objeto desde el almacenamiento. La serialización controla todos los detalles de los punteros y referencias circulares a objetos que se usan al serializar un objeto. Un punto clave es que el propio objeto es responsable de leer y escribir su propio estado. Por lo tanto, para que una clase sea serializable, debe implementar las operaciones de serialización básica. Como se muestra en el grupo de serialización de artículos, es fácil agregar esta funcionalidad a una clase.

MFC utiliza un objeto de la `CArchive` clase como un intermediario entre el objeto que se va a serializar y el medio de almacenamiento. Este objeto siempre se asocia un `CFile` objeto desde la que obtiene la información necesaria para la serialización, incluido el nombre de archivo y si la operación solicitada es una lectura o escritura. Puede usar el objeto que realiza una operación de serialización la `CArchive` objeto sin tener en cuenta la naturaleza del medio de almacenamiento.

Un `CArchive` objeto utiliza inserción sobrecargado (**<\<**) y la extracción (**>>**) operadores para realizar la escritura y lectura de operaciones. Para obtener más información, consulte [almacenar y cargar CObjects a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md) en el artículo de serialización: Serializar un objeto.

> [!NOTE]
>  No confunda la `CArchive` con el formato clase con las clases iostream de propósito general, que son de sólo texto. La `CArchive` clase es para los objetos serializados en formato binario.

Si lo desea, puede omitir la serialización de MFC para crear su propio mecanismo de almacenamiento de datos persistente. Deberá reemplazar las funciones miembro de clase que inician la serialización en línea de comandos del usuario. Vea la explicación en [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md) de los comandos estándar ID_FILE_OPEN, ID_FILE_SAVE y ID_FILE_SAVE_AS.

Los artículos siguientes tratan las dos tareas principales necesarias para la serialización:

- [Serialización: crear una clase serializable](../mfc/serialization-making-a-serializable-class.md)

- [Serialización: serializar un objeto](../mfc/serialization-serializing-an-object.md)

El artículo [serialización: serialización frente a Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md) describe cuando la serialización es una técnica de entrada/salida adecuada en las aplicaciones de base de datos.

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CArchive (clase)](../mfc/reference/carchive-class.md)<br/>
[CObject (clase)](../mfc/reference/cobject-class.md)<br/>
[CDocument (clase)](../mfc/reference/cdocument-class.md)<br/>
[CFile (clase)](../mfc/reference/cfile-class.md)
