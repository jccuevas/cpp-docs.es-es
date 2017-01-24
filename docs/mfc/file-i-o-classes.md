---
title: "Clases de E/S de archivos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de archivo de disco"
  - "clases de archivos E/S [C++]"
  - "E/S [C++], clases MFC"
  - "E/S [MFC], clases"
  - "clases de archivos de memoria"
  - "secuencias OLE"
  - "clases de sockets"
  - "stdio (clases)"
  - "stream (clases)"
  - "clases traducidas stream"
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de E/S de archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases proporcionan una interfaz a los archivos de disco tradicionales, los archivos de en\- memoria, las secuencias activo, y Windows Sockets.  Todas las clases derivadas de `CFile` se pueden utilizar con un objeto de `CArchive` para realizar la serialización.  
  
 Utilice las clases siguientes, especialmente `CArchive` y `CFile`, si escribe posee el procesamiento de entrada\/salida.  Normalmente no necesita derivar de estas clases.  Si utiliza el marco de aplicación, las implementaciones predeterminadas de los comandos de **Abierta** y de **Guardar** en el menú de **archivo** administrarán E\/S de archivo \(mediante la clase `CArchive`\), siempre que se reemplace la función de `Serialize` de documentos para proporcionar los detalles sobre cómo un documento serializa su contenido.  Para obtener más información sobre las clases y la serialización de archivo, vea el artículo [Archivos en MFC](../mfc/files-in-mfc.md) y el caso [Serialización](../mfc/serialization-in-mfc.md).  
  
 [Archivo C](../mfc/reference/cfile-class.md)  
 Proporciona una interfaz a los archivos de disco binarios.  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 Proporciona una interfaz de `CFile` a los archivos de disco almacenado en búfer de la secuencia, normalmente en modo de texto.  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 Proporciona una interfaz de `CFile` a los archivos de en\-memoria.  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 Proporciona una interfaz de `CFile` a archivos compartidos de en\- memoria.  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Utiliza la interfaz COM de `IStream` para proporcionar acceso de `CFile` a archivos compuestos.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 Proporciona una interfaz de `CFile` a un socket de Windows.  
  
## Clases relacionadas  
 [CArchive](../mfc/reference/carchive-class.md)  
 Coopera con un objeto de `CFile` el almacenamiento persistente de implementan para los objetos con la serialización \(vea [CObject::Serialize](../Topic/CObject::Serialize.md)\).  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Una excepción del archivo.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Una excepción orientada al archivo.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Proporciona un cuadro de diálogo estándar para abrir o guardar un archivo.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Mantiene la lista de archivos usados recientemente utilizada de \(MRU\).  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)