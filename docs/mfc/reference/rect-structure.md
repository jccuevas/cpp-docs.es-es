---
title: RECT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eae2b248f4aa4586bf6453dcc37b521387327d25
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334572"
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
