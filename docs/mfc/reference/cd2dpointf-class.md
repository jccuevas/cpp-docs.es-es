---
title: Clase CD2DPointF
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 5d66c31289f9e17df99df4681cff1d5cf6a0ec86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369159"
---
# <a name="cd2dpointf-class"></a>Clase CD2DPointF

Contenedor para `D2D1_POINT_2F`.

## <a name="syntax"></a>Sintaxis

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Sobrecargado. Construye un `CD2DPointF` objeto `D2D1_POINT_2F` a partir de un objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DPointF::operador CPoint](#operator_cpoint)|Convierte `CD2DPointF` en `CPoint` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dpointfcd2dpointf"></a><a name="cd2dpointf"></a>CD2DPointF::CD2DPointF

Construye un objeto CD2DPointF a partir del objeto CPoint.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
punto fuente

*Fx*<br/>
fuente X

*Fy*<br/>
fuente Y

## <a name="cd2dpointfoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointF::operador CPoint

Convierte CD2DPointF en CPoint objeto.

```
operator CPoint();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del punto D2D.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
