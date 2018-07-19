---
title: COMPAREITEMSTRUCT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c42f356cb323bb7690b6c39b1fc7bd9ce0485f3
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850594"
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
 *CtlType*  
 Odt_combobox (que especifica un cuadro de lista dibujado por el propietario) o ODT_COMBOBOX (que especifica un cuadro de cuadro combinado dibujado por el propietario).  
  
 *CtlID*  
 Identificador del control de cuadro de lista o cuadro combinado.  
  
 *hwndItem*  
 El identificador de ventana del control.  
  
 *itemID1*  
 El índice del primer elemento en el cuadro de lista o cuadro combinado que se están comparando.  
  
 *itemData1*  
 Datos proporcionados por la aplicación para el primer elemento que se va a comparar. Este valor se pasa en la llamada que se agregó el elemento al cuadro combinado o lista.  
  
 *itemID2*  
 Índice del segundo elemento en el cuadro de lista o cuadro combinado que se están comparando.  
  
 *itemData2*  
 Datos proporcionados por la aplicación para el segundo elemento que se va a comparar. Este valor se pasa en la llamada que se agregó el elemento al cuadro combinado o lista.  
  
## <a name="remarks"></a>Comentarios  
 Cada vez que una aplicación agrega un nuevo elemento a un cuadro de lista dibujado por el propietario o el cuadro combinado creada con el estilo CBS_SORT o LBS_SORT, Windows envía al propietario de un mensaje WM_COMPAREITEM. El *lParam* parámetro del mensaje contiene un puntero largo a un `COMPAREITEMSTRUCT` estructura. Al recibir el mensaje, el propietario compara los dos elementos y devuelve un valor que indica qué elemento se ordena antes que el otro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

