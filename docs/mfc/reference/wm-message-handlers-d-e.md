---
title: "Controladores de mensajes WM_: D - E | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_ERASEBKGND"
  - "ON_WM_DEVICECHANGE"
  - "ON_WM_ENTERIDLE"
  - "ON_WM_DESTROYCLIPBOARD"
  - "ON_WM_DESTROY"
  - "ON_WM_DEADCHAR"
  - "ON_WM_DELETEITEM"
  - "ON_WM_DROPFILES"
  - "ON_WM_DEVMODECHANGE"
  - "ON_WM_ENDSESSION"
  - "ON_WM_ENABLE"
  - "ON_WM_DRAWITEM"
  - "ON_WM_DRAWCLIPBOARD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_DEADCHAR"
  - "ON_WM_DELETEITEM"
  - "ON_WM_DESTROY"
  - "ON_WM_DESTROYCLIPBOARD"
  - "ON_WM_DEVICECHANGE"
  - "ON_WM_DEVMODECHANGE"
  - "ON_WM_DRAWCLIPBOARD"
  - "ON_WM_DRAWITEM"
  - "ON_WM_DROPFILES"
  - "ON_WM_ENABLE"
  - "ON_WM_ENDSESSION"
  - "ON_WM_ENTERIDLE"
  - "ON_WM_ERASEBKGND"
  - "WM_ messages"
ms.assetid: 56fb89c8-68a8-4adf-883e-a9f63bf677e9
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Controladores de mensajes WM_: D - E
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las entradas de mapa siguiente a la izquierda corresponden a los prototipos de función a la derecha:  
  
|Entrada de asignación|Prototipo de función|  
|---------------------------|--------------------------|  
|ON\_WM\_DEADCHAR\(\)|afx\_msg [OnDeadChar](../Topic/CWnd::OnDeadChar.md)vacío \(UINT, UINT, UINT\);|  
|ON\_WM\_DELETEITEM\(\)|afx\_msg [OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)vacío \(LPDELETEITEMSTRUCT\);|  
|ON\_WM\_DESTROY\(\)|afx\_msg [OnDestroy](../Topic/CWnd::OnDestroy.md)vacío \(\);|  
|ON\_WM\_DESTROYCLIPBOARD\(\)|afx\_msg [OnDestroyClipboard](../Topic/CWnd::OnDestroyClipboard.md)vacío \(\);|  
|ON\_WM\_DEVICECHANGE\(\)|afx\_msg [OnDeviceChange](../Topic/CWnd::OnDeviceChange.md)vacío \(UINT, DWORD\);|  
|ON\_WM\_DEVMODECHANGE\(\)|afx\_msg [OnDevModeChange](../Topic/CWnd::OnDevModeChange.md)vacío \(LPSTR\);|  
|ON\_WM\_DRAWCLIPBOARD\(\)|afx\_msg [OnDrawClipboard](../Topic/CWnd::OnDrawClipboard.md)vacío \(\);|  
|ON\_WM\_DRAWITEM\(\)|afx\_msg [OnDrawItem](../Topic/CWnd::OnDrawItem.md)vacío \(LPDRAWITEMSTRUCT\);|  
|ON\_WM\_DROPFILES\(\)|afx\_msg [OnDropFiles](../Topic/CWnd::OnDropFiles.md)vacío \(HDROP\);|  
|ON\_WM\_DWMCOLORIZATIONCOLORCHANGED\(\)|afx\_msg [OnColorizationColorChanged](../Topic/CWnd::OnColorizationColorChanged.md)vacío \(DWORD, BOOL\);|  
|ON\_WM\_DWMCOMPOSITIONCHANGED\(\)|afx\_msg [OnCompositionChanged](../Topic/CWnd::OnCompositionChanged.md)vacío \(\);|  
|ON\_WM\_DWMNCRENDERINGCHANGED\(\)|afx\_msg [OnNcRenderingChanged](../Topic/CWnd::OnNcRenderingChanged.md)vacío \(BOOL\);|  
|ON\_WM\_DWMWINDOWMAXIMIZEDCHANGE\(\)|afx\_msg [OnWindowMaximizedChanged](../Topic/CWnd::OnWindowMaximizedChanged.md)vacío \(BOOL\);|  
|ON\_WM\_ENABLE\(\)|afx\_msg [OnEnable](../Topic/CWnd::OnEnable.md)vacío \(BOOL\);|  
|ON\_WM\_ENDSESSION\(\)|afx\_msg [OnEndSession](../Topic/CWnd::OnEndSession.md)vacío \(BOOL\);|  
|ON\_WM\_ENTERIDLE\(\)|afx\_msg [OnEnterIdle](../Topic/CWnd::OnEnterIdle.md)vacío \(UINT, CWnd\*\);|  
|ON\_WM\_ENTERSIZEMOVE\(\)|afx\_msg [OnEnterSizeMove](../Topic/CWnd::OnEnterSizeMove.md)vacío \(\);|  
|ON\_WM\_ERASEBKGND\(\)|afx\_msg BOOL [OnEraseBkgnd](../Topic/CWnd::OnEraseBkgnd.md)\(CDC\*\);|  
|ON\_WM\_EXITSIZEMOVE\(\)|afx\_msg [OnExitSizeMove](../Topic/CWnd::OnExitSizeMove.md)vacío \(\);|  
  
## Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)   
 [Controladores de mensajes WM\_](../../mfc/reference/handlers-for-wm-messages.md)