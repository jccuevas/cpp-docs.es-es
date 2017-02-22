---
title: "CDHtmlDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDHtmlDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDHtmlDialog class"
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDHtmlDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza para crear cuadros de diálogo que utilizan HTML en lugar de recursos de cuadro de diálogo para implementar la interfaz de usuario.  
  
## Sintaxis  
  
```  
class CDHtmlDialog : public CDialog, public CDHtmlEventSink  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDHtmlDialog::CDHtmlDialog](../Topic/CDHtmlDialog::CDHtmlDialog.md)|Construye un objeto CDHtmlDialog.|  
|[CDHtmlDialog::~CDHtmlDialog](../Topic/CDHtmlDialog::~CDHtmlDialog.md)|Destruye un objeto CDHtmlDialog.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDHtmlDialog::CanAccessExternal](../Topic/CDHtmlDialog::CanAccessExternal.md)|Overridable denominado como comprobación de acceso para ver si los objetos de script en la página carga pueden tener acceso al envío externo del sitio del control.  Las comprobaciones para asegurarse de distribución son o seguro para el script o la zona actual permite los objetos que no son seguros para el script.|  
|[CDHtmlDialog::CreateControlSite](../Topic/CDHtmlDialog::CreateControlSite.md)|Overridable utilizada para crear una instancia del sitio del control para hospedar el control WebBrowser en el diálogo.|  
|[CDHtmlDialog::DDX\_DHtml\_AxControl](../Topic/CDHtmlDialog::DDX_DHtml_AxControl.md)|MFC intercambia datos entre una variable miembro y el valor de propiedad de un control ActiveX en una página HTML.|  
|[CDHtmlDialog::DDX\_DHtml\_CheckBox](../Topic/CDHtmlDialog::DDX_DHtml_CheckBox.md)|MFC intercambia datos entre una variable miembro y una casilla en una página HTML.|  
|[CDHtmlDialog::DDX\_DHtml\_ElementText](../Topic/CDHtmlDialog::DDX_DHtml_ElementText.md)|MFC intercambia datos entre una variable miembro y cualquier propiedad del elemento HTML en una página HTML.|  
|[CDHtmlDialog::DDX\_DHtml\_Radio](../Topic/CDHtmlDialog::DDX_DHtml_Radio.md)|MFC intercambia datos entre una variable miembro y un botón de radio en una página HTML.|  
|[CDHtmlDialog::DDX\_DHtml\_SelectIndex](../Topic/CDHtmlDialog::DDX_DHtml_SelectIndex.md)|obtiene o establece el índice de un cuadro de lista en una página HTML.|  
|[CDHtmlDialog::DDX\_DHtml\_SelectString](../Topic/CDHtmlDialog::DDX_DHtml_SelectString.md)|Obtiene o establece el texto para mostrar de una entrada del cuadro de lista \(según el índice actual\) en una página HTML.|  
|[CDHtmlDialog::DDX\_DHtml\_SelectValue](../Topic/CDHtmlDialog::DDX_DHtml_SelectValue.md)|Obtiene o establece el valor de una entrada del cuadro de lista \(según el índice actual\) en una página HTML.|  
|[CDHtmlDialog::DestroyModeless](../Topic/CDHtmlDialog::DestroyModeless.md)|Destruye un cuadro de diálogo no modal.|  
|[CDHtmlDialog::EnableModeless](../Topic/CDHtmlDialog::EnableModeless.md)|Habilita los cuadros de diálogo no modal.|  
|[CDHtmlDialog::FilterDataObject](../Topic/CDHtmlDialog::FilterDataObject.md)|Permite que el diálogo filtrar los objetos de datos del portapapeles creados por el explorador hospedado.|  
|[CDHtmlDialog::GetControlDispatch](../Topic/CDHtmlDialog::GetControlDispatch.md)|Recupera la interfaz de `IDispatch` en un control ActiveX incrustado en el documento HTML.|  
|[CDHtmlDialog::GetControlProperty](../Topic/CDHtmlDialog::GetControlProperty.md)|Recupera la propiedad solicitada de controles ActiveX especificado.|  
|[CDHtmlDialog::GetCurrentUrl](../Topic/CDHtmlDialog::GetCurrentUrl.md)|Recupera el Localizador uniforme \(URL\) de recursos asociados con el documento actual.|  
|[CDHtmlDialog::GetDHtmlDocument](../Topic/CDHtmlDialog::GetDHtmlDocument.md)|recupera la interfaz de IHTMLDocument2 en el documento HTML actualmente cargado.|  
|[CDHtmlDialog::GetDropTarget](../Topic/CDHtmlDialog::GetDropTarget.md)|Llamado por el control contenido WebBrowser cuando se usa como destino para permitir que el diálogo proporcione [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)alternativo.|  
|[CDHtmlDialog::GetElement](../Topic/CDHtmlDialog::GetElement.md)|Obtiene una interfaz en un elemento HTML.|  
|[CDHtmlDialog::GetElementHtml](../Topic/CDHtmlDialog::GetElementHtml.md)|Recupera la propiedad de **innerHTML** de un elemento HTML.|  
|[CDHtmlDialog::GetElementInterface](../Topic/CDHtmlDialog::GetElementInterface.md)|Recupera el puntero solicitado de interfaz de un elemento HTML.|  
|[CDHtmlDialog::GetElementProperty](../Topic/CDHtmlDialog::GetElementProperty.md)|Recupera el valor de la propiedad de un elemento HTML.|  
|[CDHtmlDialog::GetElementText](../Topic/CDHtmlDialog::GetElementText.md)|Recupera la propiedad de **innerText** de un elemento HTML.|  
|[CDHtmlDialog::GetEvent](../Topic/CDHtmlDialog::GetEvent.md)|Obtiene el puntero de **IHTMLEventObj** al objeto de suceso actual.|  
|[CDHtmlDialog::GetExternal](../Topic/CDHtmlDialog::GetExternal.md)|Obtiene la interfaz de `IDispatch` host.|  
|[CDHtmlDialog::GetHostInfo](../Topic/CDHtmlDialog::GetHostInfo.md)|Recupera las funciones de la interfaz de usuario del host.|  
|[CDHtmlDialog::GetOptionKeyPath](../Topic/CDHtmlDialog::GetOptionKeyPath.md)|Recupera la clave del Registro en el que se almacenan las preferencias del usuario.|  
|[CDHtmlDialog::HideUI](../Topic/CDHtmlDialog::HideUI.md)|Oculta la interfaz de usuario del host.|  
|[CDHtmlDialog::IsExternalDispatchSafe](../Topic/CDHtmlDialog::IsExternalDispatchSafe.md)|Indica si la interfaz de `IDispatch` host es segura para el script.|  
|[CDHtmlDialog::LoadFromResource](../Topic/CDHtmlDialog::LoadFromResource.md)|Carga el recurso especificado en el control WebBrowser.|  
|[CDHtmlDialog::Navigate](../Topic/CDHtmlDialog::Navigate.md)|Navega hasta la dirección URL especificada.|  
|[CDHtmlDialog::OnBeforeNavigate](../Topic/CDHtmlDialog::OnBeforeNavigate.md)|Llamado por el marco antes de un evento de navegación se desencadena.|  
|[CDHtmlDialog::OnDocumentComplete](../Topic/CDHtmlDialog::OnDocumentComplete.md)|Llamado por el marco para notificar a una aplicación cuando un documento se ha alcanzado el estado de `READYSTATE_COMPLETE` .|  
|[CDHtmlDialog::OnDocWindowActivate](../Topic/CDHtmlDialog::OnDocWindowActivate.md)|Llamado por el marco cuando se activa o desactiva la ventana de documento.|  
|[CDHtmlDialog::OnFrameWindowActivate](../Topic/CDHtmlDialog::OnFrameWindowActivate.md)|Llamado por el marco cuando se activa o desactiva la ventana de marco.|  
|[CDHtmlDialog::OnInitDialog](../Topic/CDHtmlDialog::OnInitDialog.md)|Denominado en respuesta a **WM\_INITDIALOG** el mensaje.|  
|[CDHtmlDialog::OnNavigateComplete](../Topic/CDHtmlDialog::OnNavigateComplete.md)|Llamado por el marco después de un evento de navegación se completa.|  
|[CDHtmlDialog::ResizeBorder](../Topic/CDHtmlDialog::ResizeBorder.md)|Alerta el objeto que necesita cambiar el tamaño del espacio del borde.|  
|[CDHtmlDialog::SetControlProperty](../Topic/CDHtmlDialog::SetControlProperty.md)|Establece la propiedad de un control ActiveX en un nuevo valor.|  
|[CDHtmlDialog::SetElementHtml](../Topic/CDHtmlDialog::SetElementHtml.md)|establece la propiedad de **innerHTML** de un elemento HTML.|  
|[CDHtmlDialog::SetElementProperty](../Topic/CDHtmlDialog::SetElementProperty.md)|establece una propiedad de un elemento HTML.|  
|[CDHtmlDialog::SetElementText](../Topic/CDHtmlDialog::SetElementText.md)|Establece la propiedad de **innerText** de un elemento HTML.|  
|[CDHtmlDialog::SetExternalDispatch](../Topic/CDHtmlDialog::SetExternalDispatch.md)|Establece la interfaz de `IDispatch` host.|  
|[CDHtmlDialog::SetHostFlags](../Topic/CDHtmlDialog::SetHostFlags.md)|Establece los marcadores de la interfaz de usuario del host.|  
|[CDHtmlDialog::ShowContextMenu](../Topic/CDHtmlDialog::ShowContextMenu.md)|Llamado cuando un menú contextual está a punto de mostrarse.|  
|[CDHtmlDialog::ShowUI](../Topic/CDHtmlDialog::ShowUI.md)|Muestra la interfaz de usuario del host.|  
|[CDHtmlDialog::TranslateAccelerator](../Topic/CDHtmlDialog::TranslateAccelerator.md)|Denominado para procesar mensajes de la tecla de aceleración del menú.|  
|[CDHtmlDialog::TranslateUrl](../Topic/CDHtmlDialog::TranslateUrl.md)|Denominado para modificar la dirección URL que se va a cargar.|  
|[CDHtmlDialog::UpdateUI](../Topic/CDHtmlDialog::UpdateUI.md)|Denominado para notificar al host que el estado de comando ha cambiado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDHtmlDialog::m\_bUseHtmlTitle](../Topic/CDHtmlDialog::m_bUseHtmlTitle.md)|Indica si utilizar el título del documento HTML como el título del diálogo.|  
|[CDHtmlDialog::m\_nHtmlResID](../Topic/CDHtmlDialog::m_nHtmlResID.md)|Id. de recurso de recursos HTML que se va a mostrar.|  
|[CDHtmlDialog::m\_pBrowserApp](../Topic/CDHtmlDialog::m_pBrowserApp.md)|Un puntero a una aplicación de explorador web.|  
|[CDHtmlDialog::m\_spHtmlDoc](../Topic/CDHtmlDialog::m_spHtmlDoc.md)|un puntero a un documento HTML.|  
|[CDHtmlDialog::m\_strCurrentUrl](../Topic/CDHtmlDialog::m_strCurrentUrl.md)|La dirección URL actual.|  
|[CDHtmlDialog::m\_szHtmlResID](../Topic/CDHtmlDialog::m_szHtmlResID.md)|Versión de cadena del identificador de recursos HTML|  
  
## Comentarios  
 **CDHtmlDialog** puede cargar HTML se muestre desde un recurso HTML o una dirección URL.  
  
 `CDHtmlDialog` puede hacer de intercambio de datos con controles HTML y controlar los eventos de los controles HTML, como clics del botón.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CDHtmlDialog`  
  
## Requisitos  
 **encabezado:** afxdhtml.h  
  
## Vea también  
 [ejemplo DHtmlExplore de MFC](../../top/visual-cpp-samples.md)   
 [DDX\_DHtml Helper Macros](../../mfc/reference/ddx-dhtml-helper-macros.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)