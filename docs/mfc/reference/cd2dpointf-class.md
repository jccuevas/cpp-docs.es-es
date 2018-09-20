---
title: Clase CD2DPointF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f36756579a07692f190e0ea919d6d82e3cb4128d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439853"
---
# <a name="cd2dpointf-class"></a>Clase CD2DPointF

Contenedor para `D2D1_POINT_2F`.

## <a name="syntax"></a>Sintaxis

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Sobrecargado. Construye un `CD2DPointF` objeto `D2D1_POINT_2F` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CPoint CD2DPointF::operator](#operator_cpoint)|Convierte `CD2DPointF` a `CPoint` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF

Construye un objeto CD2DPointF CPoint objeto.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Parámetros

*PT*<br/>
punto de origen

*fX*<br/>
origen X

*año fiscal*<br/>
origen Y

##  <a name="operator_cpoint"></a>  CPoint CD2DPointF::operator

Convierte CD2DPointF CPoint objeto.

```
operator CPoint();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del punto de D2D.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
