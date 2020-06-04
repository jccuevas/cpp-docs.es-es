---
title: Serializar datos en y desde archivos
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: 043ba019c6b5ad79db2cedb6314c9e65f14b14b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376931"
---
# <a name="serializing-data-to-and-from-files"></a>Serializar datos en y desde archivos

La idea básica de persistencia es que un objeto debe ser capaz de escribir su estado actual, indicado por los valores de sus variables miembro, en el almacenamiento persistente. Más adelante, el objeto se puede volver a crear leyendo o "deserializando", el estado del objeto desde el almacenamiento persistente. Un punto clave aquí es que el objeto en sí es responsable de leer y escribir su propio estado. Por lo tanto, para que una clase sea persistente, debe implementar las operaciones de serialización básicas.

El marco de trabajo proporciona una implementación predeterminada para guardar documentos en archivos de disco en respuesta a los comandos Guardar y Guardar como del menú Archivo y para cargar documentos desde archivos de disco en respuesta al comando Abrir. Con muy poco trabajo, puede implementar la capacidad de un documento para escribir y leer sus datos hacia y desde un archivo. Lo principal que debe hacer es invalidar el [Serialize](../mfc/reference/cobject-class.md#serialize) función miembro en la clase de documento.

El Asistente para aplicaciones MFC coloca `CDocument` una `Serialize` invalidación esquelética de la función miembro en la clase de documento que crea automáticamente. Después de implementar las variables miembro de la `Serialize` aplicación, puede rellenar la invalidación con código que envía los datos a un "objeto de archivo" conectado a un archivo. Un [cArchive](../mfc/reference/carchive-class.md) objeto es similar a los objetos de entrada/salida de **cin** y **cout** de la biblioteca iostream C++. Sin `CArchive` embargo, escribe y lee el formato binario, no el texto con formato.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Serialización](../mfc/serialization-in-mfc.md)

- [El papel del documento en la serialización](#_core_the_document.92.s_role_in_serialization)

- [El rol de los datos en la serialización](#_core_the_data.92.s_role_in_serialization)

- [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)

## <a name="the-documents-role-in-serialization"></a><a name="_core_the_document.92.s_role_in_serialization"></a>El papel del documento en la serialización

El marco de trabajo responde automáticamente a los comandos Abrir, Guardar y `Serialize` Guardar como del menú Archivo llamando a la función miembro del documento si se implementa. Un comando ID_FILE_OPEN, por ejemplo, llama a una función de controlador en el objeto de aplicación. Durante este proceso, el usuario ve y responde al cuadro de diálogo Abrir archivo y el marco de trabajo obtiene el nombre de archivo que el usuario elige. El marco `CArchive` de trabajo crea un objeto configurado para cargar `Serialize`datos en el documento y pasa el archivo a . El marco de trabajo ya ha abierto el archivo. El código de la `Serialize` función miembro del documento lee los datos a través del archivo, reconstruyendo objetos de datos según sea necesario. Para obtener más información acerca de la serialización, vea el artículo [Serialización](../mfc/serialization-in-mfc.md).

## <a name="the-datas-role-in-serialization"></a><a name="_core_the_data.92.s_role_in_serialization"></a>El rol de los datos en la serialización

En general, los datos de tipo de clase deben poder serializarse. Es decir, cuando se pasa un objeto a un archivo, el objeto debe saber cómo escribirse a sí mismo en el archivo y cómo leerse a sí mismo desde el archivo. MFC proporciona compatibilidad para hacer que las clases serializables de esta manera. Si diseña una clase para definir un tipo de datos y tiene la intención de serializar datos de ese tipo, diseñe para la serialización.

## <a name="see-also"></a>Consulte también

[Usar documentos](../mfc/using-documents.md)
