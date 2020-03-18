---
title: Funciones globales de conversión de pixel-HIMETRIC
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423019"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Funciones globales de conversión de pixel/HIMETRIC

Estas funciones proporcionan compatibilidad para la conversión a y desde unidades de píxel y HIMETRIC.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Convierte unidades HIMETRIC (cada unidad es de 0,01 milímetros) en píxeles.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Convierte píxeles en unidades HIMETRIC (cada unidad es 0,01 milímetros).|

##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel

Convierte un tamaño de objeto en unidades HIMETRIC (cada unidad es de 0,01 milímetros) a un tamaño en píxeles del dispositivo de pantalla.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parámetros

*lpSizeInHiMetric*<br/>
de Puntero al tamaño del objeto en unidades de HIMETRIC.

*lpSizeInPix*<br/>
enuncia Puntero al lugar donde se devolverá el tamaño del objeto en píxeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric

Convierte un tamaño de objeto especificado en píxeles en el dispositivo de pantalla en un tamaño especificado en unidades HIMETRIC (cada unidad es de 0,01 milímetros).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parámetros

*lpSizeInPix*<br/>
de Puntero al tamaño del objeto en píxeles.

*lpSizeInHiMetric*<br/>
enuncia Puntero al lugar donde se devolverá el tamaño del objeto en unidades HIMETRIC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

## <a name="see-also"></a>Consulte también

[Funciones](../../atl/reference/atl-functions.md)
