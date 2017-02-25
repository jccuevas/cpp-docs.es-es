---
title: "C&#243;mo: Cargar un recurso de cinta desde una aplicaci&#243;n MFC | Microsoft Docs"
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
  - "recurso de cinta, cargar"
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# C&#243;mo: Cargar un recurso de cinta desde una aplicaci&#243;n MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para utilizar el recurso de la cinta de opciones en la aplicación, modifique la aplicación para cargar el recurso de la cinta de opciones.  
  
### Para cargar un recurso de la cinta de opciones  
  
1.  Declare el objeto de `Ribbon Control` en la clase de `CMainFrame` .  
  
    ```  
    CMFCRibbonBar m_wndRibbonBar;   
    ```  
  
2.  En `CMainFrame::OnCreate`, cree e inicialice el Control ribbon.  
  
    ```  
    if (!m_wndRibbonBar.Create (this))  
    {  
        return -1;  
    }  
  
    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))  
    {  
        return -1;  
    }  
    ```  
  
## Vea también  
 [Diseñador de la cinta de opciones \(MFC\)](../mfc/ribbon-designer-mfc.md)