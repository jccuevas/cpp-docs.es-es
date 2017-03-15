---
title: "Mensajes WM_: T - Z | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_TCARD"
  - "ON_WM_WININICHANGE"
  - "ON_WM_VSCROLLCLIPBOARD"
  - "ON_WM_VSCROLL"
  - "ON_WM_WINDOWPOSCHANGED"
  - "ON_WM_TIMECHANGE"
  - "ON_WM_TIMER"
  - "ON_WM_VKEYTOITEM"
  - "ON_WM_WINDOWPOSCHANGING"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_TCARD"
  - "ON_WM_TIMECHANGE"
  - "ON_WM_TIMER"
  - "ON_WM_VKEYTOITEM"
  - "ON_WM_VSCROLL"
  - "ON_WM_VSCROLLCLIPBOARD"
  - "ON_WM_WINDOWPOSCHANGED"
  - "ON_WM_WINDOWPOSCHANGING"
  - "ON_WM_WININICHANGE"
  - "WM_ messages"
ms.assetid: c528bb2e-ddb5-4da6-b652-432a387408b8
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Mensajes WM_: T - Z
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las entradas de mapa siguiente corresponden a los prototipos de función:  
  
|Entrada de asignación|Prototipo de función|  
|---------------------------|--------------------------|  
|ON\_WM\_TCARD\(\)|afx\_msg [OnTCard](../Topic/CWnd::OnTCard.md)vacío \(UINT, DWORD\);|  
|ON\_WM\_TIMECHANGE\(\)|afx\_msg [OnTimeChange](../Topic/CWnd::OnTimeChange.md)vacío \(\);|  
|ON\_WM\_TIMER\(\)|afx\_msg [OnTimer](../Topic/CWnd::OnTimer.md)vacío \(UINT\_PTR\);|  
|ON\_WM\_UNICHAR\(\)|afx\_msg [OnUniChar](../Topic/CWnd::OnUniChar.md)vacío \(UINT, UINT, UINT\);|  
|ON\_WM\_UNINITMENUPOPUP\(\)|afx\_msg [OnUnInitMenuPopup](../Topic/CWnd::OnUnInitMenuPopup.md)vacío \(CMenu\*, UINT\);|  
|ON\_WM\_USERCHANGED\(\)|afx\_msg [OnUserChanged](../Topic/CWnd::OnUserChanged.md)vacío \(\);|  
|ON\_WM\_VKEYTOITEM\(\)|afx\_msg int [OnVKeyToItem](../Topic/CWnd::OnVKeyToItem.md)\(UINT, CWnd\*, UINT\);|  
|ON\_WM\_VSCROLL\(\)|afx\_msg [OnVScroll](../Topic/CWnd::OnVScroll.md)vacío \(UINT, UINT, CWnd\*\);|  
|ON\_WM\_VSCROLLCLIPBOARD\(\)|afx\_msg [OnVScrollClipboard](../Topic/CWnd::OnVScrollClipboard.md)vacío \(CWnd\*, UINT, UINT\);|  
|ON\_WM\_WINDOWPOSCHANGED\(\)|afx\_msg [OnWindowPosChanged](../Topic/CWnd::OnWindowPosChanged.md)vacío \(WINDOWPOS\*\);|  
|ON\_WM\_WINDOWPOSCHANGING\(\)|afx\_msg [OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)vacío \(WINDOWPOS\*\);|  
|ON\_WM\_WININICHANGE\(\)|afx\_msg [OnWinIniChange](../Topic/CWnd::OnWinIniChange.md)vacío \(LPSTR\);|  
|ON\_WM\_WTSSESSION\_CHANGE\(\)|afx\_msg [OnSessionChange](../Topic/CWnd::OnSessionChange.md)vacío \(UINT, UINT\);|  
|ON\_WM\_XBUTTONDBLCLK\(\)|afx\_msg [OnXButtonDblClk](../Topic/CWnd::OnXButtonDblClk.md)vacío \(UINT, UINT, CPoint\);|  
|ON\_WM\_XBUTTONDOWN\(\)|afx\_msg [OnXButtonDown](../Topic/CWnd::OnXButtonDown.md)vacío \(UINT, UINT, CPoint\);|  
|ON\_WM\_XBUTTONUP\(\)|afx\_msg [OnXButtonUp](../Topic/CWnd::OnXButtonUp.md)vacío \(UINT, UINT, CPoint\);|  
  
## Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)   
 [Controladores de mensajes WM\_](../../mfc/reference/handlers-for-wm-messages.md)