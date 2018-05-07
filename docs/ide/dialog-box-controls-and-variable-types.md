---
title: Controles de cuadro de diálogo y tipos de Variable | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2fbae37072f50898181334a9059a7dc9c6a83a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-box-controls-and-variable-types"></a>Tipos de controles de cuadro de diálogo y tipos de variable
Puede usar el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para agregar una variable de miembro a un control de cuadro de diálogo creado mediante MFC. El tipo de control para el que se agregue la variable miembro determina las opciones que aparecen en el cuadro de diálogo.  
  
 La tabla siguiente describen todos los tipos de control de cuadro de diálogo admitidos en MFC y la [Editor de cuadro de diálogo](../windows/dialog-editor.md)y sus tipos y valores disponibles.  
  
|Control|Tipo de control|Tipo de variable de control|Tipo de variable de valor|Valores mínimos y máximos (tipo de valor únicamente)|  
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|  
|Animation (control)|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|None; sólo el control|N/D|  
|Botón|BOTÓN|[CButton](../mfc/reference/cbutton-class.md)|None; sólo el control|N/D|  
|Casilla de verificación|COMPROBAR|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Valor de máximo y mínimo|  
|Cuadro combinado|CUADRO COMBINADO|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Número máximo de caracteres|  
|Control de selector de fecha hora|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Valor de máximo y mínimo|  
|Cuadro de edición|EDITAR|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime`, o **COleCurrency**|Valor de máximo y mínimo; Algunos caracteres como máximo soporte técnico|  
|Control de tecla de acceso rápido|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|None; sólo el control|N/D|  
|Cuadro de lista|CUADRO DE LISTA|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Número máximo de caracteres|  
|List (control)|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|None; sólo el control|N/D|  
|Month Calendar (control)|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Valor de máximo y mínimo|  
|Control de progreso|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|None; sólo el control|N/D|  
|Control Rich Edit 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Número máximo de caracteres|  
|Control Rich Edit|RICHEDIT|`CRichEditCtrl`|`CString`|Número máximo de caracteres|  
|Barra de desplazamiento (vertical u horizontal|BARRA DE DESPLAZAMIENTO|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Valor de máximo y mínimo|  
|Control deslizante|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Valor de máximo y mínimo|  
|Control de botón de número|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|None; sólo el control|N/D|  
|Control Tab|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|None; sólo el control|N/D|  
|Tree (control)|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|None; sólo el control|N/D|  
  
## <a name="see-also"></a>Vea también  
 [Agregar una Variable miembro](../ide/adding-a-member-variable-visual-cpp.md)