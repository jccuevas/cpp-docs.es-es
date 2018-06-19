---
title: DELETEITEMSTRUCT (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f56a09742276c7fcb1bd66ff1a36b1d17cdf882
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370951"
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


