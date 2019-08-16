---
title: Funciones globales de conversión de píxel e HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276840"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Funciones globales de conversión de píxel/HIMETRIC

Estas funciones proporcionan compatibilidad para la conversión entre píxeles y unidades HIMETRIC.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Convierte unidades HIMETRIC (cada unidad es de 0,01 milímetros) en píxeles.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Convierte los píxeles en unidades HIMETRIC (cada unidad es de 0,01 milímetros).|

##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel

Convierte un tamaño de objeto en unidades HIMETRIC (cada unidad es de 0,01 milímetros) a un tamaño en píxeles del dispositivo de pantalla.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parámetros

*lpSizeInHiMetric*<br/>
[in] Puntero al tamaño del objeto en unidades HIMETRIC.

*lpSizeInPix*<br/>
[out] Puntero a donde el tamaño del objeto en píxeles se va a devolver.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric

Convierte un tamaño de objeto especificado en píxeles en el dispositivo de pantalla en un tamaño especificado en unidades HIMETRIC (cada unidad es de 0,01 milímetros).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parámetros

*lpSizeInPix*<br/>
[in] Puntero al tamaño del objeto en píxeles.

*lpSizeInHiMetric*<br/>
[out] Puntero a donde el tamaño del objeto en unidades HIMETRIC se va a devolver.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
