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
ms.openlocfilehash: 6289d33aa0672d1ee423d91b11527dccfc868da7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177176"
---
# <a name="cd2dpointu-class"></a>Clase CD2DPointU

Contenedor para `D2D1_POINT_2U`.

## <a name="syntax"></a>Sintaxis

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Sobrecargado. Construye un objeto `CD2DPointU` a partir `D2D1_POINT_2U` de un objeto de objeto.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DPointU::operator CPoint](#operator_cpoint)|`CD2DPointU` Convierte en`CPoint` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget. h

##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU

Construye un objeto CD2DPointU a partir del objeto CPoint.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
punto de origen

*uX*<br/>
origen X

*uY*<br/>
Y de origen

##  <a name="operator_cpoint"></a>  CD2DPointU::operator CPoint

Convierte CD2DPointU en el objeto CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del punto D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
