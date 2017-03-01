---
title: WINDOWPOS estructura-1 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
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
ms.openlocfilehash: 522b15d630c3a5a3593010250db0491601493c69
ms.lasthandoff: 02/24/2017

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
 Identifica la ventana subyacente que se coloca esta ventana.  
  
 *x*  
 Especifica la posición del borde izquierdo de la ventana.  
  
 *y*  
 Especifica la posición del borde derecho de la ventana.  
  
 `cx`  
 Especifica el ancho de la ventana, en píxeles.  
  
 `cy`  
 Especifica el alto de la ventana, en píxeles.  
  
 `flags`  
 Especifica las opciones de ubicación de ventana. Este miembro puede ser uno de los siguientes valores:  
  
- **SWP_DRAWFRAME** dibuja un marco (definido en la descripción de la clase de la ventana) alrededor de la ventana. La ventana recibe un `WM_NCCALCSIZE` mensaje.  
  
- **SWP_FRAMECHANGED** envía una `WM_NCCALCSIZE` a la ventana de mensajes incluso si no se está cambiando el tamaño de la ventana. Si no se especifica este marcador, `WM_NCCALCSIZE` sólo se envía cuando se cambia el tamaño de la ventana.  
  
- **SWP_HIDEWINDOW** oculta la ventana.  
  
- `SWP_NOACTIVATE`No se activa la ventana.  
  
- **SWP_NOCOPYBITS** descarta todo el contenido del área de cliente. Si no se especifica este marcador, el contenido válido del área de cliente se guarda y se copia en el área de cliente después de la ventana es un tamaño o posición.  
  
- `SWP_NOMOVE`Conserva la posición actual (omite el **x** y **y** miembros).  
  
- **SWP_NOOWNERZORDER** no cambia la posición de la ventana de propietario en el orden Z.  
  
- `SWP_NOSIZE`Conserva el tamaño actual (omite el **cx** y **cy** miembros).  
  
- **SWP_NOREDRAW** no volver a dibujar cambios.  
  
- **SWP_NOREPOSITION** igual que **SWP_NOOWNERZORDER**.  
  
- **SWP_NOSENDCHANGING** evita que la ventana de recepción el `WM_WINDOWPOSCHANGING` mensaje.  
  
- `SWP_NOZORDER`Conserva el orden actual (omite el **hwndInsertAfter** miembro).  
  
- **SWP_SHOWWINDOW** muestra la ventana.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)


