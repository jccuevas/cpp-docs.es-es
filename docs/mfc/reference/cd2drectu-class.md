---
title: Clase CD2DRectU
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 26e647ae01a498a6ad8ca2d7c866f33b01910881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369109"
---
# <a name="cd2drectu-class"></a>Clase CD2DRectU

Contenedor para `D2D1_RECT_U`.

## <a name="syntax"></a>Sintaxis

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|Sobrecargado. Construye un `CD2DRectU` objeto `D2D1_RECT_U` a partir de un objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|Devuelve un valor **booleano** que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRectU::operador CRect](#operator_crect)|Convierte `CD2DRectU` en `CRect` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2DRectU::CD2DRectU

Construye un objeto CD2DRectU a partir del objeto CRect.

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
rectángulo de origen

*uLeft*<br/>
fuente de la izquierda coordenada

*uTop*<br/>
fuente coordenada superior

*uRight*<br/>
fuente derecha coordenada

*uBottom*<br/>
fuente coordenada inferior

## <a name="cd2drectuisnull"></a><a name="isnull"></a>CD2DRectU::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi los valores superior, izquierdo, inferior y derecho del rectángulo son todos iguales a 0; de lo contrario FALSO.

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU::operador CRect

Convierte CD2DRectU en CRect objeto.

```
operator CRect();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del rectángulo D2D.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
