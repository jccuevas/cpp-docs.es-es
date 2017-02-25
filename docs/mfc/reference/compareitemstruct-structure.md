---
title: "COMPAREITEMSTRUCT (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COMPAREITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMPAREITEMSTRUCT (estructura)"
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# COMPAREITEMSTRUCT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Fuentes de la estructura de `COMPAREITEMSTRUCT` los identificadores y los datos aplicación\- proporcionados para dos elementos en un cuadro de lista o un cuadro combinado ordenados, propietario\- dibujado.  
  
## Sintaxis  
  
```  
  
      typedef struct tagCOMPAREITEMSTRUCT {  
    UINT   CtlType;  
    UINT   CtlID;  
    HWND   hwndItem;  
    UINT   itemID1;  
    DWORD  itemData1;  
    UINT   itemID2;  
    DWORD  itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### Parámetros  
 `CtlType`  
 **ODT\_LISTBOX** \(que especifica un cuadro de lista de propietario\- dibujo\) o **ODT\_COMBOBOX** \(que especifica un cuadro combinado propietario\- dibujo\).  
  
 `CtlID`  
 El identificador del control del cuadro de lista o el cuadro combinado.  
  
 `hwndItem`  
 El identificador de ventana del control.  
  
 *itemID1*  
 El índice del primer elemento del cuadro de lista o el cuadro combinado que es comparable.  
  
 *itemData1*  
 Datos Aplicación\- proporcionados para el primer elemento que se compara.  Este valor se ha pasado en la llamada que agregó el elemento a la combinación o el cuadro de lista.  
  
 *itemID2*  
 Índice del segundo elemento del cuadro de lista o el cuadro combinado que es comparable.  
  
 *itemData2*  
 Datos Aplicación\- proporcionados para el segundo elemento que se compara.  Este valor se ha pasado en la llamada que agregó el elemento a la combinación o el cuadro de lista.  
  
## Comentarios  
 Cada vez que una aplicación agregue un nuevo elemento a un cuadro de lista o un cuadro combinado propietario\- dibujado creado con el estilo de **CBS\_SORT** o de **LBS\_SORT** , Windows envía el propietario un mensaje de `WM_COMPAREITEM` .  El parámetro de `lParam` de mensajes contiene un puntero largo en una estructura de `COMPAREITEMSTRUCT` .  Al recibir el mensaje, el propietario compara los dos elementos y devuelve un valor que indica qué elemento ordena antes del otro.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)