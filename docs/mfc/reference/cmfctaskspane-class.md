---
title: "CMFCTasksPane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPane class"
ms.assetid: b456328e-2525-4642-b78b-9edd1a1a7d3f
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCTasksPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 La clase `CMFCTasksPane` implementa una lista de elementos interactivos \(tareas\).  
  
## Sintaxis  
  
```  
class CMFCTasksPane : public CDockablePane  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPane::CMFCTasksPane](../Topic/CMFCTasksPane::CMFCTasksPane.md)|Construye un objeto `CMFCTasksPane`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPane::AddGroup](../Topic/CMFCTasksPane::AddGroup.md)|Agrega un grupo de tareas nuevo al control del panel de tareas.|  
|[CMFCTasksPane::AddLabel](../Topic/CMFCTasksPane::AddLabel.md)|Agrega una etiqueta estática nueva al grupo de tareas especificado.|  
|[CMFCTasksPane::AddMRUFilesList](../Topic/CMFCTasksPane::AddMRUFilesList.md)|Agrega tareas especificadas por una lista de archivos usados más recientemente \(MRU\) a un grupo.|  
|[CMFCTasksPane::AddPage](../Topic/CMFCTasksPane::AddPage.md)|Agrega una nueva página al panel de tareas.|  
|[CMFCTasksPane::AddSeparator](../Topic/CMFCTasksPane::AddSeparator.md)||  
|[CMFCTasksPane::AddTask](../Topic/CMFCTasksPane::AddTask.md)|Agrega una tarea nueva al grupo de tareas especificado.|  
|[CMFCTasksPane::AddWindow](../Topic/CMFCTasksPane::AddWindow.md)|Agrega una ventana secundaria al panel de tareas.|  
|[CMFCTasksPane::CollapseAllGroups](../Topic/CMFCTasksPane::CollapseAllGroups.md)||  
|[CMFCTasksPane::CollapseGroup](../Topic/CMFCTasksPane::CollapseGroup.md)|Contrae un grupo con programación.|  
|[CMFCTasksPane::CreateDefaultMiniframe](../Topic/CMFCTasksPane::CreateDefaultMiniframe.md)|\(Invalida [CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md)\).|  
|[CMFCTasksPane::CreateMenu](../Topic/CMFCTasksPane::CreateMenu.md)|Lo llama el marco para crear un menú para el botón de menú **Otros paneles de tareas**.|  
|[CMFCTasksPane::EnableAnimation](../Topic/CMFCTasksPane::EnableAnimation.md)|Habilita o deshabilita la animación al contraer o expandir los grupos de tareas.|  
|[CMFCTasksPane::EnableGroupCollapse](../Topic/CMFCTasksPane::EnableGroupCollapse.md)|Especifica si se pueden contraer los grupos de tareas.|  
|[CMFCTasksPane::EnableHistoryMenuButtons](../Topic/CMFCTasksPane::EnableHistoryMenuButtons.md)|Habilita o deshabilita los menús desplegables en los botones de navegación **Siguiente** y **Anterior**.|  
|[CMFCTasksPane::EnableNavigationToolbar](../Topic/CMFCTasksPane::EnableNavigationToolbar.md)|Habilita o deshabilita la barra de herramientas de navegación.|  
|[CMFCTasksPane::EnableOffsetCustomControls](../Topic/CMFCTasksPane::EnableOffsetCustomControls.md)||  
|[CMFCTasksPane::EnableScrollButtons](../Topic/CMFCTasksPane::EnableScrollButtons.md)|Habilita botones de desplazamiento en lugar de una barra de desplazamiento.|  
|[CMFCTasksPane::EnableWrapLabels](../Topic/CMFCTasksPane::EnableWrapLabels.md)|Habilita o deshabilita el ajuste de líneas para etiquetas.|  
|[CMFCTasksPane::EnableWrapTasks](../Topic/CMFCTasksPane::EnableWrapTasks.md)|Habilita o deshabilita el ajuste de líneas para tareas.|  
|[CMFCTasksPane::GetActivePage](../Topic/CMFCTasksPane::GetActivePage.md)|Devuelve el índice de base cero para la página activa.|  
|[CMFCTasksPane::GetGroupCaptionHeight](../Topic/CMFCTasksPane::GetGroupCaptionHeight.md)|Devuelve la altura de los títulos de grupo.|  
|[CMFCTasksPane::GetGroupCaptionHorzOffset](../Topic/CMFCTasksPane::GetGroupCaptionHorzOffset.md)|Devuelve el desplazamiento actual del título de un grupo con respecto a los bordes izquierdo y derecho del panel de tareas.|  
|[CMFCTasksPane::GetGroupCaptionVertOffset](../Topic/CMFCTasksPane::GetGroupCaptionVertOffset.md)|Devuelve el desplazamiento actual del título de un grupo con respecto a los bordes superior e inferior del panel de tareas.|  
|[CMFCTasksPane::GetGroupCount](../Topic/CMFCTasksPane::GetGroupCount.md)|Devuelve el número total de grupos.|  
|[CMFCTasksPane::GetGroupLocation](../Topic/CMFCTasksPane::GetGroupLocation.md)|Devuelve el índice de grupo interno para un grupo determinado.|  
|[CMFCTasksPane::GetGroupVertOffset](../Topic/CMFCTasksPane::GetGroupVertOffset.md)|Devuelve el desplazamiento vertical de un grupo.|  
|[CMFCTasksPane::GetHorzMargin](../Topic/CMFCTasksPane::GetHorzMargin.md)|Devuelve el espaciado horizontal entre un panel de tareas y los bordes del área de cliente.|  
|[CMFCTasksPane::GetNextPages](../Topic/CMFCTasksPane::GetNextPages.md)||  
|[CMFCTasksPane::GetPageByGroup](../Topic/CMFCTasksPane::GetPageByGroup.md)|Recupera el índice de página para un grupo especificado.|  
|[CMFCTasksPane::GetPagesCount](../Topic/CMFCTasksPane::GetPagesCount.md)|Devuelve el número de páginas.|  
|[CMFCTasksPane::GetPreviousPages](../Topic/CMFCTasksPane::GetPreviousPages.md)||  
|[CMFCTasksPane::GetScrollBarCtrl](../Topic/CMFCTasksPane::GetScrollBarCtrl.md)|\(Invalida [CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)\).|  
|[CMFCTasksPane::GetTask](../Topic/CMFCTasksPane::GetTask.md)|Recupera una tarea.|  
|[CMFCTasksPane::GetTaskCount](../Topic/CMFCTasksPane::GetTaskCount.md)|Devuelve el número de elementos de tarea del grupo especificado.|  
|[CMFCTasksPane::GetTaskGroup](../Topic/CMFCTasksPane::GetTaskGroup.md)|Devuelve un grupo de tareas para el índice de un grupo determinado.|  
|[CMFCTasksPane::GetTaskLocation](../Topic/CMFCTasksPane::GetTaskLocation.md)|Devuelve el grupo y el índice de una tarea determinada.|  
|[CMFCTasksPane::GetTasksHorzOffset](../Topic/CMFCTasksPane::GetTasksHorzOffset.md)|Devuelve el desplazamiento horizontal de las tareas con respecto a los bordes izquierdos y derecho de sus grupos primarios.|  
|[CMFCTasksPane::GetTasksIconHorzOffset](../Topic/CMFCTasksPane::GetTasksIconHorzOffset.md)||  
|[CMFCTasksPane::GetTasksIconVertOffset](../Topic/CMFCTasksPane::GetTasksIconVertOffset.md)||  
|[CMFCTasksPane::GetVertMargin](../Topic/CMFCTasksPane::GetVertMargin.md)|Devuelve el espaciado vertical entre un panel de tareas y los bordes del área de cliente.|  
|[CMFCTasksPane::IsAccessibilityCompatible](../Topic/CMFCTasksPane::IsAccessibilityCompatible.md)|\(Invalida `CDockablePane::IsAccessibilityCompatible`\).|  
|[CMFCTasksPane::IsAnimationEnabled](../Topic/CMFCTasksPane::IsAnimationEnabled.md)|Indica si la animación está habilitada.|  
|[CMFCTasksPane::IsBackButtonEnabled](../Topic/CMFCTasksPane::IsBackButtonEnabled.md)|Indica si el botón Atrás está habilitado.|  
|[CMFCTasksPane::IsForwardButtonEnabled](../Topic/CMFCTasksPane::IsForwardButtonEnabled.md)|Indica si el botón Adelante está habilitado.|  
|[CMFCTasksPane::IsGroupCollapseEnabled](../Topic/CMFCTasksPane::IsGroupCollapseEnabled.md)||  
|[CMFCTasksPane::IsHistoryMenuButtonsEnabled](../Topic/CMFCTasksPane::IsHistoryMenuButtonsEnabled.md)|Indica si los botones de navegación **Siguiente** y **Anterior** tienen menús desplegables.|  
|[CMFCTasksPane::IsNavigationToolbarEnabled](../Topic/CMFCTasksPane::IsNavigationToolbarEnabled.md)|Indica si está la barra de herramientas de navegación está habilitada.|  
|[CMFCTasksPane::IsToolBox](../Topic/CMFCTasksPane::IsToolBox.md)||  
|[CMFCTasksPane::IsWrapLabelsEnabled](../Topic/CMFCTasksPane::IsWrapLabelsEnabled.md)|Indica si el panel de tareas ajusta las líneas en las etiquetas.|  
|[CMFCTasksPane::IsWrapTasksEnabled](../Topic/CMFCTasksPane::IsWrapTasksEnabled.md)|Indica si el panel de tareas ajusta las líneas en las tareas.|  
|[CMFCTasksPane::LoadState](../Topic/CMFCTasksPane::LoadState.md)|\(Invalida [CDockablePane::LoadState](http://msdn.microsoft.com/es-es/96110136-4f46-4764-8a76-3b4abaf77917)\).|  
|[CMFCTasksPane::OnCancel](../Topic/CMFCTasksPane::OnCancel.md)||  
|[CMFCTasksPane::OnClickTask](../Topic/CMFCTasksPane::OnClickTask.md)|Lo llama el marco cuando el usuario hace clic en un elemento del panel de tareas.|  
|[CMFCTasksPane::OnOK](../Topic/CMFCTasksPane::OnOK.md)||  
|[CMFCTasksPane::OnPressBackButton](../Topic/CMFCTasksPane::OnPressBackButton.md)|Lo llama el marco cuando el usuario hace clic en el botón Atrás.|  
|[CMFCTasksPane::OnPressForwardButton](../Topic/CMFCTasksPane::OnPressForwardButton.md)|Lo llama el marco cuando el usuario hace clic en el botón de navegación Adelante.|  
|[CMFCTasksPane::OnPressHomeButton](../Topic/CMFCTasksPane::OnPressHomeButton.md)|Lo llama el marco cuando el usuario hace clic en el botón de navegación Inicio.|  
|[CMFCTasksPane::OnPressOtherButton](../Topic/CMFCTasksPane::OnPressOtherButton.md)||  
|[CMFCTasksPane::OnSetAccData](../Topic/CMFCTasksPane::OnSetAccData.md)|\(Invalida [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)\).|  
|[CMFCTasksPane::OnUpdateCmdUI](../Topic/CMFCTasksPane::OnUpdateCmdUI.md)|\(Invalida [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/es-es/5dd61606-1c12-40d4-b024-f3839aa5e2e0)\).|  
|[CMFCTasksPane::PreTranslateMessage](../Topic/CMFCTasksPane::PreTranslateMessage.md)|\(Invalida [CDockablePane::PreTranslateMessage](http://msdn.microsoft.com/es-es/49a242cc-b158-400e-9e01-0345ec9c3ffd)\).|  
|[CMFCTasksPane::RecalcLayout](../Topic/CMFCTasksPane::RecalcLayout.md)|\(Invalida [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)\).|  
|[CMFCTasksPane::RemoveAllGroups](../Topic/CMFCTasksPane::RemoveAllGroups.md)|Quita todos los grupos de la página especificada.|  
|[CMFCTasksPane::RemoveAllPages](../Topic/CMFCTasksPane::RemoveAllPages.md)|Quita todas las páginas del panel de tareas excepto la página predeterminada \(primera\).|  
|[CMFCTasksPane::RemoveAllTasks](../Topic/CMFCTasksPane::RemoveAllTasks.md)|Quita todas las tareas del grupo.|  
|[CMFCTasksPane::RemoveGroup](../Topic/CMFCTasksPane::RemoveGroup.md)|Quita un grupo.|  
|[CMFCTasksPane::RemovePage](../Topic/CMFCTasksPane::RemovePage.md)|Quita una página especificada desde el panel de tareas.|  
|[CMFCTasksPane::RemoveTask](../Topic/CMFCTasksPane::RemoveTask.md)|Quita una tarea de un grupo de tareas.|  
|[CMFCTasksPane::SaveState](../Topic/CMFCTasksPane::SaveState.md)|\(Invalida [CDockablePane::SaveState](http://msdn.microsoft.com/es-es/c5c24249-8d0d-46cb-96d9-9f5c6dc191db)\).|  
|[CMFCTasksPane::Serialize](../Topic/CMFCTasksPane::Serialize.md)|\(Invalida [CDockablePane::Serialize](http://msdn.microsoft.com/es-es/09787e59-e446-4e76-894b-206d303dcfd6)\).|  
|[CMFCTasksPane::SetActivePage](../Topic/CMFCTasksPane::SetActivePage.md)|Quita una página especificada del panel de tareas.|  
|[CMFCTasksPane::SetCaption](../Topic/CMFCTasksPane::SetCaption.md)|Establece el nombre del título de un panel de tareas.|  
|[CMFCTasksPane::SetGroupCaptionHeight](../Topic/CMFCTasksPane::SetGroupCaptionHeight.md)|Establece la altura de un título de grupo.|  
|[CMFCTasksPane::SetGroupCaptionHorzOffset](../Topic/CMFCTasksPane::SetGroupCaptionHorzOffset.md)|Establece el desplazamiento horizontal del título de un grupo.|  
|[CMFCTasksPane::SetGroupCaptionVertOffset](../Topic/CMFCTasksPane::SetGroupCaptionVertOffset.md)|Establece el desplazamiento vertical del título de un grupo.|  
|[CMFCTasksPane::SetGroupName](../Topic/CMFCTasksPane::SetGroupName.md)|Establece el nombre de un grupo.|  
|[CMFCTasksPane::SetGroupTextColor](../Topic/CMFCTasksPane::SetGroupTextColor.md)|Establece el color del texto del título de un grupo.|  
|[CMFCTasksPane::SetGroupVertOffset](../Topic/CMFCTasksPane::SetGroupVertOffset.md)|Establece el desplazamiento vertical de un grupo.|  
|[CMFCTasksPane::SetHorzMargin](../Topic/CMFCTasksPane::SetHorzMargin.md)|Establece el espaciado horizontal entre un panel de tareas y los bordes del área de cliente.|  
|[CMFCTasksPane::SetIconsList](../Topic/CMFCTasksPane::SetIconsList.md)|Establece la lista de imágenes asociadas a las tareas.|  
|[CMFCTasksPane::SetPageCaption](../Topic/CMFCTasksPane::SetPageCaption.md)|Establece el texto del título de la página de un panel de tareas.|  
|[CMFCTasksPane::SetTaskName](../Topic/CMFCTasksPane::SetTaskName.md)|Establece el nombre de una tarea.|  
|[CMFCTasksPane::SetTasksIconHorzOffset](../Topic/CMFCTasksPane::SetTasksIconHorzOffset.md)||  
|[CMFCTasksPane::SetTasksIconVertOffset](../Topic/CMFCTasksPane::SetTasksIconVertOffset.md)||  
|[CMFCTasksPane::SetTaskTextColor](../Topic/CMFCTasksPane::SetTaskTextColor.md)|Establece el color del texto de una tarea.|  
|[CMFCTasksPane::SetTasksHorzOffset](../Topic/CMFCTasksPane::SetTasksHorzOffset.md)|Establece el desplazamiento horizontal de las tareas con respecto a los bordes izquierdos y derecho de sus grupos primarios.|  
|[CMFCTasksPane::SetVertMargin](../Topic/CMFCTasksPane::SetVertMargin.md)|Establece el espaciado vertical entre un panel de tareas y los bordes del área de cliente.|  
|[CMFCTasksPane::SetWindowHeight](../Topic/CMFCTasksPane::SetWindowHeight.md)|Establece la altura de una ventana.|  
|[CMFCTasksPane::ShowCommandMessageString](../Topic/CMFCTasksPane::ShowCommandMessageString.md)||  
|[CMFCTasksPane::ShowTask](../Topic/CMFCTasksPane::ShowTask.md)|Muestra u oculta una tarea.|  
|[CMFCTasksPane::ShowTaskByCmdId](../Topic/CMFCTasksPane::ShowTaskByCmdId.md)|Muestra u oculta una tarea según su identificador de comando.|  
|[CMFCTasksPane::Update](../Topic/CMFCTasksPane::Update.md)|Actualiza los elementos de la interfaz gráfica de usuario que pertenecen a un panel de tareas.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPane::OnActivateTasksPanePage](../Topic/CMFCTasksPane::OnActivateTasksPanePage.md)|Lo llama el marco cuando se activa una página nueva de panel de tareas.|  
  
## Comentarios  
 La clase `CMFCTasksPane` implementa las funciones siguientes:  
  
-   Los elementos se pueden agrupar y cada agrupación de elementos puede tener un título asociado.  
  
-   Las agrupaciones de elementos se pueden contraer o expandir.  
  
-   Se puede asignar un icono a cada elemento del panel de tareas.  
  
-   Los elementos individuales se pueden asociar con un identificador de comando que se inicia cuando un usuario hace clic en el elemento.  Cuando se produce el clic, el mensaje `WM_COMMAND` se envía al propietario del control del panel de tareas.  
  
 Para usar el control `CMFCTasksPane` de la aplicación, siga estos pasos:  
  
1.  Incruste un objeto `CMFCTasksPane` en la clase de ventana de marco principal.  
  
2.  Al procesar el mensaje `WM_CREATE`, llame al método `Create`.  Puede usar los estilos [CControlBar](../../mfc/reference/ccontrolbar-class.md) habituales.  Para obtener más información, consulta `CControlBar::Create`.  
  
3.  Llame al método [CMFCTasksPane::AddGroup](../Topic/CMFCTasksPane::AddGroup.md) para agregar varios grupos.  
  
4.  Llame a las funciones miembro [CMFCTasksPane::AddTask](../Topic/CMFCTasksPane::AddTask.md), [CMFCTasksPane::AddLabel](../Topic/CMFCTasksPane::AddLabel.md) o [CMFCTasksPane::AddMRUFilesList](../Topic/CMFCTasksPane::AddMRUFilesList.md) para agregar nuevos elementos \(tareas\) a cada grupo.  
  
5.  Llame a [CMFCTasksPane::EnableGroupCollapse](../Topic/CMFCTasksPane::EnableGroupCollapse.md) para especificar si se pueden contraer grupos de elementos.  
  
 En la siguiente ilustración se muestra un control de panel de tareas típicas.  El primer grupo es un grupo *especial* y su título es un color más oscuro.  El tercer grupo está contraído.  El último grupo está alineado en la parte inferior del panel de tareas y no tiene título, y la última tarea del grupo es una etiqueta sencilla:  
  
 ![Ejemplo de panel de tareas](../../mfc/reference/media/nexttaskpane.png "NextTaskPane")  
  
 Puede personalizar la apariencia del panel de tareas ajustando varios márgenes y desplazamientos.  En la siguiente ilustración se explica el significado de estas variables:  
  
 ![Grupo de tareas personalizado](../../mfc/reference/media/nexttaskgrpcustom.png "NextTaskGrpCustom")  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo construir un objeto `CMFCTasksPane` y cómo usar varios métodos de la clase `CMFCTasksPane`.  En el ejemplo se muestra cómo habilitar la contracción de grupos de tareas, habilitar los menús desplegables en los botones de navegación **Siguiente** y **Anterior**, habilitar los botones de desplazamiento en lugar de una barra de desplazamiento, habilitar el ajuste de líneas para el texto de las etiquetas, establecer el nombre del título del panel de tareas, establecer el color del texto del título de un grupo y establecer los márgenes horizontales y verticales.  
  
 [!code-cpp[NVC_MFC_RibbonApp#28](../../mfc/reference/codesnippet/CPP/cmfctaskspane-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)  
  
## Requisitos  
 **Encabezado:** afxTasksPane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md)   
 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)