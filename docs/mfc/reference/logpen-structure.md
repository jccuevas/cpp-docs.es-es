---
title: LOGPEN (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a535858a0d5540db481fd42918b4079f30c90728
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375678"
---
# <a name="logpen-structure"></a>LOGPEN (Estructura)

El `LOGPEN` estructura define el estilo, ancho y color de un lápiz, un objeto de dibujo que se usa para dibujar líneas y bordes. El [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) función usa el `LOGPEN` estructura.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagLOGPEN {  /* lgpn */
    UINT lopnStyle;
    POINT lopnWidth;
    COLORREF lopnColor;
} LOGPEN;
```

#### <a name="parameters"></a>Parámetros

*lopnStyle*<br/>
Especifica el tipo de lápiz. Este miembro puede ser uno de los siguientes valores:

- PS_SOLID crea un lápiz sólido.

- PS_DASH crea una pluma discontinua. (Válido solo cuando el ancho del lápiz es 1).

- PS_DOT crea un lápiz con puntos. (Válido solo cuando el ancho del lápiz es 1).

- PS_DASHDOT crea una pluma con alternos guiones y puntos. (Válido solo cuando el ancho del lápiz es 1).

- PS_DASHDOTDOT crea un lápiz con guiones y puntos dobles alternos. (Válido solo cuando el ancho del lápiz es 1).

- PS_NULL crea una pluma de null.

- PS_INSIDEFRAME crea genera un lápiz que dibuja una línea dentro del marco de las formas cerradas en GDI funciones que especifican un rectángulo delimitador de salida (por ejemplo, el `Ellipse`, `Rectangle`, `RoundRect`, `Pie`, y `Chord` miembro funciones). Cuando se usa este estilo con GDI funciones que no especifican un rectángulo delimitador de salida (por ejemplo, el `LineTo` función miembro), el área de dibujo de la pluma no está limitado por un marco.

     Si un lápiz tiene el estilo PS_INSIDEFRAME y un color que no coincide con un color en la tabla de colores lógico, el lápiz se dibuja con un color interpolado. El estilo de lápiz PS_SOLID no se puede usar para crear un lápiz con un color interpolado. El estilo PS_INSIDEFRAME es idéntico al PS_SOLID si el ancho del lápiz es menor o igual que 1.

     Cuando se usa el estilo PS_INSIDEFRAME con objetos GDI generados por funciones distintas de `Ellipse`, `Rectangle`, y `RoundRect`, la línea no puede ser totalmente dentro del marco especificado.

*lopnWidth*<br/>
Especifica el ancho del lápiz, en unidades lógicas. Si el `lopnWidth` miembro es 0, el lápiz es 1 píxel de ancho en dispositivos de trama independientemente del modo de asignación actual.

*lopnColor*<br/>
Especifica el color del lápiz.

## <a name="remarks"></a>Comentarios

El `y` valor en el [punto](../../mfc/reference/point-structure1.md) de estructura para el `lopnWidth` miembro no se usa.

## <a name="requirements"></a>Requisitos

**Encabezado:** wingdi.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

