---
title: RGNDATA (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- RGNDATA
dev_langs:
- C++
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b775b14cb2f6b0f87bca1c81938c1a4c05c1304
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335674"
---
# <a name="rgndata-structure"></a>RGNDATA (Estructura)
El `RGNDATA` estructura contiene un encabezado y una matriz de rectángulos que componen una región. Estos rectángulos, ordenado arriba a abajo de izquierda a derecha, no se superponen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _RGNDATA { /* rgnd */  
    RGNDATAHEADER rdh;  
    char Buffer[1];  
} RGNDATA;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *rdh*  
 Especifica un [RGNDATAHEADER](http://msdn.microsoft.com/library/windows/desktop/dd162941) estructura. (Para obtener más información sobre esta estructura, consulte el SDK de Windows). Los miembros de esta estructura de especifican el tipo de región (si es rectangular o trapezoidal), el número de rectángulos que componen la región, el tamaño del búfer que contiene las estructuras de rectángulo, y así sucesivamente.  
  
 *Búfer*  
 Especifica un búfer de tamaño arbitrario que contiene el [RECT](../../mfc/reference/rect-structure1.md) estructuras que constituyen la región.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

