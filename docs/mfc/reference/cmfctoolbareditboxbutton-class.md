---
title: "CMFCToolBarEditBoxButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "OnDrawOnCustomizeList"
  - "OnDraw"
  - "CMFCToolBarEditBoxButton::OnDrawOnCustomizeList"
  - "CMFCToolBarEditBoxButton.SetACCData"
  - "CMFCToolBarEditBoxButton::OnDraw"
  - "OnCalculateSize"
  - "SetACCData"
  - "CMFCToolBarEditBoxButton"
  - "CMFCToolBarEditBoxButton::SetACCData"
  - "CMFCToolBarEditBoxButton::Serialize"
  - "CMFCToolBarEditBoxButton.OnDraw"
  - "CMFCToolBarEditBoxButton.OnDrawOnCustomizeList"
  - "CMFCToolBarEditBoxButton::OnCalculateSize"
  - "Serialize"
  - "CMFCToolBarEditBoxButton.Serialize"
  - "CMFCToolBarEditBoxButton.OnCalculateSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarEditBoxButton class"
  - "OnCalculateSize method"
  - "OnDraw method"
  - "OnDrawOnCustomizeList method"
  - "Serialize method"
  - "SetACCData method"
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCToolBarEditBoxButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

un botón de la barra de herramientas que contiene un control de edición \([CEdit Class](../../mfc/reference/cedit-class.md)\).  
  
## Sintaxis  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](../Topic/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton.md)|Crea un objeto `CMFCToolBarEditBoxButton`.|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](../Topic/CMFCToolBarEditBoxButton::CanBeStretched.md)|Especifica si un usuario puede ajustar el botón durante la personalización.  \(Reemplaza [CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md).\)|  
|[CMFCToolBarEditBoxButton::CopyFrom](../Topic/CMFCToolBarEditBoxButton::CopyFrom.md)|Copia las propiedades de otro botón de la barra de herramientas para el botón actual.  \(Reemplaza [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md).\)|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](../Topic/CMFCToolBarEditBoxButton::CreateEdit.md)|Crea un nuevo control de edición del botón.|  
|`CMFCToolBarEditBoxButton::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCToolBarEditBoxButton::GetByCmd](../Topic/CMFCToolBarEditBoxButton::GetByCmd.md)|Recupera el primer objeto de `CMFCToolBarEditBoxButton` en la aplicación que tiene el identificador especificado de comando|  
|[CMFCToolBarEditBoxButton::GetContentsAll](../Topic/CMFCToolBarEditBoxButton::GetContentsAll.md)|Recupera el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador especificado de comando|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](../Topic/CMFCToolBarEditBoxButton::GetContextMenuID.md)|Recupera el Id. de recurso de menú contextual que está asociado al botón.|  
|[CMFCToolBarEditBoxButton::GetEditBorder](../Topic/CMFCToolBarEditBoxButton::GetEditBorder.md)|Recupera el rectángulo delimitador de la parte de edición del botón del cuadro de edición.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](../Topic/CMFCToolBarEditBoxButton::GetEditBox.md)|Devuelve un puntero al control de edición que se inserta en el botón.|  
|[CMFCToolBarEditBoxButton::GetHwnd](../Topic/CMFCToolBarEditBoxButton::GetHwnd.md)|Recupera el identificador de ventana que está asociado al botón de la barra de herramientas.  \(Reemplaza [CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md).\)|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](../Topic/CMFCToolBarEditBoxButton::GetInvalidateRect.md)|Recupera la región del área cliente del botón que debe volver a dibujar.  \(Reemplaza [CMFCToolBarButton::GetInvalidateRect](../Topic/CMFCToolBarButton::GetInvalidateRect.md).\)|  
|`CMFCToolBarEditBoxButton::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](../Topic/CMFCToolBarEditBoxButton::HaveHotBorder.md)|Determina si un borde del botón de cuando un usuario hace clic en el botón.  \(Reemplaza [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md).\)|  
|[CMFCToolBarEditBoxButton::IsFlatMode](../Topic/CMFCToolBarEditBoxButton::IsFlatMode.md)|Determina si los botones del cuadro de edición tienen un estilo plano.|  
|[CMFCToolBarEditBoxButton::NotifyCommand](../Topic/CMFCToolBarEditBoxButton::NotifyCommand.md)|especifica si el botón procesa el mensaje de [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) .  \(Reemplaza [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md).\)|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](../Topic/CMFCToolBarEditBoxButton::OnAddToCustomizePage.md)|Llamado por el marco cuando el botón se agrega a un cuadro de diálogo de **Personalizar** .  \(Reemplaza [CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md).\)|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Llamado por el marco para calcular el tamaño del botón para el contexto y el estado de vinculación especificados del dispositivo.  \(Reemplaza [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md).\)|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](../Topic/CMFCToolBarEditBoxButton::OnChangeParentWnd.md)|Llamado por el marco cuando el botón se inserta en una nueva barra de herramientas.  \(Reemplaza [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md).\)|  
|[CMFCToolBarEditBoxButton::OnClick](../Topic/CMFCToolBarEditBoxButton::OnClick.md)|Llamado por el marco cuando el usuario hace clic en el botón del mouse.  \(Reemplaza [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md).\)|  
|[CMFCToolBarEditBoxButton::OnCtlColor](../Topic/CMFCToolBarEditBoxButton::OnCtlColor.md)|Llamado por el marco cuando la barra de herramientas principal controla un mensaje de `WM_CTLCOLOR` .  \(Reemplaza [CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md).\)|  
|`CMFCToolBarEditBoxButton::OnDraw`|Llamado por el marco para dibujar el botón mediante los estilos y las opciones especificados.  \(Reemplaza [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md).\)|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Llamado por el marco para dibujar el botón del panel de Commandos del cuadro de diálogo de **Personalizar** .  \(Reemplaza [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md).\)|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](../Topic/CMFCToolBarEditBoxButton::OnGlobalFontsChanged.md)|Llamado por el marco cuando la fuente global ha cambiado.  \(Reemplaza [CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md).\)|  
|[CMFCToolBarEditBoxButton::OnMove](../Topic/CMFCToolBarEditBoxButton::OnMove.md)|Llamado por el marco cuando la barra de herramientas principal se mueve.  \(Reemplaza [CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md).\)|  
|[CMFCToolBarEditBoxButton::OnShow](../Topic/CMFCToolBarEditBoxButton::OnShow.md)|Llamado por el marco cuando el botón se vuelve visible o invisible.  \(Reemplaza [CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md).\)|  
|[CMFCToolBarEditBoxButton::OnSize](../Topic/CMFCToolBarEditBoxButton::OnSize.md)|Llamado por el marco cuando la barra de herramientas principal cambia sus causas o el tamaño de la posición y de este cambio el botón al tamaño del cambio.  \(Reemplaza [CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md).\)|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](../Topic/CMFCToolBarEditBoxButton::OnUpdateToolTip.md)|Llamado por el marco cuando la barra de herramientas principal actualiza el texto de información sobre herramientas.  \(Reemplaza [CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md).\)|  
|`CMFCToolBarEditBoxButton::Serialize`|Lee este objeto de un archivo o de escribe en un archivo.  \(Reemplaza [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md).\)|  
|`CMFCToolBarEditBoxButton::SetACCData`|Rellena el objeto proporcionado de `CAccessibilityData` con datos de accesibilidad del botón de la barra de herramientas.  \(Reemplaza [CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md).\)|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](../Topic/CMFCToolBarEditBoxButton::SetContents.md)|Establece el texto del control de edición del botón.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](../Topic/CMFCToolBarEditBoxButton::SetContentsAll.md)|Encuentra el botón del control de edición que tiene un identificador especificado de comando, y establece el texto del control de edición de ese botón.|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](../Topic/CMFCToolBarEditBoxButton::SetContextMenuID.md)|Especifica el Id. de recurso de menú contextual que está asociado al botón.|  
|[CMFCToolBarEditBoxButton::SetFlatMode](../Topic/CMFCToolBarEditBoxButton::SetFlatMode.md)|Especifique el aspecto plano de estilo de los botones del cuadro de edición de la aplicación.|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](../Topic/CMFCToolBarEditBoxButton::SetStyle.md)|Especifica el estilo de botón.  \(Reemplaza [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md).\)|  
  
## Comentarios  
 Para agregar un botón del cuadro de edición a una barra de herramientas, siga estos pasos:  
  
 1.  Reserva un Id. de recurso ficticio para el botón del recurso primario de la barra de herramientas.  
  
 2.  Construya un objeto `CMFCToolBarEditBoxButton`.  
  
 3.  En el controlador de mensajes que procesa el mensaje de `AFX_WM_RESETTOOLBAR` , reemplace el botón ficticio con el nuevo botón de cuadro combinado con [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md).  
  
 Para obtener más información, vea [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCToolBarEditBoxButton` .  El ejemplo muestra cómo especificar que un usuario puede ajustar el botón durante la personalización, especifica que un borde del botón de cuando un usuario hace clic en el botón, establece el texto del control de cuadro de texto, especifique el aspecto plano de estilo de los botones del cuadro de edición de la aplicación, y especifica el estilo de un control de cuadro de edición de la barra de herramientas.  
  
 [!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/CPP/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbareditboxbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)