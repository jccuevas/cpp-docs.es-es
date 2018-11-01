---
title: DRAWITEMSTRUCT (estructura)
ms.date: 11/04/2016
f1_keywords:
- DRAWITEMSTRUCT
helpviewer_keywords:
- DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
ms.openlocfilehash: 9c5bfc12bd371761682102dad6d7bcb75ef44151
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624437"
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

*CtlType*<br/>
Tipo de control. Los valores de tipos de control son los siguientes:

- Botón dibujado por el propietario ODT_BUTTON

- Cuadro combinado dibujado por el propietario ODT_COMBOBOX

- Cuadro de lista dibujado por el propietario de odt_combobox

- Menú dibujado por el propietario ODT_MENU

- Control de vista de lista ODT_LISTVIEW

- ODT_STATIC control estático dibujado por el propietario

- Control de ficha ODT_TAB

*CtlID*<br/>
Identificador del control de un cuadro combinado, un cuadro de lista o un botón. Este miembro no se usa para un menú.

*itemID*<br/>
Identificador de elemento de menú de un menú o índice del elemento en un cuadro de lista o cuadro combinado. Para un cuadro de lista vacío o un cuadro combinado, este miembro es un valor negativo, que permite que la aplicación dibujar solo el rectángulo de foco en las coordenadas especificadas por el `rcItem` miembro incluso si no hay ningún elemento en el control. Así se puede mostrar al usuario si el cuadro de lista o cuadro combinado tiene el foco de entrada. La configuración de los bits de la `itemAction` miembro determina si el rectángulo se dibujará como si el cuadro de lista o cuadro combinado tiene foco de entrada.

*itemAction*<br/>
Define la acción de dibujo necesaria. Será uno o varios de los bits siguientes:

- ODA_DRAWENTIRE este bit se establece cuando es necesario dibujar todo el control.

- ODA_FOCUS este bit se establece cuando el control obtiene o pierde el foco de entrada. El `itemState` miembro debe comprobarse para determinar si el control tiene el foco.

- ODA_SELECT este bit se establece cuando ha cambiado el estado de la selección. El `itemState` miembro debe comprobarse para determinar el nuevo estado de selección.

*itemState*<br/>
Especifica el estado visual del elemento una vez realizada la acción de dibujo actual. Es decir, si un elemento de menú se va a atenuar, el indicador de estado ODS_GRAYED se establecerá. Los indicadores de estado son los siguientes:

- ODS_CHECKED este bit se establece si el elemento de menú es se va a comprobar. Este bit sólo se usa en un menú.

- ODS_DISABLED este bit se establece si el elemento se va a dibujar como deshabilitado.

- ODS_FOCUS este bit se establece si el elemento tiene foco de entrada.

- ODS_GRAYED este bit se establece si el elemento se va a atenuar. Este bit sólo se usa en un menú.

- ODS_SELECTED este bit se establece si se selecciona el estado del artículo.

- ODS_COMBOBOXEDIT el dibujo tiene lugar en el campo de selección (control de edición) de un cuadro combinado ownerdrawn.

- ODS_DEFAULT el elemento es el elemento predeterminado.

*hwndItem*<br/>
Especifica el identificador de ventana del control de cuadros combinados, cuadros de lista y botones. Especifica el identificador del menú (HMENU) que contiene el elemento en los menús.

*hDC*<br/>
Identifica un contexto de dispositivo. Este contexto de dispositivo debe usarse al realizar operaciones de dibujo en el control.

*rcItem*<br/>
Un rectángulo en el contexto de dispositivo especificado por el *hDC* miembro que define los límites del control que se va a dibujar. Windows recorta automáticamente todo lo que el propietario dibuja en el contexto de dispositivo de cuadros combinados, cuadros de lista y botones, pero no recorta los elementos de menú. Al dibujar elementos de menú, el propietario no debe dibujar fuera de los límites del rectángulo definido por el `rcItem` miembro.

*itemData*<br/>
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

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

