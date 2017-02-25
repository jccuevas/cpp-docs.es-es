---
title: "Controladores de mensajes WM_: A - C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_CREATE"
  - "ON_WM_COMPACTING"
  - "ON_WM_CHARTOITEM"
  - "ON_WM_ASKCBFORMATNAME"
  - "ON_WM_CTLCOLOR"
  - "ON_WM_COMPAREITEM"
  - "ON_WM_CHILDACTIVATE"
  - "ON_WM_CONTEXTMENU"
  - "ON_WM_ACTIVATE"
  - "ON_WM_CANCELMODE"
  - "ON_WM_CLOSE"
  - "ON_WM_CAPTURECHANGED"
  - "ON_WM_ACTIVATEAPP"
  - "ON_WM_CHAR"
  - "ON_WM_CHANGECBCHAIN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_ACTIVATE"
  - "ON_WM_ACTIVATEAPP"
  - "ON_WM_ASKCBFORMATNAME"
  - "ON_WM_CANCELMODE"
  - "ON_WM_CAPTURECHANGED"
  - "ON_WM_CHANGECBCHAIN"
  - "ON_WM_CHAR"
  - "ON_WM_CHARTOITEM"
  - "ON_WM_CHILDACTIVATE"
  - "ON_WM_CLOSE"
  - "ON_WM_COMPACTING"
  - "ON_WM_COMPAREITEM"
  - "ON_WM_CONTEXTMENU"
  - "ON_WM_CREATE"
  - "ON_WM_CTLCOLOR"
  - "WM_ messages"
ms.assetid: 4e315896-d646-4b87-b0ab-41a4a753b045
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Controladores de mensajes WM_: A - C
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las entradas de mapa siguiente a la izquierda corresponden a los prototipos de función a la derecha:  
  
|Entrada de asignación|Prototipo de función|  
|---------------------------|--------------------------|  
|ON\_WM\_ACTIVATE\(\)|afx\_msg [OnActivate](../Topic/CWnd::OnActivate.md)vacío \(UINT, CWnd\*, BOOL\);|  
|ON\_WM\_ACTIVATEAPP\(\)|afx\_msg [OnActivateApp](../Topic/CWnd::OnActivateApp.md)vacío \(BOOL, DWORD\);|  
|ON\_WM\_APPCOMMAND\(\)|afx\_msg [OnAppCommand](../Topic/CWnd::OnAppCommand.md)vacío \(CWnd\*, UINT, UINT, UINT\);|  
|ON\_WM\_ASKCBFORMATNAME\(\)|afx\_msg [OnAskCbFormatName](../Topic/CWnd::OnAskCbFormatName.md)vacío \(UINT, LPSTR\);|  
|ON\_WM\_CANCELMODE\(\)|afx\_msg [OnCancelMode](../Topic/CWnd::OnCancelMode.md)vacío \(\);|  
|ON\_WM\_CAPTURECHANGED\(\)|afx\_msg [OnCaptureChanged](../Topic/CWnd::OnCaptureChanged.md)vacío \(CWnd\*\);|  
|ON\_WM\_CHANGECBCHAIN\(\)|afx\_msg [OnChangeCbChain](../Topic/CWnd::OnChangeCbChain.md)vacío \(HWND, HWND\);|  
|ON\_WM\_CHAR\(\)|afx\_msg [OnChar](../Topic/CWnd::OnChar.md)vacío \(UINT, UINT, UINT\);|  
|ON\_WM\_CHARTOITEM\(\)|afx\_msg int [OnCharToItem](../Topic/CWnd::OnCharToItem.md)\(UINT, CWnd\*, UINT\);|  
|ON\_WM\_CHILDACTIVATE\(\)|afx\_msg [OnChildActivate](../Topic/CWnd::OnChildActivate.md)vacío \(\);|  
|ON\_WM\_CLIPBOARDUPDATE\(\)|afx\_msg [OnClipboardUpdate](../Topic/CWnd::OnClipboardUpdate.md)vacío \(\);|  
|ON\_WM\_CLOSE\(\)|afx\_msg [OnClose](../Topic/CWnd::OnClose.md)vacío \(\);|  
|ON\_WM\_COMPACTING\(\)|afx\_msg [OnCompacting](../Topic/CWnd::OnCompacting.md)vacío \(UINT\);|  
|ON\_WM\_COMPAREITEM\(\)|afx\_msg int [OnCompareItem](../Topic/CWnd::OnCompareItem.md)\(LPCOMPAREITEMSTRUCT\);|  
|ON\_WM\_CONTEXTMENU\(\)|afx\_msg [OnContextMenu](../Topic/CWnd::OnContextMenu.md)vacío \(CWnd\*, CPoint\);|  
|ON\_WM\_COPYDATA\(\)|afx\_msg BOOL [OnCopyData](../Topic/CWnd::OnCopyData.md)\(pWnd de CWnd\*, pCopyDataStruct de COPYDATASTRUCT\*\);|  
|ON\_WM\_CREATE\(\)|afx\_msg int [OnCreate](../Topic/CWnd::OnCreate.md)\(LPCREATESTRUCT\);|  
|ON\_WM\_CTLCOLOR\(\)|afx\_msg HBRUSH [OnCtlColor](../Topic/CWnd::OnCtlColor.md)\(CDC\*, CWnd\*, UINT\);|  
  
## Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)   
 [Controladores de mensajes WM\_](../../mfc/reference/handlers-for-wm-messages.md)