---
title: "CDockablePane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockablePane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockablePane class"
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CDockablePane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un panel que se puede acoplar en un sitio de vinculación o incluir en un panel con fichas.  
  
## Sintaxis  
  
```  
class CDockablePane : public CPane  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockablePane::CDockablePane](../Topic/CDockablePane::CDockablePane.md)|Las construcciones e inicializan un objeto de `CDockablePane` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)|Asocia un panel a otro panel.  Esto crea un panel con fichas.|  
|[CDockablePane::CalcFixedLayout](../Topic/CDockablePane::CalcFixedLayout.md)|Devuelve el tamaño del rectángulo del panel.|  
|[CDockablePane::CanAcceptMiniFrame](../Topic/CDockablePane::CanAcceptMiniFrame.md)|Determina si es el mínimo cuadro especificado se puede acoplar el panel.|  
|[CDockablePane::CanAcceptPane](../Topic/CDockablePane::CanAcceptPane.md)|Determina si otro panel se puede acoplar el panel actual.|  
|[CDockablePane::CanAutoHide](../Topic/CDockablePane::CanAutoHide.md)|Determina si el panel admite oculta automáticamente el modo.  \(Reemplaza [CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md).\)|  
|[CDockablePane::CanBeAttached](../Topic/CDockablePane::CanBeAttached.md)|determina si el panel actual se puede acoplar a otro panel.|  
|[CDockablePane::ConvertToTabbedDocument](../Topic/CDockablePane::ConvertToTabbedDocument.md)|Convierte uno o varios paneles acoplable a MDI con documentos.|  
|[CDockablePane::CopyState](../Topic/CDockablePane::CopyState.md)|Copia el estado de un panel acoplable.|  
|[CDockablePane::Create](../Topic/CDockablePane::Create.md)|Hace que el control de Windows y lo asocia al objeto de `CDockablePane` .|  
|[CDockablePane::CreateDefaultPaneDivider](../Topic/CDockablePane::CreateDefaultPaneDivider.md)|Crea un divisor predeterminado para el panel mientras se está acoplado a una ventana de marco.|  
|[CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md)|Hace que el control de Windows y lo asocia al objeto de `CDockablePane` .|  
|[CDockablePane::CreateTabbedPane](../Topic/CDockablePane::CreateTabbedPane.md)|Crea un panel con fichas del panel actual.|  
|[CDockablePane::DockPaneContainer](../Topic/CDockablePane::DockPaneContainer.md)|Acoplar un contenedor al panel.|  
|[CDockablePane::DockPaneStandard](../Topic/CDockablePane::DockPaneStandard.md)|Acoplar un panel mediante el acoplamiento de esquema \(estándar\).|  
|`CDockablePane::DockToFrameWindow`|Utilizado de forma interna.  Para acoplar un panel, utilice [CPane::DockPane](../Topic/CPane::DockPane.md) o [CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md).|  
|[CDockablePane::DockToRecentPos](../Topic/CDockablePane::DockToRecentPos.md)|Acoplar un panel a su posición reciente almacenada de acoplamiento.|  
|[CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md)|Lo acopla un panel de acoplamiento a otro panel acoplable.|  
|[CDockablePane::EnableAutohideAll](../Topic/CDockablePane::EnableAutohideAll.md)|Habilita o las neutralizaciones ocultan automáticamente el modo para este panel junto con otros paneles del contenedor.|  
|[CDockablePane::EnableGripper](../Topic/CDockablePane::EnableGripper.md)|Muestra u oculta la leyenda \(de\).|  
|[CDockablePane::GetAHRestoredRect](../Topic/CDockablePane::GetAHRestoredRect.md)|Especifica la posición del panel a es visible en ocultan automáticamente el modo.|  
|[CDockablePane::GetAHSlideMode](../Topic/CDockablePane::GetAHSlideMode.md)|Recupera el modo automático de la diapositiva hide para el panel.|  
|`CDockablePane::GetAutoHideButton`|Utilizado de forma interna.|  
|`CDockablePane::GetAutoHideToolBar`|Utilizado de forma interna.|  
|[CDockablePane::GetCaptionHeight](../Topic/CDockablePane::GetCaptionHeight.md)|Devuelve el alto de la leyenda actual.|  
|[CDockablePane::GetDefaultPaneDivider](../Topic/CDockablePane::GetDefaultPaneDivider.md)|Devuelve el divisor de paneles predeterminado para el contenedor del panel.|  
|[CDockablePane::GetDockingStatus](../Topic/CDockablePane::GetDockingStatus.md)|Determina la capacidad de un panel de acoplarse basándose en la ubicación especificada del puntero.|  
|[CDockablePane::GetDragSensitivity](../Topic/CDockablePane::GetDragSensitivity.md)|Devuelve el carácter de arrastre de un panel acoplable.|  
|[CDockablePane::GetLastPercentInPaneContainer](../Topic/CDockablePane::GetLastPercentInPaneContainer.md)|Recupera el porcentaje de espacio que un panel ocupa dentro de su contenedor.|  
|[CDockablePane::GetTabArea](../Topic/CDockablePane::GetTabArea.md)|Recupera el área de la pestaña del panel.|  
|[CDockablePane::GetTabbedPaneRTC](../Topic/CDockablePane::GetTabbedPaneRTC.md)|Devuelve información de clase en tiempo de ejecución sobre una ventana con fichas se crea a otro panel acoplar el panel actual.|  
|[CDockablePane::HasAutoHideMode](../Topic/CDockablePane::HasAutoHideMode.md)|Especifica si un panel acoplable puede intercambiarse oculta automáticamente el modo.|  
|[CDockablePane::HitTest](../Topic/CDockablePane::HitTest.md)|Especifica la ubicación específica en un panel en el que el usuario hace clic en un mouse.|  
|`CDockablePane::IsAccessibilityCompatible`|Utilizado de forma interna.|  
|[CDockablePane::IsAutohideAllEnabled](../Topic/CDockablePane::IsAutohideAllEnabled.md)|Indica si el panel acoplable y el resto de los paneles del contenedor se pueden colocar en ocultan automáticamente el modo.|  
|[CDockablePane::IsAutoHideMode](../Topic/CDockablePane::IsAutoHideMode.md)|Determina si es un panel en oculta automáticamente el modo.|  
|`CDockablePane::IsChangeState`|Utilizado de forma interna.|  
|[CDockablePane::IsDocked](../Topic/CDockablePane::IsDocked.md)|determina si el panel actual está acoplado.|  
|[CDockablePane::IsHideInAutoHideMode](../Topic/CDockablePane::IsHideInAutoHideMode.md)|Determina el comportamiento de un panel que sea en ocultar automáticamente el modo si se muestre \(o oculto\) llamando a `ShowPane`.|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](../Topic/CDockablePane::IsInFloatingMultiPaneFrameWnd.md)|Especifica si el panel está en una ventana de marco de multi\- panel.|  
|[CDockablePane::IsResizable](../Topic/CDockablePane::IsResizable.md)|Especifica si el panel se puede cambiar.|  
|[CDockablePane::IsTabLocationBottom](../Topic/CDockablePane::IsTabLocationBottom.md)|Especifica si las pestañas se encuentran en la parte superior o inferior del panel.|  
|[CDockablePane::IsTracked](../Topic/CDockablePane::IsTracked.md)|Especifica si un panel sea arrastrado por el usuario.|  
|[CDockablePane::IsVisible](../Topic/CDockablePane::IsVisible.md)|Determina si el panel actual está visible.|  
|[CDockablePane::LoadState](http://msdn.microsoft.com/es-es/96110136-4f46-4764-8a76-3b4abaf77917)|Utilizado de forma interna.|  
|[CDockablePane::OnAfterChangeParent](../Topic/CDockablePane::OnAfterChangeParent.md)|Llamado por el marco al elemento primario de un panel ha cambiado.  \(Reemplaza [CPane::OnAfterChangeParent](../Topic/CPane::OnAfterChangeParent.md).\)|  
|[CDockablePane::OnAfterDockFromMiniFrame](../Topic/CDockablePane::OnAfterDockFromMiniFrame.md)|Llamado por el marco cuando se acopla de punto flotante de una barra de acoplamiento en una ventana de marco.|  
|[CDockablePane::OnBeforeChangeParent](../Topic/CDockablePane::OnBeforeChangeParent.md)|Llamado por el marco al elemento primario del panel va a cambiar.  \(Reemplaza [CPane::OnBeforeChangeParent](../Topic/CPane::OnBeforeChangeParent.md).\)|  
|[CDockablePane::OnBeforeFloat](../Topic/CDockablePane::OnBeforeFloat.md)|Llamado por el marco cuando un panel está a punto de flotar.  \(Reemplaza [CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md).\)|  
|[CDockablePane::RemoveFromDefaultPaneDividier](../Topic/CDockablePane::RemoveFromDefaultPaneDividier.md)|El marco de trabajo llama a este método cuando se desacoplando un panel.|  
|[CDockablePane::ReplacePane](../Topic/CDockablePane::ReplacePane.md)|Reemplaza el panel con un panel especificado.|  
|[CDockablePane::RestoreDefaultPaneDivider](../Topic/CDockablePane::RestoreDefaultPaneDivider.md)|El marco de trabajo llama a este método mientras un panel se deserializa para restaurar el divisor de paneles predeterminado.|  
|`CDockablePane::SaveState`|Utilizado de forma interna.|  
|`CDockablePane::Serialize`|Serializa el panel.  \(Reemplaza `CBasePane::Serialize`.\)|  
|[CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)|Alterna el panel acoplable entre visible y oculta automáticamente el modo.|  
|[CDockablePane::SetAutoHideParents](../Topic/CDockablePane::SetAutoHideParents.md)|Establece el botón de ocultar automáticamente y oculta automáticamente la barra de herramientas del panel.|  
|`CDockablePane::SetDefaultPaneDivider`|Utilizado de forma interna.|  
|[CDockablePane::SetLastPercentInPaneContainer](../Topic/CDockablePane::SetLastPercentInPaneContainer.md)|Establece el porcentaje de espacio que un panel ocupa dentro de su contenedor.|  
|`CDockablePane::SetResizeMode`|Utilizado de forma interna.|  
|[CDockablePane::SetRestoredDefaultPaneDivider](../Topic/CDockablePane::SetRestoredDefaultPaneDivider.md)|Establece el divisor de paneles predeterminado restaurado.|  
|[CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md)|Establece la información de la clase en tiempo de ejecución para una ventana con fichas se crea a dos paneles se acoplan.|  
|[CDockablePane::ShowPane](../Topic/CDockablePane::ShowPane.md)|Muestra u oculta el panel.|  
|[CDockablePane::Slide](../Topic/CDockablePane::Slide.md)|Muestra u oculta un panel con una animación el deslizar que se muestra cuando el panel en oculta automáticamente el modo.|  
|[CDockablePane::ToggleAutoHide](../Topic/CDockablePane::ToggleAutoHide.md)|Alterna ocultan automáticamente el modo.  \(Reemplaza [CPane::ToggleAutoHide](../Topic/CPane::ToggleAutoHide.md) .\)|  
|[CDockablePane::UndockPane](../Topic/CDockablePane::UndockPane.md)|Desacopla un panel de la ventana de marco principal o de un contenedor de ventana de marco.|  
|`CDockablePane::UnSetAutoHideMode`|Utilizado de forma interna.  Para establecer el modo de ocultar automáticamente, utilice [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockablePane::CheckAutoHideCondition](../Topic/CDockablePane::CheckAutoHideCondition.md)|Determina si el panel acoplable está oculto \(en ocultar automáticamente el modo\).|  
|[CDockablePane::CheckStopSlideCondition](../Topic/CDockablePane::CheckStopSlideCondition.md)|Determina cuando un panel de acoplamiento de ocultar automáticamente parará deslizar.|  
|[CDockablePane::DrawCaption](../Topic/CDockablePane::DrawCaption.md)|Dibuja la leyenda del panel acoplable \(de\).|  
|[CDockablePane::OnPressButtons](../Topic/CDockablePane::OnPressButtons.md)|Se llama cuando el usuario presiona un botón de título distinto de los botones de `AFX_HTCLOSE` y de `AFX_HTMAXBUTTON` .|  
|[CDockablePane::OnSlide](../Topic/CDockablePane::OnSlide.md)|Llamado por el marco para mostrar el efecto de la diapositiva de ocultar automáticamente cuando se muestra o se oculta el panel.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockablePane::m\_bDisableAnimation](../Topic/CDockablePane::m_bDisableAnimation.md)|Especifica si ocultar automáticamente la animación de panel acoplable está deshabilitado.|  
|[CDockablePane::m\_bHideInAutoHideMode](../Topic/CDockablePane::m_bHideInAutoHideMode.md)|Determina el comportamiento del panel cuando el panel en oculta automáticamente el modo.|  
|[CDockablePane::m\_nSlideSteps](../Topic/CDockablePane::m_nSlideSteps.md)|Especifica la velocidad de la animación del panel cuando se está mostrando o se está mostrando cuando en ocultar automáticamente el modo.|  
  
## Comentarios  
 `CDockablePane` implementa la siguiente funcionalidad:  
  
-   Acoplar un panel a una ventana de marco principal.  
  
-   Pasa un panel a ocultar automáticamente el modo.  
  
-   Adjuntar un panel a una ventana con fichas.  
  
-   Flotante de un panel en una ventana de marco.  
  
-   Acoplar un panel a otro panel que flota en una ventana de marco.  
  
-   Cambiar el tamaño de un panel.  
  
-   Estado y de carga para un panel acoplable.  
  
    > [!NOTE]
    >  La información de estado se guarda en el Registro de Windows.  
  
-   Crear un panel con o sin una leyenda.  La leyenda puede tener una etiqueta de texto y puede rellenarse con un color de degradado.  
  
-   Arrastrar un panel mientras muestra el contenido del panel  
  
-   Arrastrar un panel mientras muestra un rectángulo de arrastre.  
  
 Para utilizar un panel acoplable en la aplicación, derive la clase del panel de la clase de `CDockablePane` .  Inserte el objeto derivado en el objeto de la ventana de marco principal o en un objeto de la ventana que controla la instancia del panel.  Llamar a continuación al método de [CDockablePane::Create](../Topic/CDockablePane::Create.md) o el método de [CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md) cuando se procesa el mensaje de `WM_CREATE` en la ventana de marco principal.  Finalmente, configurar el objeto de panel llamando a [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md), [CBasePane::DockPane](../Topic/CBasePane::DockPane.md), o [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md).  
  
## Sugerencias de personalización  
 Las sugerencias siguientes se aplican a los objetos de `CDockablePane` :  
  
-   Si llama a [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) para dos no\-tabulados, los paneles acoplables, un puntero a una ventana con fichas se devolverán en el parámetro de `ppTabbedControlBar` .  Puede agregar las pestañas en la ventana con fichas mediante este parámetro.  
  
-   La clase de panel con fichas creado por [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) viene determinada por el objeto de `CDockablePane` en el parámetro de `pTabControlBarAttachTo` .  Puede llamar a [CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md) para establecer la clase de panel con fichas que `CDockablePane` creará.  `dwTabbedStyle` de [CDockablePane::Create](../Topic/CDockablePane::Create.md) determina el tipo predeterminado al crear `CDockablePane`.  si `dwTabbedStyle` es AFX\_CBRS\_OUTLOOK\_TABS el tipo predeterminado es [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md); si `dwTabbedStyle` es AFX\_CBRS\_REGULAR\_TABS el tipo predeterminado es [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md).  
  
-   Si desea acoplar un panel acoplable a otro, llame al método de [CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md) .  El panel original debe acoplar en alguna parte antes de llamar a este método.  
  
-   Los controles de [CDockablePane::m\_bHideInAutoHideMode](../Topic/CDockablePane::m_bHideInAutoHideMode.md) de variable miembro cómo los paneles acoplable se comportan en modo de ocultar automáticamente cuando se llama a [CDockablePane::ShowPane](../Topic/CDockablePane::ShowPane.md).  Si está establecido en esta variable miembro a `TRUE`, los paneles acoplable y sus botones automático de ocultar se ocultarán.  Si no, deslizarán en y out.  
  
-   Puede deshabilitar oculta automáticamente la animación estableciendo a la variable miembro de [CDockablePane::m\_bDisableAnimation](../Topic/CDockablePane::m_bDisableAnimation.md) a `TRUE`.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto de `CDockablePane` mediante varios métodos en la clase de `CDockablePane` .  El ejemplo muestra cómo habilitar el ocultar automáticamente toda la característica del panel acoplable, habilita la leyenda o el agarrador, habilita el modo de ocultar automáticamente, muestra el panel, y anima un panel que sea en ocultar automáticamente el modo.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#27](../../mfc/codesnippet/CPP/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#28](../../mfc/codesnippet/CPP/cdockablepane-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## Requisitos  
 **encabezado:** afxDockablePane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)