---
title: WINDOWPOS estructura-1 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WINDOWPOS
dev_langs: C++
helpviewer_keywords: WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7db3991a6767e33c73857daf40a977ac5f6f0b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windowpos-structure1"></a>WINDOWPOS estructura-1
El `WINDOWPOS` estructura contiene información sobre el tamaño y la posición de una ventana.  
  
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
 *HWND*  
 Identifica la ventana.  
  
 *hwndInsertAfter*  
 Identifica la ventana detrás de la cual se coloca esta ventana.  
  
 *x*  
 Especifica la posición del borde izquierdo de la ventana.  
  
 *y*  
 Especifica la posición del borde derecho de la ventana.  
  
 `cx`  
 Especifica el ancho de la ventana, en píxeles.  
  
 `cy`  
 Especifica el alto de la ventana, en píxeles.  
  
 `flags`  
 Especifica las opciones de posición de ventana. Este miembro puede ser uno de los siguientes valores:  
  
- **SWP_DRAWFRAME** dibuja un marco (definido en la descripción de la clase de la ventana) alrededor de la ventana. La ventana recibe un `WM_NCCALCSIZE` mensaje.  
  
- **SWP_FRAMECHANGED** envía una `WM_NCCALCSIZE` de mensajes a la ventana, incluso si no se está cambiando el tamaño de la ventana. Si no se especifica este marcador, `WM_NCCALCSIZE` sólo se envía cuando se cambia el tamaño de la ventana.  
  
- **SWP_HIDEWINDOW** oculta la ventana.  
  
- `SWP_NOACTIVATE`No se activa la ventana.  
  
- **SWP_NOCOPYBITS** descarta todo el contenido del área de cliente. Si no se especifica este marcador, el contenido del área de cliente válido se guarda y se copian en el área de cliente después de la ventana es de tamaño o mover.  
  
- `SWP_NOMOVE`Conserva la posición actual (pasa por alto el **x** y **y** miembros).  
  
- **SWP_NOOWNERZORDER** no cambia la posición de la ventana propietaria del orden Z.  
  
- `SWP_NOSIZE`Conserva el tamaño actual (pasa por alto el **cx** y **cy** miembros).  
  
- **SWP_NOREDRAW** no volver a dibujarse cambios.  
  
- **SWP_NOREPOSITION** igual que **SWP_NOOWNERZORDER**.  
  
- **SWP_NOSENDCHANGING** impide que la ventana de recepción el `WM_WINDOWPOSCHANGING` mensaje.  
  
- `SWP_NOZORDER`Conserva la ordenación actual (pasa por alto el **hwndInsertAfter** miembro).  
  
- **SWP_SHOWWINDOW** muestra la ventana.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

