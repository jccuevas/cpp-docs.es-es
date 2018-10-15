---
title: POINT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- POINT
- LPPOINT
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d2aaafe65b742ded6c0adf49fac430679e24380
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334563"
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
