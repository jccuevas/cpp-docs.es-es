---
title: COLORADJUSTMENT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfa3d3393143b32e5e7a882918aedbc061b9b219
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431065"
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT (Estructura)

El `COLORADJUSTMENT` estructura define los valores de ajuste de color usados por el Windows `StretchBlt` y `StretchDIBits` funciones cuando el `StretchBlt` modo es semitono.

## <a name="syntax"></a>Sintaxis

```
typedef struct  tagCOLORADJUSTMENT {    /* ca */
    WORD caSize;
    WORD caFlags;
    WORD caIlluminantIndex;
    WORD caRedGamma;
    WORD caGreenGamma;
    WORD caBlueGamma;
    WORD caReferenceBlack;
    WORD caReferenceWhite;
    SHORT caContrast;
    SHORT caBrightness;
    SHORT caColorfulness;
    SHORT caRedGreenTint;
} COLORADJUSTMENT;
```

#### <a name="parameters"></a>Parámetros

*caSize*<br/>
Especifica el tamaño de la estructura en bytes.

*caFlags*<br/>
Especifica cómo se debe preparar la imagen de salida. Este miembro puede establecerse en NULL o cualquier combinación de los siguientes valores:

- CA_NEGATIVE especifica que debe mostrarse el negativo de la imagen original.

- CA_LOG_FILTER especifica que una función logarítmica debe aplicarse a la densidad de los colores de la salida final. Esto aumentará el contraste de color cuando la luminancia es baja.

*caIlluminantIndex*<br/>
Especifica la luminancia de la fuente de luz en la que se ve el objeto de imagen. Este miembro puede establecerse en uno de los valores siguientes:

- ILLUMINANT_EQUAL_ENERGY

- ILLUMINANT_A

- ILLUMINANT_B

- ILLUMINANT_C

- ILLUMINANT_D50

- ILLUMINANT_D55

- ILLUMINANT_D65

- ILLUMINANT_D75

- ILLUMINANT_F2

- ILLUMINANT_TURNGSTEN

- ILLUMINANT_DAYLIGHT

- ILLUMINANT_FLUORESCENT

- ILLUMINANT_NTSC

*caRedGamma*<br/>
Especifica el valor de corrección gamma elevado para la red principal de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10 000 significa que ninguna corrección gamma.

*caGreenGamma*<br/>
Especifica el valor de corrección gamma power enésimo verde del elemento principal de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10 000 significa que ninguna corrección gamma.

*caBlueGamma*<br/>
Especifica el valor de corrección gamma power nth del primario azul de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10 000 significa que ninguna corrección gamma.

*caReferenceBlack*<br/>
Especifica la referencia negra para los colores de origen. Los colores más oscuros que esto se tratan como negro. El valor debe ser en el intervalo comprendido entre 0 y 4000.

*caReferenceWhite*<br/>
Especifica la referencia en blanco para los colores de origen. Los colores que son más claros que esto se tratan como en blanco. El valor debe ser en el rango de 6.000 a 10.000.

*caContrast*<br/>
Especifica la cantidad de contraste que se aplica al objeto de origen. El valor debe ser en el intervalo entre -100 y 100. Un valor de 0 significa que ningún ajuste de contraste.

*caBrightness*<br/>
Especifica la cantidad de brillo para aplicarse al objeto de origen. El valor debe ser en el intervalo entre -100 y 100. Un valor de 0 significa que ningún ajuste de brillo.

*caColorfulness*<br/>
Especifica la cantidad de colorfulness para aplicarse al objeto de origen. El valor debe ser en el intervalo entre -100 y 100. Un valor de 0 significa que ningún ajuste colorfulness.

*caRedGreenTint*<br/>
Especifica la cantidad de ajuste de tono rojo o verde para aplicarse al objeto de origen. El valor debe ser en el intervalo entre -100 y 100. Podrían ajustar los números positivos hacia el rojo y ajustar los números negativos hacia el verde. Un 0 significa que ningún ajuste de tono.

## <a name="requirements"></a>Requisitos

**Encabezado:** wingdi.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)


