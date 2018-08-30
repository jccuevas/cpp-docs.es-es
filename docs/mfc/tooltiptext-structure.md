---
title: TOOLTIPTEXT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TOOLTIPTEXT
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f65b94294b3b3d55f9839dffa99a18be61c5639
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195989"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT (Estructura)
Escribir su [controlador de notificación de información sobre herramienta](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), deberá usar el **TOOLTIPTEXT** estructura. Los miembros de la **TOOLTIPTEXT** estructura son:  
  
 `typedef struct {`  
  
 `NMHDR     hdr;        // required for all WM_NOTIFY messages`  
  
 `LPTSTR    lpszText;   // see below`  
  
 `TCHAR     szText[80]; // buffer for tool tip text`  
  
 `HINSTANCE hinst;      // see below`  
  
 `UINT      uflags;     // flag indicating how to interpret the`  
  
 `// idFrom member of the NMHDR structure`  
  
 `// that is included in the structure`  
  
 `} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;`  
  
 *HDR*  
 Identifica la herramienta que necesita el texto. El único miembro de esta estructura que necesita es el identificador de comando. del control Será el identificador de comando del control en el *idFrom* miembro de la **NMHDR** estructura, obtiene acceso con la sintaxis `hdr.idFrom`. Consulte [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) para obtener una explicación de los miembros de la **NMHDR** estructura.  
  
 *lpszText*  
 Dirección de una cadena que recibe el texto para una herramienta.  
  
 *szText*  
 Búfer que recibe el texto de sugerencia. Una aplicación puede copiar el texto a este búfer como una alternativa a especificar una dirección de la cadena.  
  
 *hinst*  
 Identificador de la instancia que contiene una cadena que se usará como el texto de sugerencia. Si *lpszText* es la dirección del texto de sugerencia de herramienta, este miembro es NULL.  
  
 Cuando controle el `TTN_NEEDTEXT` notificación de mensaje, especifique la cadena que se mostrará en una de las maneras siguientes:  
  
-   Copie el texto en el búfer especificado por el *szText* miembro.  
  
-   Copie la dirección del búfer que contiene el texto a la *lpszText* miembro.  
  
-   Copie el identificador de un recurso de cadena a la *lpszText* miembro y copie el identificador de la instancia que contiene el recurso para el *hinst* miembro.  
  
## <a name="see-also"></a>Vea también  
 [Información sobre herramientas en ventanas no derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

