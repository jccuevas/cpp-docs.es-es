---
title: POINT (Estructura)
ms.date: 10/12/2018
f1_keywords:
- POINT
- LPPOINT
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
ms.openlocfilehash: c53f250b714c66e74a12432b879cbc4bcc1fd88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646906"
---
# <a name="point-structure"></a>POINT (Estructura)

El `POINT` estructura define la x*-* y coordenadas y de un punto.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagPOINT {
    LONG x;
    LONG y;
} POINT;
```

#### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica la coordenada x de un punto.

*y*<br/>
Especifica la coordenada y de un punto.

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/cpp/point-structure1_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** windef.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPoint (clase)](../../atl-mfc-shared/reference/cpoint-class.md)
