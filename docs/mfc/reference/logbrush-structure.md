---
title: "LOGBRUSH (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LOGBRUSH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LOGBRUSH (estructura)"
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LOGBRUSH (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `LOGBRUSH` define el estilo, el color, y el modelo de un pincel físico.  Utiliza Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) y [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) funciona.  
  
## Sintaxis  
  
```  
  
      typedef struct tag LOGBRUSH { /* lb */  
   UINT lbStyle;  
   COLORREF lbColor;  
   LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### Parámetros  
 `lbStyle`  
 Especifica el estilo del lápiz.  El miembro de `lbStyle` debe ser uno de los estilos siguientes:  
  
-   Pincel de modelo de**BS\_DIBPATTERN**A definido por una especificación de \(DIB\) de mapa de bits independiente del dispositivo.  Si `lbStyle` es **BS\_DIBPATTERN**, el miembro de **lbHatch** contiene un identificador del archivo DIB empaquetado.  
  
-   Pincel de modelo de**BS\_DIBPATTERNPT**A definido por una especificación de \(DIB\) de mapa de bits independiente del dispositivo.  Si `lbStyle` es **BS\_DIBPATTERNPT**, el miembro de **lbHatch** contiene un puntero al archivo DIB empaquetado.  
  
-   Pincel tramado de**BS\_HATCHED**.  
  
-   Pincel de**BS\_HOLLOW**Hollow.  
  
-   **BS\_NULL** Same que **BS\_HOLLOW**.  
  
-   Pincel de modelo de**BS\_PATTERN**definido por un mapa de bits de memoria.  
  
-   Pincel sólido de**BS\_SOLID**.  
  
 `lbColor`  
 Especifica el color en las que el pincel se debe dibujar.  Si `lbStyle` es el estilo de **BS\_HOLLOW** o de **BS\_PATTERN** , se omite **lbColor** .  Si `lbStyle` es **BS\_DIBPATTERN** o **BS\_DIBPATTERNBT**, word de orden inferior de **lbColor** especifica si los miembros de **bmiColors** de la estructura de [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) contienen explícito rojo, verde, los valores azul de \(RGB\) o índices en la paleta lógica actualmente observada.  El miembro de **lbColor** debe ser uno de los siguientes valores:  
  
-   La paleta de colores de**DIB\_PAL\_COLORS**The consta de una matriz de índices de 16 bits en la paleta lógica actualmente observada.  
  
-   La paleta de colores de**DIB\_RGB\_COLORS**The contiene valores literales RGB.  
  
 *lbHatch*  
 Especifica un estilo de trama.  El significado depende del estilo del lápiz definido por `lbStyle`.  Si `lbStyle` es **BS\_DIBPATTERN**, el miembro de **lbHatch** contiene un identificador del archivo DIB empaquetado.  Si `lbStyle` es **BS\_DIBPATTERNPT**, el miembro de **lbHatch** contiene un puntero al archivo DIB empaquetado.  Si `lbStyle` es **BS\_HATCHED**, el miembro de **lbHatch** especifica la guía de las líneas empleadas para crear el sombreado.  Puede ser uno de los siguientes valores:  
  
-   `HS_BDIAGONAL` A 45 grados de ascendente, sombreado de izquierda a derecha  
  
-   sombreado doble horizontal y vertical de`HS_CROSS`  
  
-   sombreado doble de 45 \- grado de`HS_DIAGCROSS`  
  
-   `HS_FDIAGONAL` A 45 grados de abajo, sombreado de izquierda a derecha  
  
-   sombreado de`HS_HORIZONTAL`Horizontal  
  
-   sombreado de`HS_VERTICAL`Vertical  
  
 Si `lbStyle` es **BS\_PATTERN**, **lbHatch** es un identificador al mapa de bits que define el modelo.  Si `lbStyle` es **BS\_SOLID** o **BS\_HOLLOW**, se omite **lbHatch** .  
  
## Comentarios  
 Aunque **lbColor** controla el color de primer plano de un pincel tramado, las funciones de [CDC::SetBkMode](../Topic/CDC::SetBkMode.md) y de [CDC::SetBkColor](../Topic/CDC::SetBkColor.md) controlan el color de fondo.  
  
## Requisitos  
 **Encabezado:** wingdi.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)