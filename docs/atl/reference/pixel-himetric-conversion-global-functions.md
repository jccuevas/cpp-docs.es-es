---
title: Funciones globales de conversión Pixel-HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 08c72c0d8f3d061950d6945d9fb412c0a16355da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326144"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Funciones globales de conversión de píxeles/HIMETRIC

Estas funciones proporcionan soporte para convertir a y desde unidades de píxeles y HIMETRIC.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Convierte unidades HIMETRIC (cada unidad es 0,01 milímetros) en píxeles.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Convierte píxeles en unidades HIMETRIC (cada unidad es 0,01 milímetros).|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a>AtlHiMetricToPixel

Convierte un tamaño de objeto en unidades HIMETRIC (cada unidad es de 0,01 milímetros) a un tamaño en píxeles del dispositivo de pantalla.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parámetros

*lpSizeInHiMetric*<br/>
[en] Puntero al tamaño del objeto en unidades HIMETRIC.

*lpSizeInPix*<br/>
[fuera] Puntero al lugar donde se va a devolver el tamaño del objeto en píxeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a>AtlPixelToHiMetric

Convierte un tamaño de objeto especificado en píxeles en el dispositivo de pantalla en un tamaño especificado en unidades HIMETRIC (cada unidad es de 0,01 milímetros).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parámetros

*lpSizeInPix*<br/>
[en] Puntero al tamaño del objeto en píxeles.

*lpSizeInHiMetric*<br/>
[fuera] Puntero al lugar donde se va a devolver el tamaño del objeto en unidades HIMETRIC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
