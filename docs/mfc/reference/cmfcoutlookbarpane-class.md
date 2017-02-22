---
title: "CMFCOutlookBarPane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCOutlookBarPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanBeRestored method"
  - "CMFCOutlookBarPane class"
  - "Dock method"
  - "IsChangeState method"
  - "OnBeforeFloat method"
  - "RestoreOriginalstate method"
  - "SmartUpdate method"
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCOutlookBarPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Un control derivado de [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) que se pueden insertar en una barra de Outlook \([CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)\).  El panel de barra de Outlook contiene una columna de botones grandes.  El usuario puede subir y bajar la lista de botones si es mayor que el panel.  Cuando el usuario desasocia un panel de barra de Outlook de la barra de Outlook, puede flotar o acoplar en la ventana de marco principal.  
  
## Sintaxis  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Constructor predeterminado.|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](../Topic/CMFCOutlookBarPane::AddButton.md)|Agrega un botón al panel de barra de Outlook.|  
|[CMFCOutlookBarPane::CanBeAttached](../Topic/CMFCOutlookBarPane::CanBeAttached.md)|Determina si el panel se puede acoplar a otra ventana del panel o del cuadro.  \(Reemplaza [CBasePane::CanBeAttached](../Topic/CBasePane::CanBeAttached.md).\)|  
|`CMFCOutlookBarPane::CanBeRestored`|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización.  \(Reemplaza [CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md).\)|  
|[CMFCOutlookBarPane::ClearAll](../Topic/CMFCOutlookBarPane::ClearAll.md)|Libera los recursos utilizados por las imágenes en el panel de barra de Outlook.|  
|[CMFCOutlookBarPane::Create](../Topic/CMFCOutlookBarPane::Create.md)|Crear el panel de barra de Outlook.|  
|`CMFCOutlookBarPane::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCOutlookBarPane::Dock`|Llamado por el marco para acoplar el panel de barra de Outlook. \(Reemplaza `CPane::Dock`.\)|  
|[CMFCOutlookBarPane::EnablePageScrollMode](../Topic/CMFCOutlookBarPane::EnablePageScrollMode.md)|Especifica si las flechas de desplazamiento en el responsable de panel de barra de Outlook la lista de botones por página, o en el botón.|  
|[CMFCOutlookBarPane::GetRegularColor](../Topic/CMFCOutlookBarPane::GetRegularColor.md)|Devuelve el color del texto \(no seleccionado\) normal del panel de barra de Outlook.|  
|`CMFCOutlookBarPane::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCOutlookBarPane::IsBackgroundTexture](../Topic/CMFCOutlookBarPane::IsBackgroundTexture.md)|Determina si una imagen de fondo cargada para el panel de barra de Outlook.|  
|`CMFCOutlookBarPane::IsChangeState`|Determina si un panel flotante puede acoplarse.  \(Reemplaza `CPane::IsChangeState`.\)|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](../Topic/CMFCOutlookBarPane::IsDrawShadedHighlight.md)|Determina si el borde del botón se ve oscurecido cuando se resalta un botón y se muestra una imagen de fondo.|  
|`CMFCOutlookBarPane::OnBeforeFloat`|Llamado por el marco cuando un panel está a punto de flotar.  \(Reemplaza [CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md).\)|  
|[CMFCOutlookBarPane::RemoveButton](../Topic/CMFCOutlookBarPane::RemoveButton.md)|Quita el botón que tiene un identificador especificada de comando|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaura el estado original de una barra de herramientas.  \(Reemplaza [CMFCToolBar::RestoreOriginalState](../Topic/CMFCToolBar::RestoreOriginalState.md).\)|  
|[CMFCOutlookBarPane::SetBackColor](../Topic/CMFCOutlookBarPane::SetBackColor.md)|Establece el color de fondo.|  
|[CMFCOutlookBarPane::SetBackImage](../Topic/CMFCOutlookBarPane::SetBackImage.md)|establece la imagen de fondo.|  
|[CMFCOutlookBarPane::SetDefaultState](../Topic/CMFCOutlookBarPane::SetDefaultState.md)|Restaurar el panel de barra de Outlook al original establecido de botones.|  
|[CMFCOutlookBarPane::SetExtraSpace](../Topic/CMFCOutlookBarPane::SetExtraSpace.md)|Establece el número de píxeles de relleno utilizados alrededor del panel de barra de Outlook.|  
|[CMFCOutlookBarPane::SetTextColor](../Topic/CMFCOutlookBarPane::SetTextColor.md)|Establece los colores de texto normal y resaltada en el panel de barra de Outlook.|  
|[CMFCOutlookBarPane::SetTransparentColor](../Topic/CMFCOutlookBarPane::SetTransparentColor.md)|Establece el color transparente para el panel de barra de Outlook.|  
|`CMFCOutlookBarPane::SmartUpdate`|Se utiliza internamente para actualizar la barra de Outlook.  \(Reemplaza `CMFCToolBar::SmartUpdate`.\)|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](../Topic/CMFCOutlookBarPane::EnableContextMenuItems.md)|Especifica que los elementos de menú contextual se muestran en modo de personalización.|  
|[CMFCOutlookBarPane::RemoveAllButtons](../Topic/CMFCOutlookBarPane::RemoveAllButtons.md)|Quita todos los botones del panel de barra de Outlook.  \(Reemplaza [CMFCToolBar::RemoveAllButtons](../Topic/CMFCToolBar::RemoveAllButtons.md).\)|  
  
## Comentarios  
 Para obtener información sobre cómo implementar una barra de Outlook, vea [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Para obtener un ejemplo de una barra de Outlook, vea el ejemplo OutlookDemo proyectar.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar los diversos métodos de la clase de `CMFCOutlookBarPane` .  El ejemplo muestra cómo crear un panel de barra de Outlook, habilita el manejo vertical de muestra de la página, habilita el acoplamiento, y establece el color de fondo de la barra de Outlook.  Este fragmento de código es parte de [Ejemplo de vistas de Outlook Múltiples](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/CPP/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/CPP/cmfcoutlookbarpane-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## Requisitos  
 **encabezado:** afxoutlookbarpane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)