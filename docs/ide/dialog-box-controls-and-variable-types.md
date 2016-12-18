---
title: "Tipos de controles de cuadro de di&#225;logo y tipos de variable | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles de cuadro de diálogo, variables miembro"
  - "controles de cuadro de diálogo, tipos de variables"
  - "variables, variables miembro de controles de cuadro de diálogo"
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipos de controles de cuadro de di&#225;logo y tipos de variable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para agregar una variable miembro a un control de cuadro de diálogo creado mediante MFC.  El tipo de control al que agregue la variable miembro determina las opciones que aparecerán en el cuadro de diálogo.  
  
 La tabla siguiente describe todos los tipos de controles de cuadro de diálogo que admiten MFC y el [Editor de cuadros de diálogo](../mfc/dialog-editor.md), así como sus tipos y valores disponibles.  
  
|Control|Tipo de control|Tipo de variable de control|Tipo de variable de valor|Valores máximo y mínimo \(sólo tipo de valor\)|  
|-------------|---------------------|---------------------------------|-------------------------------|----------------------------------------------------|  
|Control de animación|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Ninguna; sólo el control|N\/D|  
|Button|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|Ninguna; sólo el control|N\/D|  
|Check Box|CHECK|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Valor máximo y mínimo|  
|Combo Box|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Número máximo de caracteres|  
|Control selector de fecha y hora|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Valor máximo y mínimo|  
|Cuadro de edición|EDIT|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime`u **OLECurrency**.|Valor máximo y mínimo; algunos admiten el máximo de caracteres.|  
|Control de tecla de acceso rápido|msctls\_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Ninguna; sólo el control|N\/D|  
|Cuadro de lista|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Número máximo de caracteres|  
|Control List|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Ninguna; sólo el control|N\/D|  
|Month Calendar|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Valor máximo y mínimo|  
|Control de progreso|msctls\_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Ninguna; sólo el control|N\/D|  
|Control Rich Edit 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Número máximo de caracteres|  
|Control Rich Edit|RICHEDIT|`CRichEditCtrl`|`CString`|Número máximo de caracteres|  
|Barra de desplazamiento \(vertical u horizontal\)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Valor máximo y mínimo|  
|Slider|msctls\_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Valor máximo y mínimo|  
|Spin|msctls\_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Ninguna; sólo el control|N\/D|  
|Tab|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Ninguna; sólo el control|N\/D|  
|Tree|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Ninguna; sólo el control|N\/D|  
  
## Vea también  
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)