---
title: Clase CD2DEllipse
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 82ad2fbfb8558486134f85d7ec9bcaa6eb4e7507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369268"
---
# <a name="cd2dellipse-class"></a>Clase CD2DEllipse

Contenedor para `D2D1_ELLIPSE`.

## <a name="syntax"></a>Sintaxis

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Sobrecargado. Construye un `CD2DEllipse` objeto `D2D1_ELLIPSE` a partir de un objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a>CD2DEllipse::CD2DEllipse

Construye un objeto CD2DEllipse a partir del objeto CD2DRectF.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
rectángulo de origen

*ellipse*<br/>
fuente elipse

*ptCenter*<br/>
El punto central de la elipse.

*sizeRadius*<br/>
El radio X y el radio Y de la elipse.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
