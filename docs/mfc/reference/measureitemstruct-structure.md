---
title: "MEASUREITEMSTRUCT (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MEASUREITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MEASUREITEMSTRUCT (estructura)"
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# MEASUREITEMSTRUCT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `MEASUREITEMSTRUCT` informa a Windows las dimensiones de un control o un elemento de menú propietario\- dibujado.  
  
## Sintaxis  
  
```  
  
      typedef struct tagMEASUREITEMSTRUCT {  
   UINT CtlType;  
   UINT CtlID;  
   UINT itemID;  
   UINT itemWidth;  
   UINT itemHeight;  
   DWORD itemData  
} MEASUREITEMSTRUCT;  
```  
  
#### Parámetros  
 `CtlType`  
 Contiene el tipo de control.  Los valores de los tipos de control son:  
  
-   Cuadro combinado Propietario\- dibujo de**ODT\_COMBOBOX**  
  
-   Cuadro de lista de Propietario\- dibujo de**ODT\_LISTBOX**  
  
-   Menú de Propietario\- dibujo de**ODT\_MENU**  
  
 `CtlID`  
 Contiene el identificador de control de un cuadro combinado, un cuadro de lista, o un botón.  No utilizan este miembro para un menú.  
  
 `itemID`  
 Contiene el identificador de elemento de menú de un menú o identificador del lista\-cuadro\- elemento para un cuadro combinado o un cuadro de lista de variable\- alto.  No utilizan este miembro para un cuadro combinado o un cuadro de lista de altitud fija, o para un botón.  
  
 *itemWidth*  
 Especifica el ancho de un elemento de menú.  El propietario del elemento de menú de propietario\- dibujo debe rellenar este miembro antes de volver de mensajes.  
  
 *itemHeight*  
 Especifica el alto de un elemento individual de un cuadro de lista o un menú.  Antes de que vuelva de mensajes, el propietario del cuadro combinado, el cuadro de lista, o el elemento de menú de propietario\- dibujo debe completar este miembro.  El alto máximo de un elemento del cuadro de lista es 255.  
  
 `itemData`  
 Para un cuadro combinado o un cuadro de lista, este miembro contiene el valor que se pasó al cuadro de lista con uno de los valores siguientes:  
  
-   [CComboBox::AddString](../Topic/CComboBox::AddString.md)  
  
-   [CComboBox::InsertString](../Topic/CComboBox::InsertString.md)  
  
-   [CListBox::AddString](../Topic/CListBox::AddString.md)  
  
-   [CListBox::InsertString](../Topic/CListBox::InsertString.md)  
  
 Para obtener un menú, este miembro contiene el valor que se pasó al menú por uno de los siguientes:  
  
-   [CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)  
  
-   [CMenu::InsertMenu](../Topic/CMenu::InsertMenu.md)  
  
-   [CMenu::ModifyMenu](../Topic/CMenu::ModifyMenu.md)  
  
 Esto permite que Windows procesa la interacción del usuario con el control correctamente.  El error completar los miembros adecuados en la estructura de `MEASUREITEMSTRUCT` hará que la operación incorrecta del control.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)