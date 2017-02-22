---
title: "CMFCDropDownToolbarButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDropDownToolbarButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownToolbarButton class"
  - "OnCancelMode method"
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCDropDownToolbarButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un tipo de botón de la barra de herramientas que se comporta como un botón normal cuando se haga clic en.  Sin embargo, abra una barra de herramientas desplegable \([CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) si el usuario aprieta y mantiene el botón de la barra de herramientas.  
  
## Sintaxis  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../Topic/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton.md)|Crea un objeto `CMFCDropDownToolbarButton`.|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CopyFrom](../Topic/CMFCDropDownToolbarButton::CopyFrom.md)|Copia las propiedades de otro botón de la barra de herramientas para el botón actual.  \(Reemplaza [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md).\)|  
|`CMFCDropDownToolbarButton::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCDropDownToolbarButton::DropDownToolbar](../Topic/CMFCDropDownToolbarButton::DropDownToolbar.md)|Abra una barra de herramientas desplegable.|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](../Topic/CMFCDropDownToolbarButton::ExportToMenuButton.md)|Copia el texto del botón de la barra de herramientas a un menú.  \(Reemplaza [CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md).\)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](../Topic/CMFCDropDownToolbarButton::GetDropDownToolBar.md)|Recupera la barra de herramientas desplegable que está asociado al botón.|  
|`CMFCDropDownToolbarButton::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCDropDownToolbarButton::IsDropDown](../Topic/CMFCDropDownToolbarButton::IsDropDown.md)|Determina si la barra de herramientas desplegable está abierto.|  
|[CMFCDropDownToolbarButton::IsExtraSize](../Topic/CMFCDropDownToolbarButton::IsExtraSize.md)|Determina si el botón se puede mostrar con un borde extendido.  \(Reemplaza [CMFCToolBarButton::IsExtraSize](../Topic/CMFCToolBarButton::IsExtraSize.md).\)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](../Topic/CMFCDropDownToolbarButton::OnCalculateSize.md)|Llamado por el marco para calcular el tamaño del botón para el contexto y el estado de vinculación especificados del dispositivo.  \(Reemplaza [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md).\)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|Llamado por el marco para procesar el mensaje de [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) .  \(Reemplaza `CMCToolBarButton::OnCancelMode`.\)|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](../Topic/CMFCDropDownToolbarButton::OnChangeParentWnd.md)|Llamado por el marco cuando el botón se inserta en una nueva barra de herramientas.  \(Reemplaza [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md).\)|  
|[CMFCDropDownToolbarButton::OnClick](../Topic/CMFCDropDownToolbarButton::OnClick.md)|Llamado por el marco cuando el usuario hace clic en el botón del mouse.  \(Reemplaza [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md).\)|  
|[CMFCDropDownToolbarButton::OnClickUp](../Topic/CMFCDropDownToolbarButton::OnClickUp.md)|Llamado por el marco cuando el usuario suelta el botón del mouse.  \(Reemplaza [CMFCToolBarButton::OnClickUp](../Topic/CMFCToolBarButton::OnClickUp.md).\)|  
|[CMFCDropDownToolbarButton::OnContextHelp](../Topic/CMFCDropDownToolbarButton::OnContextHelp.md)|Llamado por el marco cuando la barra de herramientas principal controla un mensaje de `WM_HELPHITTEST` .  \(Reemplaza [CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md).\)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](../Topic/CMFCDropDownToolbarButton::OnCustomizeMenu.md)|Modifica el menú proporcionado cuando la aplicación muestra un menú contextual en la barra de herramientas principal.  \(Reemplaza [CMFCToolBarButton::OnCustomizeMenu](../Topic/CMFCToolBarButton::OnCustomizeMenu.md).\)|  
|[CMFCDropDownToolbarButton::OnDraw](../Topic/CMFCDropDownToolbarButton::OnDraw.md)|Llamado por el marco para dibujar el botón mediante los estilos y las opciones especificados.  \(Reemplaza [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md).\)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](../Topic/CMFCDropDownToolbarButton::OnDrawOnCustomizeList.md)|Llamado por el marco para dibujar el botón del panel de Commandos del cuadro de diálogo de **Personalizar** .  \(Reemplaza [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md).\)|  
|[CMFCDropDownToolbarButton::Serialize](../Topic/CMFCDropDownToolbarButton::Serialize.md)|Lee este objeto de un archivo o de escribe en un archivo.  \(Reemplaza [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md).\)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](../Topic/CMFCDropDownToolbarButton::SetDefaultCommand.md)|Establece el comando predeterminado que el marco de trabajo usa cuando un usuario hace clic en el botón.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m\_uiShowBarDelay](../Topic/CMFCDropDownToolbarButton::m_uiShowBarDelay.md)|Especifica el intervalo de tiempo que un usuario debe adjuntar el botón del mouse hacia abajo antes de que aparezca la barra de herramientas desplegable.|  
  
## Comentarios  
 `CMFCDropDownToolBarButton` diferencia de un botón normal en que tiene una flecha pequeña situada en la esquina inferior derecha del botón.  Después de que el usuario selecciona un botón de la barra de herramientas desplegable, el marco muestra el icono en el botón de la barra de herramientas de nivel superior \(el botón con la flecha pequeña situada en la esquina inferior derecha\).  
  
 Para obtener información sobre cómo implementar una barra de herramientas desplegable, vea [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md).  
  
 El objeto de `CMFCDropDownToolBarButton` se puede exportar a un objeto de [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) y mostrar como botón de menú con un menú emergente.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxdropdowntoolbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)