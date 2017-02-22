---
title: "COLORADJUSTMENT (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLORADJUSTMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLORADJUSTMENT (estructura)"
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# COLORADJUSTMENT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `COLORADJUSTMENT` define los valores de ajuste en color utilizados por Windows `StretchBlt` y **StretchDIBits** funciona cuando el modo de `StretchBlt` es **HALFTONE**.  
  
## Sintaxis  
  
```  
  
      typedef struct  tagCOLORADJUSTMENT {    /* ca */  
    WORD  caSize;  
    WORD  caFlags;  
    WORD  caIlluminantIndex;  
    WORD  caRedGamma;  
    WORD  caGreenGamma;  
    WORD  caBlueGamma;  
    WORD  caReferenceBlack;  
    WORD  caReferenceWhite;  
    SHORT caContrast;  
    SHORT caBrightness;  
    SHORT caColorfulness;  
    SHORT caRedGreenTint;  
} COLORADJUSTMENT;  
```  
  
#### Parámetros  
 *caSize*  
 Especifica el tamaño de la estructura en bytes.  
  
 *caFlags*  
 Especifica cómo la imagen de salida debe ser preparada.  Este miembro se puede establecer en **nulo** o cualquier combinación de los siguientes valores:  
  
-   **CA\_NEGATIVE** especifica que la negativa de la imagen original debe mostrar.  
  
-   **CA\_LOG\_FILTER** especifica que una función logarítmica se debe aplicar a la densidad final de los colores de salida.  Esto aumentará el contraste de color cuando la luminancia es baja.  
  
 *caIlluminantIndex*  
 Especifica la luminancia de la fuente de luz en la que se ve el objeto de imagen.  Este miembro se puede establecer en uno de los siguientes valores:  
  
-   **ILLUMINANT\_EQUAL\_ENERGY**  
  
-   **ILLUMINANT\_A**  
  
-   **ILLUMINANT\_B**  
  
-   **ILLUMINANT\_C**  
  
-   **ILLUMINANT\_D50**  
  
-   **ILLUMINANT\_D55**  
  
-   **ILLUMINANT\_D65**  
  
-   **ILLUMINANT\_D75**  
  
-   **ILLUMINANT\_F2**  
  
-   **ILLUMINANT\_TURNGSTEN**  
  
-   **ILLUMINANT\_DAYLIGHT**  
  
-   **ILLUMINANT\_FLUORESCENT**  
  
-   **ILLUMINANT\_NTSC**  
  
 *caRedGamma*  
 Especifica el enésimo valor de la gamma\- corrección de energía para el rojo primario de color de origen.  El valor debe estar en el intervalo comprendido entre 2.500 y 65.000.  Un valor de 10.000 es sin gamma\- corrección.  
  
 *caGreenGamma*  
 Especifica el enésimo valor de la gamma\- corrección de energía para el verde primario de color de origen.  El valor debe estar en el intervalo comprendido entre 2.500 y 65.000.  Un valor de 10.000 es sin gamma\- corrección.  
  
 *caBlueGamma*  
 Especifica el enésimo valor de la gamma\- corrección de energía del color azul primario de color de origen.  El valor debe estar en el intervalo comprendido entre 2.500 y 65.000.  Un valor de 10.000 es sin gamma\- corrección.  
  
 *caReferenceBlack*  
 Especifica la referencia negra para los colores de origen.  Cualquier color que sea más oscuro que esto se trata como negro.  El valor debe estar en el intervalo comprendido entre 0 y 4.000.  
  
 *caReferenceWhite*  
 Especifica la referencia blanca de colores de origen.  Cualquier color que sea más ligero que esto se trata como blanco.  El valor debe estar en el intervalo comprendido entre 6.000 y 10.000.  
  
 *caContrast*  
 Especifica la cantidad de contraste para aplicar al objeto de origen.  El valor debe estar en el intervalo comprendido entre \-100 y 100.  Un valor de 0 no indica ningún ajuste de contraste.  
  
 *caBrightness*  
 Especifica la cantidad de ajuste que aplicar al objeto de origen.  El valor debe estar en el intervalo comprendido entre \-100 y 100.  Un valor de 0 no indica ningún ajuste de ajuste.  
  
 *caColorfulness*  
 Especifica la cantidad de colorfulness que aplicar al objeto de origen.  El valor debe estar en el intervalo comprendido entre \-100 y 100.  Un valor de 0 no indica ningún ajuste de colorfulness.  
  
 *caRedGreenTint*  
 Especifica la cantidad de ajuste de tono de rojo o verde se aplicará al objeto de origen.  El valor debe estar en el intervalo comprendido entre \-100 y 100.  Los números positivos ajustarían como ajuste de rojo y los números negativos hacia verde.  El valor 0 no indica ningún ajuste de tono.  
  
## Requisitos  
 **Encabezado:** wingdi.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../Topic/CDC::GetColorAdjustment.md)