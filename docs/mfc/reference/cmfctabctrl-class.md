---
title: "CMFCTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabCtrl class"
  - "CMFCTabCtrl constructor"
  - "CMFCTabCtrl::GetTabFromPoint method"
  - "CMFCTabCtrl::IsPtInTabArea method"
  - "CMFCTabCtrl::MoveTab method"
  - "CMFCTabCtrl::PreTranslateMessage method"
  - "CMFCTabCtrl::RecalcLayout method"
  - "CMFCTabCtrl::SwapTabs method"
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
caps.latest.revision: 33
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCTabCtrl` proporciona funcionalidad para un control de ficha.  El control de ficha muestra una ventana acoplable con pestañas planas o tridimensionales en la parte superior o inferior.  Las fichas pueden mostrar texto y una imagen y pueden cambiar color cuando está activo.  
  
## Sintaxis  
  
```  
class CMFCTabCtrl : public CMFCBaseTabCtrl  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCTabCtrl::CMFCTabCtrl`|Constructor predeterminado.|  
|`CMFCTabCtrl::~CMFCTabCtrl`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTabCtrl::ActivateMDITab](../Topic/CMFCTabCtrl::ActivateMDITab.md)|Muestra la ficha especificada del control de tabulación y establece el foco en esa ficha.|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](../Topic/CMFCTabCtrl::AllowDestroyEmptyTabbedPane.md)||  
|[CMFCTabCtrl::AutoSizeWindow](../Topic/CMFCTabCtrl::AutoSizeWindow.md)|Especifica si el marco es cambiar el tamaño del área cliente de todas las ventanas de control de ficha cuando un elemento de la interfaz de usuario del control cambia de la pestaña.|  
|[CMFCTabCtrl::CalcRectEdit](../Topic/CMFCTabCtrl::CalcRectEdit.md)|Desinfla el tamaño del área especificada de la pestaña.  \(Reemplaza `CMFCBaseTabCtrl::CalcRectEdit`.\)|  
|[CMFCTabCtrl::Create](../Topic/CMFCTabCtrl::Create.md)|Crear el control de ficha y lo asocia al objeto de `CMFCTabCtrl` .|  
|`CMFCTabCtrl::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](../Topic/CMFCTabCtrl::EnableActiveTabCloseButton.md)|Muestra u oculta un botón cerrar \(x\) en la pestaña activa.|  
|[CMFCTabCtrl::EnableInPlaceEdit](../Topic/CMFCTabCtrl::EnableInPlaceEdit.md)|Habilita o deshabilita etiquetas editable de la pestaña.  \(Reemplaza [CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md).\)|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](../Topic/CMFCTabCtrl::EnableTabDocumentsMenu.md)|Reemplaza dos botones que desplacen las fichas de la ventana con un botón que abre un menú de ventanas con fichas.|  
|[CMFCTabCtrl::EnsureVisible](../Topic/CMFCTabCtrl::EnsureVisible.md)|Garantiza que una ficha esté visible.|  
|[CMFCTabCtrl::GetDocumentIcon](../Topic/CMFCTabCtrl::GetDocumentIcon.md)|Recupera el símbolo que se está asociado a una ficha en un menú emergente de ventanas con fichas.|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](../Topic/CMFCTabCtrl::GetFirstVisibleTabNum.md)|Recupera el índice de la primera pestaña que está visible en el control de tabulación.|  
|[CMFCTabCtrl::GetResizeMode](../Topic/CMFCTabCtrl::GetResizeMode.md)|Recupera un valor que especifica cómo el control de tabulación puede cambiar de tamaño.|  
|[CMFCTabCtrl::GetScrollBar](../Topic/CMFCTabCtrl::GetScrollBar.md)|Recupera un puntero al objeto de la barra de desplazamiento que está asociado al control de ficha.|  
|[CMFCTabCtrl::GetTabArea](../Topic/CMFCTabCtrl::GetTabArea.md)|Recupera el rectángulo delimitador de la etiqueta de la ficha en la parte superior o inferior del control de ficha.  \(Reemplaza [CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md).\)|  
|`CMFCTabCtrl::GetTabFromPoint`|Recupera la pestaña que contiene un punto especificado.  \(Reemplaza [CMFCBaseTabCtrl::GetTabFromPoint](../Topic/CMFCBaseTabCtrl::GetTabFromPoint.md).\)|  
|[CMFCTabCtrl::GetTabMaxWidth](../Topic/CMFCTabCtrl::GetTabMaxWidth.md)|Recupera el ancho máximo de una pestaña.|  
|[CMFCTabCtrl::GetTabsHeight](../Topic/CMFCTabCtrl::GetTabsHeight.md)|Recupera el alto de la pestaña de control de tabulación.|  
|[CMFCTabCtrl::GetTabsRect](../Topic/CMFCTabCtrl::GetTabsRect.md)|Recupera un rectángulo que restringe el área de la pestaña de control de tabulación.  \(Reemplaza [CMFCBaseTabCtrl::GetTabsRect](../Topic/CMFCBaseTabCtrl::GetTabsRect.md).\)|  
|`CMFCTabCtrl::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCTabCtrl::GetWndArea](../Topic/CMFCTabCtrl::GetWndArea.md)|Recupera el límite del área de cliente del control de tabulación.|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](../Topic/CMFCTabCtrl::HideActiveWindowHorzScrollBar.md)|Oculta la barra de desplazamiento horizontal, si existe, la ventana activa.|  
|[CMFCTabCtrl::HideInactiveWindow](../Topic/CMFCTabCtrl::HideInactiveWindow.md)|Especifica si el marco es mostrar ventanas de control inactivas de la pestaña.|  
|[CMFCTabCtrl::HideNoTabs](../Topic/CMFCTabCtrl::HideNoTabs.md)|Habilita o deshabilita el dibujo del área de la pestaña si no hay pestañas visible.|  
|[CMFCTabCtrl::HideSingleTab](../Topic/CMFCTabCtrl::HideSingleTab.md)|Habilita o deshabilita la creación de una pestaña cuando hay una sola ventana con fichas.  \(Reemplaza [CMFCBaseTabCtrl::HideSingleTab](../Topic/CMFCBaseTabCtrl::HideSingleTab.md).\)|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](../Topic/CMFCTabCtrl::IsActiveInMDITabGroup.md)|Indica si la ficha actual de un control de ficha es la ficha activa en un grupo de la ficha de la interfaz de múltiples documentos.|  
|[CMFCTabCtrl::IsActiveTabBoldFont](../Topic/CMFCTabCtrl::IsActiveTabBoldFont.md)|Indica si el texto de la pestaña activa se muestra con una fuente en negrita.|  
|[CMFCTabCtrl::IsActiveTabCloseButton](../Topic/CMFCTabCtrl::IsActiveTabCloseButton.md)|Indica si el botón cerrar \(x\) se muestra en una pestaña activa o la esquina superior derecha del área de la ficha.|  
|[CMFCTabCtrl::IsDrawFrame](../Topic/CMFCTabCtrl::IsDrawFrame.md)|Indica si la ventana con fichas dibuja un rectángulo de cuadro alrededor de los paneles incrustados.|  
|[CMFCTabCtrl::IsFlatFrame](../Topic/CMFCTabCtrl::IsFlatFrame.md)|Indica si el cuadro alrededor del área de la ficha es plano o 3D.|  
|[CMFCTabCtrl::IsFlatTab](../Topic/CMFCTabCtrl::IsFlatTab.md)|Indica si la apariencia de fichas en el control de tabulación es plano o no.|  
|[CMFCTabCtrl::IsLeftRightRounded](../Topic/CMFCTabCtrl::IsLeftRightRounded.md)|Indica si el aspecto del lado izquierdo y derecho de una pestaña del control de tabulación está redondeado.|  
|[CMFCTabCtrl::IsMDITabGroup](../Topic/CMFCTabCtrl::IsMDITabGroup.md)|Indica si el control de tabulación está contenido en el área cliente de una ventana de interfaz de múltiples documentos.|  
|[CMFCTabCtrl::IsOneNoteStyle](../Topic/CMFCTabCtrl::IsOneNoteStyle.md)|Indica si el control de tabulación se muestra en el estilo de Microsoft OneNote.|  
|`CMFCTabCtrl::IsPtInTabArea`|Determina si un punto está dentro del área de la ficha.  \(Reemplaza [CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md).\)|  
|[CMFCTabCtrl::IsSharedScroll](../Topic/CMFCTabCtrl::IsSharedScroll.md)|Indica si el control de tabulación tiene una barra de desplazamiento que pueda desplazarse sus pestañas como grupo.|  
|[CMFCTabCtrl::IsTabDocumentsMenu](../Topic/CMFCTabCtrl::IsTabDocumentsMenu.md)|Indica si el control de ficha muestra botones de desplazamiento o un botón que muestra un menú de ventanas con fichas.|  
|[CMFCTabCtrl::IsVS2005Style](../Topic/CMFCTabCtrl::IsVS2005Style.md)|Indica si las fichas aparecen en el estilo Visual Studio .NET 2005.|  
|[CMFCTabCtrl::ModifyTabStyle](../Topic/CMFCTabCtrl::ModifyTabStyle.md)|Especifica la apariencia de fichas del control de tabulación.|  
|`CMFCTabCtrl::MoveTab`|Mueve una pestaña a otra posición de pestaña.  \(Reemplaza [CMFCBaseTabCtrl::MoveTab](../Topic/CMFCBaseTabCtrl::MoveTab.md).\)|  
|[CMFCTabCtrl::OnDragEnter](../Topic/CMFCTabCtrl::OnDragEnter.md)|Llamado por el marco cuando el cursor primero se arrastra en la ventana de control de ficha.|  
|[CMFCTabCtrl::OnDragOver](../Topic/CMFCTabCtrl::OnDragOver.md)|Llamado por el marco durante una operación de arrastre cuando el mouse se mueve sobre la ventana de destino.  \(Reemplaza [CMFCBaseTabCtrl::OnDragOver](../Topic/CMFCBaseTabCtrl::OnDragOver.md).\)|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](../Topic/CMFCTabCtrl::OnShowTabDocumentsMenu.md)|Muestra un menú emergente de ventanas con fichas, espera hasta que el usuario seleccione una ficha, y hace que la ficha seleccionada la pestaña activa.|  
|`CMFCTabCtrl::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CMFCBaseTabCtrl::PreTranslateMessage](../Topic/CMFCBaseTabCtrl::PreTranslateMessage.md).\)|  
|`CMFCTabCtrl::RecalcLayout`|Actualiza el diseño interno del control de ficha.  \(Reemplaza [CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md).\)|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](../Topic/CMFCTabCtrl::SetActiveInMDITabGroup.md)|Establece la ficha actual de un control de ficha como la pestaña activa en un grupo de la ficha de la interfaz de múltiples documentos.|  
|[CMFCTabCtrl::SetActiveTab](../Topic/CMFCTabCtrl::SetActiveTab.md)|Provoca una pestaña.  \(Reemplaza [CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md).\)|  
|[CMFCTabCtrl::SetActiveTabBoldFont](../Topic/CMFCTabCtrl::SetActiveTabBoldFont.md)|Habilita o deshabilita el uso de una fuente negrita en fichas activo.|  
|[CMFCTabCtrl::SetDrawFrame](../Topic/CMFCTabCtrl::SetDrawFrame.md)|Habilita o deshabilita el rectángulo del cuadro de drawinga alrededor de una barra incrustada.|  
|[CMFCTabCtrl::SetFlatFrame](../Topic/CMFCTabCtrl::SetFlatFrame.md)|Especifica si dibujar un plano o cuadro 3D alrededor del área de la ficha.|  
|[CMFCTabCtrl::SetImageList](../Topic/CMFCTabCtrl::SetImageList.md)|Especifica una lista de imágenes.  \(Reemplaza [CMFCBaseTabCtrl::SetImageList](../Topic/CMFCBaseTabCtrl::SetImageList.md).\)|  
|[CMFCTabCtrl::SetResizeMode](../Topic/CMFCTabCtrl::SetResizeMode.md)|Especifica cómo el control de tabulación puede cambiar de tamaño y después vuelve a mostrar el control.|  
|[CMFCTabCtrl::SetTabMaxWidth](../Topic/CMFCTabCtrl::SetTabMaxWidth.md)|Especifica el ancho máximo de la pestaña en una ventana con fichas.|  
|[CMFCTabCtrl::StopResize](../Topic/CMFCTabCtrl::StopResize.md)|Finaliza la ejecución cambian el tamaño de la operación en el control de ficha.|  
|`CMFCTabCtrl::SwapTabs`|Cambia un par de fichas.  \(Reemplaza [CMFCBaseTabCtrl::SwapTabs](../Topic/CMFCBaseTabCtrl::SwapTabs.md).\)|  
|[CMFCTabCtrl::SynchronizeScrollBar](../Topic/CMFCTabCtrl::SynchronizeScrollBar.md)|Dibuja una barra de desplazamiento horizontal en un control de ficha que muestra las fichas planas.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTabCtrl::m\_bEnableActivate](../Topic/CMFCTabCtrl::m_bEnableActivate.md)|Evita la vista activa de foco se ejecuta cuando se insertan y se habilita una nueva pestaña.|  
  
## Comentarios  
 la clase de `CMFCTabCtrl` admite:  
  
-   Estilos de control tab que incluyen 3D, plano, y totalmente con una barra de desplazamiento horizontal compartida.  
  
-   Fichas situadas en la parte superior o inferior de la ventana.  
  
-   Fichas que muestran texto, imágenes, como texto e imágenes.  
  
-   Fichas que cambian de color cuando la ficha está activa.  
  
-   Cambios de tamaño del borde de las pestañas ajustables.  
  
-   Ventanas con fichas desmontables.  
  
 La clase de `CMFCTabCtrl` se puede utilizar con un cuadro de diálogo, pero está pensado para las aplicaciones que utilizan acoplar barras de controles como [!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)] y [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  Para obtener más información, vea [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
 Siga estos pasos para agregar un de tamaño variable, acoplar el control de ficha en la aplicación:  
  
1.  Cree una instancia de [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md).  
  
2.  Llamar a [CDockablePane::Create](../Topic/CDockablePane::Create.md).  
  
3.  Utilice [CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md) o [CMFCBaseTabCtrl::InsertTab](../Topic/CMFCBaseTabCtrl::InsertTab.md) para agregar nuevas pestañas.  
  
4.  Llame a [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md) de modo que el control de tabulación de acoplamiento puede acoplar en la ventana de marco principal.  
  
5.  Llame a [CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md) para acoplar la ventana en la cuadro principal.  
  
 Para obtener un ejemplo de cómo crear una ventana con fichas como barra de control de acoplamiento, vea [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md).  Para utilizar `CMFCTabCtrl` como control de no\-muelle, cree un objeto de `CMFCTabCtrl` y llame a [CMFCTabCtrl::Create](../Topic/CMFCTabCtrl::Create.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCTabCtrl` para configurar un objeto de `CMFCTabCtrl` .  El ejemplo explica cómo agregar una pestaña, mostrar el botón cerrar en la pestaña activa, permite etiquetas editable de la ficha, y muestra un menú emergente de las etiquetas de ventana con fichas.  Este ejemplo forma parte de [Ejemplo de colección de estado](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/CPP/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#3](../../mfc/reference/codesnippet/CPP/cmfctabctrl-class_2.cpp)]  
  
## Requisitos  
 **encabezado:** afxtabctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)