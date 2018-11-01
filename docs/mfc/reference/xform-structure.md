---
title: XFORM (Estructura)
ms.date: 11/04/2016
f1_keywords:
- XFORM
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
ms.openlocfilehash: 621a01accf3c323f8098da68667f06f48b9d169b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457259"
---
# <a name="xform-structure"></a>XFORM (Estructura)

El `XFORM` estructura tiene el formato siguiente:

## <a name="syntax"></a>Sintaxis

```
typedef struct  tagXFORM {  /* xfrm */
    FLOAT eM11;
    FLOAT eM12;
    FLOAT eM21;
    FLOAT eM22;
    FLOAT eDx;
    FLOAT eDy;
} XFORM;
```

## <a name="remarks"></a>Comentarios

El `XFORM` estructura especifica un espacio global para la transformación de espacio en la página. El `eDx` y `eDy` los miembros especifican los componentes de la traslación horizontal y vertical, respectivamente. En la tabla siguiente se muestra cómo se utilizan los demás miembros, dependiendo de la operación:

|Operación|eM11|eM12|eM21|eM22|
|---------------|----------|----------|----------|----------|
|`Rotation`|Coseno del ángulo de giro|Seno del ángulo de giro|Negativo seno del ángulo de giro|Coseno del ángulo de giro|
|`Scaling`|Componente de escalado horizontal|Nothing|Nothing|Componente de escala vertical|
|`Shear`|Nothing|Constante proporcionalidad horizontal|Constante proporcionalidad vertical|Nothing|
|`Reflection`|Componente horizontal de reflexión|Nothing|Nothing|Componente vertical de reflexión|

## <a name="requirements"></a>Requisitos

**Encabezado:** wingdi.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

