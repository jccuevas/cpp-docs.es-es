---
title: "Using the RichEdit 1.0 Control with MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "RichEdit 1.0 control"
  - "rich edit controls, RichEdit 1.0"
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using the RichEdit 1.0 Control with MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para utilizar un control RichEdit, se debe llamar primero a [AfxInitRichEdit2](../Topic/AfxInitRichEdit2.md) para cargar el control RichEdit 2.0 \(RICHED20.DLL\), o bien llamar a [AfxInitRichEdit](../Topic/AfxInitRichEdit.md) para cargar el control RichEdit 1.0 anterior \(RICHED32.DLL\).  
  
 La clase [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) actual puede utilizarse con el control RichEdit 1.0 anterior, pero sólo está diseñada para el control RichEdit 2.0.  Dado que RichEdit 1.0 y RichEdit 2.0 son muy similares, la mayoría de los métodos funcionarán correctamente; no obstante, debe tenerse en cuenta que existen algunas diferencias entre los controles 1.0 y 2.0, por lo tanto, algunos métodos podrían no funcionar o hacerlo incorrectamente.  
  
## Requisitos  
 MFC  
  
## Vea también  
 [Troubleshooting the Dialog Editor](../mfc/troubleshooting-the-dialog-editor.md)   
 [Dialog Editor](../mfc/dialog-editor.md)