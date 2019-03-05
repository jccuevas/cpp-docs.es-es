---
title: Clase CD2DSizeU
ms.date: 11/04/2016
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: f6b0bc12933100c6f2401f4f4cb9e1fae52dda65
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278657"
---
# <a name="cd2dsizeu-class"></a>Clase CD2DSizeU

Un contenedor para D2D1_SIZE_U.

## <a name="syntax"></a>Sintaxis

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Sobrecargado. Construye un `CD2DSizeU` objeto `D2D1_SIZE_U` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|Devuelve un **booleano** valor que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSizeU::operator CSize](#operator_csize)|Convierte `CD2DSizeU` a `CSize` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="cd2dsizeu"></a>  CD2DSizeU::CD2DSizeU

Construye un objeto CD2DSizeU CSize objeto.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
  CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
tamaño de origen

*cx*<br/>
ancho de origen

*cy*<br/>
alto de origen

##  <a name="isnull"></a>  CD2DSizeU::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el ancho y alto están vacíos; en caso contrario, FALSE.

##  <a name="operator_csize"></a>  CD2DSizeU::operator CSize

Convierte CD2DSizeU CSize objeto.

```
operator CSize();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de tamaño D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
