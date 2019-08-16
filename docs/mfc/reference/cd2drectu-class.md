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
ms.openlocfilehash: 4bbf7014fc1b612804289dcb647f85b5e7905aeb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244399"
---
# <a name="cd2drectu-class"></a>Clase CD2DRectU

Contenedor para `D2D1_RECT_U`.

## <a name="syntax"></a>Sintaxis

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|Sobrecargado. Construye un `CD2DRectU` objeto `D2D1_RECT_U` objeto.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|Devuelve un **booleano** valor que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRect CD2DRectU::operator](#operator_crect)|Convierte `CD2DRectU` a `CRect` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="cd2drectu"></a>  CD2DRectU::CD2DRectU

Construye un objeto CD2DRectU del objeto CRect.

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

*rect*<br/>
rectángulo de origen

*uLeft*<br/>
Coordenada izquierda de origen

*uTop*<br/>
Coordenada superior de origen

*uRight*<br/>
Coordenada derecha de origen

*uBottom*<br/>
Coordenada inferior de origen

##  <a name="isnull"></a>  CD2DRectU::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si son iguales a 0; superior, izquierdo, inferior y valores correctos del rectángulo en caso contrario, FALSE.

##  <a name="operator_crect"></a>  CRect CD2DRectU::operator

Convierte CD2DRectU objeto CRect.

```
operator CRect();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del rectángulo de D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
