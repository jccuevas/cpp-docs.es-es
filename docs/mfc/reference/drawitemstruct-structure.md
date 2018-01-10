---
title: DRAWITEMSTRUCT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DRAWITEMSTRUCT
dev_langs: C++
helpviewer_keywords: DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 438d698b486b455d7898a836d510aa5ec1c6e454
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 `CtlType`  
 Tipo de control. Los valores de tipos de control son los siguientes:  
  
- **ODT_BUTTON** Botón dibujado por el propietario  
  
- **ODT_COMBOBOX** Cuadro combinado dibujado por el propietario  
  
- **ODT_COMBOBOX** Cuadro de lista dibujado por el propietario  
  
- **ODT_MENU** Menú dibujado por el propietario  
  
- **ODT_LISTVIEW** Control de vista de lista  
  
- **ODT_STATIC** Control estático dibujado por el propietario  
  
- **ODT_TAB** Control de pestaña  
  
 `CtlID`  
 Identificador del control de un cuadro combinado, un cuadro de lista o un botón. Este miembro no se usa para un menú.  
  
 `itemID`  
 Identificador de elemento de menú de un menú o índice del elemento en un cuadro de lista o cuadro combinado. Para un cuadro de lista o un cuadro combinado vacío, este miembro es un valor negativo, que permite a la aplicación dibujar solo el rectángulo de foco en las coordenadas que especifica el miembro **rcItem** , aunque no exista ningún elemento en el control. Así se puede mostrar al usuario si el cuadro de lista o cuadro combinado tiene el foco de entrada. La configuración de bits del miembro **itemAction** determina si el rectángulo se dibujará como si el cuadro de lista o cuadro combinado tuviese el foco de entrada.  
  
 `itemAction`  
 Define la acción de dibujo necesaria. Será uno o varios de los bits siguientes:  
  
- **ODA_DRAWENTIRE** Este bit se establece cuando es necesario dibujar todo el control.  
  
- **ODA_FOCUS** Este bit se establece cuando el control obtiene o pierde el foco de entrada. El miembro **itemState** debe comprobarse para determinar si el control tiene el foco.  
  
- **ODA_SELECT** Este bit se establece cuando solo cambia el estado de la selección. El miembro **itemState** debe comprobarse para determinar el nuevo estado de selección.  
  
 *itemState*  
 Especifica el estado visual del elemento una vez realizada la acción de dibujo actual. Es decir, si un elemento de menú se va a atenuar, se establecerá el indicador de estado **ODS_GRAYED** . Los indicadores de estado son los siguientes:  
  
- **ODS_CHECKED** Este bit se establece si el elemento de menú debe comprobarse. Este bit sólo se usa en un menú.  
  
- **ODS_DISABLED** Este bit se establece si el elemento se va a dibujar como deshabilitado.  
  
- **ODS_FOCUS** Este bit se establece si el elemento tiene el foco de entrada.  
  
- **ODS_GRAYED** Este bit se establece si el elemento se va a atenuar. Este bit sólo se usa en un menú.  
  
- **ODS_SELECTED** Este bit se establece si se selecciona el estado del artículo.  
  
- **ODS_COMBOBOXEDIT** El dibujo tiene lugar en el campo de selección (control de edición) de un cuadro combinado ownerdrawn.  
  
- **ODS_DEFAULT** El elemento es el predeterminado.  
  
 `hwndItem`  
 Especifica el identificador de ventana del control de cuadros combinados, cuadros de lista y botones. Especifica el identificador del menú (`HMENU`) que contiene el elemento de los menús.  
  
 `hDC`  
 Identifica un contexto de dispositivo. Este contexto de dispositivo debe usarse al realizar operaciones de dibujo en el control.  
  
 *rcItem*  
 Rectángulo en el contexto de dispositivo especificado por el miembro `hDC` que define los límites del control que se va a dibujar. Windows recorta automáticamente todo lo que el propietario dibuja en el contexto de dispositivo de cuadros combinados, cuadros de lista y botones, pero no recorta los elementos de menú. Al dibujar elementos de menú, el propietario no debe dibujar fuera de los límites del rectángulo definido por el miembro **rcItem** .  
  
 `itemData`  
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
 La ventana propietaria del elemento de menú o control dibujado por el propietario recibe un puntero a esta estructura como el parámetro `lParam` del mensaje `WM_DRAWITEM` .  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

