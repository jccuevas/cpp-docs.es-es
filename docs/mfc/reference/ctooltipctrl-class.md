---
title: "CToolTipCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolTipCtrl class"
  - "data tips [C++]"
  - "información sobre herramientas [C++], tool tip controls"
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula la funcionalidad de un “control de información sobre herramientas,” una pequeña ventana emergente que muestra una única línea de texto que describe el propósito de una herramienta de una aplicación.  
  
## Sintaxis  
  
```  
class CToolTipCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CToolTipCtrl::CToolTipCtrl](../Topic/CToolTipCtrl::CToolTipCtrl.md)|Crea un objeto `CToolTipCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CToolTipCtrl::Activate](../Topic/CToolTipCtrl::Activate.md)|Activa y desactiva el control de información sobre herramientas.|  
|[CToolTipCtrl::AddTool](../Topic/CToolTipCtrl::AddTool.md)|Registra una herramienta en el control de información sobre herramientas.|  
|[CToolTipCtrl::AdjustRect](../Topic/CToolTipCtrl::AdjustRect.md)|Convierte entre el rectángulo de la vista de texto de un control de información sobre herramientas y su rectángulo de ventana.|  
|[CToolTipCtrl::Create](../Topic/CToolTipCtrl::Create.md)|Crea un control de información sobre herramientas y lo asocia a un objeto de `CToolTipCtrl` .|  
|[CToolTipCtrl::CreateEx](../Topic/CToolTipCtrl::CreateEx.md)|Crea un control de información sobre herramientas con Windows especificado extendidas estilos y lo asocia a un objeto de `CToolTipCtrl` .|  
|[CToolTipCtrl::DelTool](../Topic/CToolTipCtrl::DelTool.md)|Quita una herramienta de control tooltip.|  
|[CToolTipCtrl::GetBubbleSize](../Topic/CToolTipCtrl::GetBubbleSize.md)|Recupera el tamaño de la información sobre herramientas.|  
|[CToolTipCtrl::GetCurrentTool](../Topic/CToolTipCtrl::GetCurrentTool.md)|Recupera información, como el tamaño, la posición, y el texto, la ventana de información sobre herramientas del control actual de información sobre herramientas muestra.|  
|[CToolTipCtrl::GetDelayTime](../Topic/CToolTipCtrl::GetDelayTime.md)|Recupera la inicial, el elemento emergente, y duraciones de reshow definidas actualmente para un control de información sobre herramientas.|  
|[CToolTipCtrl::GetMargin](../Topic/CToolTipCtrl::GetMargin.md)|Recupera la parte superior, izquierda, basa, y right los márgenes establecidos para una ventana de información sobre herramientas.|  
|[CToolTipCtrl::GetMaxTipWidth](../Topic/CToolTipCtrl::GetMaxTipWidth.md)|Recupera el ancho máximo para una ventana de información sobre herramientas.|  
|[CToolTipCtrl::GetText](../Topic/CToolTipCtrl::GetText.md)|Recupera el texto que un control de información sobre herramientas mantiene de herramienta.|  
|[CToolTipCtrl::GetTipBkColor](../Topic/CToolTipCtrl::GetTipBkColor.md)|Recupera el color de fondo en una ventana de información sobre herramientas.|  
|[CToolTipCtrl::GetTipTextColor](../Topic/CToolTipCtrl::GetTipTextColor.md)|Recupera el color del texto en una ventana de información sobre herramientas.|  
|[CToolTipCtrl::GetTitle](../Topic/CToolTipCtrl::GetTitle.md)|Recupera el título del control actual de información sobre herramientas.|  
|[CToolTipCtrl::GetToolCount](../Topic/CToolTipCtrl::GetToolCount.md)|Recupera un recuento de las herramientas que mantiene un control tooltip.|  
|[CToolTipCtrl::GetToolInfo](../Topic/CToolTipCtrl::GetToolInfo.md)|Recupera la información que un control de información sobre herramientas mantiene sobre una herramienta.|  
|[CToolTipCtrl::HitTest](../Topic/CToolTipCtrl::HitTest.md)|Prueba un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada.  Si es así información de recupera a la herramienta.|  
|[CToolTipCtrl::Pop](../Topic/CToolTipCtrl::Pop.md)|Quita una ventana mostrada de información sobre herramientas de la vista.|  
|[CToolTipCtrl::Popup](../Topic/CToolTipCtrl::Popup.md)|Hace que el control actual de información sobre herramientas en la pantalla en coordenadas del último mensaje del mouse.|  
|[CToolTipCtrl::RelayEvent](../Topic/CToolTipCtrl::RelayEvent.md)|Pasa un mensaje del mouse en un control tooltip para procesar.|  
|[CToolTipCtrl::SetDelayTime](../Topic/CToolTipCtrl::SetDelayTime.md)|Establece el inicial, el elemento emergente, y duraciones de reshow para un control de información sobre herramientas.|  
|[CToolTipCtrl::SetMargin](../Topic/CToolTipCtrl::SetMargin.md)|Establece la parte superior, izquierda, basa, y right los márgenes de una ventana de información sobre herramientas.|  
|[CToolTipCtrl::SetMaxTipWidth](../Topic/CToolTipCtrl::SetMaxTipWidth.md)|Establece el ancho máximo para una ventana de información sobre herramientas.|  
|[CToolTipCtrl::SetTipBkColor](../Topic/CToolTipCtrl::SetTipBkColor.md)|Establece el color de fondo en una ventana de información sobre herramientas.|  
|[CToolTipCtrl::SetTipTextColor](../Topic/CToolTipCtrl::SetTipTextColor.md)|Establece el color del texto en una ventana de información sobre herramientas.|  
|[CToolTipCtrl::SetTitle](../Topic/CToolTipCtrl::SetTitle.md)|Agrega una cadena estándar de icono y title en una información sobre herramientas.|  
|[CToolTipCtrl::SetToolInfo](../Topic/CToolTipCtrl::SetToolInfo.md)|Establece la información que una información sobre herramientas mantiene de herramienta.|  
|[CToolTipCtrl::SetToolRect](../Topic/CToolTipCtrl::SetToolRect.md)|Establece un nuevo rectángulo delimitador para la herramienta.|  
|[CToolTipCtrl::SetWindowTheme](../Topic/CToolTipCtrl::SetWindowTheme.md)|Establece el estilo visual de la ventana de información sobre herramientas.|  
|[CToolTipCtrl::Update](../Topic/CToolTipCtrl::Update.md)|Fuerza la herramienta actual que se rediseñará.|  
|[CToolTipCtrl::UpdateTipText](../Topic/CToolTipCtrl::UpdateTipText.md)|Establece el texto de información sobre herramientas de una herramienta.|  
  
## Comentarios  
 Una “nombre herramienta” es una ventana, como una ventana secundaria o un control, o un área rectangular definido por la aplicación dentro de un área de cliente de ventana.  Una información sobre herramientas se oculta la mayoría de las veces, produciendo sólo cuando el usuario coloca el cursor en una herramienta y deja allí para aproximadamente la mitad segundo.  La información sobre herramientas aparece cerca del cursor y desaparece cuando el usuario hace clic en un botón del mouse o mueve el cursor de la herramienta.  
  
 `CToolTipCtrl` proporciona la funcionalidad para controlar la hora inicial y duración de información sobre herramientas, los anchos de margen rodeando el texto de información sobre herramientas, el ancho de la ventana de la propia información sobre herramientas, y el fondo y el color del texto de información sobre herramientas.  Un único control de información sobre herramientas puede proporcionar información para más de una herramienta.  
  
 La clase de `CToolTipCtrl` proporciona la funcionalidad del control común de información sobre herramientas de Windows.  Este control \(y por consiguiente la clase de `CToolTipCtrl` \) sólo está disponible para los programas que se ejecutan en versiones de Windows 3,51 95 \/98 y Windows NT y posterior.  
  
 Para obtener más información sobre cómo habilitar información sobre herramientas, vea [Información sobre herramientas en Windows no derivado de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
 Para obtener más información sobre cómo utilizar `CToolTipCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CToolTipCtrl](../../mfc/using-ctooltipctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)