---
title: LOGBRUSH (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
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
ms.openlocfilehash: eea7caf6139fd43dd77163271701d170c7a744e2
ms.lasthandoff: 02/24/2017

---
# <a name="logbrush-structure"></a>LOGBRUSH (Estructura)
El `LOGBRUSH` estructura define el estilo, el color y el patrón de un pincel de diseño físico. Se utiliza Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) y [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) funciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lbStyle`  
 Especifica el estilo de pincel. El `lbStyle` miembro debe ser uno de los siguientes estilos:  
  
- **BS_DIBPATTERN** un pincel de modelo definido por la especificación de un mapa de bits independiente del dispositivo (DIB). Si `lbStyle` es **BS_DIBPATTERN**, **lbHatch** miembro contiene un identificador de un DIB empaquetado.  
  
- **BS_DIBPATTERNPT** un pincel de modelo definido por la especificación de un mapa de bits independiente del dispositivo (DIB). Si `lbStyle` es **BS_DIBPATTERNPT**, **lbHatch** miembro contiene un puntero a un DIB empaquetado.  
  
- **BS_HATCHED** sombreada pincel.  
  
- **BS_HOLLOW** hueco pincel.  
  
- **BS_NULL** igual que **BS_HOLLOW**.  
  
- **BS_PATTERN** patrón pincel definido por un mapa de bits de memoria.  
  
- **BS_SOLID** pincel sólido.  
  
 `lbColor`  
 Especifica el color en el que el pincel es necesario dibujar. Si `lbStyle` es el **BS_HOLLOW** o **BS_PATTERN** estilo, **lbColor** se omite. Si `lbStyle` es **BS_DIBPATTERN** o **BS_DIBPATTERNBT**, la palabra de orden inferior de **lbColor** especifica si la **bmiColors** los miembros de la [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) estructura contienen explícita rojo, verde, azul (RGB) valores o índices en la paleta lógica actualmente realizada. El **lbColor** miembro debe ser uno de los siguientes valores:  
  
- **DIB_PAL_COLORS** la tabla de colores se compone de una matriz de índices de 16 bits en la paleta lógica actualmente realizada.  
  
- **DIB_RGB_COLORS** la tabla de colores contiene valores RGB literales.  
  
 *lbHatch*  
 Especifica el estilo de trama. El significado depende el estilo de pincel definido por `lbStyle`. Si `lbStyle` es **BS_DIBPATTERN**, **lbHatch** miembro contiene un identificador de un DIB empaquetado. Si `lbStyle` es **BS_DIBPATTERNPT**, **lbHatch** miembro contiene un puntero a un DIB empaquetado. Si `lbStyle` es **BS_HATCHED**, **lbHatch** miembro especifica la orientación de las líneas utilizadas para crear la trama. Puede ser uno de los siguientes valores:  
  
- `HS_BDIAGONAL`Una trama de 45 grados ascendente, de izquierda a derecha  
  
- `HS_CROSS`Sombreado horizontal y vertical  
  
- `HS_DIAGCROSS`rayado de 45 grados  
  
- `HS_FDIAGONAL`Una trama de 45 grados hacia abajo, de izquierda a derecha  
  
- `HS_HORIZONTAL`Sombreado horizontal  
  
- `HS_VERTICAL`Sombreado vertical  
  
 Si `lbStyle` es **BS_PATTERN**, **lbHatch** es un identificador para el mapa de bits que define el patrón. Si `lbStyle` es **BS_SOLID** o **BS_HOLLOW**, **lbHatch** se omite.  
  
## <a name="remarks"></a>Comentarios  
 Aunque **lbColor** controla el color de primer plano de un pincel de trama, el [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) y [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) funciones controlan el color de fondo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


