---
title: "Clase CHtmlView | Microsoft Docs"
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
  - "CHtmlView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exploradores, compatibilidad de MFC para"
  - "CHtmlView (clase)"
  - "WebBrowser (control)"
  - "WebBrowser (control), compatibilidad de MFC"
ms.assetid: 904976af-73de-4aba-84ac-cfae8e2be09a
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase CHtmlView
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control WebBrowser en el contexto de la arquitectura de vista\/documento de MFC.  
  
## Sintaxis  
  
```  
class CHtmlView : public CFormView  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CHtmlView::Create](../Topic/CHtmlView::Create.md)|Crea el control WebBrowser.|  
|[CHtmlView::CreateControlSite](../Topic/CHtmlView::CreateControlSite.md)|Reemplazable usado para crear una instancia del sitio de control para hospedar un control en el formulario.|  
|[CHtmlView::ExecFormsCommand](../Topic/CHtmlView::ExecFormsCommand.md)|Ejecuta el comando especificado mediante el método `IOleCommandTarget::Exec`.|  
|[CHtmlView::ExecWB](../Topic/CHtmlView::ExecWB.md)|Ejecuta un comando.|  
|[CHtmlView::GetAddressBar](../Topic/CHtmlView::GetAddressBar.md)|Determina si la barra de direcciones del objeto de Internet Explorer está visible. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::GetApplication](../Topic/CHtmlView::GetApplication.md)|Recupera un objeto de aplicación que representa la aplicación que contiene la instancia actual de la aplicación Internet Explorer.|  
|[CHtmlView::GetBusy](../Topic/CHtmlView::GetBusy.md)|Recupera un valor que indica si una descarga u otra actividad sigue en curso.|  
|[CHtmlView::GetContainer](../Topic/CHtmlView::GetContainer.md)|Recupera el contenedor del control WebBrowser.|  
|[CHtmlView::GetFullName](../Topic/CHtmlView::GetFullName.md)|Recupera el nombre completo, incluida la ruta de acceso, del recurso que se muestra en el explorador web. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::GetFullScreen](../Topic/CHtmlView::GetFullScreen.md)|Indica si el control WebBrowser está funcionando en modo de pantalla completa o en modo de ventana normal.|  
|[CHtmlView::GetHeight](../Topic/CHtmlView::GetHeight.md)|Recupera el alto de la ventana principal de Internet Explorer.|  
|[CHtmlView::GetHtmlDocument](../Topic/CHtmlView::GetHtmlDocument.md)|Recupera el documento HTML activo.|  
|[CHtmlView::GetLeft](../Topic/CHtmlView::GetLeft.md)|Recupera la coordenada de pantalla del borde izquierdo de la ventana principal de Internet Explorer.|  
|[CHtmlView::GetLocationName](../Topic/CHtmlView::GetLocationName.md)|Recupera el nombre del recurso que WebBrowser muestra actualmente.|  
|[CHtmlView::GetLocationURL](../Topic/CHtmlView::GetLocationURL.md)|Recupera la dirección URL del recurso que WebBrowser muestra actualmente.|  
|[CHtmlView::GetMenuBar](../Topic/CHtmlView::GetMenuBar.md)|Recupera un valor que determina si la barra de menús está visible.|  
|[CHtmlView::GetOffline](../Topic/CHtmlView::GetOffline.md)|Recupera un valor que determina si el control está sin conexión.|  
|[CHtmlView::GetParentBrowser](../Topic/CHtmlView::GetParentBrowser.md)|Recupera un puntero a la interfaz `IDispatch`. Para obtener más información, consulta [Implementing the IDispatch Interface](http://msdn.microsoft.com/es-es/0e171f7f-0022-4e9b-ac8e-98192828e945).|  
|[CHtmlView::GetProperty](../Topic/CHtmlView::GetProperty.md)|Recupera el valor actual de una propiedad asociada con el objeto especificado.|  
|[CHtmlView::GetReadyState](../Topic/CHtmlView::GetReadyState.md)|Recupera el estado listo del objeto de explorador web.|  
|[CHtmlView::GetRegisterAsBrowser](../Topic/CHtmlView::GetRegisterAsBrowser.md)|Indica si el control WebBrowser está registrado como un explorador de nivel superior para la resolución de nombres de destino.|  
|[CHtmlView::GetRegisterAsDropTarget](../Topic/CHtmlView::GetRegisterAsDropTarget.md)|Indica si el control WebBrowser está registrado como un destino para colocar para la navegación.|  
|[CHtmlView::GetSilent](../Topic/CHtmlView::GetSilent.md)|Indica si se pueden mostrar los cuadros de diálogo.|  
|[CHtmlView::GetSource](../Topic/CHtmlView::GetSource.md)|Código fuente HTML de la página web.|  
|[CHtmlView::GetStatusBar](../Topic/CHtmlView::GetStatusBar.md)|Indica si la barra de estado de Internet Explorer está visible. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::GetTheaterMode](../Topic/CHtmlView::GetTheaterMode.md)|Indica si el control WebBrowser está en modo de pantalla completa.|  
|[CHtmlView::GetToolBar](../Topic/CHtmlView::GetToolBar.md)|Recupera un valor que determina si la barra de herramientas está visible.|  
|[CHtmlView::GetTop](../Topic/CHtmlView::GetTop.md)|Recupera la coordenada de pantalla del borde superior de la ventana principal de Internet Explorer.|  
|[CHtmlView::GetTopLevelContainer](../Topic/CHtmlView::GetTopLevelContainer.md)|Recupera un valor que indica si el objeto actual es el contenedor de nivel superior del control WebBrowser.|  
|[CHtmlView::GetType](../Topic/CHtmlView::GetType.md)|Recupera el nombre de tipo del objeto de documento.|  
|[CHtmlView::GetVisible](../Topic/CHtmlView::GetVisible.md)|Recupera un valor que indica si el objeto está visible u oculto.|  
|[CHtmlView::GetWidth](../Topic/CHtmlView::GetWidth.md)|Recupera el ancho de la ventana principal de Internet Explorer.|  
|[CHtmlView::GoBack](../Topic/CHtmlView::GoBack.md)|Navega al elemento anterior de la lista de historial.|  
|[CHtmlView::GoForward](../Topic/CHtmlView::GoForward.md)|Navega al elemento siguiente de la lista de historial.|  
|[CHtmlView::GoHome](../Topic/CHtmlView::GoHome.md)|Navega a la página de inicio o principal actual.|  
|[CHtmlView::GoSearch](../Topic/CHtmlView::GoSearch.md)|Navega a la página de búsqueda actual.|  
|[CHtmlView::LoadFromResource](../Topic/CHtmlView::LoadFromResource.md)|Carga un recurso en el control WebBrowser.|  
|[CHtmlView::Navigate](../Topic/CHtmlView::Navigate.md)|Navega al recurso identificado con una dirección URL.|  
|[CHtmlView::Navigate2](../Topic/CHtmlView::Navigate2.md)|Navega al recurso identificado con una dirección URL o al archivo identificado mediante una ruta de acceso completa.|  
|[CHtmlView::OnBeforeNavigate2](../Topic/CHtmlView::OnBeforeNavigate2.md)|Se llama antes de que tenga lugar la navegación en el control WebBrowser especificado \(en un elemento de ventana o conjunto de marcos\)|  
|[CHtmlView::OnCommandStateChange](../Topic/CHtmlView::OnCommandStateChange.md)|Se llama para notificar a una aplicación que el estado habilitado de un comando de explorador web ha cambiado.|  
|[CHtmlView::OnDocumentComplete](../Topic/CHtmlView::OnDocumentComplete.md)|Se llama para notificar a una aplicación que un documento alcanzó el estado `READYSTATE_COMPLETE`.|  
|[CHtmlView::OnDocWindowActivate](../Topic/CHtmlView::OnDocWindowActivate.md)|Se llamada desde la implementación de Internet Explorer o MSHTML de [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281), que notifica al objeto en contexto activo cuando la ventana de documento del contenedor se activa o desactiva.|  
|[CHtmlView::OnDownloadBegin](../Topic/CHtmlView::OnDownloadBegin.md)|Se llama para notificar a una aplicación que se está iniciando una operación de navegación.|  
|[CHtmlView::OnDownloadComplete](../Topic/CHtmlView::OnDownloadComplete.md)|Se llama cuando una operación de navegación termina, se detiene o no se puede realizar.|  
|[CHtmlView::OnEnableModeless](../Topic/CHtmlView::OnEnableModeless.md)|Se llama para habilitar o deshabilitar los cuadros de diálogo no modales cuando el contenedor crea o destruye un cuadro de diálogo modal.|  
|[CHtmlView::OnFilterDataObject](../Topic/CHtmlView::OnFilterDataObject.md)|Internet Explorer o MSHTML lo llaman en el host para permitir que el host reemplace el objeto de datos de Internet Explorer o MSHTML.|  
|[CHtmlView::OnFrameWindowActivate](../Topic/CHtmlView::OnFrameWindowActivate.md)|Se llama desde [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) para notificar al objeto cuando la ventana marco de nivel superior del contenedor se activa o desactiva.|  
|[CHtmlView::OnFullScreen](../Topic/CHtmlView::OnFullScreen.md)|Se llama cuando la propiedad FullScreen cambia.|  
|[CHtmlView::OnGetDropTarget](../Topic/CHtmlView::OnGetDropTarget.md)|Internet Explorer o MSHTML lo llaman cuando se usa como destino para colocar para permitir que el host proporcione un [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) alternativo.|  
|[CHtmlView::OnGetExternal](../Topic/CHtmlView::OnGetExternal.md)|Internet Explorer o MSHTML lo llaman para obtener la interfaz `IDispatch` del host.|  
|[CHtmlView::OnGetHostInfo](../Topic/CHtmlView::OnGetHostInfo.md)|Recupera las capacidades de la interfaz de usuario del host de Internet Explorer o MSHTML.|  
|[CHtmlView::OnGetOptionKeyPath](../Topic/CHtmlView::OnGetOptionKeyPath.md)|Devuelve la clave del registro bajo la que Internet Explorer o MSHTML almacenan las preferencias del usuario.|  
|[CHtmlView::OnHideUI](../Topic/CHtmlView::OnHideUI.md)|Se llama cuando Internet Explorer o MSHTML quita sus menús y barras de herramientas.|  
|[CHtmlView::OnMenuBar](../Topic/CHtmlView::OnMenuBar.md)|Se llama cuando la propiedad MenuBar cambia.|  
|[CHtmlView::OnNavigateComplete2](../Topic/CHtmlView::OnNavigateComplete2.md)|Se llama cuando se completa la navegación a un hipervínculo \(en un elemento de ventana o conjunto de marcos\)|  
|[CHtmlView::OnNavigateError](../Topic/CHtmlView::OnNavigateError.md)|El marco de trabajo lo llama si la navegación a un hipervínculo no se realiza correctamente.|  
|[CHtmlView::OnNewWindow2](../Topic/CHtmlView::OnNewWindow2.md)|Se llama cuando se va a crear una nueva ventana para mostrar un recurso.|  
|[CHtmlView::OnProgressChange](../Topic/CHtmlView::OnProgressChange.md)|Se llama para notificar a una aplicación que se actualizó el progreso de una operación de descarga.|  
|[CHtmlView::OnPropertyChange](../Topic/CHtmlView::OnPropertyChange.md)|Se llama para notificar a una aplicación que el método [PutProperty](../Topic/CHtmlView::PutProperty.md) cambió el valor de una propiedad.|  
|[CHtmlView::OnQuit](../Topic/CHtmlView::OnQuit.md)|Se llama para notificar a una aplicación que la aplicación Internet Explorer está preparada para cerrarse. \(Se aplica a Internet Explorer solamente\)|  
|[CHtmlView::OnResizeBorder](../Topic/CHtmlView::OnResizeBorder.md)|Se llama desde la implementación de Internet Explorer o MSHTML de [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053), que alerta al objeto que debe cambiar el tamaño del espacio del borde.|  
|[CHtmlView::OnShowContextMenu](../Topic/CHtmlView::OnShowContextMenu.md)|Se llama desde Internet Explorer o MSHTML cuando está a punto de mostrar el menú contextual.|  
|[CHtmlView::OnShowUI](../Topic/CHtmlView::OnShowUI.md)|Se llama antes de que Internet Explorer o MSHTML muestren sus menús y barras de herramientas.|  
|[CHtmlView::OnStatusBar](../Topic/CHtmlView::OnStatusBar.md)|Se llama cuando la propiedad StatusBar cambia.|  
|[CHtmlView::OnStatusTextChange](../Topic/CHtmlView::OnStatusTextChange.md)|Se llama para notificar a una aplicación que el texto de la barra de estado asociada con el control WebBrowser ha cambiado.|  
|[CHtmlView::OnTheaterMode](../Topic/CHtmlView::OnTheaterMode.md)|Se llama cuando la propiedad TheaterMode cambia.|  
|[CHtmlView::OnTitleChange](../Topic/CHtmlView::OnTitleChange.md)|Se llama para notificar a una aplicación si el título de un documento del control WebBrowser está disponible o cambia.|  
|[CHtmlView::OnToolBar](../Topic/CHtmlView::OnToolBar.md)|Se llama cuando la propiedad ToolBar cambia.|  
|[CHtmlView::OnTranslateAccelerator](../Topic/CHtmlView::OnTranslateAccelerator.md)|Internet Explorer o MSHTML lo llaman cuando [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) o [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) se llaman para procesar mensajes de tecla de aceleración de menú de la cola de mensajes del contenedor.|  
|[CHtmlView::OnTranslateUrl](../Topic/CHtmlView::OnTranslateUrl.md)|Internet Explorer o MSHTML lo llaman para ofrecer al host la oportunidad de modificar la dirección URL que se va a cargar.|  
|[CHtmlView::OnUpdateUI](../Topic/CHtmlView::OnUpdateUI.md)|Notifica al host que cambió el estado del comando.|  
|[CHtmlView::OnVisible](../Topic/CHtmlView::OnVisible.md)|Se llama cuando la ventana del control WebBrowser debería estar visible u oculta.|  
|[CHtmlView::PutProperty](../Topic/CHtmlView::PutProperty.md)|Recupera el valor actual de una propiedad asociada con el objeto especificado.|  
|[CHtmlView::QueryFormsCommand](../Topic/CHtmlView::QueryFormsCommand.md)|Consulta el estado de uno o más comandos generados por eventos de interfaz de usuario.|  
|[CHtmlView::QueryStatusWB](../Topic/CHtmlView::QueryStatusWB.md)|Consulta el estado de un comando procesado por el control WebBrowser.|  
|[CHtmlView::Refresh](../Topic/CHtmlView::Refresh.md)|Vuelve a cargar la página actual.|  
|[CHtmlView::Refresh2](../Topic/CHtmlView::Refresh2.md)|Vuelve a cargar el archivo actual y, opcionalmente, impide que se envíe el encabezado `pragma:nocache`.|  
|[CHtmlView::SetAddressBar](../Topic/CHtmlView::SetAddressBar.md)|Muestra u oculta la barra de direcciones del objeto de Internet Explorer. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::SetFullScreen](../Topic/CHtmlView::SetFullScreen.md)|Establece un valor para determinar si el control está funcionando en modo de pantalla completa o en modo de ventana normal. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::SetHeight](../Topic/CHtmlView::SetHeight.md)|Establece el alto de la ventana principal de Internet Explorer.|  
|[CHtmlView::SetLeft](../Topic/CHtmlView::SetLeft.md)|Establece la posición horizontal de la ventana principal de Internet Explorer.|  
|[CHtmlView::SetMenuBar](../Topic/CHtmlView::SetMenuBar.md)|Establece un valor para determinar si la barra de menús del control está visible. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::SetOffline](../Topic/CHtmlView::SetOffline.md)|Establece un valor para determinar si el control está sin conexión.|  
|[CHtmlView::SetRegisterAsBrowser](../Topic/CHtmlView::SetRegisterAsBrowser.md)|Establece un valor que indica si el control WebBrowser está registrado como un explorador de nivel superior para la resolución de nombres de destino.|  
|[CHtmlView::SetRegisterAsDropTarget](../Topic/CHtmlView::SetRegisterAsDropTarget.md)|Establece un valor que indica si el control WebBrowser está registrado como un destino para colocar para la navegación.|  
|[CHtmlView::SetSilent](../Topic/CHtmlView::SetSilent.md)|Establece un valor para determinar si el control mostrará cuadros de diálogo.|  
|[CHtmlView::SetStatusBar](../Topic/CHtmlView::SetStatusBar.md)|Establece un valor para determinar si la barra de estado de Internet Explorer está visible. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::SetTheaterMode](../Topic/CHtmlView::SetTheaterMode.md)|Establece un valor que indica si el control WebBrowser está en modo de pantalla completa.|  
|[CHtmlView::SetToolBar](../Topic/CHtmlView::SetToolBar.md)|Establece un valor para determinar si la barra de herramientas del control está visible. \(El control WebBrowser se omite; solo Internet Explorer\).|  
|[CHtmlView::SetTop](../Topic/CHtmlView::SetTop.md)|Establece la posición vertical de la ventana principal de Internet Explorer.|  
|[CHtmlView::SetVisible](../Topic/CHtmlView::SetVisible.md)|Establece un valor que indica si el objeto está visible u oculto.|  
|[CHtmlView::SetWidth](../Topic/CHtmlView::SetWidth.md)|Establece el ancho de la ventana principal de Internet Explorer.|  
|[CHtmlView::Stop](../Topic/CHtmlView::Stop.md)|Detiene la apertura de un archivo.|  
  
## Comentarios  
 El control WebBrowser es una ventana en la que el usuario puede examinar sitios en World Wide Web, así como carpetas en el sistema de archivos local y en una red. El control WebBrowser admite hipervínculos, navegación de localizador uniforme de recursos \(URL\) y mantiene una lista de historial.  
  
## Uso de la clase CHtmlView en una aplicación MFC  
 En la aplicación de marco de trabajo MFC estándar \(basada en SDI o MDI\), el objeto de vista se deriva normalmente de un conjunto de clases especializado. Estas clases, todas ellas derivadas de `CView`, proporcionan funciones especializadas más allá de las que proporciona `CView`.  
  
 Al basar la clase de vista de la aplicación en `CHtmlView` se proporciona la vista con el control WebBrowser. De este modo, la aplicación se convierte de manera eficaz en un explorador web. El método preferido para crear una aplicación de estilo de explorador web es usar el Asistente para aplicaciones MFC y especificar `CHtmlView` como la clase de vista. Para obtener más información sobre la implementación y el uso del control WebBrowser en aplicaciones MFC, vea [Creating a Web Browser\-Style Application](../../mfc/reference/creating-a-web-browser-style-mfc-application.md) \(Crear una aplicación de estilo de navegador web\).  
  
> [!NOTE]
>  El control ActiveX WebBrowser \(y por tanto `CHtmlView`\) solo está disponible para programas que se ejecutan en Windows NT 4.0 o versiones posteriores, con Internet Explorer 4.0 o posterior instalado.  
  
 `CHtmlView` está diseñado para aplicaciones que acceden a la Web \(y\/o a documentos HTML\). La siguientes funciones miembro `CHtmlView` se aplican solo a la aplicación Internet Explorer. Estas funciones se ejecutarán correctamente en el control WebBrowser, pero no tendrán ningún efecto visible.  
  
-   [GetAddressBar](../Topic/CHtmlView::GetAddressBar.md)  
  
-   [GetFullName](../Topic/CHtmlView::GetFullName.md)  
  
-   [GetStatusBar](../Topic/CHtmlView::GetStatusBar.md)  
  
-   [GetAddressBar](../Topic/CHtmlView::SetAddressBar.md)  
  
-   [SetFullScreen](../Topic/CHtmlView::SetFullScreen.md)  
  
-   [SetMenuBar](../Topic/CHtmlView::SetMenuBar.md)  
  
-   [SetStatusBar](../Topic/CHtmlView::SetStatusBar.md)  
  
-   [SetToolBar](../Topic/CHtmlView::SetToolBar.md)  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CHtmlView`  
  
## Requisitos  
 **Encabezado:** afxhtml.h  
  
## Vea también  
 [Ejemplo MFCIE de MFC](../../top/visual-cpp-samples.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [IWebBrowser2](https://msdn.microsoft.com/en-us/library/aa752127.aspx)