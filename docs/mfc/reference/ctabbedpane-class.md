---
title: "CTabbedPane Class | Microsoft Docs"
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
  - "CTabbedPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabbedPane class"
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTabbedPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad de un panel con pestañas separables.  
  
## Sintaxis  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CTabbedPane::CTabbedPane`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabbedPane::DetachPane](../Topic/CTabbedPane::DetachPane.md)|\(Reemplaza a [CBaseTabbedPane::DetachPane](../Topic/CBaseTabbedPane::DetachPane.md)\).|  
|[CTabbedPane::EnableTabAutoColor](../Topic/CTabbedPane::EnableTabAutoColor.md)|Habilita o deshabilita el coloreado automático de pestañas.|  
|[CTabbedPane::FloatTab](../Topic/CTabbedPane::FloatTab.md)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable.  \(Reemplaza a [CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)\).|  
|[CTabbedPane::GetTabArea](../Topic/CTabbedPane::GetTabArea.md)|Devuelve el tamaño y la posición del área de pestañas de la ventana con pestañas.|  
|[CTabbedPane::GetTabWnd](../Topic/CTabbedPane::GetTabWnd.md)||  
|[CTabbedPane::HasAutoHideMode](../Topic/CTabbedPane::HasAutoHideMode.md)|Determina si el panel con pestañas se puede cambiar a modo de ocultación automática.  \(Reemplaza a [CBaseTabbedPane::HasAutoHideMode](../Topic/CBaseTabbedPane::HasAutoHideMode.md)\).|  
|[CTabbedPane::IsTabLocationBottom](../Topic/CTabbedPane::IsTabLocationBottom.md)|Determina si las pestañas se sitúan en la parte inferior de la ventana.|  
|[CTabbedPane::ResetTabs](../Topic/CTabbedPane::ResetTabs.md)|Restablece todos los paneles con pestañas al estado predeterminado.|  
|[CTabbedPane::SetTabAutoColors](../Topic/CTabbedPane::SetTabAutoColors.md)|Establece una lista de colores personalizados que se pueden usar cuando se habilita la característica de color automático.|  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CTabbedPane::m\_bTabsAlwaysTop](../Topic/CTabbedPane::m_bTabsAlwaysTop.md)|La ubicación predeterminada de las pestañas en la aplicación.|  
|[CTabbedPane::m\_pTabWndRTC](../Topic/CTabbedPane::m_pTabWndRTC.md)|Información de clase en tiempo de ejecución para un derivado de `CMFCTabCtrl` personalizado.|  
  
## Comentarios  
 El marco de trabajo crea automáticamente una instancia de esta clase cuando un usuario adjunta un panel a otro apuntando al título del segundo panel.  Todos los paneles con pestañas que se crean mediante el marco de trabajo tienen un identificador de \-1.  
  
 Para especificar pestañas normales en lugar de pestañas de tipo Outlook, pase el estilo `AFX_CBRS_REGULAR_TABS` al método [CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md).  
  
 Si crea un panel con pestañas separables, el marco de trabajo puede destruir automáticamente el panel, por lo que no debe almacenar el puntero.  Para obtener un puntero al panel con pestañas, llame al método `CBasePane::GetParentTabbedPane`.  
  
## Ejemplo  
 En este ejemplo, crearemos un objeto `CTabbedPane`.  Después usaremos [CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md) para asociar otras pestañas.  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);  
if (!pTabbededBar->Create (_T(""), this, CRect (0, 0, 200, 200),  
                           TRUE,   
                           (UINT) -1,  
                           WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
                           WS_CLIPCHILDREN | CBRS_LEFT |    
                           CBRS_FLOAT_MULTI))  
{  
    TRACE0("Failed to create Solution Explorer bar\n");  
    return FALSE;      // fail to create  
}  
  
pTabbededBar->AddTab (&m_wndClassView);  
pTabbededBar->AddTab (&m_wndResourceView);  
pTabbededBar->AddTab (&m_wndFileView);  
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);  
DockPane(pTabbededBar);  
```  
  
## Ejemplo  
 Otra forma de crear un objeto de la barra de control con pestañas es usar [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md).  El método `AttachToTabWnd` crea dinámicamente un objeto de panel con pestañas que usa información de clase en tiempo de ejecución establecido por [CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md).  
  
 En este ejemplo se crea dinámicamente un panel con pestañas, se asocian dos pestañas y se convierte la segunda pestaña en no separable.  
  
```  
DockPane(&m_wndClassView);  
CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView, DM_SHOW, TRUE,  
                                  (CDockablePane**) &pTabbedBar);  
m_wndFileView.AttachToTabWnd (pTabbedBar, DM_SHOW, TRUE,  
                              (CDockablePane**) &pTabbedBar);  
pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1, FALSE);  
```  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## Requisitos  
 **Encabezado:** afxTabbedPane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CBaseTabbedPane \(Clase\)](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)