---
title: Clase CD2DBrushProperties
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: 2db720fd09c62f8b86baecea9229d946f3892333
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754184"
---
# <a name="cd2dbrushproperties-class"></a>Clase CD2DBrushProperties

Contenedor para `D2D1_BRUSH_PROPERTIES`.

## <a name="syntax"></a>Sintaxis

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Sobrecargado. Crea `CD2D_BRUSH_PROPERTIES` una estructura|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicializa el objeto|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>CD2DBrushProperties::CD2DBrushProperties

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
La opacidad base del pincel. El valor predeterminado es 1,0.

*_transform*<br/>
La transformación que se aplicará al pincel

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>CD2DBrushProperties::CommonInit

Inicializa el objeto

```cpp
void CommonInit();
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
