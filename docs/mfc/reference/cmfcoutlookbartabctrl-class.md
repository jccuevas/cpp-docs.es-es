---
title: "CMFCOutlookBarTabCtrl Class | Microsoft Docs"
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
  - "CMFCOutlookBarTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCOutlookBarTabCtrl class"
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCOutlookBarTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un control de ficha que tiene el aspecto visual de **Panel de navegacin** en Microsoft Outlook.  
  
## Sintaxis  
  
```  
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Constructor predeterminado.|  
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBarTabCtrl::AddControl](../Topic/CMFCOutlookBarTabCtrl::AddControl.md)|Agrega un control de Windows como una nueva ficha en la barra de Outlook.|  
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Llamado por el marco para determinar las dimensiones del cuadro de edición que se produce cuando un usuario cambia una pestaña.  \(Reemplaza `CMFCBaseTabCtrl::CalcRectEdit`.\)|  
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](../Topic/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons.md)|Llama el marco durante el tamaño operaciones para determinar si menos botones de la ficha de la barra de Outlook se pueden mostrar que actualmente visible.|  
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](../Topic/CMFCOutlookBarTabCtrl::CanShowMorePageButtons.md)|Llama el marco durante el tamaño operaciones para determinar si varios botones de la ficha de la barra de Outlook se pueden mostrar que actualmente visible.|  
|[CMFCOutlookBarTabCtrl::Create](../Topic/CMFCOutlookBarTabCtrl::Create.md)|Crear el control de ficha de la barra de Outlook.|  
|`CMFCOutlookBarTabCtrl::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCOutlookBarTabCtrl::EnableAnimation](../Topic/CMFCOutlookBarTabCtrl::EnableAnimation.md)|Especifica si la animación que durante el modificador entre las fichas activo está habilitada.|  
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](../Topic/CMFCOutlookBarTabCtrl::EnableInPlaceEdit.md)|Especifica si un usuario puede modificar las etiquetas de texto en los botones de la ficha de la barra de Outlook.  \(Reemplaza [CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md).\)|  
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](../Topic/CMFCOutlookBarTabCtrl::EnableScrollButtons.md)|Llamado por el marco para habilitar los botones que permiten al usuario desplazarse por los botones en el panel de barra de Outlook.|  
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|identifica el panel que contiene un punto especificado.  \(Reemplaza [CMFCBaseTabCtrl::FindTargetWnd](../Topic/CMFCBaseTabCtrl::FindTargetWnd.md).\)|  
|[CMFCOutlookBarTabCtrl::GetBorderSize](../Topic/CMFCOutlookBarTabCtrl::GetBorderSize.md)|Devuelve el tamaño del borde del control de ficha de Outlook.|  
|`CMFCOutlookBarTabCtrl::GetTabArea`|Recupera el tamaño y la posición del área de la ficha del control de ficha.  \(Reemplaza [CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md).\)|  
|`CMFCOutlookBarTabCtrl::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](../Topic/CMFCOutlookBarTabCtrl::GetVisiblePageButtons.md)||  
|[CMFCOutlookBarTabCtrl::IsAnimation](../Topic/CMFCOutlookBarTabCtrl::IsAnimation.md)|Determina si la animación que durante el modificador entre las fichas activo está habilitada.|  
|[CMFCOutlookBarTabCtrl::IsMode2003](../Topic/CMFCOutlookBarTabCtrl::IsMode2003.md)|Determina si el control de ficha de la barra de Outlook está en un modo que emule Microsoft Outlook 2003.|  
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Determina si un punto está dentro del área de la ficha.  \(Reemplaza [CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md).\)|  
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Determina si una pestaña es desmontable.  \(Reemplaza [CMFCBaseTabCtrl::IsTabDetachable](../Topic/CMFCBaseTabCtrl::IsTabDetachable.md).\)|  
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Llamado por el marco cuando se inserta o se quita una pestaña.  \(Reemplaza `CMFCBaseTabCtrl::OnChangeTabs`.\)|  
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](../Topic/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons.md)|Llamado por el marco para reducir el número de botones de la ficha que están visibles.|  
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](../Topic/CMFCOutlookBarTabCtrl::OnShowMorePageButtons.md)|Llamado por el marco para aumentar el número de botones de la ficha que están visibles.|  
|[CMFCOutlookBarTabCtrl::OnShowOptions](../Topic/CMFCOutlookBarTabCtrl::OnShowOptions.md)|Muestra el cuadro de diálogo **Opciones del panel de navegación** .|  
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Actualiza el diseño interno del control de ficha.  \(Reemplaza [CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md).\)|  
|[CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md)|Establece la pestaña activa.  \(Reemplaza [CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md).\)|  
|[CMFCOutlookBarTabCtrl::SetBorderSize](../Topic/CMFCOutlookBarTabCtrl::SetBorderSize.md)|Establece el tamaño del borde del control de ficha de Outlook.|  
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](../Topic/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign.md)|Establece la alineación de las etiquetas de texto en los botones de la ficha de la barra de Outlook.|  
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](../Topic/CMFCOutlookBarTabCtrl::SetToolbarImageList.md)|Establece el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook en el modo de Outlook 2003 \(vea [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)\).|  
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](../Topic/CMFCOutlookBarTabCtrl::SetVisiblePageButtons.md)||  
  
## Comentarios  
 Para crear una barra de Outlook que tiene compatibilidad de acoplamiento, utilice un objeto de `CMFCOutlookBar` para hospedar el control de ficha de la barra de Outlook.  Para obtener más información, vea [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo inicializar un objeto de `CMFCOutlookBarTabCtrl` y utilizar varios métodos en la clase de `CMFCOutlookBarTabCtrl` .  El ejemplo muestra cómo habilitar la edición en contexto de la etiqueta de texto en los botones de la ficha de la barra de Outlook, habilita la animación, los identificadores habilitados de desplazamiento que permiten al usuario desplazarse por los botones en el panel de barra de Outlook, establezca el tamaño del borde del control de ficha de Outlook, y establecer la alineación de las etiquetas de texto en los botones de la ficha de la barra de Outlook.  Este fragmento de código es parte de [Ejemplo de demostración de Outlook](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/CPP/cmfcoutlookbartabctrl-class_1.cpp)]  
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/CPP/cmfcoutlookbartabctrl-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxoutlookbartabctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)   
 [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md)