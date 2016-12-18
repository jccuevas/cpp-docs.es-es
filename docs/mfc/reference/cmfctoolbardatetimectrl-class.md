---
title: "CMFCToolBarDateTimeCtrl Class | Microsoft Docs"
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
  - "OnDrawOnCustomizeList"
  - "CMFCToolBarDateTimeCtrl::OnDraw"
  - "OnDraw"
  - "CMFCToolBarDateTimeCtrl.Serialize"
  - "CMFCToolBarDateTimeCtrl.OnSize"
  - "CMFCToolBarDateTimeCtrl.OnDrawOnCustomizeList"
  - "OnSize"
  - "OnCalculateSize"
  - "CMFCToolBarDateTimeCtrl"
  - "CMFCToolBarDateTimeCtrl::OnCalculateSize"
  - "SetStyle"
  - "CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList"
  - "CMFCToolBarDateTimeCtrl.OnDraw"
  - "CMFCToolBarDateTimeCtrl.SetStyle"
  - "CMFCToolBarDateTimeCtrl::SetStyle"
  - "CMFCToolBarDateTimeCtrl.OnCalculateSize"
  - "CMFCToolBarDateTimeCtrl::Serialize"
  - "CMFCToolBarDateTimeCtrl::OnSize"
  - "Serialize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarDateTimeCtrl class"
  - "OnCalculateSize method"
  - "OnDraw method"
  - "OnDrawOnCustomizeList method"
  - "OnSize method"
  - "Serialize method"
  - "SetStyle method"
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
caps.latest.revision: 30
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarDateTimeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un botón de la barra de herramientas que contiene un control de selector de fecha y hora.  
  
## Sintaxis  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](../Topic/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl.md)|Crea un objeto `CMFCToolBarDateTimeCtrl`.|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](../Topic/CMFCToolBarDateTimeCtrl::CanBeStretched.md)|Especifica si un usuario puede ajustar el botón durante la personalización.  \(Reemplaza [CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md).\)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](../Topic/CMFCToolBarDateTimeCtrl::CopyFrom.md)|Copia las propiedades de otro botón de la barra de herramientas para el botón actual.  \(Reemplaza [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md).\)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Reservado para uso futuro.|  
|[CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)|Copia el texto del botón de la barra de herramientas a un menú.|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](../Topic/CMFCToolBarDateTimeCtrl::GetByCmd.md)|Recupera el primer objeto de `CMFCToolBarDateTimeCtrl` en la aplicación que tiene el identificador especificado de comando|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](../Topic/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl.md)|Devuelve un puntero al control selector de fecha y hora.|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](../Topic/CMFCToolBarDateTimeCtrl::GetHwnd.md)|Recupera el identificador de ventana que está asociado al botón de la barra de herramientas.  \(Reemplaza [CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md).\)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCToolBarDateTimeCtrl::GetTime](../Topic/CMFCToolBarDateTimeCtrl::GetTime.md)|Obtiene el tiempo seleccionado en un control de selector de fecha y hora y lo coloca en una estructura especificada de [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) .|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](../Topic/CMFCToolBarDateTimeCtrl::GetTimeAll.md)|Devuelve el tiempo seleccionado del botón de control selector de tiempo que tiene un identificador especificada de comando|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](../Topic/CMFCToolBarDateTimeCtrl::HaveHotBorder.md)|Determina si un borde del botón de cuando un usuario selecciona el botón.  \(Reemplaza [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md).\)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](../Topic/CMFCToolBarDateTimeCtrl::NotifyCommand.md)|especifica si el botón procesa el mensaje de [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) .  \(Reemplaza [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](../Topic/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage.md)|Llamado por el marco cuando el botón se agrega a un cuadro de diálogo de **Personalizar** .  \(Reemplaza [CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md).\)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Llamado por el marco para calcular el tamaño del botón para el contexto y el estado de vinculación especificados del dispositivo.  \(Reemplaza [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](../Topic/CMFCToolBarDateTimeCtrl::OnChangeParentWnd.md)|Llamado por el marco cuando el botón se inserta en una nueva barra de herramientas.  \(Reemplaza [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnClick](../Topic/CMFCToolBarDateTimeCtrl::OnClick.md)|Llamado por el marco cuando el usuario hace clic en el control.  \(Reemplaza [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](../Topic/CMFCToolBarDateTimeCtrl::OnCtlColor.md)|Llamado por el marco cuando la barra de herramientas principal controla un mensaje de `WM_CTLCOLOR` .  \(Reemplaza [CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md).\)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|Llamado por el marco para dibujar el botón mediante los estilos y las opciones especificados.  \(Reemplaza [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md).\)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Llamado por el marco para dibujar el botón del panel de Commandos del cuadro de diálogo de **Personalizar** .  \(Reemplaza [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](../Topic/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged.md)|Llamado por el marco cuando la fuente global ha cambiado.  \(Reemplaza [CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnMove](../Topic/CMFCToolBarDateTimeCtrl::OnMove.md)|Llamado por el marco cuando la barra de herramientas principal se mueve.  \(Reemplaza [CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnShow](../Topic/CMFCToolBarDateTimeCtrl::OnShow.md)|Llamado por el marco cuando el botón se vuelve visible o invisible.  \(Reemplaza [CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md).\)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|Llamado por el marco cuando la barra de herramientas principal cambia sus causas o el tamaño de la posición y de este cambio el botón al tamaño del cambio.  \(Reemplaza [CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md).\)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](../Topic/CMFCToolBarDateTimeCtrl::OnUpdateToolTip.md)|Llamado por el marco cuando la barra de herramientas principal actualiza el texto de información sobre herramientas.  \(Reemplaza [CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md).\)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|Lee este objeto de un archivo o de escribe en un archivo, \(reemplaza [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md).\)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|Establece el estilo de los botones de la barra de herramientas.  \(Reemplaza [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md).\)|  
|[CMFCToolBarDateTimeCtrl::SetTime](../Topic/CMFCToolBarDateTimeCtrl::SetTime.md)|Establece la hora y la fecha en el control selector de tiempo.|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](../Topic/CMFCToolBarDateTimeCtrl::SetTimeAll.md)|Establece la hora y fecha en todas las instancias del control selector de tiempo que tengan una identificación especificada de comando|  
  
## Comentarios  
 Para obtener un ejemplo de cómo utilizar un control de selector de fecha y hora, vea el proyecto de ejemplo de ToolbarDateTimePicker.  Para obtener información sobre cómo agregar botones de control a las barras de herramientas, vea [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbardatetimectrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)