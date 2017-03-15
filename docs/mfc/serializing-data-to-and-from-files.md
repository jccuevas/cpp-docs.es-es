---
title: "Serializar datos en y desde archivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "datos [MFC]"
  - "datos [MFC], serializar"
  - "deserialización [C++]"
  - "datos del documento [C++]"
  - "documentos [C++], guardar"
  - "documentos [C++], serialización"
  - "guardar documentos"
  - "serialización [C++], rol de datos"
  - "serialización [C++], rol de documento"
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Serializar datos en y desde archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La idea básica de persistencia es de que un objeto puede escribir su estado actual, indicado por los valores de las variables miembro, el almacenamiento persistente.  Después, el objeto puede reconstruirla leyendo, o “deserializar,” estado de objeto de almacenamiento persistente.  Un punto clave aquí es que el propio objeto es responsable de leer y escribir su propio estado.  Por tanto, para que una clase sea persistente, debe implementar las operaciones básicas de serialización.  
  
 El marco de trabajo proporciona una implementación predeterminada para guardar documentos en los archivos de disco en respuesta al Guardar y a Guardar mientras los comandos del menú archivo y cargar documentan desde el disco los archivos en respuesta al comando abierto.  Con muy poco trabajo, puede implementar la capacidad de un documento para escribir y leer los datos en un archivo.  El elemento principal que debe hacer es reemplazar la función miembro de [Serialice](../Topic/CObject::Serialize.md) en la clase del documento.  
  
 El asistente para aplicaciones MFC coloca un reemplazo básica de la función `Serialize` miembro de **CDocument** en la clase de documento que crea automáticamente.  Después de haber implementado a las variables miembro de la aplicación, puede completar la invalidación de `Serialize` con código que envía los datos a un objeto “archivo” conectado a un archivo.  Un objeto de [CArchive](../mfc/reference/carchive-class.md) es similar a los objetos de entrada y salida de `cin` y de `cout` de biblioteca iostream de C\+\+.  Sin embargo, `CArchive` escribe y lee el formato binario, no texto con formato.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Serialización](../mfc/serialization-in-mfc.md)  
  
-   [El rol del documento en la serialización](#_core_the_document.92.s_role_in_serialization)  
  
-   [El rol de los datos de la serialización](#_core_the_data.92.s_role_in_serialization)  
  
-   [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)  
  
##  <a name="_core_the_document.92.s_role_in_serialization"></a> El rol del documento en Serialización  
 El marco responde automáticamente al Abrir, a Guardar, y a Guardar desde el menú archivo mientras los comandos llamando a la función miembro de `Serialize` de documento si se implementa.  Un comando de `ID_FILE_OPEN` , por ejemplo, llama a una función de controlador en el objeto application.  Durante este proceso, el usuario ve y responde al cuadro de diálogo Abrir archivo y el marco obtiene el nombre de archivo que el usuario elija.  El marco de trabajo crea una configuración de objeto de `CArchive` para cargar datos en el documento y pasa el archivo a `Serialize`.  El marco ha abierto el archivo.  El código de la función miembro de `Serialize` de documento lee los datos de a través del archivo, reconstruyendo objetos de datos según sea necesario.  Para obtener más información sobre serialización, vea el artículo [Serialización](../mfc/serialization-in-mfc.md).  
  
##  <a name="_core_the_data.92.s_role_in_serialization"></a> El rol de Data en Serialización  
 Normalmente los datos de tipo de clase deben poder serializarse.  Es decir, cuando se pasa un objeto en un archivo, el objeto debe saber cómo escribirse en el archivo y leerse del archivo.  MFC proporciona compatibilidad para crear clases serializables de esta manera.  Si diseña una clase para definir un tipo de datos y desea serializar datos de ese tipo, diseñe para la serialización.  
  
## Vea también  
 [Usar documentos](../mfc/using-documents.md)