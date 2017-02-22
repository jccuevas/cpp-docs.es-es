---
title: "Usar documentos | Microsoft Docs"
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
  - "datos [MFC], documentos"
  - "datos [MFC], leer"
  - "arquitectura documento/vista [C++], documentos"
  - "documentos [C++]"
  - "documentos [C++], aplicaciones de C++"
  - "archivos [C++]"
  - "archivos [C++], escribir"
  - "imprimir [MFC], documentos"
  - "leer datos [C++], documentos y vistas"
  - "vistas [C++], aplicaciones de C++"
  - "escribir en archivos [C++]"
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Usar documentos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Funcionando juntos, documentos y vistas:  
  
-   Contiene, administrar, y mostrar [datos](../mfc/managing-data-with-document-data-variables.md)específico de la aplicación.  
  
-   Proporciona una interfaz [variables de datos del documento](../mfc/managing-data-with-document-data-variables.md) formado por para manipular los datos.  
  
-   Participe en [archivos de escritura y lectura](../mfc/serializing-data-to-and-from-files.md).  
  
-   Participe en [el imprimir](../mfc/role-of-the-view-in-printing.md).  
  
-   [Identificador](../mfc/handling-commands-in-the-document.md) la mayoría de los comandos y los mensajes de la aplicación.  
  
 El documento está implicado determinado de administrar datos.  Almacena los datos, normalmente, en variables miembro de clase del documento.  Vista utiliza estas variables para tener acceso a los datos para la presentación y la actualización.  El mecanismo de serialización predeterminado de documento administra la lectura y la escritura de los datos a y desde los archivos.  Los documentos también pueden controlar los comandos \(pero no los mensajes de Windows distintas de **WM\_COMMAND**\).  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Derivar de una clase de CDocument](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [Administrar datos con variables de datos del documento](../mfc/managing-data-with-document-data-variables.md)  
  
-   [Serialización de datos a y desde los archivos](../mfc/serializing-data-to-and-from-files.md)  
  
-   [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [Control de comandos en el documento](../mfc/handling-commands-in-the-document.md)  
  
-   [La función miembro de OnNewDocument](../Topic/CDocument::OnNewDocument.md)  
  
-   [La función miembro de DeleteContents](../Topic/CDocument::DeleteContents.md)  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)