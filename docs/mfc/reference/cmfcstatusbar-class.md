---
title: "CMFCStatusBar Class | Microsoft Docs"
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
  - "CMFCStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCStatusBar class"
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
caps.latest.revision: 36
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la clase de `CMFCStatusBar` implementa una barra de estado similar a la clase de `CStatusBar` .  Sin embargo, la clase de `CMFCStatusBar` tiene características no proporcionadas por la clase de `CStatusBar` , como la capacidad para mostrar imágenes, a las animaciones, y las barras de progreso; y la capacidad de responder a los doble clic del mouse.  
  
## Sintaxis  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCStatusBar::CalcFixedLayout](../Topic/CMFCStatusBar::CalcFixedLayout.md)|\(Reemplaza [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md).\)|  
|[CMFCStatusBar::CommandToIndex](../Topic/CMFCStatusBar::CommandToIndex.md)||  
|[CMFCStatusBar::Create](../Topic/CMFCStatusBar::Create.md)|Crea una barra de controles y la agrega al objeto de [CPane](../../mfc/reference/cpane-class.md) .  \(Reemplaza [CPane::Create](../Topic/CPane::Create.md).\)|  
|[CMFCStatusBar::CreateEx](../Topic/CMFCStatusBar::CreateEx.md)|Crea una barra de controles y la agrega al objeto de [CPane](../../mfc/reference/cpane-class.md) .  \(Reemplaza [CPane::CreateEx](../Topic/CPane::CreateEx.md).\)|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](../Topic/CMFCStatusBar::DoesAllowDynInsertBefore.md)|determina si otro panel se puede insertar dinámicamente entre este panel y el cuadro primario.  \(Reemplaza [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md).\)|  
|[CMFCStatusBar::EnablePaneDoubleClick](../Topic/CMFCStatusBar::EnablePaneDoubleClick.md)|Habilita o deshabilita la administración de los doble clic del mouse en la barra de estado.|  
|[CMFCStatusBar::EnablePaneProgressBar](../Topic/CMFCStatusBar::EnablePaneProgressBar.md)|Muestra una barra de progreso en el panel especificado.|  
|[CMFCStatusBar::GetCount](../Topic/CMFCStatusBar::GetCount.md)|Devuelve el número de paneles de la barra de estado.|  
|[CMFCStatusBar::GetDrawExtendedArea](../Topic/CMFCStatusBar::GetDrawExtendedArea.md)||  
|[CMFCStatusBar::GetExtendedArea](../Topic/CMFCStatusBar::GetExtendedArea.md)||  
|[CMFCStatusBar::GetItemID](../Topic/CMFCStatusBar::GetItemID.md)||  
|[CMFCStatusBar::GetItemRect](../Topic/CMFCStatusBar::GetItemRect.md)||  
|[CMFCStatusBar::GetPaneInfo](../Topic/CMFCStatusBar::GetPaneInfo.md)||  
|[CMFCStatusBar::GetPaneProgress](../Topic/CMFCStatusBar::GetPaneProgress.md)||  
|[CMFCStatusBar::GetPaneStyle](../Topic/CMFCStatusBar::GetPaneStyle.md)|Devuelve el estilo del panel.  \(Reemplaza [CBasePane::GetPaneStyle](../Topic/CBasePane::GetPaneStyle.md).\)|  
|[CMFCStatusBar::GetPaneText](../Topic/CMFCStatusBar::GetPaneText.md)||  
|[CMFCStatusBar::GetPaneWidth](../Topic/CMFCStatusBar::GetPaneWidth.md)|Devuelve el ancho, en píxeles, del panel especificado de la barra de estado.|  
|[CMFCStatusBar::GetTipText](../Topic/CMFCStatusBar::GetTipText.md)|Devuelve el texto de información sobre herramientas para el panel especificado de la barra de estado.|  
|[CMFCStatusBar::InvalidatePaneContent](../Topic/CMFCStatusBar::InvalidatePaneContent.md)|Reemplaza el panel especificado y volverá a su contenido.|  
|[CMFCStatusBar::PreCreateWindow](../Topic/CMFCStatusBar::PreCreateWindow.md)|Llamado por el marco antes de la creación de la ventana de Windows asociada a este objeto de `CWnd` .  \(Reemplaza [CWnd::PreCreateWindow](../Topic/CWnd::PreCreateWindow.md).\)|  
|[CMFCStatusBar::SetDrawExtendedArea](../Topic/CMFCStatusBar::SetDrawExtendedArea.md)||  
|[CMFCStatusBar::SetIndicators](../Topic/CMFCStatusBar::SetIndicators.md)||  
|[CMFCStatusBar::SetPaneAnimation](../Topic/CMFCStatusBar::SetPaneAnimation.md)|Asigna una animación el panel especificado.|  
|[CMFCStatusBar::SetPaneBackgroundColor](../Topic/CMFCStatusBar::SetPaneBackgroundColor.md)|Establece el color de fondo del panel especificado de la barra de estado.|  
|[CMFCStatusBar::SetPaneIcon](../Topic/CMFCStatusBar::SetPaneIcon.md)|Establece el icono de marcador para el panel especificado de la barra de estado.|  
|[CMFCStatusBar::SetPaneInfo](../Topic/CMFCStatusBar::SetPaneInfo.md)||  
|[CMFCStatusBar::SetPaneProgress](../Topic/CMFCStatusBar::SetPaneProgress.md)|establece el progreso actual de la barra de progreso para el panel especificado de la barra de estado.|  
|[CMFCStatusBar::SetPaneStyle](../Topic/CMFCStatusBar::SetPaneStyle.md)|Establece el estilo del panel.  \(Reemplaza [CBasePane::SetPaneStyle](../Topic/CBasePane::SetPaneStyle.md).\)|  
|[CMFCStatusBar::SetPaneText](../Topic/CMFCStatusBar::SetPaneText.md)||  
|[CMFCStatusBar::SetPaneTextColor](../Topic/CMFCStatusBar::SetPaneTextColor.md)|Establece el color del texto al panel especificado de la barra de estado.|  
|[CMFCStatusBar::SetPaneWidth](../Topic/CMFCStatusBar::SetPaneWidth.md)|Establece el ancho en píxeles del panel especificado de la barra de estado.|  
|[CMFCStatusBar::SetTipText](../Topic/CMFCStatusBar::SetTipText.md)|Establece el texto de información sobre herramientas para el panel especificado de la barra de estado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCStatusBar::OnDrawPane](../Topic/CMFCStatusBar::OnDrawPane.md)|Llamado por el marco cuando dibuja de nuevo el panel de barra de estado.|  
  
## Comentarios  
 El diagrama siguiente se muestra una ilustración de la barra de estado de la aplicación de [Ejemplo de demostración de la barra de estado](../../top/visual-cpp-samples.md) .  
  
 ![Ejemplo de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar")  
  
## Ejemplo  
 El ejemplo siguiente muestra las variables locales que la aplicación utiliza para llamar a los distintos métodos en la clase de `CMFCStatusBar` .  estas variables se declaran en StatusBarDemoView.h.  El marco principal se declara en MainFrm.h, el documento se declara en StatusBarDemoDoc.h, y la vista se declara en StatusBarDemoView.h.  Este fragmento de código es parte de [Ejemplo de demostración de la barra de estado](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_1.h)]  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo obtener una referencia al objeto de `CMFCStatusBar` mediante el método de `GetStatusBar` en MainFrm.h y después llamar a este método del método de `GetStatusBar` en StatusBarDemoView.h.  Este fragmento de código es parte de [Ejemplo de demostración de la barra de estado](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_3.h)]  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo llamar a varios métodos en la clase de `CMFCStatusBar` en StatusBarDemoView.cpp.  las constantes se declaran en MainFrm.h.  El ejemplo muestra cómo establecer el icono, establece el texto de información sobre herramientas del panel de barra de estado, muestra una barra de progreso en el panel especificado, asigne una animación el panel especificado, establece el texto y el ancho del panel de barra de estado, y establece el indicador de progreso actual de la barra de progreso para el panel de barra de estado.  Este fragmento de código es parte de [Ejemplo de demostración de la barra de estado](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/CPP/cmfcstatusbar-class_9.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)  
  
## Requisitos  
 **encabezado:** afxstatusbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CStatusBar Class](../../mfc/reference/cstatusbar-class.md)