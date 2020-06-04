---
title: Clase CD2DPointU
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 8c6db55f1dde1fd054a1f75590f5969c097b2f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369142"
---
# <a name="cd2dpointu-class"></a>Clase CD2DPointU

Contenedor para `D2D1_POINT_2U`.

## <a name="syntax"></a>Sintaxis

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Sobrecargado. Construye un `CD2DPointU` objeto `D2D1_POINT_2U` de objeto from.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DPointU::operador CPoint](#operator_cpoint)|Convierte `CD2DPointU` en `CPoint` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dpointucd2dpointu"></a><a name="cd2dpointu"></a>CD2DPointU::CD2DPointU

Construye un objeto CD2DPointU a partir del objeto CPoint.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
punto fuente

*Ux*<br/>
fuente X

*Uy*<br/>
fuente Y

## <a name="cd2dpointuoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointU::operador CPoint

Convierte CD2DPointU en CPoint objeto.

```
operator CPoint();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del punto D2D.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
