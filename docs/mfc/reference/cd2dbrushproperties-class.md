---
title: Clase CD2DBrushProperties | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6268a4478fa361b521ac662852e62dd50c56621
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071815"
---
# <a name="cd2dbrushproperties-class"></a>Clase CD2DBrushProperties

Contenedor para `D2D1_BRUSH_PROPERTIES`.

## <a name="syntax"></a>Sintaxis

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Sobrecargado. Crea un `CD2D_BRUSH_PROPERTIES` estructura|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicializa el objeto|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="cd2dbrushproperties"></a>  CD2DBrushProperties::CD2DBrushProperties

Crea una estructura CD2D_BRUSH_PROPERTIES

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>Parámetros

*_opacity*<br/>
La base opacidad del pincel. El valor predeterminado es 1,0.

*_transform*<br/>
La transformación para aplicar al pincel

##  <a name="commoninit"></a>  CD2DBrushProperties::CommonInit

Inicializa el objeto

```
void CommonInit();
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
