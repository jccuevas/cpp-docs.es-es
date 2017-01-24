---
title: "CMFCMenuBar Class | Microsoft Docs"
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
  - "CMFCMenuBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMenuBar class"
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
caps.latest.revision: 36
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCMenuBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una barra de menús que implementa el acoplamiento.  
  
## Sintaxis  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCMenuBar::AdjustLocations](../Topic/CMFCMenuBar::AdjustLocations.md)|\(Reemplaza `CMFCToolBar::AdjustLocations`.\)|  
|[CMFCMenuBar::AllowChangeTextLabels](../Topic/CMFCMenuBar::AllowChangeTextLabels.md)|Especifica si las etiquetas de texto se pueden mostrar en imágenes de los botones de la barra de herramientas.  \(Reemplaza [CMFCToolBar::AllowChangeTextLabels](../Topic/CMFCToolBar::AllowChangeTextLabels.md).\)|  
|[CMFCMenuBar::AllowShowOnPaneMenu](../Topic/CMFCMenuBar::AllowShowOnPaneMenu.md)|\(Reemplaza `CPane::AllowShowOnPaneMenu`.\)|  
|[CMFCMenuBar::CalcFixedLayout](../Topic/CMFCMenuBar::CalcFixedLayout.md)|calcula el tamaño horizontal de la barra de herramientas.  \(Reemplaza [CMFCToolBar::CalcFixedLayout](../Topic/CMFCToolBar::CalcFixedLayout.md).\)|  
|[CMFCMenuBar::CalcLayout](../Topic/CMFCMenuBar::CalcLayout.md)|\(Reemplaza `CMFCToolBar::CalcLayout`.\)|  
|[CMFCMenuBar::CalcMaxButtonHeight](../Topic/CMFCMenuBar::CalcMaxButtonHeight.md)|calcula el alto máximo de botones en la barra de herramientas.  \(Reemplaza [CMFCToolBar::CalcMaxButtonHeight](../Topic/CMFCToolBar::CalcMaxButtonHeight.md).\)|  
|[CMFCMenuBar::CanBeClosed](../Topic/CMFCMenuBar::CanBeClosed.md)|especifica si un usuario puede cerrar la barra de herramientas.  \(Reemplaza [CMFCToolBar::CanBeClosed](../Topic/CMFCToolBar::CanBeClosed.md).\)|  
|[CMFCMenuBar::CanBeRestored](../Topic/CMFCMenuBar::CanBeRestored.md)|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización.  \(Reemplaza [CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md).\)|  
|[CMFCMenuBar::Create](../Topic/CMFCMenuBar::Create.md)|Crea un control de menú y lo asocia a un objeto de `CMFCMenuBar` .|  
|[CMFCMenuBar::CreateEx](../Topic/CMFCMenuBar::CreateEx.md)|Crea un objeto de `CMFCMenuBar` con opciones adicionales de estilo.|  
|[CMFCMenuBar::CreateFromMenu](../Topic/CMFCMenuBar::CreateFromMenu.md)|Inicializa un objeto de `CMFCMenuBar` .  Acepta un parámetro de `HMENU` que actúa como plantilla para `CMFCMenuBar`rellenado.|  
|[CMFCMenuBar::EnableHelpCombobox](../Topic/CMFCMenuBar::EnableHelpCombobox.md)|Habilita un cuadro combinado de **Ayuda** que se encuentra a la derecha de la barra de menús.|  
|[CMFCMenuBar::EnableMenuShadows](../Topic/CMFCMenuBar::EnableMenuShadows.md)|Especifica si mostrar las sombras para los menús emergentes.|  
|[CMFCMenuBar::GetAvailableExpandSize](../Topic/CMFCMenuBar::GetAvailableExpandSize.md)|\(Reemplaza [CPane::GetAvailableExpandSize](../Topic/CPane::GetAvailableExpandSize.md).\)|  
|[CMFCMenuBar::GetColumnWidth](../Topic/CMFCMenuBar::GetColumnWidth.md)|devuelve el ancho de los botones de la barra de herramientas.  \(Reemplaza [CMFCToolBar::GetColumnWidth](../Topic/CMFCToolBar::GetColumnWidth.md).\)|  
|[CMFCMenuBar::GetDefaultMenu](../Topic/CMFCMenuBar::GetDefaultMenu.md)|Devuelve un identificador al menú original en el archivo de recursos.|  
|[CMFCMenuBar::GetDefaultMenuResId](../Topic/CMFCMenuBar::GetDefaultMenuResId.md)|Devuelve el identificador de recurso del menú original en el archivo de recursos.|  
|[CMFCMenuBar::GetFloatPopupDirection](../Topic/CMFCMenuBar::GetFloatPopupDirection.md)||  
|[CMFCMenuBar::GetForceDownArrows](../Topic/CMFCMenuBar::GetForceDownArrows.md)||  
|[CMFCMenuBar::GetHelpCombobox](../Topic/CMFCMenuBar::GetHelpCombobox.md)|Devuelve un puntero al cuadro combinado de **Ayuda** .|  
|[CMFCMenuBar::GetHMenu](../Topic/CMFCMenuBar::GetHMenu.md)|Devuelve el identificador al menú que se asocia al objeto de `CMFCMenuBar` .|  
|[CMFCMenuBar::GetMenuFont](../Topic/CMFCMenuBar::GetMenuFont.md)|Devuelve la fuente global actual para objetos de menú.|  
|[CMFCMenuBar::GetMenuItem](../Topic/CMFCMenuBar::GetMenuItem.md)|Devuelve el botón de la barra de herramientas asociado con el índice especificado del elemento.|  
|[CMFCMenuBar::GetRowHeight](../Topic/CMFCMenuBar::GetRowHeight.md)|devuelve el alto de botones de la barra de herramientas.  \(Reemplaza [CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md).\)|  
|[CMFCMenuBar::GetSystemButton](../Topic/CMFCMenuBar::GetSystemButton.md)||  
|[CMFCMenuBar::GetSystemButtonsCount](../Topic/CMFCMenuBar::GetSystemButtonsCount.md)||  
|[CMFCMenuBar::GetSystemMenu](../Topic/CMFCMenuBar::GetSystemMenu.md)||  
|[CMFCMenuBar::HighlightDisabledItems](../Topic/CMFCMenuBar::HighlightDisabledItems.md)|Indica si los elementos de menú deshabilitados son resaltado.|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](../Topic/CMFCMenuBar::IsButtonExtraSizeAvailable.md)|Determina si la barra de herramientas puede mostrar botones que tienen bordes extendidos.  \(Reemplaza [CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md).\)|  
|[CMFCMenuBar::IsHighlightDisabledItems](../Topic/CMFCMenuBar::IsHighlightDisabledItems.md)|Indica si los elementos deshabilitados son resaltado.|  
|[CMFCMenuBar::IsMenuShadows](../Topic/CMFCMenuBar::IsMenuShadows.md)|Indica si las sombras se que se dibujen para los menús emergentes.|  
|[CMFCMenuBar::IsRecentlyUsedMenus](../Topic/CMFCMenuBar::IsRecentlyUsedMenus.md)|Indica si se muestran los comandos de menú utilizados recientemente en la barra de menús.|  
|[CMFCMenuBar::IsShowAllCommands](../Topic/CMFCMenuBar::IsShowAllCommands.md)|Indica si los menús emergentes muestra todos los comandos.|  
|[CMFCMenuBar::IsShowAllCommandsDelay](../Topic/CMFCMenuBar::IsShowAllCommandsDelay.md)|Indica si los menús muestran todos los comandos después de un pequeño retraso.|  
|[CMFCMenuBar::LoadState](../Topic/CMFCMenuBar::LoadState.md)|Carga el estado del objeto de `CMFCMenuBar` del registro.|  
|[CMFCMenuBar::OnChangeHot](../Topic/CMFCMenuBar::OnChangeHot.md)|Llamado por el marco cuando un usuario selecciona un botón de la barra de herramientas.  \(Reemplaza [CMFCToolBar::OnChangeHot](../Topic/CMFCToolBar::OnChangeHot.md).\)|  
|[CMFCMenuBar::OnDefaultMenuLoaded](../Topic/CMFCMenuBar::OnDefaultMenuLoaded.md)|Llamado por el marco cuando una ventana de marco carga el menú predeterminado del archivo de recursos.|  
|[CMFCMenuBar::OnSendCommand](../Topic/CMFCMenuBar::OnSendCommand.md)|\(Reemplaza `CMFCToolBar::OnSendCommand`.\)|  
|[CMFCMenuBar::OnSetDefaultButtonText](../Topic/CMFCMenuBar::OnSetDefaultButtonText.md)|Llamado por el marco cuando un menú está en modo de personalización y el usuario cambia el texto de un elemento de menú.|  
|[CMFCMenuBar::OnToolHitTest](../Topic/CMFCMenuBar::OnToolHitTest.md)|\(Reemplaza `CMFCToolBar::OnToolHitTest`.\)|  
|[CMFCMenuBar::PreTranslateMessage](../Topic/CMFCMenuBar::PreTranslateMessage.md)|\(Reemplaza `CMFCToolBar::PreTranslateMessage`.\)|  
|[CMFCMenuBar::RestoreOriginalstate](../Topic/CMFCMenuBar::RestoreOriginalstate.md)|Llamado por el marco cuando un menú está en modo de personalización y el usuario selecciona **Restablecer** para una barra de menús.|  
|[CMFCMenuBar::SaveState](../Topic/CMFCMenuBar::SaveState.md)|Guarda el estado del objeto de `CMFCMenuBar` al registro.|  
|[CMFCMenuBar::SetDefaultMenuResId](../Topic/CMFCMenuBar::SetDefaultMenuResId.md)|establece el menú original en el archivo de recursos.|  
|[CMFCMenuBar::SetForceDownArrows](../Topic/CMFCMenuBar::SetForceDownArrows.md)||  
|[CMFCMenuBar::SetMaximizeMode](../Topic/CMFCMenuBar::SetMaximizeMode.md)|Llamado por el marco cuando una ventana MDI secundaria cambia al modo de presentación.  Si la ventana MDI secundaria se maximiza recientemente o se maximiza ya no, este método actualiza la barra de menús.|  
|[CMFCMenuBar::SetMenuButtonRTC](../Topic/CMFCMenuBar::SetMenuButtonRTC.md)|Establece la información de la clase en tiempo de ejecución que se genera cuando el usuario crea dinámicamente los botones de menú.|  
|[CMFCMenuBar::SetMenuFont](../Topic/CMFCMenuBar::SetMenuFont.md)|Establece la fuente de todos los menús en la aplicación.|  
|[CMFCMenuBar::SetRecentlyUsedMenus](../Topic/CMFCMenuBar::SetRecentlyUsedMenus.md)|Especifica si una barra de menús muestra comandos de menú utilizados recientemente.|  
|[CMFCMenuBar::SetShowAllCommands](../Topic/CMFCMenuBar::SetShowAllCommands.md)|especifica si la barra de menús muestra todos los comandos.|  
  
## Comentarios  
 La clase de `CMFCMenuBar` es una barra de menús que implementa funcionalidad de acoplamiento.  Se parece a una barra de herramientas, aunque no pueda cerrarse \- se muestra siempre.  
  
 `CMFCMenuBar` admite la opción de mostrar objetos utilizados recientemente del elemento de menú.  Si se habilita esta opción, `CMFCMenuBar` muestra solamente un subconjunto de los comandos disponibles en la primera vista.  Después de esto, los comandos utilizados recientemente así como el subconjunto original de comandos.  Además, el usuario puede expandir siempre el menú para ver todos los comandos disponibles.  Así, se configuran para cada comando disponible en mostrar continuamente, o para mostrar solo si ha sido seleccionados recientemente.  
  
 Para utilizar un objeto de `CMFCMenuBar` , incrustarlo en el objeto de marco de ventana principal.  Al procesar el mensaje de `WM_CREATE` , la llamada `CMFCMenuBar::Create` o `CMFCMenuBar::CreateEx`.  Independientemente de lo crea la función que utilice, pase un puntero a la ventana de marco principal.  A continuación acoplamiento de permiso llamando a [CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md).  Acople este menú llamando a [CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCMenuBar` .  El ejemplo muestra cómo establecer el estilo del panel, habilita el botón de personalizar, habilita un cuadro de Ayuda, habilita las sombras para los menús emergentes, y actualiza la barra de menús.  Este fragmento de código es parte de [Ejemplo de demostración de IE](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/CPP/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/CPP/cmfcmenubar-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)  
  
## Requisitos  
 **encabezado:** afxmenubar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)