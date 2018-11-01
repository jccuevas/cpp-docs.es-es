---
title: Clase CD2DPointU
ms.date: 11/04/2016
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 138916efe781d8bef69a1c4eb61a73c5a405be67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551858"
---
# <a name="cd2dpointu-class"></a>Clase CD2DPointU

Contenedor para `D2D1_POINT_2U`.

## <a name="syntax"></a>Sintaxis

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Sobrecargado. Construye un `CD2DPointU` del objeto `D2D1_POINT_2U` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CPoint CD2DPointU::operator](#operator_cpoint)|Convierte `CD2DPointU` a `CPoint` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU

Construye un objeto CD2DPointU CPoint objeto.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
  CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parámetros

*PT*<br/>
punto de origen

*experiencia de usuario*<br/>
origen X

*uY*<br/>
origen Y

##  <a name="operator_cpoint"></a>  CPoint CD2DPointU::operator

Convierte CD2DPointU CPoint objeto.

```
operator CPoint();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del punto de D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
