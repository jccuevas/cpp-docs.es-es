---
title: "CPaneDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaneDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneDialog class"
  - "CPaneDialog constructor"
  - "CPaneDialog::CreateObject method"
  - "CPaneDialog::OnEraseBkgnd method"
  - "CPaneDialog::OnLButtonDblClk method"
  - "CPaneDialog::OnLButtonDown method"
  - "CPaneDialog::OnUpdateCmdUI method"
  - "CPaneDialog::OnWindowPosChanging method"
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CPaneDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CPaneDialog` admite un cuadro de diálogo no modal, acoplables.  
  
## Sintaxis  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CPaneDialog::CPaneDialog`|Constructor predeterminado.|  
|`CPaneDialog::~CPaneDialog`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneDialog::Create](../Topic/CPaneDialog::Create.md)|Crea un cuadro de diálogo acoplable y lo asocia a un objeto de `CPaneDialog` .|  
|`CPaneDialog::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CPaneDialog::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CPaneDialog::HandleInitDialog](../Topic/CPaneDialog::HandleInitDialog.md)|Controla el mensaje de [WM\_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) .  \(Vuelve a definir `CBasePane::HandleInitDialog`.\)|  
|`CPaneDialog::OnEraseBkgnd`|Controlan el mensaje de [WM\_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) .  \(Vuelve a definir [CWnd::OnEraseBkgnd](../Topic/CWnd::OnEraseBkgnd.md).\)|  
|`CPaneDialog::OnLButtonDblClk`|Controlan el mensaje de [WM\_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) .  \(Vuelve a definir [CWnd::OnLButtonDblClk](../Topic/CWnd::OnLButtonDblClk.md).\)|  
|`CPaneDialog::OnLButtonDown`|Controlan el mensaje de [WM\_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607) .  \(Vuelve a definir [CWnd::OnLButtonDown](../Topic/CWnd::OnLButtonDown.md).\)|  
|`CPaneDialog::OnUpdateCmdUI`|Llamado por el marco para actualizar la ventana del cuadro de diálogo.  \(Reemplaza [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/es-es/5dd61606-1c12-40d4-b024-f3839aa5e2e0).\)|  
|`CPaneDialog::OnWindowPosChanging`|Controla el mensaje de [WM\_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653) .  \(Vuelve a definir [CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md).\)|  
|[CPaneDialog::SetOccDialogInfo](../Topic/CPaneDialog::SetOccDialogInfo.md)|Especifica la plantilla para un cuadro de diálogo que es un contenedor de controles activex.|  
  
## Comentarios  
 Crea un objeto de `CPaneDialog` en dos pasos.  Primero, cree el objeto en el código.  En segundo lugar, llamada [CPaneDialog::Create](../Topic/CPaneDialog::Create.md).  Debe especificar id. de recurso de un nombre válido de la plantilla o de plantilla y pasar un puntero a la ventana primaria.  Si no, se produce un error del proceso de creación.  El cuadro de diálogo debe especificar el estilo WS\_CHILD y de WS\_VISIBLE.  Se recomienda también especifica los estilos de WS\_CLIPCHILDREN y de WS\_CLIPSIBLINGS.  Para obtener más información, vea [Estilos de ventana](../../mfc/reference/window-styles.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## Requisitos  
 **encabezado:** afxpanedialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [Estilos de ventana](../../mfc/reference/window-styles.md)