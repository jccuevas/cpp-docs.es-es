---
title: "CMFCPopupMenu Class | Microsoft Docs"
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
  - "CMFCPopupMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPopupMenu class"
ms.assetid: 9555dca1-8c9c-44c9-af72-0659ddad128e
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPopupMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad del menú emergente de Windows y ampliarlo agregando características como rasgan menús y la información sobre herramientas.  
  
## Sintaxis  
  
```  
class CMFCPopupMenu : public CMiniFrameWnd  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPopupMenu::CMFCPopupMenu](../Topic/CMFCPopupMenu::CMFCPopupMenu.md)|Crea un objeto `CMFCPopupMenu`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPopupMenu::ActivatePopupMenu](../Topic/CMFCPopupMenu::ActivatePopupMenu.md)||  
|[CMFCPopupMenu::AlwaysShowEmptyToolsEntry](../Topic/CMFCPopupMenu::AlwaysShowEmptyToolsEntry.md)|establece si un menú emergente está habilitado para mostrar las entradas vacías para las herramientas definido por el usuario.|  
|[CMFCPopupMenu::AreAllCommandsShown](../Topic/CMFCPopupMenu::AreAllCommandsShown.md)||  
|[CMFCPopupMenu::CheckArea](../Topic/CMFCPopupMenu::CheckArea.md)|determina la ubicación de un punto en relación con el menú emergente.|  
|[CMFCPopupMenu::CloseMenu](../Topic/CMFCPopupMenu::CloseMenu.md)||  
|[CMFCPopupMenu::Create](../Topic/CMFCPopupMenu::Create.md)|Crea un menú emergente y lo asocia al objeto de `CMFCPopupMenu` .|  
|[CMFCPopupMenu::DefaultMouseClickOnClose](../Topic/CMFCPopupMenu::DefaultMouseClickOnClose.md)||  
|[CMFCPopupMenu::EnableMenuLogo](../Topic/CMFCPopupMenu::EnableMenuLogo.md)|Inicializa el logotipo para un menú emergente.|  
|[CMFCPopupMenu::EnableMenuSound](../Topic/CMFCPopupMenu::EnableMenuSound.md)|Sonido de menú de permisos.|  
|[CMFCPopupMenu::EnableResize](../Topic/CMFCPopupMenu::EnableResize.md)||  
|[CMFCPopupMenu::EnableScrolling](../Topic/CMFCPopupMenu::EnableScrolling.md)||  
|[CMFCPopupMenu::EnableVertResize](../Topic/CMFCPopupMenu::EnableVertResize.md)||  
|[CMFCPopupMenu::FindSubItemByCommand](../Topic/CMFCPopupMenu::FindSubItemByCommand.md)||  
|[CMFCPopupMenu::GetActiveMenu](../Topic/CMFCPopupMenu::GetActiveMenu.md)|Devuelve actualmente el menú activo.|  
|[CMFCPopupMenu::GetAnimationSpeed](../Topic/CMFCPopupMenu::GetAnimationSpeed.md)|Devuelve la velocidad de la animación en menús emergentes.|  
|[CMFCPopupMenu::GetAnimationType](../Topic/CMFCPopupMenu::GetAnimationType.md)|Devuelve el tipo actual de la animación de menú emergente.|  
|[CMFCPopupMenu::GetDropDirection](../Topic/CMFCPopupMenu::GetDropDirection.md)||  
|[CMFCPopupMenu::GetForceMenuFocus](../Topic/CMFCPopupMenu::GetForceMenuFocus.md)|Indica si el foco está devuelto a la barra de menús cuando se muestra un menú emergente.|  
|[CMFCPopupMenu::GetForceShadow](../Topic/CMFCPopupMenu::GetForceShadow.md)||  
|[CMFCPopupMenu::GetHMenu](../Topic/CMFCPopupMenu::GetHMenu.md)|Devuelve un identificador al recurso asociado del menú.|  
|[CMFCPopupMenu::GetMenuBar](../Topic/CMFCPopupMenu::GetMenuBar.md)|Devuelve [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) incrustado dentro del elemento emergente.|  
|[CMFCPopupMenu::GetMenuItem](../Topic/CMFCPopupMenu::GetMenuItem.md)|Devuelve un puntero al elemento en el índice especificado.|  
|[CMFCPopupMenu::GetMenuItemCount](../Topic/CMFCPopupMenu::GetMenuItemCount.md)|Devuelve el número de elementos de un menú emergente.|  
|[CMFCPopupMenu::GetMessageWnd](../Topic/CMFCPopupMenu::GetMessageWnd.md)|Devuelve un puntero a la ventana donde el marco enruta los mensajes del elemento emergente.|  
|[CMFCPopupMenu::GetParentArea](../Topic/CMFCPopupMenu::GetParentArea.md)||  
|[CMFCPopupMenu::GetParentButton](../Topic/CMFCPopupMenu::GetParentButton.md)|Devuelve un puntero al botón de la barra de herramientas principal.|  
|[CMFCPopupMenu::GetParentPopupMenu](../Topic/CMFCPopupMenu::GetParentPopupMenu.md)|Devuelve un puntero al menú emergente primario.|  
|[CMFCPopupMenu::GetParentRibbonElement](../Topic/CMFCPopupMenu::GetParentRibbonElement.md)||  
|[CMFCPopupMenu::GetParentToolBar](../Topic/CMFCPopupMenu::GetParentToolBar.md)|Devuelve un puntero a la barra de herramientas principal.|  
|[CMFCPopupMenu::GetQuickCustomizeType](../Topic/CMFCPopupMenu::GetQuickCustomizeType.md)||  
|[CMFCPopupMenu::GetSelItem](../Topic/CMFCPopupMenu::GetSelItem.md)|Devuelve un puntero al comando de menú seleccionado actualmente.|  
|[CMFCPopupMenu::HasBeenResized](../Topic/CMFCPopupMenu::HasBeenResized.md)||  
|[CMFCPopupMenu::HideRarelyUsedCommands](../Topic/CMFCPopupMenu::HideRarelyUsedCommands.md)|Indica si el elemento emergente puede ocultar comandos raramente utilizados.|  
|[CMFCPopupMenu::InCommand](../Topic/CMFCPopupMenu::InCommand.md)||  
|[CMFCPopupMenu::InsertItem](../Topic/CMFCPopupMenu::InsertItem.md)|Inserta un nuevo elemento del menú emergente en la ubicación especificada.|  
|[CMFCPopupMenu::InsertSeparator](../Topic/CMFCPopupMenu::InsertSeparator.md)|Inserta un separador del menú emergente en la ubicación especificada.|  
|[CMFCPopupMenu::IsAlwaysClose](../Topic/CMFCPopupMenu::IsAlwaysClose.md)||  
|[CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry](../Topic/CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry.md)||  
|[CMFCPopupMenu::IsCustomizePane](../Topic/CMFCPopupMenu::IsCustomizePane.md)|Indica si el elemento emergente funciona como **QuickCustomizePane**.|  
|[CMFCPopupMenu::IsEscClose](../Topic/CMFCPopupMenu::IsEscClose.md)||  
|[CMFCPopupMenu::IsIdle](../Topic/CMFCPopupMenu::IsIdle.md)|Indica si un menú emergente está inactivo.|  
|[CMFCPopupMenu::IsMenuSound](../Topic/CMFCPopupMenu::IsMenuSound.md)||  
|[CMFCPopupMenu::IsQuickCustomize](../Topic/CMFCPopupMenu::IsQuickCustomize.md)|Determina si [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) asociado está en modo de QuickCustomize.|  
|[CMFCPopupMenu::IsResizeble](../Topic/CMFCPopupMenu::IsResizeble.md)||  
|[CMFCPopupMenu::IsRightAlign](../Topic/CMFCPopupMenu::IsRightAlign.md)|Indica si el menú está alineado a la derecha o a la izquierda.|  
|[CMFCPopupMenu::IsScrollable](../Topic/CMFCPopupMenu::IsScrollable.md)||  
|[CMFCPopupMenu::IsSendMenuSelectMsg](../Topic/CMFCPopupMenu::IsSendMenuSelectMsg.md)|Indica si el marco notifica el cuadro primario cuando el usuario selecciona un comando de menú emergente.|  
|[CMFCPopupMenu::IsShown](../Topic/CMFCPopupMenu::IsShown.md)|Indica si el elemento emergente está visible actualmente.|  
|[CMFCPopupMenu::MoveTo](../Topic/CMFCPopupMenu::MoveTo.md)||  
|[CMFCPopupMenu::OnCmdMsg](../Topic/CMFCPopupMenu::OnCmdMsg.md)|\(Reemplaza `CFrameWnd::OnCmdMsg`.\)|  
|[CMFCPopupMenu::PostCommand](../Topic/CMFCPopupMenu::PostCommand.md)||  
|[CMFCPopupMenu::PreTranslateMessage](../Topic/CMFCPopupMenu::PreTranslateMessage.md)|\(Reemplaza `CFrameWnd::PreTranslateMessage`.\)|  
|[CMFCPopupMenu::RecalcLayout](../Topic/CMFCPopupMenu::RecalcLayout.md)|Llamado por el marco cuando las barras de control estándar son con. o desactivado o cuando se cambia el tamaño de la ventana de marco.  \(Reemplaza [CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md).\)|  
|[CMFCPopupMenu::RemoveAllItems](../Topic/CMFCPopupMenu::RemoveAllItems.md)|borra todos los elementos de un menú emergente.|  
|[CMFCPopupMenu::RemoveItem](../Topic/CMFCPopupMenu::RemoveItem.md)|quita el elemento especificado de un menú emergente.|  
|[CMFCPopupMenu::SaveState](../Topic/CMFCPopupMenu::SaveState.md)||  
|[CMFCPopupMenu::SetAnimationSpeed](../Topic/CMFCPopupMenu::SetAnimationSpeed.md)|Establece la velocidad de la animación en menús emergentes.|  
|[CMFCPopupMenu::SetAnimationType](../Topic/CMFCPopupMenu::SetAnimationType.md)|establece la animación escrita para el menú emergente.|  
|[CMFCPopupMenu::SetAutoDestroy](../Topic/CMFCPopupMenu::SetAutoDestroy.md)||  
|[CMFCPopupMenu::SetDefaultItem](../Topic/CMFCPopupMenu::SetDefaultItem.md)|establece el comando predeterminado para el menú emergente.|  
|[CMFCPopupMenu::SetForceMenuFocus](../Topic/CMFCPopupMenu::SetForceMenuFocus.md)|Fuerza el foco de entrada para volver a la barra de menús cuando se muestra un menú emergente.|  
|[CMFCPopupMenu::SetForceShadow](../Topic/CMFCPopupMenu::SetForceShadow.md)|Fuerza el marco para dibujar con el menú cuando los menús emergentes aparecen fuera del marco principal.|  
|[CMFCPopupMenu::SetMaxWidth](../Topic/CMFCPopupMenu::SetMaxWidth.md)|Establezca el ancho máximo del menú emergente.|  
|[CMFCPopupMenu::SetMessageWnd](../Topic/CMFCPopupMenu::SetMessageWnd.md)||  
|[CMFCPopupMenu::SetParentRibbonElement](../Topic/CMFCPopupMenu::SetParentRibbonElement.md)||  
|[CMFCPopupMenu::SetQuickCustomizeType](../Topic/CMFCPopupMenu::SetQuickCustomizeType.md)||  
|[CMFCPopupMenu::SetQuickMode](../Topic/CMFCPopupMenu::SetQuickMode.md)||  
|[CMFCPopupMenu::SetRightAlign](../Topic/CMFCPopupMenu::SetRightAlign.md)|Establece la alineación del menú para los menús emergentes.|  
|[CMFCPopupMenu::SetSendMenuSelectMsg](../Topic/CMFCPopupMenu::SetSendMenuSelectMsg.md)|Establece un marcador que controla si el menú emergente notifica el cuadro primario cuando el usuario selecciona un comando.|  
|[CMFCPopupMenu::ShowAllCommands](../Topic/CMFCPopupMenu::ShowAllCommands.md)|Fuerza el menú emergente para mostrar todos los comandos.|  
|[CMFCPopupMenu::TriggerResize](../Topic/CMFCPopupMenu::TriggerResize.md)||  
|[CMFCPopupMenu::UpdateAllShadows](../Topic/CMFCPopupMenu::UpdateAllShadows.md)|Actualiza las sombras para todos los elementos emergentes abiertos.|  
|[CMFCPopupMenu::UpdateShadow](../Topic/CMFCPopupMenu::UpdateShadow.md)|Actualiza la sombra para el elemento emergente.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPopupMenu::CreateTearOffBar](../Topic/CMFCPopupMenu::CreateTearOffBar.md)||  
|[CMFCPopupMenu::OnChangeHot](../Topic/CMFCPopupMenu::OnChangeHot.md)||  
|[CMFCPopupMenu::OnChooseItem](../Topic/CMFCPopupMenu::OnChooseItem.md)||  
  
### Comentarios  
 normalmente, MFC crea menús emergentes automáticamente.  Si desea crear un objeto de `CMFCPopupMenu` manualmente, asigna uno en la pila y llame a [CMFCPopupMenu::Create](../Topic/CMFCPopupMenu::Create.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto del elemento emergente.  El ejemplo muestra cómo establecer el logotipo y el sonido del elemento emergente, establecer la velocidad de la animación y el tipo, dibuja sombras de menú al menú emergente aparece fuera del marco principal, establezca el ancho máximo, y establece la alineación correcta del menú del menú emergente.  Este fragmento de código es parte de [Ejemplo de las páginas de personalizadas](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#2](../../mfc/reference/codesnippet/CPP/cmfcpopupmenu-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
## Requisitos  
 **encabezado:** afxpopupmenu.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenuBar \(clase\)](../../mfc/reference/cmfcpopupmenubar-class.md)