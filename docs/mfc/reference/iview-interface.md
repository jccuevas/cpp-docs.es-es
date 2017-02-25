---
title: "IView Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IView class"
  - "views [MFC]"
  - "vistas, clases"
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# IView Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa varios métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utiliza para enviar las notificaciones de la vista a un control administrado.  
  
## Sintaxis  
  
```  
interface class IView  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IView::OnActivateView](../Topic/IView::OnActivateView.md)|Llamado por MFC cuando se activa o desactiva una vista.|  
|[IView::OnInitialUpdate](../Topic/IView::OnInitialUpdate.md)|Llamado por el marco después de que la vista primero se asocia al documento, pero antes de que la vista se muestra inicialmente.|  
|[IView::OnUpdate](../Topic/IView::OnUpdate.md)|Llamado por MFC después de que se haya modificado el documento de la vista; esta función permite que la vista actualice la pantalla para reflejar modificaciones.|  
  
## Comentarios  
 `IView` implementa varios métodos que `CWinFormsView` utilice para reenviar notificaciones de vista común a un control administrado hospedado.  éstos son [OnInitialUpdate](../Topic/IView::OnInitialUpdate.md), [OnUpdate](../Topic/IView::OnUpdate.md) y [OnActivateView](../Topic/IView::OnActivateView.md).  
  
 `IView` es similar a [CView](../../mfc/reference/cview-class.md), pero solo se utiliza con vistas administradas y controles.  
  
 Para obtener más información sobre cómo utilizar los formularios Windows Forms, vea [Utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## Requisitos  
 encabezado: afxwinforms.h \(definido en el atlmfc \\ biblioteca \\ mfcmifc80.dll de ensamblado\)  
  
## Vea también  
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)