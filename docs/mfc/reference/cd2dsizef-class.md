---
title: Clase CD2DSizeF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5af0ea66ba143935689486d7b7afa3cfaf8cd033
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071276"
---
# <a name="cd2dsizef-class"></a>Clase CD2DSizeF

Un contenedor para D2D1_SIZE_F.

## <a name="syntax"></a>Sintaxis

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Sobrecargado. Construye un `CD2DSizeF` objeto `D2D1_SIZE_F` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Devuelve un **booleano** valor que indica si una expresión no contiene datos válidos (NULL).|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CSize CD2DSizeF::operator](#operator_csize)|Convierte `CD2DSizeF` a `CSize` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

Construye un objeto CD2DSizeF CSize objeto.

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

*CX*<br/>
ancho de origen

*CY*<br/>
alto de origen

##  <a name="isnull"></a>  CD2DSizeF::IsNull

Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el ancho y alto están vacíos; en caso contrario, FALSE.

##  <a name="operator_csize"></a>  CSize CD2DSizeF::operator

Convierte CD2DSizeF CSize objeto.

```
operator CSize();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de tamaño D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
