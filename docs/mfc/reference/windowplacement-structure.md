---
title: WINDOWPLACEMENT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WINDOWPLACEMENT
dev_langs: C++
helpviewer_keywords: WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e73065cdf20d68b1da4ba77d1ad555e2bf95e937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT (Estructura)
El `WINDOWPLACEMENT` estructura contiene información acerca de la ubicación de una ventana en la pantalla**.**  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
    UINT length;  
    UINT flags;  
    UINT showCmd;  
    POINT ptMinPosition;  
    POINT ptMaxPosition;  
    RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *length*  
 Especifica la longitud, en bytes, de la estructura**.**  
  
 `flags`  
 Especifica las marcas que controlan la posición de la ventana minimizada y el método por el que se restaura la ventana. Este miembro puede ser uno o ambos de los siguientes indicadores:  
  
- **WPF_SETMINPOSITION** especifica que se pueden especificar las posiciones x e y de la ventana minimizada**.** Debe ser esta marca especifica si las coordenadas se establecen los **ptMinPosition** miembro.  
  
- **WPF_RESTORETOMAXIMIZED** especifica que se maximiza la ventana restaurada, independientemente de si se estaba maximizada antes de se minimiza. Esta opción es válida sólo la próxima vez que se restaura la ventana. No cambia el comportamiento de restauración predeterminado. Esta marca solo es válido cuando el **SW_SHOWMINIMIZED** se ha indicado el **showCmd** miembro.  
  
 *showCmd*  
 Especifica el estado de visualización actual de la ventana. Este miembro puede ser uno de los siguientes valores:  
  
- **SW_HIDE** oculta la ventana y pasa la activación a otra ventana.  
  
- **SW_MINIMIZE** minimiza la ventana especificada y activa la ventana de nivel superior en la lista del sistema.  
  
- **SW_RESTORE** activa y muestra una ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición original (igual que **SW_SHOWNORMAL**).  
  
- **SW_SHOW** activa una ventana y lo muestra en su tamaño y posición actuales.  
  
- **SW_SHOWMAXIMIZED** activa una ventana y lo muestra como una ventana maximizada.  
  
- **SW_SHOWMINIMIZED** activa una ventana y lo muestra como un icono.  
  
- **SW_SHOWMINNOACTIVE** muestra una ventana como un icono. La ventana que está actualmente activa permanece activa.  
  
- **SW_SHOWNA** muestra una ventana en su estado actual. La ventana que está actualmente activa permanece activa.  
  
- **SW_SHOWNOACTIVATE** muestra una ventana en su tamaño y posición más recientes. La ventana que está actualmente activa permanece activa.  
  
- **SW_SHOWNORMAL** activa y muestra una ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición original (igual que **SW_RESTORE**).  
  
 *ptMinPosition*  
 Especifica la posición de la esquina superior izquierda de la ventana cuando se minimiza la ventana.  
  
 `ptMaxPosition`  
 Especifica la posición de la esquina superior izquierda de la ventana cuando la ventana está maximizada.  
  
 *rcNormalPosition*  
 Especifica las coordenadas de la ventana cuando la ventana está en la posición normal (restaurada).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

