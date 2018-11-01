---
title: MINMAXINFO (Estructura)
ms.date: 11/04/2016
f1_keywords:
- MINMAXINFO
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
ms.openlocfilehash: 11f55b1756623626769e21c006543b6993607b08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517850"
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO (Estructura)

El `MINMAXINFO` estructura contiene información sobre el tamaño de una ventana maximizada y posición y su tamaño máximo y mínimo de seguimiento.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagMINMAXINFO {
    POINT ptReserved;
    POINT ptMaxSize;
    POINT ptMaxPosition;
    POINT ptMinTrackSize;
    POINT ptMaxTrackSize;
} MINMAXINFO;
```

#### <a name="parameters"></a>Parámetros

*ptReserved*<br/>
Reservado para uso interno.

*ptMaxSize*<br/>
Especifica el ancho maximizado (point.x) y el alto maximizado (point.y) de la ventana.

*ptMaxPosition*<br/>
Especifica la posición del lado izquierdo de la ventana maximizada (point.x) y la posición de la parte superior de la ventana maximizada (point.y).

*ptMinTrackSize*<br/>
Especifica el ancho mínimo de seguimiento (point.x) y el mínimo alto (point.y) de la ventana de seguimiento.

*ptMaxTrackSize*<br/>
Especifica el máximo ancho (point.x) de seguimiento y la máxima altura (point.y) de la ventana de seguimiento.

## <a name="requirements"></a>Requisitos

**Encabezado:** winuser.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

