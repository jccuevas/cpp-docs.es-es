---
title: DELETEITEMSTRUCT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f5936cbb863cf8ace851609cb1dc8352e21f9456
ms.lasthandoff: 02/24/2017

---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT (Estructura)
El `DELETEITEMSTRUCT` describe la estructura de un elemento eliminado de cuadro de lista o cuadro combinado dibujado por el propietario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagDELETEITEMSTRUCT { /* ditms */  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    HWND hwndItem;  
    UINT itemData;  
} DELETEITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CtlType`  
 Especifica **ODT_LISTBOX** (un cuadro de lista dibujado por el propietario) o **ODT_COMBOBOX** (un cuadro combinado dibujado por el propietario).  
  
 `CtlID`  
 Especifica el identificador del cuadro de lista o cuadro combinado.  
  
 `itemID`  
 Especifica el índice del elemento en el cuadro de lista o cuadro combinado que se va a quitar.  
  
 `hwndItem`  
 Identifica el control.  
  
 `itemData`  
 Especifica los datos definidos por la aplicación para el elemento. Este valor se pasa al control en el **lParam** parámetro del mensaje que se agrega el elemento al cuadro de lista o cuadro combinado.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se quita un elemento de cuadro de lista o cuadro combinado o cuando se destruye el cuadro de lista o cuadro combinado, Windows envía el `WM_DELETEITEM` mensaje al propietario de cada elemento eliminado. El **lParam** parámetro del mensaje contiene un puntero a esta estructura.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)



