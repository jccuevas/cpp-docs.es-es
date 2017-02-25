---
title: "Omitir el mecanismo de serializaci&#243;n | Microsoft Docs"
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
  - "objetos de archivo [C++]"
  - "archivos [C++]"
  - "archivos [C++], serialización"
  - "excluir serialización"
  - "serialización [C++], omitir"
  - "serialización [C++], reemplazar"
  - "serialización [C++], rol de marco de trabajo"
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Omitir el mecanismo de serializaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como se ha mencionado anteriormente, el marco de trabajo proporciona una manera predeterminada a leer y escribir datos a y desde los archivos.  La de serialización a través de un objeto de archivo satisface las necesidades de grandes muchas aplicaciones.  Una aplicación lee un archivo completamente en memoria, permite al usuario actualizar el archivo, y escribe la versión actualizada en el disco de nuevo.  
  
 Sin embargo, algunas aplicaciones de datos muy de manera diferente, y para estas aplicaciones la serialización a través de un archivo no es adecuado.  Programas de base de datos de los ejemplos se incluyen, programas que editan únicamente las partes de archivos grandes, los programas que escriben los archivos de solo texto, y los programas que comparten los archivos de datos.  
  
 En estos casos, puede reemplazar la función de [Serialice](../Topic/CObject::Serialize.md) de una manera diferente para mediar acciones a través de un objeto de [Archivo C](../mfc/reference/cfile-class.md) en lugar de un objeto de [CArchive](../mfc/reference/carchive-class.md) .  
  
 Puede utilizar **Abierta**, **de lectura**, **Escribir**, **cerrar**, y funciones miembro de `Seek` de la clase `CFile` para abrir un archivo, mueva el puntero de archivo \(búsqueda\) a un punto concreto en el archivo, lee un registro \(un número de bytes especificado\) en ese momento, permitir que el usuario actualizar el registro, la búsqueda al mismo punto de nuevo y escribir el registro al archivo.  El marco abrirá el archivo para usted, y utilizar la función miembro de `GetFile` de la clase `CArchive` para obtener un puntero al objeto de `CFile` .  Para el uso aún más complejo y flexible, puede reemplazar las funciones miembro de [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) y de [OnSaveDocument](../Topic/CDocument::OnSaveDocument.md) de la clase `CWinApp`.  Para obtener más información, vea la clase [Archivo C](../mfc/reference/cfile-class.md) en *la referencia de MFC*.  
  
 En este escenario, la invalidación de `Serialize` no hace nada, a menos que, por ejemplo, desea ejecutarlo leer y escribir un encabezado de archivo para mantenerla actualizada en que se cierra el documento.  
  
## Vea también  
 [Usar documentos](../mfc/using-documents.md)