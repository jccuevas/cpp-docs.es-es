---
title: Clase CD2DSizeU
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: a5b87fe2ddd8fb32ddbbb2884c630952afdb079c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359290"
---
# <a name="cd2dsizeu-class"></a>Clase CD2DSizeU

Un envoltorio para D2D1_SIZE_U.

## <a name="syntax"></a>Sintaxis

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Sobrecargado. Construye un `CD2DSizeU` objeto `D2D1_SIZE_U` a partir de un objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|Devuelve un valor **booleano** que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DSizeU::operator CSize](#operator_csize)|Convierte `CD2DSizeU` en `CSize` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU

Construye un CD2DSizeU objeto a partir de CSize objeto.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
tamaño de la fuente

*Cx*<br/>
ancho de fuente

*Cy*<br/>
altura de la fuente

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a>CD2DSizeU::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi width y height están vacíos; de lo contrario FALSO.

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a>CD2DSizeU::operator CSize

Convierte CD2DSizeU en CSize objeto.

```
operator CSize();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del tamaño D2D.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
