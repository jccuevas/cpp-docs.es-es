---
title: TOOLTIPTEXT (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: 8cae7efbee59b24ff34518b62ff212d436973053
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953937"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT (Estructura)
En la escritura su [controlador de notificación de sugerencia de herramienta](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), debe usar el **TOOLTIPTEXT** estructura. Los miembros de la **TOOLTIPTEXT** estructura son:  
  
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
 Identifica la herramienta que necesita texto. El único miembro de esta estructura que tendrá que es el identificador del comando. del control Identificador de comando del control estará en el *idFrom* miembro de la **NMHDR** estructura, obtiene acceso con la sintaxis `hdr.idFrom`. Vea [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) para obtener una explicación de los miembros de la **NMHDR** estructura.  
  
 *lpszText*  
 Dirección de una cadena que recibe el texto de una herramienta.  
  
 *szText*  
 Búfer que recibe el texto de información sobre herramientas. Una aplicación puede copiar el texto en este búfer como una alternativa a especificar una dirección de cadena.  
  
 *hinst*  
 Identificador de la instancia que contiene una cadena que se usará como el texto de información sobre herramientas. Si *lpszText* es la dirección del texto de información sobre herramientas, este miembro es NULL.  
  
 Al controlar la `TTN_NEEDTEXT` notificación de mensaje, especifique la cadena que se mostrará en una de las maneras siguientes:  
  
-   Copie el texto en el búfer especificado por el *szText* miembro.  
  
-   Copie la dirección del búfer que contiene el texto para el *lpszText* miembro.  
  
-   Copie el identificador de un recurso de cadena para el *lpszText* miembro y copie el identificador de la instancia que contiene el recurso a la *hinst* miembro.  
  
## <a name="see-also"></a>Vea también  
 [Información sobre herramientas en ventanas no derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

