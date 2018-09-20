---
title: Serialización en MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebd11488f0f86123bcf95d210072cc61dcc31c60
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409238"
---
# <a name="serialization-in-mfc"></a>Serialización en MFC

En este artículo se explica el mecanismo de serialización proporcionado en la base clase biblioteca MFC (Microsoft) para permitir que los objetos se conserven entre las ejecuciones del programa.

La serialización es el proceso de escritura o lectura de un objeto a o desde un medio de almacenamiento persistente, como un archivo de disco. La serialización es ideal para situaciones donde se desea mantener el estado de los datos estructurados (como las clases de C++ o estructuras) durante o después de la ejecución de un programa. Uso de los objetos de serialización proporcionados por MFC permite esto se produzca de manera coherente y estándar, lo cual elimina la necesidad de realizar operaciones de archivos de forma manual el usuario.

MFC proporciona compatibilidad integrada para la serialización en la clase `CObject`. Por lo tanto, todas las clases derivadas de `CObject` puede sacar partido de `CObject`del protocolo de serialización.

La idea básica de la serialización es que un objeto debe ser capaz de escribir su estado actual, que normalmente está indicado por el valor de sus variables miembro, en un almacenamiento persistente. Más adelante, el objeto se puede crear volver a leer o deserializar, el estado del objeto desde el almacenamiento. La serialización controla todos los detalles de los punteros y referencias circulares a objetos que se usan al serializar un objeto. Un punto clave es que el propio objeto es responsable de leer y escribir su propio estado. Por lo tanto, para que una clase sea serializable, debe implementar las operaciones de serialización básica. Como se muestra en el grupo de serialización de artículos, es fácil agregar esta funcionalidad a una clase.

MFC utiliza un objeto de la `CArchive` clase como un intermediario entre el objeto que se va a serializar y el medio de almacenamiento. Este objeto siempre se asocia un `CFile` objeto desde la que obtiene la información necesaria para la serialización, incluido el nombre de archivo y si la operación solicitada es una lectura o escritura. Puede usar el objeto que realiza una operación de serialización la `CArchive` objeto sin tener en cuenta la naturaleza del medio de almacenamiento.

Un `CArchive` objeto utiliza inserción sobrecargado (**<\<**) y la extracción (**>>**) operadores para realizar la escritura y lectura de operaciones. Para obtener más información, consulte [almacenar y cargar CObjects a través de un archivo](../mfc/storing-and-loading-cobjects-via-an-archive.md) en el artículo serialización: serializar un objeto.

> [!NOTE]
>  No confunda la `CArchive` con el formato clase con las clases iostream de propósito general, que son de sólo texto. La `CArchive` clase es para los objetos serializados en formato binario.

Si lo desea, puede omitir la serialización de MFC para crear su propio mecanismo de almacenamiento de datos persistente. Deberá reemplazar las funciones miembro de clase que inician la serialización en línea de comandos del usuario. Vea la explicación en [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md) de los comandos estándar ID_FILE_OPEN, ID_FILE_SAVE y ID_FILE_SAVE_AS.

Los artículos siguientes tratan las dos tareas principales necesarias para la serialización:

- [Serialización: Crear una clase serializable](../mfc/serialization-making-a-serializable-class.md)

- [Serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md)

El artículo [serialización: serialización frente. Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md) describe cuando la serialización es una técnica de entrada/salida adecuada en las aplicaciones de base de datos.

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CArchive (clase)](../mfc/reference/carchive-class.md)<br/>
[CObject (clase)](../mfc/reference/cobject-class.md)<br/>
[CDocument (clase)](../mfc/reference/cdocument-class.md)<br/>
[CFile (clase)](../mfc/reference/cfile-class.md)
