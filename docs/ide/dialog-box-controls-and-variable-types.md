---
title: Tipos de controles de cuadro de diálogo y tipos de variable
ms.date: 11/04/2016
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
ms.openlocfilehash: efacd6382d5773c4c47896a99910d9fe9934397a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600133"
---
# <a name="dialog-box-controls-and-variable-types"></a>Tipos de controles de cuadro de diálogo y tipos de variable

Se puede usar el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para agregar una variable miembro a un control de cuadro de diálogo creado mediante MFC. El tipo de control para el que se agregue la variable miembro determina las opciones que aparecen en el cuadro de diálogo.

En la tabla siguiente se describen todos los tipos de control de cuadro de diálogo admitidos en MFC y el [Editor de cuadros de diálogo](../windows/dialog-editor.md), y sus tipos y valores disponibles.

|Control|Tipo de control|Tipo de variable de control|Tipo de variable de valor|Valores mínimos y máximos (solo tipo de valor)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Animation (control)|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Ninguno; solo el control|N/D|
|Botón|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|Ninguno; solo el control|N/D|
|Casilla de verificación|CHECK|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Valor máximo y mínimo|
|Cuadro combinado|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Número máximo de caracteres|
|Control de selector de fecha y hora|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Valor máximo y mínimo|
|Cuadro de edición|EDITAR|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime` o **COleCurrency**|Valor máximo y mínimo; algunos admiten número máximo de caracteres|
|Control de tecla de acceso rápido|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Ninguno; solo el control|N/D|
|Cuadro de lista|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Número máximo de caracteres|
|List (control)|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Ninguno; solo el control|N/D|
|Month Calendar (control)|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Valor máximo y mínimo|
|Control de progreso|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Ninguno; solo el control|N/D|
|Control de edición de texto enriquecido 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Número máximo de caracteres|
|Control de edición de texto enriquecido|RICHEDIT|`CRichEditCtrl`|`CString`|Número máximo de caracteres|
|Barra de desplazamiento (vertical u horizontal)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Valor máximo y mínimo|
|Control deslizante|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Valor máximo y mínimo|
|Control de botón de número|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Ninguno; solo el control|N/D|
|Control Tab|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Ninguno; solo el control|N/D|
|Tree (control)|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Ninguno; solo el control|N/D|

## <a name="see-also"></a>Vea también

[Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)