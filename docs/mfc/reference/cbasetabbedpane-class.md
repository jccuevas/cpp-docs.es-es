---
title: "CBaseTabbedPane (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBaseTabbedPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseTabbedPane (clase)"
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CBaseTabbedPane (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Extiende la funcionalidad de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) para admitir la creación de ventanas con fichas.  
  
## Sintaxis  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## Members  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md)|Agrega una nueva pestaña a un panel con fichas.|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../Topic/CBaseTabbedPane::AllowDestroyEmptyTabbedPane.md)|Especifica si un panel con fichas vacío puede ser destruido.|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](../Topic/CBaseTabbedPane::ApplyRestoredTabInfo.md)|Aplicar las opciones de tabulación, que se cargan de registro, panel tabulado.|  
|[CBaseTabbedPane::CanFloat](../Topic/CBaseTabbedPane::CanFloat.md)|Determina si el panel puede flotar.  \(Reemplaza [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md).\)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](../Topic/CBaseTabbedPane::CanSetCaptionTextToTabName.md)|Determina si la leyenda del panel con fichas debe mostrar el mismo texto que la pestaña activa.|  
|[CBaseTabbedPane::ConvertToTabbedDocument](../Topic/CBaseTabbedPane::ConvertToTabbedDocument.md)|\(Reemplaza [CDockablePane::ConvertToTabbedDocument](../Topic/CDockablePane::ConvertToTabbedDocument.md).\)|  
|[CBaseTabbedPane::DetachPane](../Topic/CBaseTabbedPane::DetachPane.md)|Convierte uno o varios paneles acoplable a MDI con documentos.|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](../Topic/CBaseTabbedPane::EnableSetCaptionTextToTabName.md)|Habilita o deshabilita la capacidad de panel con fichas de sincronizar el texto de título con el texto de la etiqueta en la pestaña activa.|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](../Topic/CBaseTabbedPane::FillDefaultTabsOrderArray.md)|Restablece la pestaña interna ordenada un estado predeterminada.|  
|[CBaseTabbedPane::FindBarByTabNumber](../Topic/CBaseTabbedPane::FindBarByTabNumber.md)|Devuelve un panel que resida en una pestaña a la pestaña se identifica mediante un índice cero\- basado en la ficha.|  
|||  
|[CBaseTabbedPane::FindPaneByID](../Topic/CBaseTabbedPane::FindPaneByID.md)|Devuelve un panel que sea identificado por identificador de panel|  
|[CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)|Flota un panel, pero solo si el panel se encuentra actualmente en una pestaña desmontable.|  
|[CBaseTabbedPane::GetDefaultTabsOrder](../Topic/CBaseTabbedPane::GetDefaultTabsOrder.md)|Devuelve el orden predeterminado de fichas en el panel.|  
|[CBaseTabbedPane::GetFirstVisibleTab](../Topic/CBaseTabbedPane::GetFirstVisibleTab.md)|Recupera un puntero a la pestaña primero mostrada.|  
|[CBaseTabbedPane::GetMinSize](../Topic/CBaseTabbedPane::GetMinSize.md)|Recupera el mínimo permitido el tamaño del panel.  \(Reemplaza [CPane::GetMinSize](../Topic/CPane::GetMinSize.md).\)|  
|[CBaseTabbedPane::GetPaneIcon](../Topic/CBaseTabbedPane::GetPaneIcon.md)|Devuelve un identificador al icono del panel.  \(Reemplaza [CBasePane::GetPaneIcon](../Topic/CBasePane::GetPaneIcon.md).\)|  
|[CBaseTabbedPane::GetPaneList](../Topic/CBaseTabbedPane::GetPaneList.md)|Devuelve una lista de paneles que se incluyen en el panel con fichas.|  
|[CBaseTabbedPane::GetTabArea](../Topic/CBaseTabbedPane::GetTabArea.md)|Devuelve los rectángulos delimitadores en la parte superior y bottom áreas de la pestaña.|  
|[CBaseTabbedPane::GetTabsNum](../Topic/CBaseTabbedPane::GetTabsNum.md)|Devuelve el número de fichas en una ventana de la pestaña.|  
|[CBaseTabbedPane::GetUnderlyingWindow](../Topic/CBaseTabbedPane::GetUnderlyingWindow.md)|Obtiene la ventana \(incluida\) de la pestaña subyacente.|  
|[CBaseTabbedPane::GetVisibleTabsNum](../Topic/CBaseTabbedPane::GetVisibleTabsNum.md)|Devuelve el número de fichas mostradas.|  
|[CBaseTabbedPane::HasAutoHideMode](../Topic/CBaseTabbedPane::HasAutoHideMode.md)|Determina a si el panel con fichas puede intercambiarse oculta automáticamente el modo.|  
|[CBaseTabbedPane::IsHideSingleTab](../Topic/CBaseTabbedPane::IsHideSingleTab.md)|Determina si el panel con fichas está oculto si se muestra sólo una pestaña.|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Se utiliza internamente durante la serialización.|  
|[CBaseTabbedPane::RecalcLayout](../Topic/CBaseTabbedPane::RecalcLayout.md)|Actualiza la información de diseño del panel.  \(Reemplaza [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md).\)|  
|[CBaseTabbedPane::RemovePane](../Topic/CBaseTabbedPane::RemovePane.md)|Quita un panel de panel con fichas.|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|Se utiliza internamente durante la serialización.|  
|`CBaseTabbedPane::Serialize`|\(Reemplaza [CDockablePane::Serialize](http://msdn.microsoft.com/es-es/09787e59-e446-4e76-894b-206d303dcfd6).\)|  
|`CBaseTabbedPane::SerializeTabWindow`|Se utiliza internamente durante la serialización.|  
|[CBaseTabbedPane::SetAutoDestroy](../Topic/CBaseTabbedPane::SetAutoDestroy.md)|Determina si la barra de control con fichas se destruida automáticamente.|  
|[CBaseTabbedPane::SetAutoHideMode](../Topic/CBaseTabbedPane::SetAutoHideMode.md)|Alterna el panel acoplable entre mostrar y ocultar automáticamente el modo.  \(Reemplaza [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md).\)|  
|[CBaseTabbedPane::ShowTab](../Topic/CBaseTabbedPane::ShowTab.md)|Muestra u oculta una pestaña.|  
  
## Comentarios  
 Esta clase es una clase abstracta y no se pueden crear instancias.  Implementa servicios que son comunes a todos los tipos de paneles con pestañas.  
  
 Actualmente, la biblioteca incluye dos clases con pestañas de panel derivadas: [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) y [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Un objeto de `CBaseTabbedPane` contiene un puntero a un objeto de [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md).  [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) se convierte en una ventana secundaria de panel con fichas.  
  
 Para obtener más información sobre cómo crear paneles con pestañas, vea [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md), y [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
## Requisitos  
 **Encabezado:** afxBaseTabbedPane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)