---
title: Serializar datos en y desde archivos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec6bfbe647045a334af9fe95cd6d1ab40625a51f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-data-to-and-from-files"></a>Serializar datos en y desde archivos
La idea básica de la persistencia es que un objeto debe ser capaz de escribir su estado actual, indicado por los valores de sus variables miembro, en un almacenamiento persistente. Más adelante, el objeto se puede crear volver a leer, o "deserializando", el estado del objeto desde el almacenamiento persistente. Un punto clave aquí es que el propio objeto es responsable de leer y escribir su propio estado. Por lo tanto, para que una clase sea persistente, debe implementar las operaciones de serialización básica.  
  
 El marco de trabajo proporciona una implementación predeterminada para guardar los documentos en archivos de disco en respuesta a la operación de guardar y guardar como comandos en el menú archivo así como para cargar documentos desde archivos de disco en respuesta al comando Abrir. Con muy poco esfuerzo, puede implementar la capacidad de un documento para escribir y leer sus datos a y desde un archivo. Lo principal que debe hacer es invalidar la [Serialize](../mfc/reference/cobject-class.md#serialize) función miembro en la clase de documento.  
  
 El Asistente para aplicaciones MFC coloca una invalidación de esqueleto de la **CDocument** función miembro `Serialize` en la clase de documento que crea para usted. Después de haber implementado las variables de miembro de la aplicación, puede rellenar el `Serialize` reemplazar con código que envía los datos a un "objeto de almacenamiento" conectado a un archivo. A [CArchive](../mfc/reference/carchive-class.md) objeto es similar a la `cin` y `cout` objetos de la biblioteca iostream de C++ de entrada/salida. Sin embargo, `CArchive` escribe y lee en formato binario, no tener formato de texto.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Serialización](../mfc/serialization-in-mfc.md)  
  
-   [La función del documento en la serialización](#_core_the_document.92.s_role_in_serialization)  
  
-   [Función de los datos en la serialización](#_core_the_data.92.s_role_in_serialization)  
  
-   [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a> La función del documento en la serialización  
 El marco de trabajo responde automáticamente al abrir del menú archivo, guardar y guardar como comandos mediante una llamada del documento `Serialize` función de miembro si se implementa. Un `ID_FILE_OPEN` comando, por ejemplo, llama a una función de controlador en el objeto application. Durante este proceso, el usuario ve y responde al cuadro de diálogo Abrir archivo y el marco de trabajo Obtiene el nombre de archivo que el usuario elige. El marco de trabajo crea un `CArchive` objeto configurado para cargar datos en el documento y pasa el archivo a `Serialize`. El marco de trabajo ya ha abierto el archivo. El código en el documento `Serialize` función miembro lee los datos de a través del archivo, reconstruir los objetos de datos según sea necesario. Para obtener más información acerca de la serialización, vea el artículo [serialización](../mfc/serialization-in-mfc.md).  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a> Función de los datos en la serialización  
 En general, los datos de tipo de clase deben ser capaz de serializar a sí mismo. Es decir, cuando se pasa un objeto en un archivo, el objeto debe saber cómo escribirse en el archivo de almacenamiento y cómo leerse desde el archivo. MFC proporciona compatibilidad para hacer que las clases serializables de esta manera. Si diseña una clase para definir un tipo de datos y se va a serializar los datos de ese tipo, el diseño para la serialización.  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

