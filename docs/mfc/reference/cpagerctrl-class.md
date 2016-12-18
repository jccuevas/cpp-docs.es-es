---
title: "CPagerCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPagerCtrl class"
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPagerCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CPagerCtrl` ajusta el control de paginación de Windows, que puede desplazarse en la vista una ventana contenida que no ajusta la ventana que contiene.  
  
## Sintaxis  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPagerCtrl::CPagerCtrl](../Topic/CPagerCtrl::CPagerCtrl.md)|Crea un objeto `CPagerCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPagerCtrl::Create](../Topic/CPagerCtrl::Create.md)|Crea un control de paginación con estilos especificados y lo asocia al objeto actual de `CPagerCtrl` .|  
|[CPagerCtrl::CreateEx](../Topic/CPagerCtrl::CreateEx.md)|Crea un control de paginación con estilos extendidos especificados y lo asocia al objeto actual de `CPagerCtrl` .|  
|[CPagerCtrl::ForwardMouse](../Topic/CPagerCtrl::ForwardMouse.md)|Habilita o deshabilita reenviar los mensajes de [WM\_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) a la ventana del control actual de paginación.|  
|[CPagerCtrl::GetBkColor](../Topic/CPagerCtrl::GetBkColor.md)|Recupera el color de fondo del control actual de paginación.|  
|[CPagerCtrl::GetBorder](../Topic/CPagerCtrl::GetBorder.md)|Recupera el tamaño del borde del control actual de paginación.|  
|[CPagerCtrl::GetButtonSize](../Topic/CPagerCtrl::GetButtonSize.md)|Recupera el tamaño del botón del control actual de paginación.|  
|[CPagerCtrl::GetButtonState](../Topic/CPagerCtrl::GetButtonState.md)|Recupera el estado del botón especificado en el control actual de paginación.|  
|[CPagerCtrl::GetDropTarget](../Topic/CPagerCtrl::GetDropTarget.md)|Recupera la interfaz de [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) del control actual de paginación.|  
|[CPagerCtrl::GetScrollPos](../Topic/CPagerCtrl::GetScrollPos.md)|Recupera la posición de desplazamiento del control actual de paginación.|  
|[CPagerCtrl::IsButtonDepressed](../Topic/CPagerCtrl::IsButtonDepressed.md)|Indica si el botón especificado del control actual de paginación está en el estado de `pressed` .|  
|[CPagerCtrl::IsButtonGrayed](../Topic/CPagerCtrl::IsButtonGrayed.md)|Indica si el botón especificado del control actual de paginación está en el estado de `grayed` .|  
|[CPagerCtrl::IsButtonHot](../Topic/CPagerCtrl::IsButtonHot.md)|Indica si el botón especificado del control actual de paginación está en el estado de `hot` .|  
|[CPagerCtrl::IsButtonInvisible](../Topic/CPagerCtrl::IsButtonInvisible.md)|Indica si el botón especificado del control actual de paginación está en el estado de `invisible` .|  
|[CPagerCtrl::IsButtonNormal](../Topic/CPagerCtrl::IsButtonNormal.md)|Indica si el botón especificado del control actual de paginación está en el estado de `normal` .|  
|[CPagerCtrl::RecalcSize](../Topic/CPagerCtrl::RecalcSize.md)|Hace que el control actual de buscapersonas para actualizar el tamaño de la ventana contenida.|  
|[CPagerCtrl::SetBkColor](../Topic/CPagerCtrl::SetBkColor.md)|Establece el color de fondo del control actual de paginación.|  
|[CPagerCtrl::SetBorder](../Topic/CPagerCtrl::SetBorder.md)|Establece el tamaño del borde del control actual de paginación.|  
|[CPagerCtrl::SetButtonSize](../Topic/CPagerCtrl::SetButtonSize.md)|Establece el tamaño del botón del control actual de paginación.|  
|[CPagerCtrl::SetChild](../Topic/CPagerCtrl::SetChild.md)|Establece la ventana contenida del control actual de paginación.|  
|[CPagerCtrl::SetScrollPos](../Topic/CPagerCtrl::SetScrollPos.md)|Establece la posición de desplazamiento del control actual de paginación.|  
  
## Comentarios  
 El control de paginación es una ventana que contiene otra ventana que sea lineal y mayor que la que contiene, y permite desplazar la ventana contenida en la vista.  El control de paginación muestra dos botones de desplazamiento que automáticamente desaparezcan cuando la ventana contenida se desplazará a la extensión última columna, y reaparecen de otra manera.  Puede crear un control de paginación que desplaza horizontalmente o verticalmente.  
  
 Por ejemplo, si la aplicación tiene una barra de herramientas que no es de ancho en lugar de mostrar todos sus elementos, puede asignar la barra de herramientas a un control de paginación y los usuarios podrán mover la barra de herramientas a la izquierda o derecha de obtener acceso a todos los elementos.  La versión 4,0 \(versión 4,71 de Microsoft Internet Explorer de commctrl.dll\) presenta el control de paginación.  
  
 la clase de `CPagerCtrl` es derivada de la clase de [CWnd](../../mfc/reference/cwnd-class.md) .  Para obtener más información y un ejemplo de un control de paginación, vea [Controles de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760855).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CPagerCtrl Class](../../mfc/reference/cpagerctrl-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Pager Controls](http://msdn.microsoft.com/library/windows/desktop/bb760855)