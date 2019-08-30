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
ms.openlocfilehash: 21087682d40dac521cc949a39ef4b1aab23e7d71
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177213"
---
# <a name="cd2dellipse-class"></a>Clase CD2DEllipse

Contenedor para `D2D1_ELLIPSE`.

## <a name="syntax"></a>Sintaxis

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Sobrecargado. Construye un objeto `CD2DEllipse` a partir `D2D1_ELLIPSE` de un objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget. h

##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse

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

*rect*<br/>
rectángulo de origen

*ellipse*<br/>
elipse de origen

*ptCenter*<br/>
Punto central de la elipse.

*sizeRadius*<br/>
Radio X e y de la elipse.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
