---
title: "WM_ Messages: S | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_SYSDEADCHAR"
  - "ON_WM_SYSKEYDOWN"
  - "ON_WM_STYLECHANGING"
  - "ON_WM_STYLECHANGED"
  - "ON_WM_SPOOLERSTATUS"
  - "ON_WM_SYSCHAR"
  - "ON_WM_SETFOCUS"
  - "ON_WM_SIZE"
  - "ON_WM_SIZING"
  - "ON_WM_SETCURSOR"
  - "ON_WM_SYSCOMMAND"
  - "ON_WM_SETTINGCHANGE"
  - "ON_WM_SHOWWINDOW"
  - "ON_WM_SYSKEYUP"
  - "ON_WM_SIZECLIPBOARD"
  - "ON_WM_SYSCOLORCHANGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_SETCURSOR"
  - "ON_WM_SETFOCUS"
  - "ON_WM_SETTINGCHANGE"
  - "ON_WM_SHOWWINDOW"
  - "ON_WM_SIZE"
  - "ON_WM_SIZECLIPBOARD"
  - "ON_WM_SIZING"
  - "ON_WM_SPOOLERSTATUS"
  - "ON_WM_STYLECHANGED"
  - "ON_WM_STYLECHANGING"
  - "ON_WM_SYSCHAR"
  - "ON_WM_SYSCOLORCHANGE"
  - "ON_WM_SYSCOMMAND"
  - "ON_WM_SYSDEADCHAR"
  - "ON_WM_SYSKEYDOWN"
  - "ON_WM_SYSKEYUP"
  - "WM_ messages"
ms.assetid: 4b9aec79-a98f-4aa0-a3d9-110941b6dcbc
caps.latest.revision: 14
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WM_ Messages: S
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las entradas de mapa siguiente corresponden a los prototipos de función.  
  
|Entrada de asignación|Prototipo de función|  
|---------------------------|--------------------------|  
|ON\_WM\_SETCURSOR \(\)|afx\_msg BOOL [OnSetCursor](../Topic/CWnd::OnSetCursor.md)\(CWnd\*, UINT, UINT\);|  
|ON\_WM\_SETFOCUS \(\)|afx\_msg [OnSetFocus](../Topic/CWnd::OnSetFocus.md)vacío \(CWnd\*\);|  
|ON\_WM\_SETTINGCHANGE \(\)|afx\_msg [OnSettingChange](../Topic/CWnd::OnSettingChange.md)vacío \(uFlags de UINT, lpszSection de LPCTSTR\);|  
|ON\_WM\_SHOWWINDOW \(\)|afx\_msg [OnShowWindow](../Topic/CWnd::OnShowWindow.md)vacío \(BOOL, UINT\);|  
|ON\_WM\_SIZE \(\)|afx\_msg [OnSize](../Topic/CWnd::OnSize.md)vacío \(UINT, int, int\);|  
|ON\_WM\_SIZECLIPBOARD \(\)|afx\_msg [OnSizeClipboard](../Topic/CWnd::OnSizeClipboard.md)vacío \(CWnd\*, IDENTIFIER\);|  
|ON\_WM\_SIZING \(\)|afx\_msg [OnSizing](../Topic/CWnd::OnSizing.md)vacío \(UINT, LPRECT\);|  
|ON\_WM\_SPOOLERSTATUS \(\)|afx\_msg [OnSpoolerStatus](../Topic/CWnd::OnSpoolerStatus.md)vacío \(UINT, UINT\);|  
|ON\_WM\_STYLECHANGED \(\)|afx\_msg [OnStyleChanged](../Topic/CWnd::OnStyleChanged.md)vacío \(int, LPSTYLESTRUCT\);|  
|ON\_WM\_STYLECHANGING \(\)|afx\_msg [OnStyleChanging](../Topic/CWnd::OnStyleChanging.md)vacío \(int, LPSTYLESTRUCT\);|  
|ON\_WM\_SYSCHAR \(\)|afx\_msg [OnSysChar](../Topic/CWnd::OnSysChar.md)vacío \(UINT, UINT, UINT\);|  
|ON\_WM\_SYSCOLORCHANGE \(\)|afx\_msg [OnSysColorChange](../Topic/CWnd::OnSysColorChange.md)vacío \(\);|  
|ON\_WM\_SYSCOMMAND \(\)|afx\_msg [OnSysCommand](../Topic/CWnd::OnSysCommand.md)vacío \(UINT, LONG\);|  
|ON\_WM\_SYSDEADCHAR \(\)|afx\_msg [OnSysDeadChar](../Topic/CWnd::OnSysDeadChar.md)vacío \(UINT, UINT, UINT\);|  
|ON\_WM\_SYSKEYDOWN \(\)|afx\_msg [OnSysKeyDown](../Topic/CWnd::OnSysKeyDown.md)vacío \(UINT, UINT, UINT\);|  
|ON\_WM\_SYSKEYUP \(\)|afx\_msg [OnSysKeyUp](../Topic/CWnd::OnSysKeyUp.md)vacío \(UINT, UINT, UINT\);|  
  
## Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)   
 [Controladores de mensajes WM\_](../../mfc/reference/handlers-for-wm-messages.md)