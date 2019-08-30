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
ms.openlocfilehash: df895c278003e2c71f37a00af6bf14912756701a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177206"
---
# <a name="cd2dsizef-class"></a>Clase CD2DSizeF

Un contenedor para D2D1_SIZE_F.

## <a name="syntax"></a>Sintaxis

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Sobrecargado. Construye un objeto `CD2DSizeF` a partir `D2D1_SIZE_F` de un objeto.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Devuelve un valor **booleano** que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CD2DSizeF:: Operator CSize](#operator_csize)|`CD2DSizeF` Convierte en`CSize` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget. h

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

Construye un objeto CD2DSizeF a partir del objeto CSize.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
tamaño de origen

*cx*<br/>
ancho de origen

*cy*<br/>
alto de origen

##  <a name="isnull"></a>  CD2DSizeF::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (NULL).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el ancho y el alto están vacíos; en caso contrario, FALSE.

##  <a name="operator_csize"></a>CD2DSizeF:: Operator CSize

Convierte CD2DSizeF en el objeto CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del tamaño de D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
