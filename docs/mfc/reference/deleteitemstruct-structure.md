---
title: "DELETEITEMSTRUCT (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DELETEITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DELETEITEMSTRUCT (estructura)"
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: 13
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DELETEITEMSTRUCT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `DELETEITEMSTRUCT` describe un elemento propietario\- dibujado eliminado del cuadro de lista o de cuadro combinado.  
  
## Sintaxis  
  
```  
  
      typedef struct tagDELETEITEMSTRUCT { /* ditms */  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    HWND hwndItem;  
    UINT itemData;  
} DELETEITEMSTRUCT;  
```  
  
#### Parámetros  
 `CtlType`  
 Especifica **ODT\_LISTBOX** \(un cuadro de lista propietario\- dibujado\) o **ODT\_COMBOBOX** \(un cuadro combinado propietario\- dibujado\).  
  
 `CtlID`  
 Especifica el identificador del cuadro de lista o de cuadro combinado.  
  
 `itemID`  
 Especifica el índice del elemento en el cuadro de lista o el cuadro combinado que se quita.  
  
 `hwndItem`  
 Identifica el control.  
  
 `itemData`  
 Especifica los datos definidos por la aplicación para el elemento.  Este valor se pasa al control en el parámetro de **lParam** de mensajes que agrega el elemento al cuadro de lista o el cuadro combinado.  
  
## Comentarios  
 Cuando se quita un elemento de cuadro de lista o de cuadro combinado o cuando se destruye el cuadro de lista o el cuadro combinado, Windows envía el mensaje de `WM_DELETEITEM` el propietario para cada elemento eliminado.  El parámetro de **lParam** de mensajes contiene un puntero a esta estructura.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)