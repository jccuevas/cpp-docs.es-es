---
title: POINT (Structure1) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 82955bb42ae68cb7f07fb89be94a7fcf424ee81c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416102"
---
# <a name="point-structure1"></a>POINT (Structure1)

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
