---
title: "Mapping Windows Messages to Your (Clase) | Microsoft Docs"
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
  - "asignaciones, mensajes a clases del cuadro de diálogo"
  - "mapas de mensajes [C++], en clases del cuadro de diálogo"
  - "mapas de mensajes [C++], asignar mensajes de Windows a clases"
  - "mensajes a clases del cuadro de diálogo"
  - "mensajes a clases del cuadro de diálogo, asignar"
  - "cuadros de diálogo de MFC, mensajes de Windows"
  - "mensajes de Windows [C++], asignar en clases del cuadro de diálogo"
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Mapping Windows Messages to Your (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si necesita el cuadro de diálogo administrar mensajes de Windows, reemplazar las funciones adecuadas de controlador.  Para ello, utilice la ventana Propiedades a [asigne los mensajes](../mfc/reference/mapping-messages-to-functions.md) a la clase de diálogo.  Se escribe una entrada de mensaje\- mapa para cada mensaje y agrega las funciones miembro de controladores de mensajes a la clase.  Utilice el editor de código fuente de Visual C\+\+ para escribir código en los controladores de mensajes.  
  
 También puede reemplazar funciones miembro de [CDialog](../mfc/reference/cdialog-class.md) y sus clases base, especialmente [CWnd](../mfc/reference/cwnd-class.md).  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Control de mensajes y asignación](../mfc/message-handling-and-mapping.md)  
  
-   [Funciones normalmente invalidadas miembro](../mfc/commonly-overridden-member-functions.md)  
  
-   [Funciones normalmente agregadas de miembro](../mfc/commonly-added-member-functions.md)  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)