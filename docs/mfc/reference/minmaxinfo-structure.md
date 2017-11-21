---
title: MINMAXINFO (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MINMAXINFO
dev_langs: C++
helpviewer_keywords: MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 997e00d8d4fd70281f2dbfeeecbc9d5823c5050a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO (Estructura)
El `MINMAXINFO` estructura contiene información sobre el tamaño de una ventana maximizada y posición y su tamaño máximo y mínimo de seguimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagMINMAXINFO {  
    POINT ptReserved;  
    POINT ptMaxSize;  
    POINT ptMaxPosition;  
    POINT ptMinTrackSize;  
    POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ptReserved*  
 Reservado para uso interno.  
  
 *ptMaxSize*  
 Especifica el ancho maximizado (point.x) y el alto maximizado (point.y) de la ventana.  
  
 `ptMaxPosition`  
 Especifica la posición del lado izquierdo de la ventana maximizada (point.x) y la posición de la parte superior de la ventana maximizada (point.y).  
  
 *ptMinTrackSize*  
 Especifica el ancho mínimo de seguimiento (point.x) y el mínimo alto (point.y) de la ventana de seguimiento.  
  
 *ptMaxTrackSize*  
 Especifica el máximo ancho (point.x) de seguimiento y el máximo alto (point.y) de la ventana de seguimiento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

