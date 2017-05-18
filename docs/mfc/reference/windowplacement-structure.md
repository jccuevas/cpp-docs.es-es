---
title: WINDOWPLACEMENT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 62cf7003f43d50d5998dd527ae5ad7b10ab95686
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
  
- **WPF_SETMINPOSITION** especifica que se pueden especificar las posiciones x y y de la ventana minimizada**.** Esta marca debe ser especifica si las coordenadas se establecen en los **ptMinPosition** miembro.  
  
- **WPF_RESTORETOMAXIMIZED** especifica que se maximiza la ventana restaurada, independientemente de si se estaba maximizada antes de se ha minimizado. Esta configuración es válida sólo la próxima vez que se restaura la ventana. No cambia el comportamiento de restauración predeterminado. Esta marca solo es válido cuando el **SW_SHOWMINIMIZED** valor especificado para la **showCmd** miembro.  
  
 *showCmd*  
 Especifica el estado actual de la presentación de la ventana. Este miembro puede ser uno de los siguientes valores:  
  
- **SW_HIDE** oculta la ventana y pasa la activación a otra ventana.  
  
- **SW_MINIMIZE** minimiza la ventana especificada y se activa la ventana de nivel superior en la lista del sistema.  
  
- **SW_RESTORE** activa y muestra una ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición originales (igual que **SW_SHOWNORMAL**).  
  
- **SW_SHOW** una ventana se activa y se muestra en su tamaño y posición actuales.  
  
- **SW_SHOWMAXIMIZED** activa una ventana y lo muestra como una ventana maximizada.  
  
- **SW_SHOWMINIMIZED** activa una ventana y lo muestra como un icono.  
  
- **SW_SHOWMINNOACTIVE** muestra una ventana como un icono. La ventana activa permanece activa.  
  
- **SW_SHOWNA** muestra una ventana en su estado actual. La ventana activa permanece activa.  
  
- **SW_SHOWNOACTIVATE** muestra una ventana de su tamaño y posición más recientes. La ventana activa permanece activa.  
  
- **SW_SHOWNORMAL** activa y muestra una ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición originales (igual que **SW_RESTORE**).  
  
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


