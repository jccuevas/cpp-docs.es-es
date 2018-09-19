---
title: WINDOWPLACEMENT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dbd9a921194146e260eb79f5266311caa3d0300
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026200"
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT (Estructura)
El `WINDOWPLACEMENT` estructura contiene información sobre la colocación de una ventana en la pantalla.  
  
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
Especifica la longitud, en bytes, de la estructura.  
  
*flags*  
Especifica las marcas que controlan la posición de la ventana minimizada y el método por el que la ventana está restaurada. Este miembro puede ser una o ambas de las marcas siguientes:  
  
 - WPF_SETMINPOSITION especifica que se pueden especificar las posiciones x y y de la ventana minimizada. Debe ser esta marca especifica si las coordenadas se establecen el `ptMinPosition` miembro.  
      
 - WPF_RESTORETOMAXIMIZED especifica que se maximiza la ventana restaurada, independientemente de si se estaba maximizada antes de estaba minimizado. Esta configuración es válida sólo la próxima vez que la ventana está restaurada. No se cambia el comportamiento de restauración predeterminado. Esta marca solo es válida cuando se especifica el valor SW_SHOWMINIMIZED para el `showCmd` miembro.  
  
*showCmd*  
Especifica el estado actual de visualización de la ventana. Este miembro puede ser uno de los siguientes valores:  
  
 - SW_HIDE oculta la ventana y pasa la activación a otra ventana.  
      
 - SW_MINIMIZE minimiza la ventana especificada y activa la ventana de nivel superior en la lista del sistema.  
      
 - SW_RESTORE activa y muestra una ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición (igual que SW_SHOWNORMAL) original.  
      
 - SW_SHOW activa una ventana y se muestra en su tamaño y posición actuales.  
      
 - SW_SHOWMAXIMIZED activa una ventana y lo muestra como una ventana maximizada.  
      
 - SW_SHOWMINIMIZED activa una ventana y lo muestra como un icono.  
      
 - SW_SHOWMINNOACTIVE muestra una ventana como un icono. La ventana que está activa actualmente permanece activa.  
      
 - SW_SHOWNA muestra una ventana en su estado actual. La ventana que está activa actualmente permanece activa.  
      
 - SW_SHOWNOACTIVATE muestra una ventana en su tamaño y posición más reciente. La ventana que está activa actualmente permanece activa.  
      
 - SW_SHOWNORMAL activa y muestra una ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición (igual que SW_RESTORE) original.  
  
*ptMinPosition*  
Especifica la posición de la esquina superior izquierda de la ventana cuando la ventana está minimizada.  
  
*ptMaxPosition*  
Especifica la posición de la esquina superior izquierda de la ventana cuando la ventana está maximizada.  
  
*rcNormalPosition*  
Especifica las coordenadas de la ventana cuando la ventana está en la posición normal (restaurada).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

