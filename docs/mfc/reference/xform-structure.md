---
title: XFORM (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab1a2fe23f364dc35a2368d325db5e4274fc8e64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411643"
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

