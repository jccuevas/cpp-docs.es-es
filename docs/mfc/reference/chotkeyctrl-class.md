---
title: "CHotKeyCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHotKeyCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHotKeyCtrl class"
  - "hot key controls"
  - "Windows common controls [C++], CHotKeyCtrl"
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHotKeyCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de controles comunes de la tecla de acceso rápido de Windows.  
  
## Sintaxis  
  
```  
class CHotKeyCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHotKeyCtrl::CHotKeyCtrl](../Topic/CHotKeyCtrl::CHotKeyCtrl.md)|Crea un objeto `CHotKeyCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHotKeyCtrl::Create](../Topic/CHotKeyCtrl::Create.md)|Crea un control de la tecla de acceso rápido y lo asocia a un objeto de `CHotKeyCtrl` .|  
|[CHotKeyCtrl::CreateEx](../Topic/CHotKeyCtrl::CreateEx.md)|Crea un control de la tecla de acceso rápido con Windows especificado extendidas estilos y lo asocia a un objeto de `CHotKeyCtrl` .|  
|[CHotKeyCtrl::GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md)|Recupera los indicadores de código de tecla virtual y de modificador de una tecla de acceso rápido de una tecla de acceso rápido.|  
|[CHotKeyCtrl::GetHotKeyName](../Topic/CHotKeyCtrl::GetHotKeyName.md)|Recupera el nombre de la clave, en el juego de caracteres local, asignado a una tecla de acceso rápido.|  
|[CHotKeyCtrl::GetKeyName](../Topic/CHotKeyCtrl::GetKeyName.md)|Recupera el nombre de la clave, en el juego de caracteres local, asignado a código de tecla virtual especificado.|  
|[CHotKeyCtrl::SetHotKey](../Topic/CHotKeyCtrl::SetHotKey.md)|Establece la combinación de teclas de acceso rápido para un control de la tecla de acceso rápido.|  
|[CHotKeyCtrl::SetRules](../Topic/CHotKeyCtrl::SetRules.md)|Define las combinaciones válidas y no la combinación predeterminada del modificador de un control de la tecla de acceso rápido.|  
  
## Comentarios  
 Un “control de la tecla de acceso rápido” es una ventana que permita crear una tecla de acceso rápido.  Una “tecla de acceso rápido” es una combinación de teclas que el usuario puede presionar para realizar una acción rápidamente.  \(Por ejemplo, un usuario puede crear una tecla de acceso rápido que provoca una ventana especificada y la vez a la parte superior del orden Z.\) El control de la tecla de acceso rápido muestra las opciones de usuario y asegura que el usuario selecciona una combinación de teclas válida.  
  
 Este control \(y por consiguiente la clase de `CHotKeyCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 Cuando el usuario elige una combinación de teclas, la aplicación puede recuperar la combinación de teclas especificada del control y utilizar el mensaje de **WM\_SETHOTKEY** para configurar la tecla de acceso rápido en el sistema.  Siempre que el usuario presione la tecla de acceso rápido después, de cualquier parte del sistema, la ventana especificada en el mensaje de **WM\_SETHOTKEY** recibe un mensaje de `WM_SYSCOMMAND` que especifica **SC\_HOTKEY**.  Este mensaje activa la ventana que se reciben.  la tecla de acceso rápido sigue siendo válida hasta la aplicación que sale **WM\_SETHOTKEY** denominado.  
  
 Este mecanismo es diferente de la compatibilidad con la tecla de acceso rápido que depende del mensaje de **WM\_HOTKEY** y funciona Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) y [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) .  
  
 Para obtener más información sobre cómo utilizar `CHotKeyCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)