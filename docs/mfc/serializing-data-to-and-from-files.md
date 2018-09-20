---
title: Serializar datos hacia y desde archivos | Microsoft Docs
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
ms.openlocfilehash: 65cf6d8944c1b14d6c55ce2c35a257bfa63a3606
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395393"
---
# <a name="serializing-data-to-and-from-files"></a>Serializar datos en y desde archivos

La idea básica de persistencia es que un objeto debe ser capaz de escribir su estado actual, indicado por los valores de sus variables miembro, en un almacenamiento persistente. Más adelante, el objeto se puede crear volver a lectura, o "deserialización", el estado del objeto desde el almacenamiento persistente. Un punto clave aquí es que el propio objeto es responsable de leer y escribir su propio estado. Por lo tanto, para que una clase sea persistente, debe implementar las operaciones de serialización básica.

El marco de trabajo proporciona una implementación predeterminada para guardar documentos en archivos de disco en respuesta a la operación de guardar y guardar como comandos en el menú archivo y para cargar documentos de archivos de disco en respuesta al comando Abrir. Con muy poco trabajo, puede implementar la capacidad de un documento para escribir y leer sus datos a y desde un archivo. Lo principal que debe hacer es invalidar el [Serialize](../mfc/reference/cobject-class.md#serialize) función miembro en la clase de documento.

MFC Application Wizard coloca una invalidación de esqueleto de la `CDocument` función miembro `Serialize` en la clase de documento que se crea para usted. Después de haber implementado las variables de miembro de la aplicación, puede rellenar el `Serialize` reemplazar con código que envía los datos a un "objeto de almacenamiento" conectado a un archivo. Un [CArchive](../mfc/reference/carchive-class.md) objeto es similar a la **cin** y **cout** entrada/salida de los objetos de la biblioteca iostream de C++. Sin embargo, `CArchive` escribe y lee en formato binario, no tener formato de texto.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Serialización](../mfc/serialization-in-mfc.md)

- [La función del documento en la serialización](#_core_the_document.92.s_role_in_serialization)

- [Función de los datos en la serialización](#_core_the_data.92.s_role_in_serialization)

- [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)

##  <a name="_core_the_document.92.s_role_in_serialization"></a> La función del documento en la serialización

El marco de trabajo responde automáticamente al abrir del menú archivo, guardar y guardar como comandos mediante una llamada del documento `Serialize` función de miembro si se implementa. Por ejemplo, un comando ID_FILE_OPEN llama una función de controlador en el objeto de aplicación. Durante este proceso, el usuario ve y responde al cuadro de diálogo Abrir archivo y el marco de trabajo Obtiene el usuario elige el nombre de archivo. El marco de trabajo crea un `CArchive` objeto configurado para cargar datos en el documento y pasa el archivo en `Serialize`. El marco de trabajo ya ha abierto el archivo. El código en el documento `Serialize` función miembro lee los datos a través de archivo, reconstruir los objetos de datos según sea necesario. Para obtener más información acerca de la serialización, vea el artículo [serialización](../mfc/serialization-in-mfc.md).

##  <a name="_core_the_data.92.s_role_in_serialization"></a> Función de los datos en la serialización

En general, los datos de tipo de clase deben ser capaz de serializar a sí mismo. Es decir, cuando se pasa un objeto a un archivo, el objeto debe conocer para escribirse en el archivo y cómo leerse desde el archivo. MFC proporciona compatibilidad para hacer que las clases serializables de esta manera. Si diseña una clase para definir un tipo de datos y se va a serializar los datos de ese tipo, el diseño para la serialización.

## <a name="see-also"></a>Vea también

[Uso de documentos](../mfc/using-documents.md)

