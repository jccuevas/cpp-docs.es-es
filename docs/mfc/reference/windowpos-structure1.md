---
title: WINDOWPOS (Structure1) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04cb2ae6fa2903ae5d9c015c188068e80c59ede7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421614"
---
# <a name="windowpos-structure1"></a>WINDOWPOS (Structure1)

El `WINDOWPOS` estructura contiene información sobre el tamaño y posición de una ventana.

## <a name="syntax"></a>Sintaxis

```
typedef struct tagWINDOWPOS { /* wp */
    HWND hwnd;
    HWND hwndInsertAfter;
    int x;
    int y;
    int cx;
    int cy;
    UINT flags;
} WINDOWPOS;
```

#### <a name="parameters"></a>Parámetros

*HWND*<br/>
Identifica la ventana.

*hwndInsertAfter*<br/>
Identifica la ventana detrás de la cual se coloca esta ventana.

*x*<br/>
Especifica la posición del borde izquierdo de la ventana.

*y*<br/>
Especifica la posición del borde derecho de la ventana.

*CX*<br/>
Especifica el ancho de la ventana, en píxeles.

*CY*<br/>
Especifica el alto de la ventana, en píxeles.

*flags*<br/>
Especifica las opciones de ubicación de ventana. Este miembro puede ser uno de los siguientes valores:

- SWP_DRAWFRAME dibuja un marco (definido en la descripción de la clase de la ventana) alrededor de la ventana. La ventana recibe un mensaje WM_NCCALCSIZE.

- SWP_FRAMECHANGED envía un WM_NCCALCSIZE mensajes a la ventana, incluso si no se está cambiando el tamaño de la ventana. Si no se especifica este marcador, se envía WM_NCCALCSIZE solo cuando se cambia el tamaño de la ventana.

- SWP_HIDEWINDOW oculta la ventana.

- SWP_NOACTIVATE no se activa la ventana.

- SWP_NOCOPYBITS descarta todo el contenido del área de cliente. Si no se especifica esta marca, el contenido del área de cliente válido se guarda y se vuelven a copiar en el área de cliente después de la ventana es de tamaño o cambiar de posición.

- SWP_NOMOVE conserva la posición actual (omite la `x` y `y` miembros).

- SWP_NOOWNERZORDER no cambia la posición de la ventana propietaria del orden Z.

- Tamaño actual conserva SWP_NOSIZE (omite la `cx` y `cy` miembros).

- No SWP_NOREDRAW redibuja cambios.

- SWP_NOREPOSITION igual que SWP_NOOWNERZORDER.

- SWP_NOSENDCHANGING evita que la ventana recibe el mensaje WM_WINDOWPOSCHANGING.

- SWP_NOZORDER conserva la ordenación actual (omite la `hwndInsertAfter` miembro).

- SWP_SHOWWINDOW muestra la ventana.

## <a name="requirements"></a>Requisitos

**Encabezado:** winuser.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

