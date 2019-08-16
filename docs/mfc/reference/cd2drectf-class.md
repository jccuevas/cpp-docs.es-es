---
title: Clase CD2DRectF
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 9b91cfaec3827a61152c4116b56e817a436606be
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682402"
---
# <a name="cd2drectf-class"></a>Clase CD2DRectF

Contenedor para `D2D1_RECT_F`.

## <a name="syntax"></a>Sintaxis

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Sobrecargado. Construye un objeto `CD2DRectF` a partir `D2D1_RECT_F` de un objeto.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|Devuelve un valor **booleano** que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DRectF:: Operator CRect](#operator_crect)|`CD2DRectF` Convierte en`CRect` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget. h

##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF

Construye un objeto CD2DRectF a partir del objeto CRect.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
rectángulo de origen

*fLeft*<br/>
Coordenada izquierda de origen

*fTop*<br/>
coordenada superior de origen

*fRight*<br/>
coordenada derecha de origen

*fBottom*<br/>
coordenada inferior de origen

##  <a name="isnull"></a>  CD2DRectF::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (NULL).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si los valores superior, izquierdo, inferior y derecho del rectángulo son iguales a 0; en caso contrario, FALSE.

##  <a name="operator_crect"></a>CD2DRectF:: Operator CRect

Convierte CD2DRectF en el objeto CRect.

```
operator CRect();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del rectángulo D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
