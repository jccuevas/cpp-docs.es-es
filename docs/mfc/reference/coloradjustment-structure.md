---
title: COLORADJUSTMENT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 7f88877fa009abf4e811ba0a99b7e0e1683f998a
ms.lasthandoff: 02/24/2017

---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT (Estructura)
El `COLORADJUSTMENT` estructura define los valores de ajuste de color utilizados por Windows `StretchBlt` y **StretchDIBits** funciones cuando el `StretchBlt` modo es **SEMITONOS**.  
  
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
 Especifica cómo se debe preparar la imagen de salida. Este miembro puede establecerse en **NULL** o cualquier combinación de los siguientes valores:  
  
- **CA_NEGATIVE** especifica que debe mostrarse el negativo de la imagen original.  
  
- **CA_LOG_FILTER** especifica que una función logarítmica debe aplicarse a la densidad de los colores de salida final. Esto aumentará el contraste de color cuando la luminancia es baja.  
  
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
 Especifica el valor de corrección gamma elevado para el rojo principal de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10.000 no significa ninguna corrección gamma.  
  
 *caGreenGamma*  
 Especifica el valor de corrección gamma elevado para el verde primario de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10.000 no significa ninguna corrección gamma.  
  
 *caBlueGamma*  
 Especifica el valor de corrección gamma n-ésima potencia del primario azul de los colores de origen. El valor debe ser en el intervalo de 2.500 a 65.000. Un valor de 10.000 no significa ninguna corrección gamma.  
  
 *caReferenceBlack*  
 Especifica la referencia de negra para los colores de origen. Los colores más oscuros que esto se tratan como negro. El valor debe oscilar entre 0 y 4.000.  
  
 *caReferenceWhite*  
 Especifica la referencia de blanca para los colores de origen. Los colores que son más claros que esto se tratan como blanco. El valor debe ser en el rango de 6.000 a 10.000.  
  
 *caContrast*  
 Especifica la cantidad de contraste que se aplicará al objeto de origen. El valor debe oscilar entre -100 y 100. Un valor de 0 significa que no hay ajuste de contraste.  
  
 *caBrightness*  
 Especifica la cantidad de brillo para aplicarse al objeto de origen. El valor debe oscilar entre -100 y 100. Un valor de 0 significa que no hay ajuste de brillo.  
  
 *caColorfulness*  
 Especifica la cantidad de colorfulness al aplicarse al objeto de origen. El valor debe oscilar entre -100 y 100. Un valor de 0 significa que no hay ajuste colorfulness.  
  
 *caRedGreenTint*  
 Especifica la cantidad de ajuste de tono de rojo o verde que se aplicará al objeto de origen. El valor debe oscilar entre -100 y 100. ¿Ajustar números positivos hacia el rojo y ajustar los números negativos hacia el verde. Un 0 significa que no hay ajuste de tono.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)



