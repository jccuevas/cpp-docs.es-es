---
title: "COleControlSite Class | Microsoft Docs"
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
  - "COleControlSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControlSite class"
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
caps.latest.revision: 24
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControlSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona compatibilidad con interfaces de control de cliente personalizadas.  
  
## Sintaxis  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::COleControlSite](../Topic/COleControlSite::COleControlSite.md)|Crea un objeto `COleControlSite`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::BindDefaultProperty](../Topic/COleControlSite::BindDefaultProperty.md)|Enlaza la propiedad predeterminada del control hospedado en un origen de datos.|  
|[COleControlSite::BindProperty](../Topic/COleControlSite::BindProperty.md)|Enlaza una propiedad del control hospedado en un origen de datos.|  
|[COleControlSite::CreateControl](../Topic/COleControlSite::CreateControl.md)|crea un control ActiveX hospedado.|  
|[COleControlSite::DestroyControl](../Topic/COleControlSite::DestroyControl.md)|Destruye el control hospedado.|  
|[COleControlSite::DoVerb](../Topic/COleControlSite::DoVerb.md)|Ejecuta un verbo específico del control hospedado.|  
|[COleControlSite::EnableDSC](../Topic/COleControlSite::EnableDSC.md)|Compra de componentes de los datos de los permisos para un sitio del control.|  
|[COleControlSite::EnableWindow](../Topic/COleControlSite::EnableWindow.md)|Habilita el sitio del control.|  
|[COleControlSite::FreezeEvents](../Topic/COleControlSite::FreezeEvents.md)|Especifica si el sitio del control está aceptando eventos.|  
|[COleControlSite::GetDefBtnCode](../Topic/COleControlSite::GetDefBtnCode.md)|Recupera el código del botón predeterminado del control hospedado.|  
|[COleControlSite::GetDlgCtrlID](../Topic/COleControlSite::GetDlgCtrlID.md)|Recupera el identificador del control.|  
|[COleControlSite::GetEventIID](../Topic/COleControlSite::GetEventIID.md)|Recupera el id. de una interfaz de eventos para un control de hospedado.|  
|[COleControlSite::GetExStyle](../Topic/COleControlSite::GetExStyle.md)|Recupera los estilos extendidos de sitio del control.|  
|[COleControlSite::GetProperty](../Topic/COleControlSite::GetProperty.md)|Recupera una propiedad específica del control hospedado.|  
|[COleControlSite::GetStyle](../Topic/COleControlSite::GetStyle.md)|Recupera los estilos del sitio del control.|  
|[COleControlSite::GetWindowText](../Topic/COleControlSite::GetWindowText.md)|Recupera el texto del control hospedado.|  
|[COleControlSite::InvokeHelper](../Topic/COleControlSite::InvokeHelper.md)|Invoca un método específico del control hospedado.|  
|[COleControlSite::InvokeHelperV](../Topic/COleControlSite::InvokeHelperV.md)|Invoca un método específico del control hospedado con una lista variable de argumentos.|  
|[COleControlSite::IsDefaultButton](../Topic/COleControlSite::IsDefaultButton.md)|Determina si el control es un botón predeterminado en la ventana.|  
|[COleControlSite::IsWindowEnabled](../Topic/COleControlSite::IsWindowEnabled.md)|Comprueba el estado de visibilidad del sitio del control.|  
|[COleControlSite::ModifyStyle](../Topic/COleControlSite::ModifyStyle.md)|Modifica los estilos extendidos actuales del sitio del control.|  
|[COleControlSite::ModifyStyleEx](../Topic/COleControlSite::ModifyStyleEx.md)|Modifica los estilos actuales del sitio del control.|  
|[COleControlSite::MoveWindow](../Topic/COleControlSite::MoveWindow.md)|Cambia la posición del sitio del control.|  
|[COleControlSite::QuickActivate](../Topic/COleControlSite::QuickActivate.md)|Quick provoca el control hospedado.|  
|[COleControlSite::SafeSetProperty](../Topic/COleControlSite::SafeSetProperty.md)|Establece una propiedad o un método de control sin la posibilidad de producir una excepción.|  
|[COleControlSite::SetDefaultButton](../Topic/COleControlSite::SetDefaultButton.md)|Establece el botón predeterminado en la ventana.|  
|[COleControlSite::SetDlgCtrlID](../Topic/COleControlSite::SetDlgCtrlID.md)|Recupera el identificador del control.|  
|[COleControlSite::SetFocus](../Topic/COleControlSite::SetFocus.md)|Establece el foco al sitio del control.|  
|[COleControlSite::SetProperty](../Topic/COleControlSite::SetProperty.md)|Establece una propiedad específica del control hospedado.|  
|[COleControlSite::SetPropertyV](../Topic/COleControlSite::SetPropertyV.md)|Establece una propiedad específica del control hospedado con una lista variable de argumentos.|  
|[COleControlSite::SetWindowPos](../Topic/COleControlSite::SetWindowPos.md)|Establece la posición del sitio del control.|  
|[COleControlSite::SetWindowText](../Topic/COleControlSite::SetWindowText.md)|Establece el texto del control hospedado.|  
|[COleControlSite::ShowWindow](../Topic/COleControlSite::ShowWindow.md)|Muestra u oculta el sitio del control.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](../Topic/COleControlSite::GetControlInfo.md)|Información y aceleradoras de teclado de recupera del control hospedado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::m\_bIsWindowless](../Topic/COleControlSite::m_bIsWindowless.md)|Determina si el control hospedado es un control sin ventana.|  
|[COleControlSite::m\_ctlInfo](../Topic/COleControlSite::m_ctlInfo.md)|Contiene información sobre el teclado que administra para el control.|  
|[COleControlSite::m\_dwEventSink](../Topic/COleControlSite::m_dwEventSink.md)|La cookie del punto de conexión del control.|  
|[COleControlSite::m\_dwMiscStatus](../Topic/COleControlSite::m_dwMiscStatus.md)|Los estados diferentes para el control hospedado.|  
|[COleControlSite::m\_dwPropNotifySink](../Topic/COleControlSite::m_dwPropNotifySink.md)|La cookie de `IPropertyNotifySink` del control.|  
|[COleControlSite::m\_dwStyle](../Topic/COleControlSite::m_dwStyle.md)|Los estilos del control hospedado.|  
|[COleControlSite::m\_hWnd](../Topic/COleControlSite::m_hWnd.md)|El identificador del sitio del control.|  
|[COleControlSite::m\_iidEvents](../Topic/COleControlSite::m_iidEvents.md)|El id. de la interfaz de eventos para el control hospedado.|  
|[COleControlSite::m\_nID](../Topic/COleControlSite::m_nID.md)|El id. del control hospedado.|  
|[COleControlSite::m\_pActiveObject](../Topic/COleControlSite::m_pActiveObject.md)|Un puntero al objeto de `IOleInPlaceActiveObject` del control hospedado.|  
|[COleControlSite::m\_pCtrlCont](../Topic/COleControlSite::m_pCtrlCont.md)|El contenedor del control hospedado.|  
|[COleControlSite::m\_pInPlaceObject](../Topic/COleControlSite::m_pInPlaceObject.md)|Un puntero al objeto de `IOleInPlaceObject` del control hospedado.|  
|[COleControlSite::m\_pObject](../Topic/COleControlSite::m_pObject.md)|Un puntero a la interfaz de `IOleObjectInterface` del control.|  
|[COleControlSite::m\_pWindowlessObject](../Topic/COleControlSite::m_pWindowlessObject.md)|Un puntero a la interfaz de `IOleInPlaceObjectWindowless` del control.|  
|[COleControlSite::m\_pWndCtrl](../Topic/COleControlSite::m_pWndCtrl.md)|Un puntero al objeto de la ventana del control hospedado.|  
|[COleControlSite::m\_rect](../Topic/COleControlSite::m_rect.md)|Las dimensiones del sitio del control.|  
  
## Comentarios  
 Esta compatibilidad está multimedia primarios por los que un control ActiveX incrustado obtiene información sobre la ubicación y la extensión del sitio de la pantalla, del moniker, su interfaz de usuario, sus propiedades de ambiente, y otros recursos proporcionados por su contenedor.  `COleControlSite` completamente implementado [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502), [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706), [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), **IBoundObjectSite**, **INotifyDBEvents**, interfaces de [IRowSetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) .  Además, la interfaz IDispatch \(proporcionar compatibilidad para las propiedades y los receptores de eventos ambiente\) también se implementa.  
  
 Para crear un sitio de controles ActiveX utilizando `COleControlSite`, derive una clase de `COleControlSite`.  En el `CWnd`\- clase derivada para la invalidación del contenedor \(por ejemplo, el cuadro de diálogo\) la función de **CWnd::CreateControlSite** .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## Requisitos  
 **encabezado:** afxocc.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleControlContainer Class](../../mfc/reference/colecontrolcontainer-class.md)