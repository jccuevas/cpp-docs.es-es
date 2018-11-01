---
title: RECT (Estructura)
ms.date: 11/04/2016
f1_keywords:
- LPRECT
- RECT
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
ms.openlocfilehash: 1cb997fc0f1ec89eabf5e4d2c2c5ccb15e3bafec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549022"
---
# <a name="rect-structure"></a>RECT (Estructura)

La estructura `RECT` define las coordenadas de las esquinas superior izquierda e inferior derecha de un rectángulo.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagRECT {
    LONG left;
    LONG top;
    LONG right;
    LONG bottom;
} RECT;
```

## <a name="members"></a>Miembros

`left`<br/>
Especifica la coordenada x de la esquina superior izquierda de un rectángulo.

`top`<br/>
Especifica la coordenada y de la esquina superior izquierda de un rectángulo.

`right`<br/>
Especifica la coordenada x de la esquina inferior derecha de un rectángulo.

`bottom`<br/>
Especifica la coordenada y de la esquina inferior derecha de un rectángulo.

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** windef.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)
