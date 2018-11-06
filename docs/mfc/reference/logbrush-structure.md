---
title: LOGBRUSH (Estructura)
ms.date: 11/04/2016
f1_keywords:
- LOGBRUSH
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
ms.openlocfilehash: 0ca635690843c6dae9db05b0a8cc246cf38ce814
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579782"
---
# <a name="logbrush-structure"></a>LOGBRUSH (Estructura)

El `LOGBRUSH` estructura define el estilo, color y el patrón de un pincel de diseño físico. Lo está usando el Windows [CreateBrushIndirect](/windows/desktop/api/wingdi/nf-wingdi-createbrushindirect) y [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen) funciones.

## <a name="syntax"></a>Sintaxis

```
typedef struct tag LOGBRUSH { /* lb */
    UINT lbStyle;
    COLORREF lbColor;
    LONG lbHatch;
} LOGBRUSH;
```

#### <a name="parameters"></a>Parámetros

*lbStyle*<br/>
Especifica el estilo de pincel. El `lbStyle` debe ser miembro de uno de los estilos siguientes:

- Pincel de BS_DIBPATTERN un modelo mediante un mapa de bits independientes del dispositivo (DIB) especificación definida. Si *lbStyle* es BS_DIBPATTERN, el `lbHatch` miembro contiene un identificador de un DIB empaquetado.

- Pincel de BS_DIBPATTERNPT un modelo mediante un mapa de bits independientes del dispositivo (DIB) especificación definida. Si *lbStyle* es BS_DIBPATTERNPT, el `lbHatch` miembro contiene un puntero a un DIB empaquetado.

- Pincel BS_HATCHED sombreada.

- Pincel BS_HOLLOW hueco.

- BS_NULL igual que BS_HOLLOW.

- Pincel de BS_PATTERN patrón definido por un mapa de bits de memoria.

- Pincel sólido BS_SOLID.

*lbColor*<br/>
Especifica el color en el que el pincel es va a dibujar. Si *lbStyle* es el estilo BS_HOLLOW o BS_PATTERN, *lbColor* se omite. Si *lbStyle* es BS_DIBPATTERN o BS_DIBPATTERNBT, la palabra de orden inferior de *lbColor* especifica si el `bmiColors` los miembros de la [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) estructura contienen explícita rojo, verde, azul (RGB) valores o índices en la paleta lógica realizada actualmente. El `lbColor` miembro debe ser uno de los siguientes valores:

- DIB_PAL_COLORS la tabla de colores consta de una matriz de índices de 16 bits en la paleta lógica realizada actualmente.

- DIB_RGB_COLORS la tabla de colores contiene los valores RGB literales.

*lbHatch*<br/>
Especifica un estilo de trama. El significado depende definido por el estilo de pincel *lbStyle*. Si *lbStyle* es BS_DIBPATTERN, el `lbHatch` miembro contiene un identificador de un DIB empaquetado. Si *lbStyle* es BS_DIBPATTERNPT, el `lbHatch` miembro contiene un puntero a un DIB empaquetado. Si *lbStyle* es BS_HATCHED, el `lbHatch` miembro especifica la orientación de las líneas que se usa para crear la trama. Puede ser uno de los siguientes valores:

- Sombreado de arriba, de izquierda a derecha de la 45 grados de un HS_BDIAGONAL

- HS_CROSS Horizontal y vertical rayado

- Rayado de 45 grados HS_DIAGCROSS

- Sombreado de hacia abajo, de izquierda a derecha de la 45 grados de un HS_FDIAGONAL

- Sombreado HS_HORIZONTAL Horizontal

- Sombreado Vertical HS_VERTICAL

Si *lbStyle* es BS_PATTERN, *lbHatch* es un identificador para el mapa de bits que define el patrón. Si *lbStyle* es BS_SOLID o BS_HOLLOW, *lbHatch* se omite.

## <a name="remarks"></a>Comentarios

Aunque *lbColor* controla el color de primer plano de un pincel de trama, el [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) y [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) el color de fondo del control de las funciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** wingdi.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

