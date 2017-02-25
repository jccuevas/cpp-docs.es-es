---
title: "CMFCWindowsManagerDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCWindowsManagerDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCWindowsManagerDialog class"
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CMFCWindowsManagerDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El objeto de `CMFCWindowsManagerDialog` permite a un usuario para administrar las ventanas MDI secundarias en una aplicación MDI.  
  
## Sintaxis  
  
```  
class CMFCWindowsManagerDialog : public CDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](../Topic/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog.md)|Crea un objeto `CMFCWindowsManagerDialog`.|  
  
## Comentarios  
 `CMFCWindowsManagerDialog` contiene una lista de ventanas secundarias MDI que estén abiertos en la aplicación.  El usuario puede controlar manualmente el estado de las ventanas MDI secundarias mediante este cuadro de diálogo.  
  
 `CMFCWindowsManagerDialog` se incrusta dentro de [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md).  `CMFCWindowsManagerDialog` no es una clase que debe crear manualmente.  En su lugar, llame a la función [CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md), y creará y mostrará un objeto de `CMFCWindowsManagerDialog` .  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCWindowsManagerDialog` llamando a `CMDIFrameWndEx::ShowWindowsDialog`.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/CPP/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## Requisitos  
 **encabezado:** afxWindowsManagerDialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md)   
 [CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)