---
title: COLORADJUSTMENT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLORADJUSTMENT
dev_langs: C++
helpviewer_keywords: COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c5f99cbd94ffc1a5549367d8f21ad15a9398acb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT (Estructura)
El `COLORADJUSTMENT` estructura define los valores de ajuste de color utilizados por las ventanas `StretchBlt` y **StretchDIBits** funciones cuando la `StretchBlt` modo es **medios TONOS**.  
  
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
 *caSize*  
 Especifica el tamaño de la estructura en bytes.  
  
 *caFlags*  
 Especifica cómo se debe preparar la imagen de salida. Este miembro se puede establecer en **NULL** o cualquier combinación de los siguientes valores:  
  
- **CA_NEGATIVE** especifica que debe mostrarse el negativo de la imagen original.  
  
- **CA_LOG_FILTER** especifica que una función logarítmica debe aplicarse a la densidad de los colores de salida final. Esto aumentará el contraste de color cuando la luminancia sea baja.  
  
 *caIlluminantIndex*  
 Especifica la luminancia de la fuente de luz en la que se ve el objeto de imagen. Este miembro puede establecerse en uno de los siguientes valores:  
  
- **ILLUMINANT_EQUAL_ENERGY**  
  
- **ILLUMINANT_A**  
  
- **ILLUMINANT_B**  
  
- **ILLUMINANT_C**  
  
- **ILLUMINANT_D50**  
  
- **ILLUMINANT_D55**  
  
- **ILLUMINANT_D65**  
  
- **ILLUMINANT_D75**  
  
- **ILLUMINANT_F2**  
  
- **ILLUMINANT_TURNGSTEN**  
  
- **ILLUMINANT_DAYLIGHT**  
  
- **ILLUMINANT_FLUORESCENT**  
  
- **ILLUMINANT_NTSC**  
  
 *caRedGamma*  
 Especifica el valor de corrección gamma de n-ésima potencia de la red principal de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10.000 no significa ninguna corrección gamma.  
  
 *caGreenGamma*  
 Especifica el valor de corrección gamma de n-ésima potencia verde principal de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10.000 no significa ninguna corrección gamma.  
  
 *caBlueGamma*  
 Especifica el valor de corrección gamma de n-ésima potencia principal azul de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10.000 no significa ninguna corrección gamma.  
  
 *caReferenceBlack*  
 Especifica la referencia negra para los colores de origen. Todos los colores que son más oscuros que esto se tratan como negro. El valor debe estar en el intervalo de 0 a 4.000.  
  
 *caReferenceWhite*  
 Especifica la referencia de blanca para los colores de origen. Todos los colores que son más claros que esto se tratan como blanco. El valor debe ser en el rango de 6.000 a 10.000.  
  
 *caContrast*  
 Especifica la cantidad de contraste para aplicarse al objeto de origen. El valor debe ser en el intervalo de -100 y 100. Un valor de 0 significa que no hay ajuste de contraste.  
  
 *caBrightness*  
 Especifica la cantidad de brillo para aplicarse al objeto de origen. El valor debe ser en el intervalo de -100 y 100. Un valor de 0 significa que no hay ajuste de brillo.  
  
 *caColorfulness*  
 Especifica la cantidad de colorfulness para aplicarse al objeto de origen. El valor debe ser en el intervalo de -100 y 100. Un valor de 0 significa que no hay ajuste colorfulness.  
  
 *caRedGreenTint*  
 Especifica la cantidad de ajuste de tono rojo o verde para aplicarse al objeto de origen. El valor debe ser en el intervalo de -100 y 100. ¿Ajustar números positivos hacia el rojo y ajustar los números negativos hacia el verde. Un valor 0 significa no hay ajuste de tono.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)


