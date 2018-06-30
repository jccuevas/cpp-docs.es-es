---
title: DRAWITEMSTRUCT (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DRAWITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4596a52170d0c6d197a0bda431963b5f0e9344
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120947"
---
# <a name="drawitemstruct-structure"></a>DRAWITEMSTRUCT (estructura)
La estructura `DRAWITEMSTRUCT` proporciona información que la ventana propietaria debe tener para determinar cómo se pinta un elemento de menú o control dibujado por el propietario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagDRAWITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    UINT itemAction;  
    UINT itemState;  
    HWND hwndItem;  
    HDC hDC;  
    RECT rcItem;  
    DWORD itemData;  
} DRAWITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *CtlType*  
 Tipo de control. Los valores de tipos de control son los siguientes:  
  
- Botón dibujado por el propietario ODT_BUTTON  
  
- Cuadro combinado dibujado por el propietario ODT_COMBOBOX  
  
- Cuadro de lista dibujado por el propietario de odt_combobox  
  
- Menú dibujado por el propietario ODT_MENU  
  
- Control de vista de lista ODT_LISTVIEW  
  
- ODT_STATIC control estático dibujado por el propietario  
  
- Control de pestaña ODT_TAB  
  
 *CtlID*  
 Identificador del control de un cuadro combinado, un cuadro de lista o un botón. Este miembro no se usa para un menú.  
  
 *itemID*  
 Identificador de elemento de menú de un menú o índice del elemento en un cuadro de lista o cuadro combinado. Para un cuadro de lista vacío o un cuadro combinado, este miembro es un valor negativo, que permite que la aplicación dibujar el rectángulo de foco en las coordenadas especificadas por la `rcItem` miembro, aunque no exista ningún elemento en el control. Así se puede mostrar al usuario si el cuadro de lista o cuadro combinado tiene el foco de entrada. La configuración de los bits de la `itemAction` miembro determina si el rectángulo se dibujará como si el cuadro de lista o cuadro combinado tiene foco de entrada.  
  
 *ItemAction*  
 Define la acción de dibujo necesaria. Será uno o varios de los bits siguientes:  
  
- ODA_DRAWENTIRE este bit se establece cuando es necesario dibujar todo el control.  
  
- ODA_FOCUS este bit se establece cuando el control obtiene o pierde el foco de entrada. El `itemState` miembro se debe comprobar para determinar si el control tiene el foco.  
  
- ODA_SELECT este bit se establece cuando ha cambiado el estado de la selección. El `itemState` miembro debe comprobarse para determinar el nuevo estado de selección.  
  
 *itemState*  
 Especifica el estado visual del elemento una vez realizada la acción de dibujo actual. Es decir, si un elemento de menú que se va a estar atenuados, la marca de estado ODS_GRAYED se establecerá. Los indicadores de estado son los siguientes:  
  
- ODS_CHECKED este bit se establece si el elemento de menú es comprobarse. Este bit sólo se usa en un menú.  
  
- ODS_DISABLED este bit se establece si el elemento se va a dibujar como deshabilitado.  
  
- ODS_FOCUS este bit se establece si el elemento tiene foco de entrada.  
  
- ODS_GRAYED este bit se establece si el elemento se va a atenuar. Este bit sólo se usa en un menú.  
  
- ODS_SELECTED este bit se establece si se selecciona el estado del artículo.  
  
- ODS_COMBOBOXEDIT el dibujo tiene lugar en el campo de selección (control de edición) de un cuadro combinado ownerdrawn.  
  
- ODS_DEFAULT el elemento es el elemento predeterminado.  
  
 *hwndItem*  
 Especifica el identificador de ventana del control de cuadros combinados, cuadros de lista y botones. Especifica el identificador del menú (HMENU) que contiene el elemento en los menús.  
  
 *hDC*  
 Identifica un contexto de dispositivo. Este contexto de dispositivo debe usarse al realizar operaciones de dibujo en el control.  
  
 *rcItem*  
 Un rectángulo en el contexto de dispositivo especificado por el *hDC* miembro que define los límites del control para dibujar. Windows recorta automáticamente todo lo que el propietario dibuja en el contexto de dispositivo de cuadros combinados, cuadros de lista y botones, pero no recorta los elementos de menú. Al dibujar elementos de menú, el propietario no debe dibujar fuera de los límites del rectángulo definido por el `rcItem` miembro.  
  
 *itemData*  
 Para un cuadro combinado o cuadro de lista, este miembro contiene el valor que uno de los siguientes elementos pasó al cuadro de lista:  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 Para un menú, este miembro contiene el valor que uno de los siguientes elementos pasó al cuadro de lista:  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
## <a name="remarks"></a>Comentarios  
 La ventana propietaria del elemento de menú o control dibujado por el propietario recibe un puntero a esta estructura como el *lParam* parámetro del mensaje WM_DRAWITEM.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

