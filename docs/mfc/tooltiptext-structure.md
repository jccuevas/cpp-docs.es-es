---
title: TOOLTIPTEXT (Estructura)
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 2eb899e66acbadbe45aae2c8adbb356bf4730191
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915247"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT (Estructura)

Al escribir el [controlador de notificación de la información sobre herramientas](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), debe usar la estructura **ToolTipText** . Los miembros de la estructura **ToolTipText** son:

```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```

*hdr*<br/>
Identifica la herramienta que necesita texto. El único miembro de esta estructura que podría necesitar es el identificador de comando del control. El identificador de comando del control estará en el miembro *idFrom* de la estructura **NMHDR** , al que se tiene acceso `hdr.idFrom`con la sintaxis. Consulte [NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr) para obtener una explicación de los miembros de la estructura **NMHDR** .

*lpszText*<br/>
Dirección de una cadena para recibir el texto de una herramienta.

*szText*<br/>
Búfer que recibe el texto de información sobre herramientas. Una aplicación puede copiar el texto en este búfer como alternativa a especificar una dirección de cadena.

*hinst*<br/>
Identificador de la instancia de que contiene una cadena que se va a usar como texto de información sobre herramientas. Si *lpszText* es la dirección del texto de información sobre herramientas, este miembro es NULL.

Al controlar el `TTN_NEEDTEXT` mensaje de notificación, especifique la cadena que se va a mostrar de una de las siguientes maneras:

- Copie el texto en el búfer especificado por el miembro *szText* .

- Copie la dirección del búfer que contiene el texto en el miembro *lpszText* .

- Copie el identificador de un recurso de cadena en el miembro *lpszText* y copie el identificador de la instancia que contiene el recurso en el miembro *HINST* .

## <a name="see-also"></a>Vea también

[Información sobre herramientas en ventanas no derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
