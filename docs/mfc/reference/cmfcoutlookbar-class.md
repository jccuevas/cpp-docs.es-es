---
title: "CMFCOutlookBar (Clase) | Microsoft Docs"
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
  - "CMFCOutlookBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCOutlookBar (clase)"
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 34
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCOutlookBar (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un panel con fichas con el aspecto visual **Panel de exploración** en Microsoft Outlook 2000 u Outlook 2003.  El objeto de `CMFCOutlookBar` contiene un objeto de [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) y una serie de fichas.  Las fichas pueden ser objetos de [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) o `CWnd`\- objetos derivados.  El usuario, la barra de Outlook aparece como una serie de botones y un área de presentación.  Cuando el usuario hace clic en un botón, se muestra el panel de control correspondiente o del botón.  
  
## Sintaxis  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## Members  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|Constructor predeterminado.|  
|`CMFCOutlookBar::~CMFCOutlookBar`|Un destructor.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](../Topic/CMFCOutlookBar::AllowDestroyEmptyTabbedPane.md)|Especifica si un panel con fichas vacío puede ser destruido.  \(Reemplaza [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../Topic/CBaseTabbedPane::AllowDestroyEmptyTabbedPane.md).\)|  
|[CMFCOutlookBar::CanAcceptPane](../Topic/CMFCOutlookBar::CanAcceptPane.md)|Determina si otro panel se puede acoplar el panel de barra de Outlook.  \(Reemplaza CDockablePane::CanAcceptPane.\)|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](../Topic/CMFCOutlookBar::CanSetCaptionTextToTabName.md)|Determina si la leyenda del panel con fichas genera el mismo texto que la pestaña activa.  \(Reemplaza [CBaseTabbedPane::CanSetCaptionTextToTabName](../Topic/CBaseTabbedPane::CanSetCaptionTextToTabName.md).\)|  
|[CMFCOutlookBar::Create](../Topic/CMFCOutlookBar::Create.md)|Crear el control de barra de Outlook.|  
|[CMFCOutlookBar::CreateCustomPage](../Topic/CMFCOutlookBar::CreateCustomPage.md)|Crea una pestaña personalizada de la barra de Outlook.|  
|`CMFCOutlookBar::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](../Topic/CMFCOutlookBar::DoesAllowDynInsertBefore.md)|Determina si un usuario puede acoplar una barra de controles en el borde externo de la barra de Outlook.|  
|[CMFCOutlookBar::FloatTab](../Topic/CMFCOutlookBar::FloatTab.md)|Flota un panel, pero solo si el panel se encuentra actualmente en una pestaña desmontable.  \(Reemplaza [CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md).\)|  
|[CMFCOutlookBar::GetButtonsFont](../Topic/CMFCOutlookBar::GetButtonsFont.md)|Devuelve la fuente del texto de los botones de la barra de Outlook.|  
|[CMFCOutlookBar::GetTabArea](../Topic/CMFCOutlookBar::GetTabArea.md)|Devuelve el tamaño y la posición de las áreas de la pestaña respecto a la barra de Outlook.  \(Reemplaza [CBaseTabbedPane::GetTabArea](../Topic/CBaseTabbedPane::GetTabArea.md).\)|  
|`CMFCOutlookBar::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|  
|[CMFCOutlookBar::IsMode2003](../Topic/CMFCOutlookBar::IsMode2003.md)|Determina si el comportamiento de los imita de la barra de Outlook que de Microsoft Office Outlook 2003 \(vea comentarios\).|  
|[CMFCOutlookBar::OnAfterAnimation](../Topic/CMFCOutlookBar::OnAfterAnimation.md)|Llamado por [CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md) después de la pestaña activa se ha establecido mediante la animación.|  
|[CMFCOutlookBar::OnBeforeAnimation](../Topic/CMFCOutlookBar::OnBeforeAnimation.md)|Llamado por [CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md) antes de una ficha se establece como la pestaña activa mediante la animación.|  
|[CMFCOutlookBar::OnScroll](../Topic/CMFCOutlookBar::OnScroll.md)|Llamado por el marco si la barra de Outlook se desplaza hacia arriba o abajo.|  
|[CMFCOutlookBar::RemoveCustomPage](../Topic/CMFCOutlookBar::RemoveCustomPage.md)|Quita una ficha personalizada de la barra de Outlook.|  
|[CMFCOutlookBar::SetButtonsFont](../Topic/CMFCOutlookBar::SetButtonsFont.md)|Establece la fuente del texto de los botones de la barra de Outlook.|  
|[CMFCOutlookBar::SetMode2003](../Topic/CMFCOutlookBar::SetMode2003.md)|Especifica si el comportamiento de los imita de la barra de Outlook que de Outlook 2003 \(vea comentarios\).|  
  
## Comentarios  
 Para obtener un ejemplo de una barra de Outlook, vea [Ejemplo de OutlookDemo: Aplicación MFC OutlookDemo](../../top/visual-cpp-samples.md).  
  
## Implementar la barra de Outlook  
 Para utilizar el control de `CMFCOutlookBar` en la aplicación, siga estos pasos:  
  
1.  Inserte un objeto de `CMFCOutlookBar` en la clase de ventana de marco principal.  
  
    ```  
    class CMainFrame : public CMDIFrameWnd  
     { ...  
         CMFCOutlookBar         m_wndOutlookBar;  
         CMFCOutlookBarPane     m_wndOutlookPane;  
    ... };  
    ```  
  
2.  Al procesar el mensaje de `WM_CREATE` en el marco principal, llame al método de [CMFCOutlookBar::Create](../Topic/CMFCOutlookBar::Create.md) para crear el control de ficha de la barra de Outlook.  
  
    ```  
    m_wndOutlookBar.Create (_T("Shortcuts"), this, CRect (0, 0, 100, 100), ID_VIEW_OUTLOOKBAR, WS_CHILD | WS_VISIBLE | CBRS_LEFT);  
    ```  
  
3.  Obtener un puntero a `CMFCOutlookBarTabCtrl` subyacente mediante [CBaseTabbedPane::GetUnderlyingWindow](../Topic/CBaseTabbedPane::GetUnderlyingWindow.md).  
  
    ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();  
    ```  
  
4.  Cree un objeto de [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) para cada pestaña que contiene los botones.  
  
    ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar, AFX_DEFAULT_TOOLBAR_STYLE, ID_OUTLOOK_PANE_GENERAL, AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);  
    // make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);  
    // add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About", ID_APP_ABOUT);  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open", ID_FILE_OPEN);  
    ```  
  
5.  Llame a [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) para agregar cada nueva pestaña.  Establezca el parámetro de `bDetachable` a `FALSE` para que una página no desmontable.  O, utilice [CMFCOutlookBarTabCtrl::AddControl](../Topic/CMFCOutlookBarTabCtrl::AddControl.md) de agregar páginas desmontables.  
  
    ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);   
    ```  
  
6.  Para agregar `CWnd`\- el control derivado \(por ejemplo, [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)\) como una ficha, crea el control y la llamada [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) para agregarlo a la barra de Outlook.  
  
> [!NOTE]
>  Debe utilizar los id. únicos de control para cada objeto de [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) y para cada `CWnd`\- objeto derivado.  
  
 Para agregar o eliminar dinámicamente las nuevas páginas en tiempo de ejecución, el uso [CMFCOutlookBar::CreateCustomPage](../Topic/CMFCOutlookBar::CreateCustomPage.md) y [CMFCOutlookBar::RemoveCustomPage](../Topic/CMFCOutlookBar::RemoveCustomPage.md).  
  
## Modo de Outlook 2003  
 En el modo de Outlook 2003, los botones de la ficha se colocan en la parte inferior del panel de barra de Outlook.  Cuando no hay suficiente espacio para mostrar botones, se muestran como iconos en una barra de herramientas\- como área a lo largo de la parte inferior del panel.  
  
 Uso [CMFCOutlookBar::SetMode2003](../Topic/CMFCOutlookBar::SetMode2003.md) de habilitar el modo de Outlook 2003.  Utilice [CMFCOutlookBarTabCtrl::SetToolbarImageList](../Topic/CMFCOutlookBarTabCtrl::SetToolbarImageList.md) para establecer el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook.  Los iconos del mapa de bits se deben ordenar por índice de tabulación.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## Requisitos  
 **Encabezado:** afxoutlookbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane \(Clase\)](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md)