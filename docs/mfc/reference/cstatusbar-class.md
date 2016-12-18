---
title: "CStatusBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBar class"
  - "indicators"
  - "indicators, status bar"
  - "barras de estado"
  - "status indicators"
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una barra de controles con una fila de texto generado los paneles, o “marcadores”.  
  
## Sintaxis  
  
```  
class CStatusBar : public CControlBar  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](../Topic/CStatusBar::CStatusBar.md)|Crea un objeto `CStatusBar`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](../Topic/CStatusBar::CommandToIndex.md)|Obtiene el índice de una identificación especificada de marcador|  
|[CStatusBar::Create](../Topic/CStatusBar::Create.md)|Crea la barra de estado, la asocia el objeto de `CStatusBar` , y establece la fuente y el alto de barras iniciales.|  
|[CStatusBar::CreateEx](../Topic/CStatusBar::CreateEx.md)|Crea un objeto de `CStatusBar` con estilos adicionales para el objeto incrustado de `CStatusBarCtrl` .|  
|[CStatusBar::DrawItem](../Topic/CStatusBar::DrawItem.md)|Llamado cuando un aspecto visual de los cambios de dibujo del propietario de un control de barra de estado.|  
|[CStatusBar::GetItemID](../Topic/CStatusBar::GetItemID.md)|Obtiene el identificador de marcador para un índice especificado.|  
|[CStatusBar::GetItemRect](../Topic/CStatusBar::GetItemRect.md)|Obtiene el rectángulo de presentación para un índice especificado.|  
|[CStatusBar::GetPaneInfo](../Topic/CStatusBar::GetPaneInfo.md)|Obtiene el identificador, el estilo, y el ancho de marcador para un índice especificado.|  
|[CStatusBar::GetPaneStyle](../Topic/CStatusBar::GetPaneStyle.md)|Obtiene el estilo de marcador para un índice especificado.|  
|[CStatusBar::GetPaneText](../Topic/CStatusBar::GetPaneText.md)|Obtiene el texto de marcador para un índice especificado.|  
|[CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md)|Permite el acceso directo al control común subyacente.|  
|[CStatusBar::SetIndicators](../Topic/CStatusBar::SetIndicators.md)|Establece id. de marcador.|  
|[CStatusBar::SetPaneInfo](../Topic/CStatusBar::SetPaneInfo.md)|Establece el identificador, el estilo, y el ancho de marcador para un índice especificado.|  
|[CStatusBar::SetPaneStyle](../Topic/CStatusBar::SetPaneStyle.md)|Establece el estilo de marcador para un índice especificado.|  
|[CStatusBar::SetPaneText](../Topic/CStatusBar::SetPaneText.md)|Establece el texto de marcador para un índice especificado.|  
  
## Comentarios  
 Los paneles de resultados se utilizan normalmente como líneas de mensajes como indicadores de estado.  Los ejemplos incluyen las líneas de AYUDA\-mensaje de menú que explican brevemente el comando de menú seleccionado y los indicadores que muestran el estado de BLOQ DESPL, de BLOQ NUM, y otras claves.  
  
 [CStatusBar:: GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md), una función miembro nueva a MFC 4,0, permite aprovechar las ventajas de la compatibilidad de controles comunes de Windows para la personalización y la funcionalidad adicional de la barra de estado.  las funciones miembro de`CStatusBar` ofrecen la mayor parte de la funcionalidad de los controles comunes de Windows; sin embargo, cuando se llama a `GetStatusBarCtrl`, puede proporcionar a barras de estado aun más de las características de Windows 95 \/98 barra de estado.  Cuando se llama a `GetStatusBarCtrl`, devolverá una referencia a un objeto de `CStatusBarCtrl` .  Vea [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) para obtener más información sobre el diseño de las barras de herramientas mediante controles comunes de Windows.  Para obtener más información general sobre los controles comunes, vea [Controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 El marco almacena información de marca de una matriz con el marcador de izquierda en la posición 0.  Cuando se crea una barra de estado, se utiliza una matriz de los id. de la cadena que el marco asocia los marcadores correspondientes.  Puede utilizar un identificador de cadena o un índice para tener acceso a una solicitud.  
  
 de forma predeterminada, el primer indicador es “elástico”: toma la longitud de la barra de estado no usa en otros paneles de marcador, de modo que los otros paneles estén alineadas a la derecha.  
  
 para crear una barra de estado, siga estos pasos:  
  
1.  Cree el objeto de `CStatusBar` .  
  
2.  Llame a la función de [Crear](../Topic/CStatusBar::Create.md) \(o [CreateEx](../Topic/CStatusBar::CreateEx.md)\) para crear la ventana de la barra de estado y para adjuntarla al objeto de `CStatusBar` .  
  
3.  Llame a [SetIndicators](../Topic/CStatusBar::SetIndicators.md) para asociar un identificador de cadena con cada marcador.  
  
 Hay tres maneras de actualizar el texto de un panel de barra de estado:  
  
1.  Llamada [CWnd:: SetWindowText](../Topic/CWnd::SetWindowText.md) para actualizar el texto del panel 0 únicamente.  
  
2.  Llamada [CCmdUI:: SetText](../Topic/CCmdUI::SetText.md) en el controlador de `ON_UPDATE_COMMAND_UI` de barra de estado.  
  
3.  Llame a [SetPaneText](../Topic/CStatusBar::SetPaneText.md) para actualizar el texto para cualquier panel.  
  
 Llame a [SetPaneStyle](../Topic/CStatusBar::SetPaneStyle.md) para actualizar el estilo de un panel de barra de estado.  
  
 Para obtener más información sobre cómo utilizar `CStatusBar`, vea el artículo [implementación de la barra de estado en MFC](../../mfc/status-bar-implementation-in-mfc.md) y [nota técnica 31: Barras de controles](../../mfc/tn031-control-bars.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo CTRLBARS de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo DLGCBR32 de MFC](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl Class](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md)   
 [CStatusBar::SetIndicators](../Topic/CStatusBar::SetIndicators.md)