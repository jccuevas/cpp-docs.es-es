---
title: COMPAREITEMSTRUCT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COMPAREITEMSTRUCT
dev_langs: C++
helpviewer_keywords: COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7903e51a83533c8f2458c4400c64717021a1ccb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT (Estructura)
El `COMPAREITEMSTRUCT` estructura proporciona los identificadores y los datos proporcionados por la aplicación para los dos elementos en un cuadro de lista dibujado por el propietario y ordenada o cuadro combinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CtlType`  
 **Odt_combobox** (que especifica un cuadro de lista dibujado por el propietario) o **ODT_COMBOBOX** (que especifica un cuadro combinado dibujado propietario).  
  
 `CtlID`  
 El identificador del control de cuadro de lista o cuadro combinado.  
  
 `hwndItem`  
 El identificador de ventana del control.  
  
 *itemID1*  
 El índice del primer elemento en el cuadro de lista o cuadro combinado que se están comparando.  
  
 *itemData1*  
 Datos proporcionados por la aplicación para el primer elemento que se va a comparar. Este valor se pasa en la llamada que se agregó el elemento en el cuadro combinado o lista.  
  
 *itemID2*  
 Índice del segundo elemento en el cuadro de lista o cuadro combinado que se están comparando.  
  
 *itemData2*  
 Datos proporcionados por la aplicación para el segundo elemento que se va a comparar. Este valor se pasa en la llamada que se agregó el elemento en el cuadro combinado o lista.  
  
## <a name="remarks"></a>Comentarios  
 Cada vez que una aplicación agrega un nuevo elemento a un cuadro de lista dibujado por el propietario o cuadro combinado se creó con la **CBS_SORT** o **LBS_SORT** estilo, Windows envía el propietario de un `WM_COMPAREITEM` mensaje. El `lParam` parámetro del mensaje contiene un puntero largo a una `COMPAREITEMSTRUCT` estructura. Al recibir el mensaje, el propietario compara los dos elementos y devuelve un valor que indica qué elemento se ordena antes que el otro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

