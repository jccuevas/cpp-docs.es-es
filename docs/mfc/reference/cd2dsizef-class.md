---
title: Clase CD2DSizeF
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: be050f98855e5af794166e1f86962111a23bfa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369062"
---
# <a name="cd2dsizef-class"></a>Clase CD2DSizeF

Un envoltorio para D2D1_SIZE_F.

## <a name="syntax"></a>Sintaxis

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Sobrecargado. Construye un `CD2DSizeF` objeto `D2D1_SIZE_F` a partir de un objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Devuelve un valor **booleano** que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DSizeF::operator CSize](#operator_csize)|Convierte `CD2DSizeF` en `CSize` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF

Construye un CD2DSizeF objeto a partir de CSize objeto.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
tamaño de la fuente

*Cx*<br/>
ancho de fuente

*Cy*<br/>
altura de la fuente

## <a name="cd2dsizefisnull"></a><a name="isnull"></a>CD2DSizeF::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi width y height están vacíos; de lo contrario FALSO.

## <a name="cd2dsizefoperator-csize"></a><a name="operator_csize"></a>CD2DSizeF::operator CSize

Convierte CD2DSizeF en CSize objeto.

```
operator CSize();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del tamaño D2D.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
