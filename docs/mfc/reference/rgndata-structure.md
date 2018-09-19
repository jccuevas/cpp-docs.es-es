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
ms.openlocfilehash: 2c539feaac9cac5bca3a41868cc03379a63bf6bb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204364"
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
 Especifica un [RGNDATAHEADER](/windows/desktop/api/wingdi/ns-wingdi-_rgndataheader) estructura. (Para obtener más información sobre esta estructura, consulte el SDK de Windows). Los miembros de esta estructura de especifican el tipo de región (si es rectangular o trapezoidal), el número de rectángulos que componen la región, el tamaño del búfer que contiene las estructuras de rectángulo, y así sucesivamente.  
  
 *búfer*  
 Especifica un búfer de tamaño arbitrario que contiene el [RECT](../../mfc/reference/rect-structure1.md) estructuras que constituyen la región.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

