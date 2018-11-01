---
title: RGNDATA (Estructura)
ms.date: 11/04/2016
f1_keywords:
- RGNDATA
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
ms.openlocfilehash: d6ee25b490aa5c7055b4e8ccf63939fbdd8dd4ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638144"
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

*rdh*<br/>
Especifica un [RGNDATAHEADER](/windows/desktop/api/wingdi/ns-wingdi-_rgndataheader) estructura. (Para obtener más información sobre esta estructura, consulte el SDK de Windows). Los miembros de esta estructura de especifican el tipo de región (si es rectangular o trapezoidal), el número de rectángulos que componen la región, el tamaño del búfer que contiene las estructuras de rectángulo, y así sucesivamente.

*búfer*<br/>
Especifica un búfer de tamaño arbitrario que contiene el [RECT](../../mfc/reference/rect-structure1.md) estructuras que constituyen la región.

## <a name="requirements"></a>Requisitos

**Encabezado:** wingdi.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)<br/>
[CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

