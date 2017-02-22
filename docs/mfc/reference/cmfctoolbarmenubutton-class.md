---
title: "CMFCToolBarMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarMenuButton class"
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCToolBarMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

un botón de la barra de herramientas que contiene un menú emergente.  
  
## Sintaxis  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](../Topic/CMFCToolBarMenuButton::CMFCToolBarMenuButton.md)|Crea un objeto `CMFCToolBarMenuButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CompareWith](../Topic/CMFCToolBarMenuButton::CompareWith.md)|compara esta instancia con el objeto proporcionado de `CMFCToolBarButton` .  \(Reemplaza [CMFCToolBarButton::CompareWith](../Topic/CMFCToolBarButton::CompareWith.md).\)|  
|[CMFCToolBarMenuButton::CopyFrom](../Topic/CMFCToolBarMenuButton::CopyFrom.md)|Copia las propiedades de otro botón de la barra de herramientas para el botón actual.  \(Reemplaza [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md).\)|  
|[CMFCToolBarMenuButton::CreateFromMenu](../Topic/CMFCToolBarMenuButton::CreateFromMenu.md)|Inicializa el menú de barras de herramientas de un identificador de menú de Windows.|  
|[CMFCToolBarMenuButton::CreateMenu](../Topic/CMFCToolBarMenuButton::CreateMenu.md)|Crear un menú de Windows que consta de los comandos del menú de barras de herramientas.  Devuelve un identificador al menú de Windows.|  
|[CMFCToolBarMenuButton::CreatePopupMenu](../Topic/CMFCToolBarMenuButton::CreatePopupMenu.md)|Crea un objeto del elemento emergente \([CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)\) para mostrar el menú de barras de herramientas.|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](../Topic/CMFCToolBarMenuButton::EnableQuickCustomize.md)||  
|[CMFCToolBarMenuButton::GetCommands](../Topic/CMFCToolBarMenuButton::GetCommands.md)|Proporciona acceso de solo lectura a la lista de comandos del menú de barras de herramientas.|  
|[CMFCToolBarMenuButton::GetImageRect](../Topic/CMFCToolBarMenuButton::GetImageRect.md)|Recupera el rectángulo delimitador de la imagen del botón.|  
|[CMFCToolBarMenuButton::GetPaletteRows](../Topic/CMFCToolBarMenuButton::GetPaletteRows.md)|Devuelve el número de filas del elemento emergente cuando el menú está en modo de la paleta.|  
|[CMFCToolBarMenuButton::GetPopupMenu](../Topic/CMFCToolBarMenuButton::GetPopupMenu.md)|Devuelve un puntero al objeto del elemento emergente que está asociado al botón.|  
|[CMFCToolBarMenuButton::HasButton](../Topic/CMFCToolBarMenuButton::HasButton.md)||  
|[CMFCToolBarMenuButton::HaveHotBorder](../Topic/CMFCToolBarMenuButton::HaveHotBorder.md)|Determina si un borde del botón de cuando un usuario selecciona el botón.  \(Reemplaza [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md).\)|  
|[CMFCToolBarMenuButton::IsBorder](../Topic/CMFCToolBarMenuButton::IsBorder.md)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](../Topic/CMFCToolBarMenuButton::IsClickedOnMenu.md)||  
|[CMFCToolBarMenuButton::IsDroppedDown](../Topic/CMFCToolBarMenuButton::IsDroppedDown.md)|Determina si el elemento emergente se muestra.|  
|[CMFCToolBarMenuButton::IsEmptyMenuAllowed](../Topic/CMFCToolBarMenuButton::IsEmptyMenuAllowed.md)|Llamado por el marco para determinar si un usuario puede abrir un submenú del elemento de menú seleccionado.|  
|[CMFCToolBarMenuButton::IsExclusive](../Topic/CMFCToolBarMenuButton::IsExclusive.md)|Determina si el botón está en modo exclusivo, es decir, si el elemento emergente permanece abierto incluso cuando el usuario mueve el puntero sobre otra barra de herramientas o botón.|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](../Topic/CMFCToolBarMenuButton::IsMenuPaletteMode.md)|Determina si el elemento emergente está en modo de la paleta.|  
|[CMFCToolBarMenuButton::IsQuickMode](../Topic/CMFCToolBarMenuButton::IsQuickMode.md)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](../Topic/CMFCToolBarMenuButton::IsTearOffMenu.md)|Determina si el elemento emergente tiene una barra de rasgón.|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](../Topic/CMFCToolBarMenuButton::OnAfterCreatePopupMenu.md)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](../Topic/CMFCToolBarMenuButton::OnBeforeDrag.md)|Especifica si el botón pueda arrastrar.  \(Reemplaza [CMFCToolBarButton::OnBeforeDrag](../Topic/CMFCToolBarButton::OnBeforeDrag.md).\)|  
|[CMFCToolBarMenuButton::OnCalculateSize](../Topic/CMFCToolBarMenuButton::OnCalculateSize.md)|Llamado por el marco para calcular el tamaño del botón para el contexto y el estado de vinculación especificados del dispositivo.  \(Reemplaza [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md).\)|  
|[CMFCToolBarMenuButton::OnCancelMode](../Topic/CMFCToolBarMenuButton::OnCancelMode.md)|Llamado por el marco para procesar el mensaje de [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) .  \(Reemplaza [CMFCToolBarButton::OnCancelMode](../Topic/CMFCToolBarButton::OnCancelMode.md).\)|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](../Topic/CMFCToolBarMenuButton::OnChangeParentWnd.md)|Llamado por el marco cuando el botón se inserta en una nueva barra de herramientas.  \(Reemplaza [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md).\)|  
|[CMFCToolBarMenuButton::OnClick](../Topic/CMFCToolBarMenuButton::OnClick.md)|Llamado por el marco cuando el usuario hace clic en el botón del mouse.  \(Reemplaza [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md).\)|  
|[CMFCToolBarMenuButton::OnClickMenuItem](../Topic/CMFCToolBarMenuButton::OnClickMenuItem.md)|Llamado por el marco cuando el usuario selecciona un elemento en el menú emergente.|  
|[CMFCToolBarMenuButton::OnContextHelp](../Topic/CMFCToolBarMenuButton::OnContextHelp.md)|Llamado por el marco cuando la barra de herramientas principal controla un mensaje de `WM_HELPHITTEST` .  \(Reemplaza [CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md).\)|  
|[CMFCToolBarMenuButton::OnDraw](../Topic/CMFCToolBarMenuButton::OnDraw.md)|Llamado por el marco para dibujar el botón mediante los estilos y las opciones especificados.  \(Reemplaza [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md).\)|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarMenuButton::OnDrawOnCustomizeList.md)|Llamado por el marco para dibujar el botón del panel de Commandos del cuadro de diálogo de **Personalizar** .  \(Reemplaza [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md).\)|  
|[CMFCToolBarMenuButton::OpenPopupMenu](../Topic/CMFCToolBarMenuButton::OpenPopupMenu.md)|Llamado por el marco cuando el usuario abre el menú emergente.|  
|[CMFCToolBarMenuButton::ResetImageToDefault](../Topic/CMFCToolBarMenuButton::ResetImageToDefault.md)|Establece el valor predeterminado la imagen que está asociado al botón.  \(Reemplaza [CMFCToolBarButton::ResetImageToDefault](../Topic/CMFCToolBarButton::ResetImageToDefault.md).\)|  
|[CMFCToolBarMenuButton::SaveBarState](../Topic/CMFCToolBarMenuButton::SaveBarState.md)|Guarda el estado del botón de la barra de herramientas.  \(Reemplaza [CMFCToolBarButton::SaveBarState](../Topic/CMFCToolBarButton::SaveBarState.md).\)|  
|[CMFCToolBarMenuButton::Serialize](../Topic/CMFCToolBarMenuButton::Serialize.md)|Lee este objeto de un archivo o de escribe en un archivo.  \(Reemplaza [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md).\)|  
|[CMFCToolBarMenuButton::SetACCData](../Topic/CMFCToolBarMenuButton::SetACCData.md)|Rellena el objeto proporcionado de `CAccessibilityData` con datos de accesibilidad del botón de la barra de herramientas.  \(Reemplaza [CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md).\)|  
|[CMFCToolBarMenuButton::SetMenuOnly](../Topic/CMFCToolBarMenuButton::SetMenuOnly.md)|especifica si el botón se puede agregar a una barra de herramientas.|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](../Topic/CMFCToolBarMenuButton::SetMenuPaletteMode.md)|Especifica si el elemento emergente está en modo de la paleta.|  
|[CMFCToolBarMenuButton::SetMessageWnd](../Topic/CMFCToolBarMenuButton::SetMessageWnd.md)||  
|[CMFCToolBarMenuButton::SetRadio](../Topic/CMFCToolBarMenuButton::SetRadio.md)|Fuerza el botón en el menú de barras de herramientas para mostrar un icono que indica que está seleccionado.|  
|[CMFCToolBarMenuButton::SetTearOff](../Topic/CMFCToolBarMenuButton::SetTearOff.md)|Especifica un identificador de la barra de rasgón para el menú emergente.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](../Topic/CMFCToolBarMenuButton::DrawDocumentIcon.md)|Dibuja un icono en el botón de menú.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::m\_bAlwaysCallOwnerDraw](../Topic/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw.md)|Si `TRUE`, el marco de trabajo llama a siempre [CFrameWndEx::OnDrawMenuImage](../Topic/CFrameWndEx::OnDrawMenuImage.md) cuando se dibuja un botón.|  
  
## Comentarios  
 `CMFCToolBarMenuButton` puede aparecer como un menú, un elemento de menú que tenga un submenú, un botón que ejecuta un comando o mostrar un menú, botón o que sólo muestra un menú.  Se determina el comportamiento y la apariencia del botón de menú especificando parámetros como la imagen, texto, el identificador de menú, y el identificador de comando que está asociado al botón en el constructor `CMFCToolbarMenuButton::CMFCToolbarMenuButton`.  
  
 una clase personalizada derivada de la clase de `CMFCToolbarMenuButton` debe utilizar la macro de [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) .  La macro de [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) genera un error cuando se cierra la aplicación.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto de `CMFCToolBarMenuButton` .  El código se muestra cómo especificar que el menú desplegable está en modo de la paleta, y especificar el identificador de la barra de rasgón que se crea cuando el usuario arrastra el botón de menú desactivada de una barra de menús.  Este fragmento de código es parte de [Ejemplo de pista de word](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#10](../../mfc/reference/codesnippet/CPP/cmfctoolbarmenubutton-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbarmenubutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)