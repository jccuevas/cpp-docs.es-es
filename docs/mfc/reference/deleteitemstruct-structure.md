---
title: DELETEITEMSTRUCT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DELETEITEMSTRUCT
dev_langs: C++
helpviewer_keywords: DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5be80d8b139f04daa0c44fc2808f61538843e3e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT (Estructura)
El `DELETEITEMSTRUCT` estructura describe un elemento eliminado de cuadro de lista o cuadro combinado dibujado por el propietario.  
  
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
 Especifica **odt_combobox** (un cuadro de lista dibujado por el propietario) o **ODT_COMBOBOX** (un cuadro combinado dibujado por el propietario).  
  
 `CtlID`  
 Especifica el identificador del cuadro de lista o cuadro combinado.  
  
 `itemID`  
 Especifica el índice del elemento en el cuadro de lista o cuadro combinado que se va a quitar.  
  
 `hwndItem`  
 Identifica el control.  
  
 `itemData`  
 Especifica los datos definidos por la aplicación para el elemento. Este valor se pasa al control en el **lParam** parámetro del mensaje que agrega el elemento en el cuadro de lista o cuadro combinado.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se quita un elemento desde el cuadro de lista o cuadro combinado o cuando se destruye el cuadro de lista o cuadro combinado, Windows envía la `WM_DELETEITEM` mensaje hasta el propietario de cada elemento eliminado. El **lParam** parámetro del mensaje contiene un puntero a esta estructura.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)


