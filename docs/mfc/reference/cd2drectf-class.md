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
ms.openlocfilehash: 33d3c5f9e795ad6c91b689436e8a3b1b56966dce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369125"
---
# <a name="cd2drectf-class"></a>Clase CD2DRectF

Contenedor para `D2D1_RECT_F`.

## <a name="syntax"></a>Sintaxis

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Sobrecargado. Construye un `CD2DRectF` objeto `D2D1_RECT_F` a partir de un objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|Devuelve un valor **booleano** que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRectF::operador CRect](#operator_crect)|Convierte `CD2DRectF` en `CRect` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a>CD2DRectF::CD2DRectF

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

*Rect*<br/>
rectángulo de origen

*fLeft*<br/>
fuente de la izquierda coordenada

*fTop*<br/>
fuente coordenada superior

*Susto*<br/>
fuente derecha coordenada

*fBottom*<br/>
fuente coordenada inferior

## <a name="cd2drectfisnull"></a><a name="isnull"></a>CD2DRectF::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi los valores superior, izquierdo, inferior y derecho del rectángulo son todos iguales a 0; de lo contrario FALSO.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a>CD2DRectF::operador CRect

Convierte CD2DRectF en CRect objeto.

```
operator CRect();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del rectángulo D2D.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
