---
title: COleControl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleControl
dev_langs:
- C++
helpviewer_keywords:
- OLE controls, MFC
- windowless controls, MFC
- windowless controls
- controls [MFC], OLE
- controls [MFC], windowless
- COleControl class
ms.assetid: 53e95299-38e8-447b-9c5f-a381d27f5123
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7ef5621aaf940be3ebe2806971dfc65d06972a5a
ms.lasthandoff: 02/24/2017

---
# <a name="colecontrol-class"></a>COleControl (clase)
Una clase base eficaz para desarrollar controles OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleControl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControl::COleControl](#colecontrol)|Crea un objeto `COleControl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControl::AmbientAppearance](#ambientappearance)|Recupera la apariencia del control actual.|  
|[COleControl::AmbientBackColor](#ambientbackcolor)|Devuelve el valor de la propiedad BackColor ambiente.|  
|[COleControl::AmbientDisplayName](#ambientdisplayname)|Devuelve el nombre del control según lo especificado por el contenedor.|  
|[COleControl::AmbientFont](#ambientfont)|Devuelve el valor de la propiedad de fuente ambiente.|  
|[COleControl::AmbientForeColor](#ambientforecolor)|Devuelve el valor de la propiedad ForeColor ambiente.|  
|[COleControl:: AmbientLocaleID](#ambientlocaleid)|Devuelve el identificador de configuración regional. del contenedor|  
|[COleControl::AmbientScaleUnits](#ambientscaleunits)|Devuelve el tipo de unidades usadas por el contenedor.|  
|[COleControl::AmbientShowGrabHandles](#ambientshowgrabhandles)|Determina si se deben mostrar las asas de captación.|  
|[COleControl::AmbientShowHatching](#ambientshowhatching)|Determina si se debe mostrar el sombreado.|  
|[COleControl::AmbientTextAlign](#ambienttextalign)|Devuelve el tipo de alineación de texto especificado por el contenedor.|  
|[COleControl::AmbientUIDead](#ambientuidead)|Determina si el control debe responder a las acciones de la interfaz de usuario.|  
|[COleControl::AmbientUserMode](#ambientusermode)|Determina el modo del contenedor.|  
|[COleControl::BoundPropertyChanged](#boundpropertychanged)|Notifica que el contenedor que se ha cambiado una propiedad enlazada.|  
|[COleControl::BoundPropertyRequestEdit](#boundpropertyrequestedit)|Solicita permiso para editar el valor de propiedad.|  
|[COleControl::ClientToParent](#clienttoparent)|Convierte un punto con respecto al origen del control a un punto con respecto al origen de su contenedor.|  
|[COleControl::ClipCaretRect](#clipcaretrect)|Ajusta un rectángulo de intercalación se superponen por un control.|  
|[COleControl::ControlInfoChanged](#controlinfochanged)|Llame a esta función después de cambia el conjunto de teclas de acceso controlado por el control.|  
|[COleControl::DisplayError](#displayerror)|Muestra los eventos de Error estándar para el usuario del control.|  
|[COleControl::DoClick](#doclick)|Implementación de las existencias `DoClick` método.|  
|[COleControl:: DoPropExchange](#dopropexchange)|Serializa las propiedades de un `COleControl` objeto.|  
|[COleControl::DoSuperclassPaint](#dosuperclasspaint)|Vuelve a dibujar un control OLE que se ha derivado de un control de Windows.|  
|[COleControl::EnableSimpleFrame](#enablesimpleframe)|Habilita la compatibilidad de marco sencillo para un control.|  
|[COleControl::ExchangeExtent](#exchangeextent)|Serializa el ancho y el alto del control.|  
|[COleControl::ExchangeStockProps](#exchangestockprops)|Serializa las propiedades estándar del control.|  
|[COleControl:: ExchangeVersion](#exchangeversion)|Serializa el número de versión del control.|  
|[COleControl::FireClick](#fireclick)|Se desencadena la acción `Click` eventos.|  
|[COleControl::FireDblClick](#firedblclick)|Se desencadena la acción `DblClick` eventos.|  
|[COleControl:: FireError](#fireerror)|Se desencadena la acción `Error` eventos.|  
|[A COleControl:: FireEvent](#fireevent)|Se desencadena un evento personalizado.|  
|[COleControl::FireKeyDown](#firekeydown)|Se desencadena la acción `KeyDown` eventos.|  
|[COleControl::FireKeyPress](#firekeypress)|Se desencadena la acción `KeyPress` eventos.|  
|[COleControl::FireKeyUp](#firekeyup)|Se desencadena la acción `KeyUp` eventos.|  
|[COleControl::FireMouseDown](#firemousedown)|Se desencadena la acción `MouseDown` eventos.|  
|[COleControl::FireMouseMove](#firemousemove)|Se desencadena la acción `MouseMove` eventos.|  
|[COleControl::FireMouseUp](#firemouseup)|Se desencadena la acción `MouseUp` eventos.|  
|[COleControl::FireReadyStateChange](#firereadystatechange)|Se desencadena un evento cuando cambia el estado del control listo.|  
|[COleControl:: GetActivationPolicy](#getactivationpolicy)|Modifica el comportamiento predeterminado de la activación de un control que admite el `IPointerInactive` interfaz.|  
|[COleControl:: GetAmbientProperty](#getambientproperty)|Devuelve el valor de la propiedad de ambiente especificada.|  
|[COleControl::GetAppearance](#getappearance)|Devuelve el valor de la propiedad de apariencia estándar.|  
|[COleControl::GetBackColor](#getbackcolor)|Devuelve el valor de la propiedad BackColor estándar.|  
|[COleControl::GetBorderStyle](#getborderstyle)|Devuelve el valor de la propiedad de estilo de borde estándar.|  
|[COleControl::GetCapture](#getcapture)|Determina si un objeto de control sin ventana, activada tiene la captura del mouse.|  
|[COleControl::GetClassID](#getclassid)|Recupera el identificador de clase OLE del control.|  
|[COleControl::GetClientOffset](#getclientoffset)|Recupera la diferencia entre la esquina superior izquierda del área rectangular del control y la esquina superior izquierda de su área cliente.|  
|[COleControl::GetClientRect](#getclientrect)|Recupera el tamaño del área cliente del control.|  
|[COleControl::GetClientSite](#getclientsite)|Consultas de un objeto para el puntero a su sitio de cliente actual dentro de su contenedor.|  
|[COleControl:: GetControlFlags](#getcontrolflags)|Recupera la configuración del indicador de control.|  
|[COleControl::GetControlSize](#getcontrolsize)|Devuelve la posición y el tamaño del control OLE.|  
|[COleControl::GetDC](#getdc)|Proporciona un medio para un control sin ventana obtener un contexto de dispositivo de su contenedor.|  
|[COleControl::GetEnabled](#getenabled)|Devuelve el valor de la propiedad Enabled de existencias.|  
|[COleControl::GetExtendedControl](#getextendedcontrol)|Recupera un puntero a un objeto de control extendido que pertenece al contenedor.|  
|[COleControl::GetFocus](#getfocus)|Determina si el control tiene el foco.|  
|[COleControl::GetFont](#getfont)|Devuelve el valor de la propiedad Font estándar.|  
|[COleControl::GetFontTextMetrics](#getfonttextmetrics)|Devuelve las métricas de un `CFontHolder` objeto.|  
|[COleControl::GetForeColor](#getforecolor)|Devuelve el valor de la propiedad ForeColor estándar.|  
|[COleControl::GetHwnd](#gethwnd)|Devuelve el valor de la propiedad hWnd stock.|  
|[COleControl::GetMessageString](#getmessagestring)|Proporciona el texto de la barra de estado para un elemento de menú.|  
|[COleControl::GetNotSupported](#getnotsupported)|Impide el acceso al valor de propiedad de un control por el usuario.|  
|[COleControl::GetReadyState](#getreadystate)|Devuelve el estado de disponibilidad del control.|  
|[COleControl::GetRectInContainer](#getrectincontainer)|Devuelve el rectángulo del control en relación con su contenedor.|  
|[COleControl::GetStockTextMetrics](#getstocktextmetrics)|Devuelve las métricas de la propiedad Font estándar.|  
|[COleControl::GetText](#gettext)|Devuelve el valor de la propiedad de título o de texto estándar.|  
|[COleControl:: GetWindowlessDropTarget](#getwindowlessdroptarget)|Invalidar para permitir que un control sin ventana sea el destino de arrastrar y colocar.|  
|[COleControl::InitializeIIDs](#initializeiids)|Informa a la clase base de los IID usará el control.|  
|[COleControl::InternalGetFont](#internalgetfont)|Devuelve un `CFontHolder` objeto para la propiedad Font estándar.|  
|[COleControl::InternalGetText](#internalgettext)|Recupera la propiedad de título o de texto estándar.|  
|[COleControl:: InternalSetReadyState](#internalsetreadystate)|Establece el estado del control preparación y desencadena el evento de cambio de estado listo.|  
|[COleControl::InvalidateControl](#invalidatecontrol)|Invalida un área del control mostrado, lo que hace que se vuelva a dibujar.|  
|[COleControl::InvalidateRgn](#invalidatergn)|Invalida el área de cliente de la ventana de contenedor dentro de la región. Puede utilizarse para volver a dibujar los controles sin ventana en la región.|  
|[COleControl::IsConvertingVBX](#isconvertingvbx)|Permite cargar especializada de un control OLE.|  
|[COleControl::IsModified](#ismodified)|Determina si el estado del control ha cambiado.|  
|[COleControl::IsOptimizedDraw](#isoptimizeddraw)|Indica si el contenedor admite dibujos optimizados para la operación de dibujo actual.|  
|[COleControl::IsSubclassedControl](#issubclassedcontrol)|Se llama para determinar si el control las subclases de control de Windows.|  
|[COleControl::Load](#load)|Restablece los datos asincrónicos anteriores e inicia una nueva carga de la propiedad del control asincrónico.|  
|[COleControl::LockInPlaceActive](#lockinplaceactive)|Determina si el contenedor se puede desactivar el control.|  
|[COleControl::OnAmbientPropertyChange](#onambientpropertychange)|Se llama cuando se cambia una propiedad de ambiente.|  
|[COleControl::OnAppearanceChanged](#onappearancechanged)|Se llama cuando se cambia la propiedad de apariencia estándar.|  
|[COleControl::OnBackColorChanged](#onbackcolorchanged)|Se llama cuando se cambia la propiedad BackColor estándar.|  
|[COleControl::OnBorderStyleChanged](#onborderstylechanged)|Se llama cuando se cambia la propiedad de estilo de borde estándar.|  
|[COleControl::OnClick](#onclick)|Se llama para activar las acciones, haga clic en eventos.|  
|[COleControl::OnClose](#onclose)|Notifica al control que `IOleControl::Close` se ha llamado.|  
|[COleControl::OnDoVerb](#ondoverb)|Se llama después de que se ha ejecutado un verbo de control.|  
|[COleControl:: OnDraw](#ondraw)|Se llama cuando se solicita un control a dibujarse.|  
|[COleControl:: OnDrawMetafile](#ondrawmetafile)|Lo llama el contenedor cuando se solicita un control a dibujarse con un contexto de dispositivo de metarchivo.|  
|[COleControl::OnEdit](#onedit)|El contenedor llama a la interfaz de usuario activar un control OLE.|  
|[COleControl::OnEnabledChanged](#onenabledchanged)|Se llama cuando cambia la propiedad habilitado estándar.|  
|[COleControl::OnEnumVerbs](#onenumverbs)|El contenedor llama para enumerar los verbos de un control.|  
|[COleControl::OnEventAdvise](#oneventadvise)|Se llama cuando están conectados o desconectados de un control de los controladores de eventos.|  
|[COleControl::OnFontChanged](#onfontchanged)|Se llama cuando se cambia la propiedad Font estándar.|  
|[COleControl::OnForeColorChanged](#onforecolorchanged)|Se llama cuando se cambia la propiedad de color de primer plano estándar.|  
|[COleControl::OnFreezeEvents](#onfreezeevents)|Se llama cuando se inmoviliza o inmovilizados eventos de un control.|  
|[COleControl::OnGetColorSet](#ongetcolorset)|Notifica al control que `IOleObject::GetColorSet` se ha llamado.|  
|[COleControl::OnGetControlInfo](#ongetcontrolinfo)|Proporciona información de tecla de acceso al contenedor.|  
|[COleControl::OnGetDisplayString](#ongetdisplaystring)|Se llama para obtener una cadena que represente un valor de propiedad.|  
|[COleControl::OnGetInPlaceMenu](#ongetinplacemenu)|Solicita el identificador del menú del control que se combinará con el contenedor.|  
|[COleControl::OnGetNaturalExtent](#ongetnaturalextent)|Invalidar para recuperar el tamaño de presentación del control más cercano al modo de tamaño y el alcance propuesto.|  
|[COleControl::OnGetPredefinedStrings](#ongetpredefinedstrings)|Devuelve las cadenas que representan los valores posibles para una propiedad.|  
|[COleControl::OnGetPredefinedValue](#ongetpredefinedvalue)|Devuelve el valor correspondiente a una cadena.|  
|[COleControl::OnGetViewExtent](#ongetviewextent)|Invalidar para recuperar el tamaño de las áreas de visualización del control (puede utilizarse para habilitar el dibujo de dos pasos).|  
|[COleControl::OnGetViewRect](#ongetviewrect)|Invalidación para convertir el tamaño del control en un rectángulo que comienza en una posición específica.|  
|[COleControl::OnGetViewStatus](#ongetviewstatus)|Invalidar para recuperar el estado de vista del control.|  
|[COleControl::OnHideToolBars](#onhidetoolbars)|El contenedor lo llama cuando el control está desactivado de la interfaz de usuario.|  
|[COleControl::OnInactiveMouseMove](#oninactivemousemove)|Invalidación para que el contenedor del control inactivo en el envío del puntero del mouse `WM_MOUSEMOVE` mensajes al control.|  
|[COleControl::OnInactiveSetCursor](#oninactivesetcursor)|Invalidación para que el contenedor del control inactivo en el envío del puntero del mouse `WM_SETCURSOR` mensajes al control.|  
|[COleControl::OnKeyDownEvent](#onkeydownevent)|Se llama después de que se ha desencadenado el evento KeyDown estándar.|  
|[COleControl::OnKeyPressEvent](#onkeypressevent)|Se llama después de que se ha desencadenado el evento KeyPress estándar.|  
|[COleControl::OnKeyUpEvent](#onkeyupevent)|Se llama después de que se ha desencadenado el evento KeyUp estándar.|  
|[COleControl::OnMapPropertyToPage](#onmappropertytopage)|Indica qué página de propiedades para editar una propiedad.|  
|[COleControl::OnMnemonic](#onmnemonic)|Se llama cuando se ha presionado una tecla de acceso del control.|  
|[COleControl::OnProperties](#onproperties)|Se llama cuando se ha invocado el verbo de "Propiedades" del control.|  
|[COleControl::OnQueryHitPoint](#onqueryhitpoint)|Invalidar para consultar si un control superpone a un momento dado.|  
|[COleControl::OnQueryHitRect](#onqueryhitrect)|Invalidar para consultar si un control superpone a cualquier punto en un rectángulo determinado.|  
|[COleControl::OnRenderData](#onrenderdata)|Llamado por el marco de trabajo para recuperar datos en el formato especificado.|  
|[COleControl::OnRenderFileData](#onrenderfiledata)|Llamado por el marco de trabajo para recuperar datos de un archivo en el formato especificado.|  
|[COleControl::OnRenderGlobalData](#onrenderglobaldata)|Llamado por el marco de trabajo para recuperar datos de la memoria global en el formato especificado.|  
|[COleControl:: OnResetState](#onresetstate)|Restablece las propiedades de un control a los valores predeterminados.|  
|[COleControl:: OnSetClientSite](#onsetclientsite)|Notifica al control que `IOleControl::SetClientSite` se ha llamado.|  
|[COleControl::OnSetData](#onsetdata)|Reemplaza los datos del control por otro valor.|  
|[COleControl::OnSetExtent](#onsetextent)|Se llama después de que ha cambiado la extensión del control.|  
|[COleControl::OnSetObjectRects](#onsetobjectrects)|Se llama después de cambiar las dimensiones del control.|  
|[COleControl::OnShowToolBars](#onshowtoolbars)|Se llama cuando el control se ha activado la IU.|  
|[COleControl::OnTextChanged](#ontextchanged)|Se llama cuando se cambia el texto de existencias o la propiedad de título.|  
|[COleControl::OnWindowlessMessage](#onwindowlessmessage)|Procesa los mensajes de ventana (que no sean los mensajes de teclado y mouse) para los controles sin ventanas.|  
|[COleControl::ParentToClient](#parenttoclient)|Convierte un punto con respecto al origen del contenedor a un punto con respecto al origen del control.|  
|[COleControl::PostModalDialog](#postmodaldialog)|Notifica al contenedor que se ha cerrado el cuadro de diálogo modal.|  
|[COleControl::PreModalDialog](#premodaldialog)|Notifica al contenedor que se mostrará un cuadro de diálogo modal.|  
|[COleControl::RecreateControlWindow](#recreatecontrolwindow)|Destruye y vuelve a crear la ventana del control.|  
|[COleControl::Refresh](#refresh)|Fuerza la actualización de la apariencia de un control.|  
|[COleControl::ReleaseCapture](#releasecapture)|Libera la captura del mouse.|  
|[COleControl::ReleaseDC](#releasedc)|Libera el contexto de dispositivo de presentación de un contenedor de un control sin ventanas.|  
|[COleControl::ReparentControlWindow](#reparentcontrolwindow)|Restablece al elemento primario de la ventana de control.|  
|[COleControl::ResetStockProps](#resetstockprops)|Inicializa `COleControl` propiedades a sus valores predeterminados estándar.|  
|[COleControl::ResetVersion](#resetversion)|Inicializa el número de versión en un valor determinado.|  
|[COleControl::ScrollWindow](#scrollwindow)|Permite a un control sin ventana desplazar un área dentro de su imagen activo en lugar de la pantalla.|  
|[COleControl::SelectFontObject](#selectfontobject)|Selecciona una propiedad de fuente personalizada en un contexto de dispositivo.|  
|[COleControl:: SelectStockFont](#selectstockfont)|Selecciona la propiedad Font estándar en un contexto de dispositivo.|  
|[COleControl::SerializeExtent](#serializeextent)|Serializa o inicializa el espacio de presentación para el control.|  
|[COleControl::SerializeStockProps](#serializestockprops)|Serializa o inicializa el `COleControl` propiedades estándar.|  
|[COleControl::SerializeVersion](#serializeversion)|Serializa o inicializa la información de versión del control.|  
|[COleControl::SetAppearance](#setappearance)|Establece el valor de la propiedad de apariencia estándar.|  
|[COleControl::SetBackColor](#setbackcolor)|Establece el valor de la propiedad BackColor estándar.|  
|[COleControl::SetBorderStyle](#setborderstyle)|Establece el valor de la propiedad de estilo de borde estándar.|  
|[COleControl::SetCapture](#setcapture)|Hace que la ventana del control contenedor tomar posesión de la captura del mouse en el nombre del control.|  
|[COleControl::SetControlSize](#setcontrolsize)|Establece la posición y el tamaño del control OLE.|  
|[COleControl::SetEnabled](#setenabled)|Establece el valor de la propiedad Enabled de existencias.|  
|[COleControl::SetFocus](#setfocus)|Hace que la ventana del control contenedor tomar posesión del foco de entrada en nombre del control.|  
|[COleControl::SetFont](#setfont)|Establece el valor de la propiedad Font estándar.|  
|[COleControl::SetForeColor](#setforecolor)|Establece el valor de la propiedad ForeColor estándar.|  
|[COleControl::SetInitialSize](#setinitialsize)|Establece el tamaño de un control cuando se muestra por primera vez en un contenedor OLE.|  
|[COleControl::SetModifiedFlag](#setmodifiedflag)|Cambia el estado modificado de un control.|  
|[COleControl:: SetNotPermitted](#setnotpermitted)|Indica que ha fallado una solicitud de edición.|  
|[COleControl:: SetNotSupported](#setnotsupported)|Evita la modificación del valor de propiedad de un control por el usuario.|  
|[COleControl::SetRectInContainer](#setrectincontainer)|Establece el rectángulo del control en relación con su contenedor.|  
|[COleControl::SetText](#settext)|Establece el valor de la propiedad de título o de texto estándar.|  
|[COleControl:: ThrowError](#throwerror)|Indica que se ha producido un error en un control OLE.|  
|[COleControl::TransformCoords](#transformcoords)|Transformaciones de valores entre un contenedor y el control de las coordenadas.|  
|[COleControl::TranslateColor](#translatecolor)|Convierte un **OLE_COLOR** valor a un **COLORREF** valor.|  
|[COleControl::WillAmbientsBeValidDuringLoad](#willambientsbevalidduringload)|Determina si las propiedades de ambiente estará disponibles la próxima vez que se cargue el control.|  
|[COleControl::WindowProc](#windowproc)|Proporciona un procedimiento para una `COleControl` objeto.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControl::DrawContent](#drawcontent)|Llamado por el marco de trabajo cuando la apariencia del control debe actualizarse.|  
|[COleControl::DrawMetafile](#drawmetafile)|Lo llama el marco de trabajo cuando se usa el contexto de dispositivo de metarchivo.|  
|[COleControl::IsInvokeAllowed](#isinvokeallowed)|Permite la invocación del método de automatización.|  
|[COleControl::SetInitialDataFormats](#setinitialdataformats)|Llamado por el marco para inicializar la lista de formatos de datos admitidos por el control.|  
  
## <a name="remarks"></a>Comentarios  
 Deriva `CWnd`, esta clase hereda toda la funcionalidad de un objeto de ventana de Windows además de funcionalidad específica de OLE, como el desencadenamiento de eventos y la capacidad para admitir los métodos y propiedades.  
  
 Controles OLE pueden insertarse en aplicaciones de contenedor OLE y comunican con el contenedor mediante un sistema bidireccional de desencadenamiento de eventos y expone métodos y propiedades para el contenedor. Tenga en cuenta que los contenedores OLE estándares admiten sólo la funcionalidad básica de un control OLE. Son no admite características extendidas de un control OLE. Desencadenamiento de eventos se produce cuando se envían eventos al contenedor como resultado de determinadas acciones tienen lugar en el control. A su vez, el contenedor se comunica con el control mediante un conjunto de métodos y propiedades análogas a las funciones miembro expuesto y miembros de datos de una clase de C++. Este enfoque permite al desarrollador controlar la apariencia del control y notificar al contenedor cuando se producen ciertas acciones.  
  
## <a name="windowless-controls"></a>Controles sin ventana  
 Controles OLE pueden ser usado activo en contexto sin una ventana. Los controles sin ventana tienen ventajas importantes:  
  
-   Los controles sin ventana pueden ser transparentes y no rectangulares  
  
-   Controles sin ventana reducen el tiempo de tamaño y la creación de instancia del objeto  
  
 Controles no necesitan una ventana. Servicios que ofrece una ventana pueden proporcionar fácilmente a través de una única ventana compartida (normalmente del contenedor) y algo de código de envío. Disponer de una ventana es principalmente una complicación innecesaria en el objeto.  
  
 Cuando se utiliza la activación sin ventana, el contenedor (que tiene una ventana) es responsable de proporcionar servicios que de lo contrario, se habría proporcionados por la ventana del control. Por ejemplo, si el control necesita consultar el foco del teclado, consulte la captura del mouse u obtener un contexto de dispositivo, estas operaciones son administradas por el contenedor. El `COleControl` [funciones miembro de operación sin ventanas](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) invocar estas operaciones en el contenedor.  
  
 Cuando se habilita la activación sin ventana, los delegados de contenedor mensajes para el control de entrada `IOleInPlaceObjectWindowless` interfaz (una extensión de [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) de soporte sin ventanas). `COleControl`de implementación de esta interfaz se encarga de enviar estos mensajes a través del mapa de mensajes del control, después de ajustar el mouse coordina adecuadamente. Puede procesar estos mensajes como mensajes de ventanas ordinarios, agregando las entradas correspondientes al mapa de mensajes.  
  
 En un control sin ventana, debe utilizar siempre el `COleControl` funciones miembro en lugar de los correspondientes `CWnd` funciones miembro o sus funciones de API de Windows relacionados.  
  
 Objetos de control OLE también pueden crear una ventana cuando estén activos, pero aumenta la cantidad de trabajo necesario para la transición de activos inactivos y disminuye la velocidad de la transición. Hay casos en que se trata de un problema: por ejemplo, considere la posibilidad de una cuadrícula de cuadros de texto. Cuando cursor arriba y abajo a través de la columna, cada control debe ser local activa y, a continuación, se desactiva. La velocidad de la transición inactivo o activo afectará directamente a la velocidad de desplazamiento.  
  
 Para obtener más información sobre el desarrollo de un marco de control OLE, consulte los artículos [controles ActiveX de MFC](../../mfc/mfc-activex-controls.md) y [información general: crear un programa de Control ActiveX de MFC](../../mfc/reference/mfc-activex-control-wizard.md). Para obtener información sobre la optimización de controles OLE, incluidos los controles sin ventana y parpadeo, consulte [controles ActiveX MFC: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `COleControl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxctl.h  
  
##  <a name="a-nameambientbackcolora--colecontrolambientbackcolor"></a><a name="ambientbackcolor"></a>COleControl::AmbientBackColor  
 Devuelve el valor de la propiedad BackColor ambiente.  
  
```  
OLE_COLOR AmbientBackColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor actual de la propiedad del contenedor ambiente BackColor, si existe. Si no se admite la propiedad, esta función devuelve el color de fondo de Windows definidos por el sistema.  
  
### <a name="remarks"></a>Comentarios  
 La propiedad BackColor ambiente está disponible para todos los controles y se define por el contenedor. Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientdisplaynamea--colecontrolambientdisplayname"></a><a name="ambientdisplayname"></a>COleControl::AmbientDisplayName  
 El nombre que ha asignado el contenedor para el control se puede utilizar en los mensajes de error que se muestra al usuario.  
  
```  
CString AmbientDisplayName();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre del control OLE. El valor predeterminado es una cadena de longitud cero.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientfonta--colecontrolambientfont"></a><a name="ambientfont"></a>COleControl::AmbientFont  
 Devuelve el valor de la propiedad de fuente ambiente.  
  
```  
LPFONTDISP AmbientFont();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la interfaz de envío de fuente ambiente del contenedor. El valor predeterminado es **NULL**. Si el valor devuelto no es igual a **NULL**, usted es responsable de liberar la fuente mediante una llamada a su [IUnknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) función miembro.  
  
### <a name="remarks"></a>Comentarios  
 La propiedad de fuente ambiente está definido por el contenedor y disponibles para todos los controles. Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientforecolora--colecontrolambientforecolor"></a><a name="ambientforecolor"></a>COleControl::AmbientForeColor  
 Devuelve el valor de la propiedad ForeColor ambiente.  
  
```  
OLE_COLOR AmbientForeColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor actual de la propiedad del contenedor ambiente ForeColor, si existe. Si no se admite esta función devuelve el color del texto definido por el sistema Windows.  
  
### <a name="remarks"></a>Comentarios  
 La propiedad de ambiente ForeColor está disponible para todos los controles y se define por el contenedor. Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientlocaleida--colecontrolambientlocaleid"></a><a name="ambientlocaleid"></a>COleControl:: AmbientLocaleID  
 Devuelve el identificador de configuración regional. del contenedor  
  
```  
LCID AmbientLocaleID();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de propiedad de LocaleID del contenedor, si existe. Si no se admite esta propiedad, esta función devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 El control puede utilizar LocaleID para adaptar la interfaz de usuario para escenarios específicos. Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientappearancea--colecontrolambientappearance"></a><a name="ambientappearance"></a>COleControl::AmbientAppearance  
 Recupera el valor de aspecto actual para el objeto de control.  
  
```  
short AmbientAppearance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La apariencia del control:  
  
- **0** planos apariencia  
  
- **1** apariencia 3D  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor actual de la **DISPID_AMBIENT_APPEARANCE** propiedad del control.  
  
##  <a name="a-nameambientscaleunitsa--colecontrolambientscaleunits"></a><a name="ambientscaleunits"></a>COleControl::AmbientScaleUnits  
 Devuelve el tipo de unidades usadas por el contenedor.  
  
```  
CString AmbientScaleUnits();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena que contiene el elemento ScaleUnits ambiente del contenedor. Si no se admite esta propiedad, esta función devuelve una cadena de longitud cero.  
  
### <a name="remarks"></a>Comentarios  
 La propiedad del contenedor ambiente ScaleUnits puede utilizarse para mostrar posiciones o dimensiones, con la etiqueta con la unidad elegida como twips o centímetros. Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientshowgrabhandlesa--colecontrolambientshowgrabhandles"></a><a name="ambientshowgrabhandles"></a>COleControl::AmbientShowGrabHandles  
 Determina si el contenedor permite el control mostrar las asas de captación para sí mismo cuando está activo.  
  
```  
BOOL AmbientShowGrabHandles();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se deben mostrar controladores de arrastre; en caso contrario, 0. Si no se admite esta propiedad, esta función devuelve cero.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientshowhatchinga--colecontrolambientshowhatching"></a><a name="ambientshowhatching"></a>COleControl::AmbientShowHatching  
 Determina si el contenedor permite el control para que se muestre con un sombreado patrón cuando activo de la interfaz de usuario.  
  
```  
BOOL AmbientShowHatching();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se debe mostrar el modelo de sombreado; en caso contrario, 0. Si no se admite esta propiedad, esta función devuelve cero.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambienttextaligna--colecontrolambienttextalign"></a><a name="ambienttextalign"></a>COleControl::AmbientTextAlign  
 Determina la alineación de texto ambiente preferida por el contenedor del control.  
  
```  
short AmbientTextAlign();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de la propiedad TextAlign de ambiente del contenedor. Si no se admite esta propiedad, esta función devuelve 0.  
  
 La siguiente es una lista de valores devueltos válidos:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|0|Alineación general (números a la derecho, texto a la izquierda).|  
|1|Alinear a la izquierda|  
|2|Centro|  
|3|Alinear a la derecha|  
  
### <a name="remarks"></a>Comentarios  
 Esta propiedad está disponible para todos los controles incrustados y se define por el contenedor. Tenga en cuenta que el contenedor no es necesario para admitir esta propiedad.  
  
##  <a name="a-nameambientuideada--colecontrolambientuidead"></a><a name="ambientuidead"></a>COleControl::AmbientUIDead  
 Determina si el contenedor desea el control que se va a responder a las acciones de la interfaz de usuario.  
  
```  
BOOL AmbientUIDead();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el control debe responder a las acciones de la interfaz de usuario; en caso contrario, 0. Si no se admite esta propiedad, esta función devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, un contenedor podría establecer esto **TRUE** en modo de diseño.  
  
##  <a name="a-nameambientusermodea--colecontrolambientusermode"></a><a name="ambientusermode"></a>COleControl::AmbientUserMode  
 Determina si el contenedor está en modo de diseño o en modo de usuario.  
  
```  
BOOL AmbientUserMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el contenedor está en modo de usuario; en caso contrario, 0 (en modo de diseño). Si no se admite esta propiedad, esta función devuelve TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, un contenedor podría establecer esto **FALSE** en modo de diseño.  
  
##  <a name="a-nameboundpropertychangeda--colecontrolboundpropertychanged"></a><a name="boundpropertychanged"></a>COleControl::BoundPropertyChanged  
 Indica que ha cambiado el valor de la propiedad enlazada.  
  
```  
void BoundPropertyChanged(DISPID dispid);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío de una propiedad enlazada del control.  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar cada vez que el valor de la propiedad cambia, incluso en casos donde no se ha realizado el cambio a través de la propiedad establece el método. Tenga en cuenta especialmente de propiedades enlazadas a los que se asignan a variables de miembro. Cada vez que un miembro variable cambios, `BoundPropertyChanged` se debe llamar.  
  
##  <a name="a-nameboundpropertyrequestedita--colecontrolboundpropertyrequestedit"></a><a name="boundpropertyrequestedit"></a>COleControl::BoundPropertyRequestEdit  
 Solicitudes de permiso de la `IPropertyNotifySink` interfaz para cambiar un valor de la propiedad enlazada proporcionado por el control.  
  
```  
BOOL BoundPropertyRequestEdit(DISPID dispid);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío de una propiedad enlazada del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se permite el cambio; en caso contrario, 0. El valor predeterminado es distinto de cero.  
  
### <a name="remarks"></a>Comentarios  
 Si se deniega el permiso, el control no debe permitir que el valor de cambio de propiedad. Esto puede hacerse por pasando por alto o se producen errores en la acción que ha intentado cambiar el valor de propiedad.  
  
##  <a name="a-nameclienttoparenta--colecontrolclienttoparent"></a><a name="clienttoparent"></a>COleControl::ClientToParent  
 Convierte las coordenadas de `pPoint` en coordenadas principales.  
  
```  
virtual void ClientToParent(
    LPCRECT lprcBounds, 
    LPPOINT pPoint) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lprcBounds`  
 Puntero a los límites del control dentro del contenedor OLE. El área de todo el control, incluidos los bordes y barras de desplazamiento, pero no en el área de cliente.  
  
 `pPoint`  
 Puntero para el punto del área de cliente OLE para traducir las coordenadas del elemento primario (contenedor).  
  
### <a name="remarks"></a>Comentarios  
 En la entrada `pPoint` es relativo al origen del área cliente del control OLE (esquina superior izquierda del área cliente del control). En la salida `pPoint` es relativo al origen del elemento primario (esquina superior izquierda del contenedor).  
  
##  <a name="a-nameclipcaretrecta--colecontrolclipcaretrect"></a><a name="clipcaretrect"></a>COleControl::ClipCaretRect  
 Ajusta un rectángulo de símbolo de intercalación si es total o parcialmente cubierta por los objetos superpuestos, opacos.  
  
```  
BOOL ClipCaretRect(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 En la entrada, un puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura que contiene el área de la intercalación que se ajusten. En la salida, el área de intercalación ajustado, o **NULL** si el rectángulo de símbolo de intercalación está cubierto completamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Un símbolo de intercalación es una línea, bloque o mapa de bits que normalmente indica dónde se insertará texto o gráficos parpadeante.  
  
 Un objeto sin ventanas con seguridad no puede mostrar un símbolo de intercalación sin comprobar primero si el símbolo de intercalación está parcial o totalmente oculto por los objetos superpuestos. Para hacerlo posible, puede utilizar un objeto `ClipCaretRect` obtener el símbolo de intercalación ajustado (reducida) para asegurarse de que se ajuste a la región de recorte.  
  
 Objetos de crear un símbolo de intercalación deben enviar el rectángulo del símbolo de intercalación a `ClipCaretRect` y utilice el rectángulo ajustado para el símbolo de intercalación. Si el símbolo de intercalación se oculta por completo, este método devolverá **FALSE** y el símbolo de intercalación no debe mostrarse en absoluto en este caso.  
  
##  <a name="a-namecolecontrola--colecontrolcolecontrol"></a><a name="colecontrol"></a>COleControl::COleControl  
 Construye un objeto `COleControl`.  
  
```  
COleControl();
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente no se llama directamente a esta función. En su lugar el control OLE normalmente se crea mediante el generador de clases.  
  
##  <a name="a-namecontrolinfochangeda--colecontrolcontrolinfochanged"></a><a name="controlinfochanged"></a>COleControl::ControlInfoChanged  
 Llame a esta función cuando ha cambiado el conjunto de teclas de acceso admitidas por el control.  
  
```  
void ControlInfoChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Al recibir esta notificación, el contenedor del control obtiene el nuevo conjunto de teclas de acceso mediante una llamada a [IOleControl::GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730). Tenga en cuenta que el contenedor no es necesario para responder a esta notificación.  
  
##  <a name="a-namedisplayerrora--colecontroldisplayerror"></a><a name="displayerror"></a>COleControl::DisplayError  
 Llamado por el marco de trabajo cuando se ha controlado el evento de Error estándar (a menos que el controlador de eventos suprime la presentación del error).  
  
```  
virtual void DisplayError(
    SCODE scode,  
    LPCTSTR lpszDescription,  
    LPCTSTR lpszSource,  
    LPCTSTR lpszHelpFile,  
    UINT nHelpID);
```  
  
### <a name="parameters"></a>Parámetros  
 *SCODE*  
 El valor de código de estado que se notifiquen. Para obtener una lista completa de los posibles códigos, vea el artículo [controles ActiveX: temas avanzados](../../mfc/mfc-activex-controls-advanced-topics.md).  
  
 `lpszDescription`  
 La descripción del error que se va a notificar.  
  
 *lpszSource*  
 El nombre del módulo que se genera el error (normalmente, el nombre del módulo de control OLE).  
  
 `lpszHelpFile`  
 El nombre del archivo de ayuda que contiene una descripción del error.  
  
 `nHelpID`  
 La Ayuda de Id. de contexto del error que se va a notificar.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado muestra un cuadro de mensaje que contiene la descripción del error, incluido en `lpszDescription`.  
  
 Reemplazar esta función para personalizar cómo se muestran los errores.  
  
##  <a name="a-namedoclicka--colecontroldoclick"></a><a name="doclick"></a>COleControl::DoClick  
 Simula un mouse haga clic en la acción en el control.  
  
```  
void DoClick();
```  
  
### <a name="remarks"></a>Comentarios  
 El reemplazable `COleControl::OnClick` se llamará la función miembro y una acción, haga clic en eventos se desencadena si se admite el control.  
  
 Esta función es compatible con la `COleControl` clase base como un método estándar, denominado DoClick. Para obtener más información, vea el artículo [controles ActiveX: métodos](../../mfc/mfc-activex-controls-methods.md).  
  
##  <a name="a-namedopropexchangea--colecontroldopropexchange"></a><a name="dopropexchange"></a>COleControl:: DoPropExchange  
 Llamado por el marco al cargar o almacenar un control a partir de una representación de almacenamiento persistente, como un conjunto de secuencia o propiedad.  
  
```  
virtual void DoPropExchange(CPropExchange* pPX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Un puntero a un `CPropExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de propiedad, incluida su dirección.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esta función realiza llamadas a la **PX_** familia de funciones para cargar o almacenar propiedades específicas definidas por el usuario de un control OLE.  
  
 Si se ha utilizado el Asistente para controles para crear el proyecto de control OLE, la versión reemplazada de esta función serializará las propiedades estándar compatibles con `COleControl` con una llamada a la función de clase base, `COleControl::DoPropExchange`. Como agregar propiedades definidas por el usuario al control OLE debe modificar esta función para serializar las propiedades de nuevo. Para obtener más información sobre la serialización, vea el artículo [controles ActiveX: serializar](../../mfc/mfc-activex-controls-serializing.md).  
  
##  <a name="a-namedosuperclasspainta--colecontroldosuperclasspaint"></a><a name="dosuperclasspaint"></a>COleControl::DoSuperclassPaint  
 Vuelve a dibujar un control OLE que se ha derivado de un control de Windows.  
  
```  
void DoSuperclassPaint(
    CDC* pDC,  
    const CRect& rcBounds);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Un puntero al contexto de dispositivo del contenedor del control.  
  
 `rcBounds`  
 El área en la que se dibuja el control.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para controlar correctamente la representación de un control inactivo de OLE. Esta función sólo debe utilizarse si OLE controla subclases de un control de Windows y se debe llamar en el `OnDraw` función de su control.  
  
 Para obtener más información sobre esta función y la creación de subclases de un control de Windows, consulte el artículo [controles ActiveX: creación de subclases de un Control de Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
##  <a name="a-namedrawcontenta--colecontroldrawcontent"></a><a name="drawcontent"></a>COleControl::DrawContent  
 Llamado por el marco de trabajo cuando la apariencia del control debe actualizarse.  
  
```  
void DrawContent(
    CDC* pDC,  
    CRect& rc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de dispositivo.  
  
 `rc`  
 Área rectangular para dibujar en.  
  
### <a name="remarks"></a>Comentarios  
 Esta función llama directamente el reemplazable `OnDraw` (función).  
  
##  <a name="a-namedrawmetafilea--colecontroldrawmetafile"></a><a name="drawmetafile"></a>COleControl::DrawMetafile  
 Lo llama el marco de trabajo cuando se usa el contexto de dispositivo de metarchivo.  
  
```  
void DrawMetafile(
    CDC* pDC,  
    CRect& rc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de dispositivo de metarchivo.  
  
 `rc`  
 Área rectangular para dibujar en.  
  
##  <a name="a-nameenablesimpleframea--colecontrolenablesimpleframe"></a><a name="enablesimpleframe"></a>COleControl::EnableSimpleFrame  
 Habilita la característica de marco sencillo para un control OLE.  
  
```  
void EnableSimpleFrame();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta característica permite a un control admitir la contención visual de otros controles, pero no es verdad contención OLE. Un ejemplo sería con varios controles dentro de un cuadro de grupo. Estos controles no son OLE contenido, pero están en el mismo cuadro de grupo.  
  
##  <a name="a-nameexchangeextenta--colecontrolexchangeextent"></a><a name="exchangeextent"></a>COleControl::ExchangeExtent  
 Serializa o se inicializa el estado de extensión del control (sus dimensiones en **HIMETRIC** unidades).  
  
```  
BOOL ExchangeExtent(CPropExchange* pPX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Un puntero a un [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de propiedad, incluida su dirección.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la función se realiza correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama mediante la implementación predeterminada de `COleControl::DoPropExchange`.  
  
##  <a name="a-nameexchangestockpropsa--colecontrolexchangestockprops"></a><a name="exchangestockprops"></a>COleControl::ExchangeStockProps  
 Serializa o inicializa el estado de las propiedades estándar del control.  
  
```  
void ExchangeStockProps(CPropExchange* pPX);
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Un puntero a un [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de propiedad, incluida su dirección.  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama mediante la implementación predeterminada de `COleControl::DoPropExchange`.  
  
##  <a name="a-nameexchangeversiona--colecontrolexchangeversion"></a><a name="exchangeversion"></a>COleControl:: ExchangeVersion  
 Serializa o inicializa el estado de un control información de versión.  
  
```  
BOOL ExchangeVersion(
    CPropExchange* pPX,  
    DWORD dwVersionDefault,  
    BOOL bConvert = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pPX`  
 Un puntero a un `CPropExchange` objeto. El marco de trabajo proporciona este objeto para establecer el contexto del intercambio de propiedad, incluida su dirección.  
  
 `dwVersionDefault`  
 El número de versión actual del control.  
  
 `bConvert`  
 Indica si los datos persistentes deben convertirse al formato más reciente al guardar o mantener en el mismo formato que se cargó.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero de la función que se realiza correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, se trata de la primera función que llama a un reemplazo del control `COleControl::DoPropExchange`. Al cargar, esta función lee el número de versión de los datos persistentes y establece el atributo de versión de la [CPropExchange](../../mfc/reference/cpropexchange-class.md) objeto según corresponda. Al guardar, esta función escribe el número de versión de los datos persistentes.  
  
 Para obtener más información sobre la persistencia y el control de versiones, vea el artículo [controles ActiveX: serializar](../../mfc/mfc-activex-controls-serializing.md).  
  
##  <a name="a-namefireclicka--colecontrolfireclick"></a><a name="fireclick"></a>COleControl::FireClick  
 Lo llama el marco de trabajo al hacer clic con el mouse sobre un control activo.  
  
```  
void FireClick();
```  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Para la activación automática de un evento de clic que se produzcan, mapa de eventos del control debe tener una acción, haga clic en evento definido.  
  
##  <a name="a-namefiredblclicka--colecontrolfiredblclick"></a><a name="firedblclick"></a>COleControl::FireDblClick  
 Llamado por el marco cuando hace doble clic en el mouse sobre un control activo.  
  
```  
void FireDblClick();
```  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Para la activación automática de que se produzca un evento DblClick, mapa de eventos del control debe tener un evento DblClick estándar definido.  
  
##  <a name="a-namefireerrora--colecontrolfireerror"></a><a name="fireerror"></a>COleControl:: FireError  
 Se desencadena el evento de Error estándar.  
  
```  
void FireError(
    SCODE scode,  
    LPCTSTR lpszDescription,  
    UINT nHelpID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *SCODE*  
 El valor de código de estado que se notifiquen. Para obtener una lista completa de los posibles códigos, vea el artículo [controles ActiveX: temas avanzados](../../mfc/mfc-activex-controls-advanced-topics.md).  
  
 `lpszDescription`  
 La descripción del error que se va a notificar.  
  
 `nHelpID`  
 El identificador de Ayuda del error que se va a notificar.  
  
### <a name="remarks"></a>Comentarios  
 Este evento proporciona una manera de señalización en lugares apropiados en el código que se ha producido un error dentro del control. A diferencia de otros eventos estándar, como Click o MouseMove, Error nunca se activa por el marco de trabajo.  
  
 Para notificar un error que se produce durante una función get de propiedad, función de conjunto de propiedad o método de automatización, llame a [COleControl:: ThrowError](#throwerror).  
  
 La implementación de Stock Error de un control OLE evento usa un `SCODE` valor. Si el control utiliza este evento y está diseñado para usarse en Visual Basic 4.0, recibirá errores porque el `SCODE` valor no se admite en Visual Basic.  
  
 Para solucionar este problema, cambie manualmente el `SCODE` parámetro en el control. Archivo ODL a un **largo**. Además, cualquier evento personalizado, método o propiedad que utiliza un `SCODE` parámetro también hace que el mismo problema.  
  
##  <a name="a-namefireeventa--colecontrolfireevent"></a><a name="fireevent"></a>A COleControl:: FireEvent  
 Se desencadena un evento definido por el usuario desde el control con cualquier número de argumentos opcionales.  
  
```  
void AFX_CDECL FireEvent(
    DISPID dispid,  
    BYTE* pbParams,  
 ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 El identificador de envío del evento que se activa.  
  
 `pbParams`  
 Un descriptor de tipos de parámetro del evento.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente esta función no se debe llamar directamente. En su lugar, llamará a las funciones de desencadenamiento de eventos en la sección de asignación de eventos de la declaración de clase del control.  
  
 El `pbParams` argumento es una lista separada por espacios de **VTS_**. Uno o varios de estos valores, separados por espacios (no por comas), especifican la lista de parámetros de la función. Los valores posibles son los siguientes:  
  
|Símbolo|Tipo de parámetro|  
|------------|--------------------|  
|**VTS_COLOR**|**OLE_COLOR**|  
|**VTS_FONT**|**IFontDisp\***|  
|**VTS_HANDLE**|`HWND`|  
|**VTS_PICTURE**|**IPictureDisp\***|  
|**VTS_OPTEXCLUSIVE**|**OLE_OPTEXCLUSIVE\***|  
|**VTS_TRISTATE**|**OLE_TRISTATE**|  
|**VTS_XPOS_HIMETRIC**|**OLE_XPOS_HIMETRIC**|  
|**VTS_YPOS_HIMETRIC**|**OLE_YPOS_HIMETRIC**|  
|**VTS_XPOS_PIXELS**|**OLE_XPOS_PIXELS**|  
|**VTS_YPOS_PIXELS**|**OLE_YPOS_PIXELS**|  
|**VTS_XSIZE_PIXELS**|**OLE_XSIZE_PIXELS**|  
|**VTS_YSIZE_PIXELS**|**OLE_XSIZE_PIXELS**|  
|**VTS_XSIZE_HIMETRIC**|**OLE_XSIZE_HIMETRIC**|  
|**VTS_YSIZE_HIMETRIC**|**OLE_XSIZE_HIMETRIC**|  
  
> [!NOTE]
>  Constantes de tipo variant adicionales se han definido para todos los tipos variant, con la excepción de **VTS_FONT** y **VTS_PICTURE**, que proporciona un puntero a la constante de datos variant. Estas constantes se denominan utilizando la **VTS_P** `constantname` convención. Por ejemplo, **VTS_PCOLOR** es un puntero a un **VTS_COLOR** constante.  
  
##  <a name="a-namefirekeydowna--colecontrolfirekeydown"></a><a name="firekeydown"></a>COleControl::FireKeyDown  
 Llamado por el marco de trabajo cuando se presiona una tecla mientras el control está activo de la interfaz de usuario.  
  
```  
void FireKeyDown(
    USHORT* pnChar,  
    short nShiftState);
```  
  
### <a name="parameters"></a>Parámetros  
 `pnChar`  
 Puntero al valor de código de tecla virtual de la tecla presionada. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h  
  
 `nShiftState`  
 Contiene una combinación de los siguientes indicadores:  
  
- **SHIFT_MASK** se presionó la tecla MAYÚS durante la acción.  
  
- **CTRL_MASK** se presionó la tecla CTRL la durante la acción.  
  
- **ALT_MASK** se presionó la tecla ALT el durante la acción.  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Para la activación automática de que se produzca un evento KeyDown, mapa de eventos del control debe tener un evento KeyDown estándar definido.  
  
##  <a name="a-namefirekeypressa--colecontrolfirekeypress"></a><a name="firekeypress"></a>COleControl::FireKeyPress  
 Lo llama el marco de trabajo cuando se presiona una tecla y se suelta mientras el control personalizado está activo de interfaz de usuario dentro del contenedor.  
  
```  
void FireKeyPress(USHORT* pnChar);
```  
  
### <a name="parameters"></a>Parámetros  
 `pnChar`  
 Un puntero al valor de carácter de la tecla presionada.  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Puede modificar el receptor del evento `pnChar`, por ejemplo, convertir todos los caracteres en minúsculas a mayúsculas. Si desea examinar el carácter modificado, reemplazar `OnKeyPressEvent`.  
  
 Para la activación automática de que se produzca un evento KeyPress, mapa de eventos del control debe tener un evento KeyPress estándar definido.  
  
##  <a name="a-namefirekeyupa--colecontrolfirekeyup"></a><a name="firekeyup"></a>COleControl::FireKeyUp  
 Llamado por el marco de trabajo cuando se suelta una tecla mientras el control personalizado está activo de interfaz de usuario dentro del contenedor.  
  
```  
void FireKeyUp(
    USHORT* pnChar,  
    short nShiftState);
```  
  
### <a name="parameters"></a>Parámetros  
 `pnChar`  
 Puntero al valor de código de tecla virtual de la clave comercial. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h  
  
 `nShiftState`  
 Contiene una combinación de los siguientes indicadores:  
  
- **SHIFT_MASK** se presionó la tecla MAYÚS durante la acción.  
  
- **CTRL_MASK** se presionó la tecla CTRL la durante la acción.  
  
- **ALT_MASK** se presionó la tecla ALT el durante la acción.  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Para la activación automática de que se produzca un evento KeyUp, mapa de eventos del control debe tener un evento KeyUp estándar definido.  
  
##  <a name="a-namefiremousedowna--colecontrolfiremousedown"></a><a name="firemousedown"></a>COleControl::FireMouseDown  
 Lo llama el marco de trabajo cuando se presiona un botón del mouse sobre un control personalizado activo.  
  
```  
void FireMouseDown(
    short nButton,  
    short nShiftState,  
    OLE_XPOS_PIXELS x,  
    OLE_YPOS_PIXELS y);
```  
  
### <a name="parameters"></a>Parámetros  
 `nButton`  
 El valor numérico del botón del mouse se presionó. Puede contener uno de los siguientes valores:  
  
- **LEFT_BUTTON** se ha presionado el botón primario del mouse.  
  
- **MIDDLE_BUTTON** se ha presionado el botón central del mouse.  
  
- **RIGHT_BUTTON** se ha presionado el botón secundario del mouse.  
  
 `nShiftState`  
 Contiene una combinación de los siguientes indicadores:  
  
- **SHIFT_MASK** se presionó la tecla MAYÚS durante la acción.  
  
- **CTRL_MASK** se presionó la tecla CTRL la durante la acción.  
  
- **ALT_MASK** se presionó la tecla ALT el durante la acción.  
  
 *x*  
 Coordenada x del cursor cuando se presiona un botón del mouse. La coordenada es relativa a la esquina superior izquierda de la ventana de control.  
  
 *y*  
 Coordenada y del cursor cuando se presiona un botón del mouse. La coordenada es relativa a la esquina superior izquierda de la ventana de control.  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Para la activación automática de que se produzca un evento MouseDown, mapa de eventos del control debe tener un evento MouseDown estándar definido.  
  
##  <a name="a-namefiremousemovea--colecontrolfiremousemove"></a><a name="firemousemove"></a>COleControl::FireMouseMove  
 Lo llama el marco de trabajo cuando se mueve el cursor sobre un control personalizado activo.  
  
```  
void FireMouseMove(
    short nButton,  
    short nShiftState,  
    OLE_XPOS_PIXELS x,  
    OLE_YPOS_PIXELS y);
```  
  
### <a name="parameters"></a>Parámetros  
 `nButton`  
 El valor numérico de los botones del mouse se presionó. Contiene una combinación de los siguientes valores:  
  
- **LEFT_BUTTON** se ha presionado el botón primario del mouse durante la acción.  
  
- **MIDDLE_BUTTON** se ha presionado el botón central del mouse durante la acción.  
  
- **RIGHT_BUTTON** se ha presionado el botón secundario del mouse durante la acción.  
  
 `nShiftState`  
 Contiene una combinación de los siguientes indicadores:  
  
- **SHIFT_MASK** se presionó la tecla MAYÚS durante la acción.  
  
- **CTRL_MASK** se presionó la tecla CTRL la durante la acción.  
  
- **ALT_MASK** se presionó la tecla ALT el durante la acción.  
  
 *x*  
 Coordenada x del cursor. La coordenada es relativa a la esquina superior izquierda de la ventana de control.  
  
 *y*  
 Coordenada y del cursor. La coordenada es relativa a la esquina superior izquierda de la ventana de control.  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Para la activación automática de que se produzca un evento MouseMove, mapa de eventos del control debe tener un evento MouseMove estándar definido.  
  
##  <a name="a-namefiremouseupa--colecontrolfiremouseup"></a><a name="firemouseup"></a>COleControl::FireMouseUp  
 Lo llama el marco de trabajo cuando se suelta un botón del mouse sobre un control personalizado activo.  
  
```  
void FireMouseUp(
    short nButton,  
    short nShiftState,  
    OLE_XPOS_PIXELS x,  
    OLE_YPOS_PIXELS y);
```  
  
### <a name="parameters"></a>Parámetros  
 `nButton`  
 El valor numérico del botón del mouse liberado. Puede tener uno de los siguientes valores:  
  
- **LEFT_BUTTON** se soltó el botón primario del mouse.  
  
- **MIDDLE_BUTTON** se soltó el botón central del mouse.  
  
- **RIGHT_BUTTON** se soltó el botón secundario del mouse.  
  
 `nShiftState`  
 Contiene una combinación de los siguientes indicadores:  
  
- **SHIFT_MASK** se presionó la tecla MAYÚS durante la acción.  
  
- **CTRL_MASK** se presionó la tecla CTRL la durante la acción.  
  
- **ALT_MASK** se presionó la tecla ALT el durante la acción.  
  
 *x*  
 Coordenada x del cursor cuando se suelta un botón del mouse. La coordenada es relativa a la esquina superior izquierda de la ventana de control.  
  
 *y*  
 Coordenada y de un cursor cuando se suelta un botón del mouse. La coordenada es relativa a la esquina superior izquierda de la ventana de control.  
  
### <a name="remarks"></a>Comentarios  
 Si este evento se define como un evento personalizado, debe determinar cuándo se activa el evento.  
  
 Para la activación automática de que se produzca un evento MouseUp, mapa de eventos del control debe tener un evento MouseUp estándar definido.  
  
##  <a name="a-namefirereadystatechangea--colecontrolfirereadystatechange"></a><a name="firereadystatechange"></a>COleControl::FireReadyStateChange  
 Se desencadena un evento con el valor actual del estado del control de lista.  
  
```  
void FireReadyStateChange();
```  
  
### <a name="remarks"></a>Comentarios  
 El estado de preparado puede ser uno de los siguientes valores:  
  
 **READYSTATE_UNINITIALIZED**  
 Estado de inicialización predeterminado  
  
 **READYSTATE_LOADING**  
 Control está cargando sus propiedades  
  
 **READYSTATE_LOADED**  
 Se ha inicializado el control  
  
 **READYSTATE_INTERACTIVE**  
 Control tiene suficientes datos para ser interactiva, pero todavía se cargan asincrónicas no todos los datos  
  
 `READYSTATE_COMPLETE`  
 Control tiene todos sus datos  
  
 Utilice [GetReadyState](#getreadystate) para determinar la preparación del actual del control.  
  
 [Adecuado](#internalsetreadystate) cambia el estado listo para el valor proporcionado para, a continuación, llama a `FireReadyStateChange`.  
  
##  <a name="a-namegetactivationpolicya--colecontrolgetactivationpolicy"></a><a name="getactivationpolicy"></a>COleControl:: GetActivationPolicy  
 Modifica el comportamiento predeterminado de la activación de un control que admite el `IPointerInactive` interfaz.  
  
```  
virtual DWORD GetActivationPolicy();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de indicadores de la **POINTERINACTIVE** (enumeración). Los indicadores posibles son:  
  
 **POINTERINACTIVE_ACTIVATEONENTRY**  
 El objeto debe estar activado cuando entra en el mouse durante una operación de movimiento del mouse (ratón) en el contexto.  
  
 **POINTERINACTIVE_DEACTIVATEONLEAVE**  
 El objeto se debe desactivar cuando el mouse deja el objeto durante una operación de movimiento del mouse.  
  
 **POINTERINACTIVE_ACTIVATEONDRAG**  
 El objeto debe estar activado cuando se arrastra el mouse sobre él durante un arrastre en contexto y la operación de desactivación.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el `IPointerInactive` interfaz está habilitada, el contenedor delegará `WM_SETCURSOR` y `WM_MOUSEMOVE` mensajes a ella. `COleControl`de implementación de esta interfaz se encarga de enviar estos mensajes a través del mapa de mensajes del control, después de ajustar el mouse coordina adecuadamente.  
  
 Cuando el contenedor recibe un `WM_SETCURSOR` o `WM_MOUSEMOVE` mensaje con el puntero del mouse sobre un objeto inactivo admitir `IPointerInactive`, debe llamar a `GetActivationPolicy` en la interfaz y los indicadores de valor devueltos de la **POINTERINACTIVE** (enumeración).  
  
 Puede procesar estos mensajes como mensajes de ventanas ordinarios, agregando las entradas correspondientes al mapa de mensajes. En los controladores, evite utilizar el `m_hWnd` variable miembro (o a cualquier función miembro que usa) sin antes de comprobar si su valor es no es **NULL**.  
  
 Cualquier objeto pretende algo más que establecer el cursor del mouse o desencadenar un evento de movimiento del mouse, tales como proporcionar comentarios visuales especiales, deben devolver el **POINTERINACTIVE_ACTIVATEONENTRY** marcar y dibujar los comentarios sólo cuando está activo. Si el objeto devuelve esta marca, el contenedor debe activarlo en el lugar inmediatamente y reenviarlo el mismo mensaje que desencadenó la llamada a `GetActivationPolicy`.  
  
 Si tanto el **POINTERINACTIVE_ACTIVATEONENTRY** y **POINTERINACTIVE_DEACTIVATEONLEAVE** marcas se devuelven, a continuación, el objeto sólo se activará cuando el mouse está sobre el objeto. Si sólo el **POINTERINACTIVE_ACTIVATEONENTRY** marca se devuelve, a continuación, el objeto sólo se activará una vez cuando el mouse entra por primera vez el objeto.  
  
 También puede ser el destino de una OLE de arrastrar y colocar la operación de un control inactivo. Esto requiere activar el control en el momento en que el usuario arrastra un objeto sobre él, para que la ventana del control se puede registrar como un destino de colocación. Para que se produzca la activación se produzca durante un arrastre, devolver el **POINTERINACTIVE_ACTIVATEONDRAG** indicador:  
  
 [!code-cpp[1 NVC_MFCAxCtl](../../mfc/reference/codesnippet/cpp/colecontrol-class_1.cpp)]  
  
 Comunique la información `GetActivationPolicy` no deben almacenarse en caché por un contenedor. En su lugar, debe llamar a este método cada vez que el mouse entra en un objeto inactivo.  
  
 Si se activa cuando el mouse entra en ella en el contexto no solicita un objeto inactivo, el contenedor debe enviar posteriores `WM_SETCURSOR` mensajes a este objeto mediante una llamada a [OnInactiveSetCursor](#oninactivesetcursor) siempre y cuando el puntero del mouse permanece sobre el objeto.  
  
 Habilitar la `IPointerInactive` interfaz significa normalmente que desea que el control sea capaz de procesar mensajes del mouse en todo momento. Para obtener este comportamiento en un contenedor que no es compatible con la `IPointerInactive` interfaz, debe tener el control siempre activado cuando está visible, lo que significa que el control debe tener la **OLEMISC_ACTIVATEWHENVISIBLE** marca entre sus indicadores varios. Sin embargo, para evitar que esta marca de surten efecto en un contenedor que es compatible con `IPointerInactive`, también puede especificar el **OLEMISC_IGNOREACTIVATEWHENVISIBLE** indicador:  
  
 [!code-cpp[NVC_MFCAxCtl&#10;](../../mfc/reference/codesnippet/cpp/colecontrol-class_2.cpp)]  
  
##  <a name="a-namegetambientpropertya--colecontrolgetambientproperty"></a><a name="getambientproperty"></a>COleControl:: GetAmbientProperty  
 Obtiene el valor de una propiedad de ambiente del contenedor.  
  
```  
BOOL GetAmbientProperty(
    DISPID dispid,  
    VARTYPE vtProp,  
    void* pvProp);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDispid*  
 El identificador de envío de la propiedad de ambiente deseada.  
  
 `vtProp`  
 Una etiqueta de tipo variant que especifica el tipo del valor que se devuelve en `pvProp`.  
  
 `pvProp`  
 Puntero a la dirección de la variable que recibirá el valor de propiedad o valor devuelto. El tipo real de este puntero debe coincidir con el tipo especificado por `vtProp`.  
  
|vtProp|Tipo de pvProp|  
|------------|--------------------|  
|`VT_BOOL`|**BOOL\***|  
|`VT_BSTR`|**CString\***|  
|`VT_I2`|**breve\***|  
|`VT_I4`|**Long\***|  
|`VT_R4`|**float\***|  
|`VT_R8`|**doble\***|  
|`VT_CY`|**CY\***|  
|**VT_COLOR**|**OLE_COLOR\***|  
|**VT_DISPATCH**|**LPDISPATCH\***|  
|**VT_FONT**|**LPFONTDISP\***|  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se admite la propiedad de ambiente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si utiliza `GetAmbientProperty` para recuperar las propiedades de DisplayName y ScaleUnits ambientales, establezca `vtProp` a `VT_BSTR` y `pvProp` a **CString\***. Si va a recuperar la propiedad de fuente ambiente, establezca `vtProp` a **VT_FONT** y `pvProp` a **LPFONTDISP\***.  
  
 Tenga en cuenta que se ya han proporcionado funciones para las propiedades de ambientales comunes, como [AmbientBackColor](#ambientbackcolor) y [AmbientFont](#ambientfont).  
  
##  <a name="a-namegetappearancea--colecontrolgetappearance"></a><a name="getappearance"></a>COleControl::GetAppearance  
 Implementa la función Get de la propiedad de apariencia estándar del control.  
  
```  
short GetAppearance ();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto especifica el valor de aspecto actual como un **corto** ( `VT_I2`) valor si se realiza correctamente. Este valor es cero si la apariencia del control es plana y 1 si la apariencia del control es 3D.  
  
##  <a name="a-namegetbackcolora--colecontrolgetbackcolor"></a><a name="getbackcolor"></a>COleControl::GetBackColor  
 Implementa la función Get de la propiedad del control stock BackColor.  
  
```  
OLE_COLOR GetBackColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto especifica el color de fondo actual como un **OLE_COLOR** valor si se realiza correctamente. Este valor se puede traducir a una **COLORREF** valor con una llamada a `TranslateColor`.  
  
##  <a name="a-namegetborderstylea--colecontrolgetborderstyle"></a><a name="getborderstyle"></a>COleControl::GetBorderStyle  
 Implementa la función Get de la propiedad de estilo de borde estándar del control.  
  
```  
short GetBorderStyle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 1 si el control tiene un borde normal; 0 si el control no tiene ningún borde.  
  
##  <a name="a-namegetcapturea--colecontrolgetcapture"></a><a name="getcapture"></a>COleControl::GetCapture  
 Determina si la `COleControl` objeto tiene la captura del mouse.  
  
```  
CWnd* GetCapture();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el control está activado y sin ventanas, devuelve **esto** si el control tiene actualmente la captura del mouse (según lo determinado por el contenedor del control), o **NULL** si no tiene la captura.  
  
 De lo contrario, devuelve el `CWnd` objeto que tiene la captura del mouse (igual que `CWnd::GetCapture`).  
  
### <a name="remarks"></a>Comentarios  
 Un control sin ventana activado recibe el mouse al capturar [SetCapture](#setcapture) se llama.  
  
##  <a name="a-namegetclassida--colecontrolgetclassid"></a><a name="getclassid"></a>COleControl::GetClassID  
 Llamado por el marco de trabajo para recuperar el identificador de clase OLE del control.  
  
```  
virtual HRESULT GetClassID(LPCLSID pclsid) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pTypeInfo*  
 Puntero a la ubicación del identificador de clase.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la llamada no se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se implementa mediante el [IMPLEMENT_OLECREATE_EX](class-factories-and-licensing.md#implement_olecreate_ex).  
  
##  <a name="a-namegetclientoffseta--colecontrolgetclientoffset"></a><a name="getclientoffset"></a>COleControl::GetClientOffset  
 Recupera la diferencia entre la esquina superior izquierda del área rectangular del control y la esquina superior izquierda de su área cliente.  
  
```  
virtual void GetClientOffset(long* pdxOffset, long* pdyOffset) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pdxOffset*  
 Puntero al desplazamiento horizontal del área cliente del control OLE.  
  
 *pdyOffset*  
 Puntero al desplazamiento vertical del área cliente del control OLE.  
  
### <a name="remarks"></a>Comentarios  
 El control OLE tiene un área rectangular dentro de su contenedor. El área cliente del control es el área de control excepto los bordes y las barras de desplazamiento. Recupera el desplazamiento `GetClientOffset` es la diferencia entre la esquina superior izquierda del área rectangular del control y la esquina superior izquierda de su área cliente. Si el control tiene elementos no cliente distinto al estándares bordes y barras de desplazamiento, reemplazar esta función miembro para especificar el desplazamiento.  
  
##  <a name="a-namegetclientrecta--colecontrolgetclientrect"></a><a name="getclientrect"></a>COleControl::GetClientRect  
 Recupera el tamaño del área cliente del control.  
  
```  
virtual void GetClientRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Puntero a un `RECT` estructura que contiene las dimensiones del área cliente del control sin ventana; es decir, el tamaño del control menos los bordes de ventana, marcos, barras de desplazamiento y así sucesivamente. El `lpRect` parámetro indica el tamaño del rectángulo de cliente del control, no su posición.  
  
##  <a name="a-namegetclientsitea--colecontrolgetclientsite"></a><a name="getclientsite"></a>COleControl::GetClientSite  
 Consultas de un objeto para el puntero a su sitio de cliente actual dentro de su contenedor.  
  
```  
LPOLECLIENTSITE GetClientSite();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al sitio de cliente actual del control en su contenedor.  
  
### <a name="remarks"></a>Comentarios  
 El puntero devuelto apunta a una instancia de `IOleClientSite`. El `IOleClientSite` interfaz, implementada por contenedores, es la vista del objeto de contexto: donde que se fija en el documento, donde obtiene su almacenamiento, interfaz de usuario y otros recursos.  
  
##  <a name="a-namegetcontrolflagsa--colecontrolgetcontrolflags"></a><a name="getcontrolflags"></a>COleControl:: GetControlFlags  
 Recupera la configuración del indicador de control.  
  
```  
virtual DWORD GetControlFlags();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación ORed de las marcas de la enumeración ControlFlags:  
  
 `enum ControlFlags {`  
  
 `fastBeginPaint = 0x0001,`  
  
 `clipPaintDC = 0x0002,`  
  
 `pointerInactive = 0x0004,`  
  
 `noFlickerActivate = 0x0008,`  
  
 `windowlessActivate = 0x0010,`  
  
 `canOptimizeDraw = 0x0020,`  
  
 `};`  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `GetControlFlags` devuelve `fastBeginPaint | clipPaintDC`.  
  
 `fastBeginPaint`  
 Si establece, función usa un dibujo begin adaptada de controles OLE en lugar de la [BeginPaint](http://msdn.microsoft.com/library/windows/desktop/dd183362) API (establecida de forma predeterminada).  
  
 `clipPaintDC`  
 Si no se establece, se deshabilita la llamada a `IntersectClipRect` realizados por `COleControl` y una ventaja de velocidad. Si utiliza activación sin ventana, la marca no tiene efecto.  
  
 `pointerInactive`  
 Si establece, proporciona interacción con el mouse mientras el control está inactivo habilitando `COleControl`de implementación de la `IPointerInactive` interfaz, que está deshabilitado de forma predeterminada.  
  
 `noFlickerActivate`  
 Si establece, elimina las operaciones de dibujo adicionales y el parpadeo visual. Se utiliza cuando el control dibuja de forma idéntica en los Estados inactivos y activos. Si utiliza activación sin ventana, la marca no tiene efecto.  
  
 `windowlessActivate`  
 Si establece, indica que el control utiliza la activación sin ventana.  
  
 `canOptimizeDraw`  
 Si establece, indica que el control realizará dibujos optimizados, si lo admite el contenedor.  
  
 Para obtener más información acerca de `GetControlFlags` y otras optimizaciones de controles OLE, vea [controles ActiveX: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
##  <a name="a-namegetcontrolsizea--colecontrolgetcontrolsize"></a><a name="getcontrolsize"></a>COleControl::GetControlSize  
 Recupera el tamaño de la ventana de control OLE.  
  
```  
void GetControlSize(
    int* pcx,  
    int* pcy);
```  
  
### <a name="parameters"></a>Parámetros  
 *PCX*  
 Especifica el ancho del control en píxeles.  
  
 *PCY*  
 Especifica el alto del control en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que todas las coordenadas para ventanas de control son relativas a la esquina superior izquierda del control.  
  
##  <a name="a-namegetdca--colecontrolgetdc"></a><a name="getdc"></a>COleControl::GetDC  
 Se proporciona para un objeto sin ventanas para obtener una pantalla (o compatible) el contexto de dispositivo de su contenedor.  
  
```  
CDC* GetDC(
    LPCRECT lprcRect = NULL,
    DWORD dwFlags = OLEDC_PAINTBKGND);
```  
  
### <a name="parameters"></a>Parámetros  
 *lprcRect*  
 Un puntero al rectángulo el control sin ventana desea volver a dibujar, en coordenadas de cliente del control. **NULL** significa la extensión del objeto completo.  
  
 `dwFlags`  
 Atributos de dibujo del contexto de dispositivo. Las opciones son:  
  
- **OLEDC_NODRAW** indica que el objeto no utiliza el contexto de dispositivo para realizar cualquier acción de dibujo pero simplemente para obtener información sobre el dispositivo de pantalla. El contenedor debe pasar simplemente el controlador de dominio de la ventana sin más procesamiento.  
  
- **OLEDC_PAINTBKGND** solicita que el contenedor de pintar el fondo antes de devolver el controlador de dominio. Un objeto debe usar esta marca si solicita un controlador de dominio para volver a dibujar un área con fondo transparente.  
  
- **OLEDC_OFFSCREEN** informa el contenedor que el objeto que desea representar en un mapa de bits fuera de la pantalla que debe copiarse en la pantalla. Un objeto debe utilizar este indicador cuando está a punto de realizar la operación de dibujo genera mucha parpadeo. El contenedor está libre para atender esta solicitud o no. Sin embargo, si no se establece este marcador, el contenedor debe entregar una pantalla DC. Esto permite realizar operaciones directas de pantalla como mostrar una selección de objetos (a través de un **XOR** operación).  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al contexto de dispositivo de presentación para el contenedor `CWnd` área cliente si realiza correctamente; en caso contrario, el valor devuelto es **NULL**. El contexto de dispositivo de presentación se puede utilizar en otras funciones GDI para dibujar en el área de cliente de la ventana del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 El [ReleaseDC](#releasedc) función miembro debe llamarse para liberar el contexto después de haber. Al llamar a `GetDC`, los objetos pasan el rectángulo que deseen dibujar en sus propias en coordenadas de cliente. `GetDC`convierte a las coordenadas del área de cliente de contenedor. El objeto no debería solicitar un rectángulo de dibujo deseado mayor que su propio rectángulo del área de cliente, el tamaño de los cuales se puede recuperar con [GetClientRect](#getclientrect). Esto impide que accidentalmente dibujo donde no se supone que objetos.  
  
##  <a name="a-namegetenableda--colecontrolgetenabled"></a><a name="getenabled"></a>COleControl::GetEnabled  
 Implementa la función Get de propiedad Enabled en existencias del control.  
  
```  
BOOL GetEnabled();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el control está habilitado; en caso contrario, 0.  
  
##  <a name="a-namegetextendedcontrola--colecontrolgetextendedcontrol"></a><a name="getextendedcontrol"></a>COleControl::GetExtendedControl  
 Obtiene un puntero a un objeto mantenido por el contenedor que representa el control con un conjunto de propiedades extendido.  
  
```  
LPDISPATCH GetExtendedControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al contenedor de ampliar el objeto de control. Si no hay ningún objeto disponible, el valor es **NULL**.  
  
 Este objeto se puede manipular mediante su `IDispatch` interfaz. También puede usar `QueryInterface` para obtener otras interfaces disponibles proporcionados por el objeto. Sin embargo, no es necesario que el objeto admite un conjunto específico de interfaces. Tenga en cuenta que depender de las características específicas del objeto de control extendido de un contenedor limita la portabilidad del control a otros contenedores arbitrarios.  
  
### <a name="remarks"></a>Comentarios  
 La función que llama a esta función es responsable de liberar el puntero cuando haya terminado con el objeto. Tenga en cuenta que el contenedor no se requiere compatibilidad con este objeto.  
  
##  <a name="a-namegetfocusa--colecontrolgetfocus"></a><a name="getfocus"></a>COleControl::GetFocus  
 Determina si la `COleControl` objeto tiene el foco.  
  
```  
CWnd* GetFocus();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el control está activado y sin ventanas, devuelve **esto** si el control actualmente tiene el foco del teclado (según lo determinado por el contenedor del control), o **NULL** si no tiene el foco.  
  
 De lo contrario, devuelve el `CWnd` objeto que tiene el foco (igual que `CWnd::GetFocus`).  
  
### <a name="remarks"></a>Comentarios  
 Un control sin ventana activado recibe el foco cuando [SetFocus](#setfocus) se llama.  
  
##  <a name="a-namegetfonta--colecontrolgetfont"></a><a name="getfont"></a>COleControl::GetFont  
 Implementa la función Get de la propiedad Font estándar.  
  
```  
LPFONTDISP GetFont();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la interfaz de envío de la fuente de la propiedad Font estándar del control.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el llamador debe liberar el objeto cuando termine. En la implementación del control, utilice `InternalGetFont` para tener acceso a objetos de fuente estándar del control. Para obtener más información sobre el uso de fuentes en el control, vea el artículo [controles ActiveX: usar fuentes en un ActiveX Control](../../mfc/mfc-activex-controls-using-fonts.md).  
  
##  <a name="a-namegetfonttextmetricsa--colecontrolgetfonttextmetrics"></a><a name="getfonttextmetrics"></a>COleControl::GetFontTextMetrics  
 Mide las métricas de texto para cualquier `CFontHolder` objeto propiedad del control.  
  
```  
void GetFontTextMetrics(
    LPTEXTMETRIC lptm,  
    CFontHolder& fontHolder);
```  
  
### <a name="parameters"></a>Parámetros  
 `lptm`  
 Puntero a un [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura.  
  
 `fontHolder`  
 Hacer referencia a un [CFontHolder](../../mfc/reference/cfontholder-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta fuente se puede seleccionar con el [COleControl::SelectFontObject](#selectfontobject) (función). `GetFontTextMetrics`se inicializará la `TEXTMETRIC` estructura que señala `lptm` con información válida de métricas sobre `fontHolder`de fuente si es correcto o rellenar la estructura con ceros si no funciona correctamente. Debe utilizar esta función en lugar de [GetTextMetrics](http://msdn.microsoft.com/library/windows/desktop/dd144941) al dibujar el control porque los controles, como cualquier incrustado objeto OLE, pueden ser necesario para representarse a sí mismos en un metarchivo.  
  
 El `TEXTMETRIC` estructura de la fuente predeterminada es cuando actualiza el [SelectFontObject](#selectfontobject) se llama la función. Debe llamar a `GetFontTextMetrics` sólo después de seleccionar la propiedad Font estándar para asegurar la información que proporciona es válido.  
  
##  <a name="a-namegetforecolora--colecontrolgetforecolor"></a><a name="getforecolor"></a>COleControl::GetForeColor  
 Implementa la función Get de la propiedad ForeColor estándar.  
  
```  
OLE_COLOR GetForeColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto especifica el color de primer plano actual como un **OLE_COLOR** valor si se realiza correctamente. Este valor se puede traducir a una [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor con una llamada a `TranslateColor`.  
  
##  <a name="a-namegethwnda--colecontrolgethwnd"></a><a name="gethwnd"></a>COleControl::GetHwnd  
 Implementa la función Get de la propiedad hWnd stock.  
  
```  
OLE_HANDLE GetHwnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de ventana del control OLE, si lo hay; de lo contrario, **NULL**.  
  
##  <a name="a-namegetmessagestringa--colecontrolgetmessagestring"></a><a name="getmessagestring"></a>COleControl::GetMessageString  
 Llamado por el marco para obtener una cadena breve que describe el propósito del elemento de menú identificado por `nID`.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Un identificador de elemento de menú.  
  
 `rMessage`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que se devolverá una cadena.  
  
### <a name="remarks"></a>Comentarios  
 Esto puede utilizarse para obtener un mensaje para su presentación en una barra de estado mientras se resalta el elemento de menú. La implementación predeterminada intenta cargar un recurso de cadena identificado por `nID`.  
  
##  <a name="a-namegetnotsupporteda--colecontrolgetnotsupported"></a><a name="getnotsupported"></a>COleControl::GetNotSupported  
 Impide el acceso al valor de propiedad de un control por el usuario.  
  
```  
void GetNotSupported();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función en lugar de la función Get de cualquier propiedad que no se admite la recuperación de la propiedad por el usuario del control. Un ejemplo sería una propiedad de sólo escritura.  
  
##  <a name="a-namegetreadystatea--colecontrolgetreadystate"></a><a name="getreadystate"></a>COleControl::GetReadyState  
 Devuelve el estado de preparación del control.  
  
```  
long GetReadyState();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de preparación del control, uno de los siguientes valores:  
  
 **READYSTATE_UNINITIALIZED**  
 Estado de inicialización predeterminado  
  
 **READYSTATE_LOADING**  
 Control está cargando sus propiedades  
  
 **READYSTATE_LOADED**  
 Se ha inicializado el control  
  
 **READYSTATE_INTERACTIVE**  
 Control tiene suficientes datos para ser interactiva, pero todavía se cargan asincrónicas no todos los datos  
  
 `READYSTATE_COMPLETE`  
 Control tiene todos sus datos  
  
### <a name="remarks"></a>Comentarios  
 La mayoría de los controles simples nunca necesitan diferenciar **LOADED** y `INTERACTIVE`. Sin embargo, los controles que admiten propiedades de ruta de acceso de datos pueden no estar preparados ser interactiva, hasta que se reciben al menos algunos datos de forma asincrónica. Un control debe intentar vuelve interactiva tan pronto como sea posible.  
  
##  <a name="a-namegetrectincontainera--colecontrolgetrectincontainer"></a><a name="getrectincontainer"></a>COleControl::GetRectInContainer  
 Obtiene las coordenadas del rectángulo del control en relación con el contenedor, expresado en unidades del dispositivo.  
  
```  
BOOL GetRectInContainer(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Puntero a la estructura de rectángulo en el que se copiarán las coordenadas del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control está activo en contexto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El rectángulo sólo es válido si el control está activo en contexto.  
  
##  <a name="a-namegetstocktextmetricsa--colecontrolgetstocktextmetrics"></a><a name="getstocktextmetrics"></a>COleControl::GetStockTextMetrics  
 Mide las métricas de texto de la propiedad Font estándar del control, que se puede seleccionar con el [SelectStockFont](#selectstockfont) (función).  
  
```  
void GetStockTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>Parámetros  
 `lptm`  
 Un puntero a un [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) estructura.  
  
### <a name="remarks"></a>Comentarios  
 El `GetStockTextMetrics` función inicializará el `TEXTMETRIC` estructura apuntada por `lptm` con información de métricas válido si se realiza correctamente o relleno de la estructura con ceros si no funciona correctamente. Use esta función en lugar de [GetTextMetrics](http://msdn.microsoft.com/library/windows/desktop/dd144941) al dibujar el control porque los controles, como cualquier incrustado objeto OLE, pueden ser necesario para representarse a sí mismos en un metarchivo.  
  
 El `TEXTMETRIC` estructura de la fuente predeterminada es cuando actualiza el `SelectStockFont` se llama la función. Esta función se debe llamar después de seleccionar la fuente para asegurar la información que proporciona cotizaciones es válido.  
  
##  <a name="a-namegettexta--colecontrolgettext"></a><a name="gettext"></a>COleControl::GetText  
 Implementa la función Get de la propiedad de título o de texto estándar.  
  
```  
BSTR GetText();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor actual de la cadena de texto del control o una cadena de longitud cero si no hay ninguna cadena.  
  
> [!NOTE]
>  Para obtener más información sobre la `BSTR` tipo de datos, consulte [tipos de datos](../../mfc/reference/data-types-mfc.md) en la sección de Macros y funciones globales.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el llamador de esta función debe llamar a `SysFreeString` en la cadena devuelta para gratis el recurso. En la implementación del control, utilice `InternalGetText` para tener acceso a las propiedades estándar de texto o el título del control.  
  
##  <a name="a-namegetwindowlessdroptargeta--colecontrolgetwindowlessdroptarget"></a><a name="getwindowlessdroptarget"></a>COleControl:: GetWindowlessDropTarget  
 Invalidar `GetWindowlessDropTarget` cuando desee un control sin ventana sea el destino de una OLE operación arrastrar y colocar.  
  
```  
virtual IDropTarget* GetWindowlessDropTarget();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al objeto `IDropTarget` interfaz. Puesto que no tiene una ventana, no se puede registrar un objeto sin ventanas una `IDropTarget` interfaz. Sin embargo, para participar en arrastrar y colocar, un objeto sin ventanas puede aún implementan la interfaz y devolverlo en `GetWindowlessDropTarget`.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esto requeriría que la ventana del control registrarse como un destino de colocación. Pero dado que el control no dispone de su propio, el contenedor utilizará su propia ventana como un destino de colocación. El control simplemente tiene que proporcionar una implementación de la `IDropTarget` interfaz a la que el contenedor puede delegar llamadas en el momento adecuado. Por ejemplo:  
  
 [!code-cpp[NVC_MFCAxCtl&#2;](../../mfc/reference/codesnippet/cpp/colecontrol-class_3.cpp)]  
  
##  <a name="a-nameinitializeiidsa--colecontrolinitializeiids"></a><a name="initializeiids"></a>COleControl::InitializeIIDs  
 Informa a la clase base de los IID usará el control.  
  
```  
void InitializeIIDs(
    const IID* piidPrimary,
    const IID* piidEvents);
```  
  
### <a name="parameters"></a>Parámetros  
 *piidPrimary*  
 Puntero al identificador de interfaz de la interfaz de envío principal del control.  
  
 *piidEvents*  
 Puntero al identificador de interfaz de la interfaz de eventos del control.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función en el constructor del control para informar a la clase base de los identificadores que se va a utilizar el control de interfaz.  
  
##  <a name="a-nameinternalgetfonta--colecontrolinternalgetfont"></a><a name="internalgetfont"></a>COleControl::InternalGetFont  
 Tiene acceso a la propiedad Font estándar del control  
  
```  
CFontHolder& InternalGetFont();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un [CFontHolder](../../mfc/reference/cfontholder-class.md) objeto que contiene el objeto de fuente estándar.  
  
##  <a name="a-nameinternalgettexta--colecontrolinternalgettext"></a><a name="internalgettext"></a>COleControl::InternalGetText  
 Tiene acceso a la propiedad Text o Caption estándar del control.  
  
```  
const CString& InternalGetText();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la cadena de texto del control.  
  
##  <a name="a-nameinternalsetreadystatea--colecontrolinternalsetreadystate"></a><a name="internalsetreadystate"></a>COleControl:: InternalSetReadyState  
 Establece el estado de preparación del control.  
  
```  
void InternalSetReadyState(long lNewReadyState);
```  
  
### <a name="parameters"></a>Parámetros  
 *lNewReadyState*  
 El estado de preparación para establecer para el control, uno de los siguientes valores:  
  
 **READYSTATE_UNINITIALIZED**  
 Estado de inicialización predeterminado  
  
 **READYSTATE_LOADING**  
 Control está cargando sus propiedades  
  
 **READYSTATE_LOADED**  
 Se ha inicializado el control  
  
 **READYSTATE_INTERACTIVE**  
 Control tiene suficientes datos para ser interactiva, pero todavía se cargan asincrónicas no todos los datos  
  
 `READYSTATE_COMPLETE`  
 Control tiene todos sus datos  
  
### <a name="remarks"></a>Comentarios  
 La mayoría de los controles simples nunca necesitan diferenciar **LOADED** y `INTERACTIVE`. Sin embargo, los controles que admiten propiedades de ruta de acceso de datos pueden no estar preparados ser interactiva, hasta que se reciben al menos algunos datos de forma asincrónica. Un control debe intentar vuelve interactiva tan pronto como sea posible.  
  
##  <a name="a-nameinvalidatecontrola--colecontrolinvalidatecontrol"></a><a name="invalidatecontrol"></a>COleControl::InvalidateControl  
 Obliga al control a dibujarse.  
  
```  
void InvalidateControl(
    LPCRECT lpRect = NULL,  
    BOOL bErase = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Puntero a la región del control que se va a invalidar.  
  
 `bErase`  
 Especifica si el fondo dentro de la región de actualización se eliminará cuando se procesa la región de actualización.  
  
### <a name="remarks"></a>Comentarios  
 Si `lpRect` tiene un **NULL** valor, se volverá a dibujar todo el control. Si `lpRect` no **NULL**, esto indica que la parte del rectángulo del control que se va a invalidar. En casos donde el control no tiene ninguna ventana o no está actualmente activo, el rectángulo se omite y se realiza una llamada en el sitio de cliente [IAdviseSink:: OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337) función miembro. Use esta función en lugar de `CWnd::InvalidateRect` o `InvalidateRect`.  
  
##  <a name="a-nameinvalidatergna--colecontrolinvalidatergn"></a><a name="invalidatergn"></a>COleControl::InvalidateRgn  
 Invalida el área de cliente de la ventana de contenedor dentro de la región.  
  
```  
void InvalidateRgn(CRgn* pRgn, BOOL bErase = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRgn`  
 Un puntero a un [CRgn](../../mfc/reference/crgn-class.md) objeto que identifica el área de presentación del objeto OLE para invalidar, en coordenadas de cliente de la ventana contenedora. Si este parámetro es **NULL**, la extensión es el objeto completo.  
  
 `bErase`  
 Especifica si se puede borrar el fondo dentro de la región invalidada. Si **TRUE**, se borra el fondo. Si **FALSE**, el fondo permanece sin cambios.  
  
### <a name="remarks"></a>Comentarios  
 Esto puede utilizarse para volver a dibujar los controles sin ventana dentro del contenedor. El área invalidada, junto con todas las demás áreas en la región de actualización está marcado para pintar cuando el siguiente [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) envía el mensaje.  
  
 Si `bErase` es **TRUE** en cualquier parte de la región de actualización, se borra el fondo de toda la región, no sólo en un artículo determinado.  
  
##  <a name="a-nameisconvertingvbxa--colecontrolisconvertingvbx"></a><a name="isconvertingvbx"></a>COleControl::IsConvertingVBX  
 Permite cargar especializada de un control OLE.  
  
```  
BOOL IsConvertingVBX();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el control que se va a convertir; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Al convertir un formulario que utiliza VBX controles a una que usa controles OLE, código de carga especial para los controles OLE puede ser necesario. Por ejemplo, si va a cargar una instancia del control OLE, podría tener una llamada a [PX_Font](persistence-of-ole-controls.md#px_font) en su `DoPropExchange`:  
  
 [!code-cpp[NVC_MFCAxCtl&3;](../../mfc/reference/codesnippet/cpp/colecontrol-class_4.cpp)]  
  
 Sin embargo, los controles VBX no tenía un objeto Font; cada propiedad de fuente se guarda por separado. En este caso, usaría `IsConvertingVBX` para distinguir entre estos dos casos:  
  
 [!code-cpp[NVC_MFCAxCtl Nº&4;](../../mfc/reference/codesnippet/cpp/colecontrol-class_5.cpp)]  
  
 Otro caso sería si el control VBX guarda los datos de propiedad binarios (en su **VBM_SAVEPROPERTY** controlador de mensajes), y el control OLE guarda datos binarios en un formato diferente. Si desea que el control OLE sea compatible con el control VBX, puede leer los formatos antiguos y nuevos con el `IsConvertingVBX` función distinguir si se cargó el control VBX o el control OLE.  
  
 En el control `DoPropExchange` función, puede comprobar esta condición y si es true, ejecutar código de carga específico para esta conversión (por ejemplo, los ejemplos anteriores). Si no se va a convertir el control, puede ejecutar código de carga normal. Esta capacidad sólo es aplicable a los controles que se está convirtiendo de homólogos VBX.  
  
##  <a name="a-nameisinvokealloweda--colecontrolisinvokeallowed"></a><a name="isinvokeallowed"></a>COleControl::IsInvokeAllowed  
 Permite la invocación del método de automatización.  
  
```  
BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha inicializado el control; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Implementación del marco de trabajo de **IDispatch:: Invoke** llamadas **IsInvokeAllowed** para determinar si una función determinada (identificado por `dispid`) pueden invocar. El comportamiento predeterminado para un control OLE es permitir que los métodos de automatización se invoca sólo si se ha inicializado el control; Sin embargo, **IsInvokeAllowed** es una función virtual y puede reemplazarse si es necesario (por ejemplo, cuando el control se está usando como un servidor de automatización). Para obtener más información, consulte el artículo de Knowledge Base Q166472, "Cómo: usar un Control OLE como un servidor de automatización." Artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="a-nameismodifieda--colecontrolismodified"></a><a name="ismodified"></a>COleControl::IsModified  
 Determina si se ha modificado el estado del control.  
  
```  
BOOL IsModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el estado del control se ha modificado desde que se guardó por última vez; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Se modifica el estado de un control cuando una propiedad cambia de valor.  
  
##  <a name="a-nameisoptimizeddrawa--colecontrolisoptimizeddraw"></a><a name="isoptimizeddraw"></a>COleControl::IsOptimizedDraw  
 Determina si el contenedor admite dibujos optimizados para la operación de dibujo actual.  
  
```  
BOOL IsOptimizedDraw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el contenedor admite optimizada de dibujo para la operación de dibujo actual; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Si no se admiten dibujos optimizados, a continuación, el control necesita selecciona objetos antiguos (lápices, pinceles, fuentes, etc.) en el contexto de dispositivo cuando finaliza el dibujo.  
  
##  <a name="a-nameissubclassedcontrola--colecontrolissubclassedcontrol"></a><a name="issubclassedcontrol"></a>COleControl::IsSubclassedControl  
 Llamado por el marco de trabajo para determinar si el control las subclases de control de Windows.  
  
```  
virtual BOOL IsSubclassedControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el control es una subclase; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe reemplazar esta función y devolver **TRUE** si OLE control subclases de un control de Windows.  
  
##  <a name="a-nameloada--colecontrolload"></a><a name="load"></a>COleControl::Load  
 Cargado de forma asincrónica de los datos anteriores se restablece y se inicia una nueva carga de la propiedad del control asincrónico.  
  
```  
void Load(LPCTSTR strNewPath, CDataPathProperty& prop);
```  
  
### <a name="parameters"></a>Parámetros  
 *strNewPath*  
 Puntero a una cadena que contiene la ruta de acceso a la que hace referencia a la ubicación absoluta de la propiedad de control asincrónico.  
  
 *Prop*  
 Un [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) objeto que implementa una propiedad de control asincrónico.  
  
##  <a name="a-namelockinplaceactivea--colecontrollockinplaceactive"></a><a name="lockinplaceactive"></a>COleControl::LockInPlaceActive  
 Impide que el contenedor de desactivar el control.  
  
```  
BOOL LockInPlaceActive(BOOL bLock);
```  
  
### <a name="parameters"></a>Parámetros  
 `bLock`  
 **TRUE** si el estado activo en el contexto del control es que se bloquee; **FALSE** si se va a desbloquear.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el bloqueo se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que cada bloqueo del control debe estar emparejado con un desbloqueo del control cuando termine. Sólo debe bloquear el control durante breves períodos, como al desencadenar un evento.  
  
##  <a name="a-nameonambientpropertychangea--colecontrolonambientpropertychange"></a><a name="onambientpropertychange"></a>COleControl::OnAmbientPropertyChange  
 Llamado por el marco de trabajo cuando una propiedad de ambiente del contenedor ha cambiado el valor.  
  
```  
virtual void OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>Parámetros  
 *dispID*  
 El identificador de envío de la propiedad de ambiente que cambió, o **DISPID_UNKNOWN** si han cambiado varias propiedades.  
  
##  <a name="a-nameonappearancechangeda--colecontrolonappearancechanged"></a><a name="onappearancechanged"></a>COleControl::OnAppearanceChanged  
 Llamado por el marco cuando ha cambiado el valor de propiedad de apariencia estándar.  
  
```  
virtual void OnAppearanceChanged ();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea notificación después de los cambios de esta propiedad. La implementación predeterminada llama `InvalidateControl`.  
  
##  <a name="a-nameonbackcolorchangeda--colecontrolonbackcolorchanged"></a><a name="onbackcolorchanged"></a>COleControl::OnBackColorChanged  
 Llamado por el marco cuando ha cambiado el valor de propiedad BackColor existencias.  
  
```  
virtual void OnBackColorChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea notificación después de los cambios de esta propiedad. La implementación predeterminada llama `InvalidateControl`.  
  
##  <a name="a-nameonborderstylechangeda--colecontrolonborderstylechanged"></a><a name="onborderstylechanged"></a>COleControl::OnBorderStyleChanged  
 Llamado por el marco de trabajo cuando ha cambiado el valor de propiedad de estilo de borde estándar.  
  
```  
virtual void OnBorderStyleChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `InvalidateControl`.  
  
 Reemplace esta función si desea notificación después de los cambios de esta propiedad.  
  
##  <a name="a-nameonclicka--colecontrolonclick"></a><a name="onclick"></a>COleControl::OnClick  
 Llamado por el marco de trabajo cuando se ha presionado un botón del mouse o se ha invocado el método de reserva DoClick.  
  
```  
virtual void OnClick(USHORT iButton);
```  
  
### <a name="parameters"></a>Parámetros  
 *iButton*  
 Índice de un botón del mouse. Puede tener uno de los siguientes valores:  
  
- **LEFT_BUTTON** se hizo clic con el botón primario del mouse.  
  
- **MIDDLE_BUTTON** se hizo clic con el botón central del mouse.  
  
- **RIGHT_BUTTON** se hizo clic con el botón secundario del mouse.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `COleControl::FireClick`.  
  
 Reemplace esta función miembro para modificar o extender el control predeterminado.  
  
##  <a name="a-nameonclosea--colecontrolonclose"></a><a name="onclose"></a>COleControl::OnClose  
 Llamado por el marco de trabajo cuando el contenedor denomina el control **IOleControl:: Close** (función).  
  
```  
virtual void OnClose(DWORD dwSaveOption);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwSaveOption`  
 Marca que indica si el objeto debe guardarse antes de la carga. Los valores válidos son:  
  
- `OLECLOSE_SAVEIFDIRTY`  
  
- `OLECLOSE_NOSAVE`  
  
- `OLECLOSE_PROMPTSAVE`  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `OnClose` guarda el objeto de control si se ha modificado y `dwSaveOption` sea `OLECLOSE_SAVEIFDIRTY` o `OLECLOSE_PROMPTSAVE`.  
  
##  <a name="a-nameondoverba--colecontrolondoverb"></a><a name="ondoverb"></a>COleControl::OnDoVerb  
 Llamado por el marco de trabajo cuando el contenedor llama el **DoVerb** función miembro.  
  
```  
virtual BOOL OnDoVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `iVerb`  
 El índice del verbo de control que se debe invocar.  
  
 `lpMsg`  
 Un puntero al mensaje de Windows que causó el verbo que se invocará.  
  
 `hWndParent`  
 El identificador de la ventana primaria del control. Si la ejecución del verbo crea una ventana (o windows), `hWndParent` debe utilizarse como el elemento primario.  
  
 `lpRect`  
 Puntero a una estructura RECT en la que se van a copiar las coordenadas del control, en relación con el contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la llamada se realiza correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada usa la `ON_OLEVERB` y `ON_STDOLEVERB` entradas de mapa para determinar la función apropiada para invocar de mensajes.  
  
 Reemplazar esta función para cambiar el control predeterminado del verbo.  
  
##  <a name="a-nameondrawa--colecontrolondraw"></a><a name="ondraw"></a>COleControl:: OnDraw  
 Llamado por el marco para dibujar el control OLE en el rectángulo delimitador especificado utilizando el contexto de dispositivo especificado.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rcBounds,  
    const CRect& rcInvalid);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 El contexto de dispositivo en el que se produce el dibujo.  
  
 `rcBounds`  
 El área rectangular del control, incluidos el borde.  
  
 `rcInvalid`  
 El área rectangular del control que no es válido.  
  
### <a name="remarks"></a>Comentarios  
 `OnDraw`Normalmente, se llama para presentación en pantalla, pasando un contexto de dispositivo de pantalla como `pDC`. El `rcBounds` parámetro identifica el rectángulo en el contexto de dispositivo de destino (con respecto a su modo de asignación actual). El `rcInvalid` parámetro es el rectángulo real que no es válido. En algunos casos se trata de un área menor que `rcBounds`.  
  
##  <a name="a-nameondrawmetafilea--colecontrolondrawmetafile"></a><a name="ondrawmetafile"></a>COleControl:: OnDrawMetafile  
 Llamado por el marco para dibujar el control OLE en el rectángulo delimitador especificado utilizando el contexto de dispositivo de metarchivo.  
  
```  
virtual void OnDrawMetafile(
    CDC* pDC,  
    const CRect& rcBounds);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 El contexto de dispositivo en el que se produce el dibujo.  
  
 `rcBounds`  
 El área rectangular del control, incluidos el borde.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama el [OnDraw](#ondraw) (función).  
  
##  <a name="a-nameonedita--colecontrolonedit"></a><a name="onedit"></a>COleControl::OnEdit  
 Hace que el control se activa de la interfaz de usuario.  
  
```  
virtual BOOL OnEdit(
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMsg`  
 Un puntero al mensaje de Windows que invocó el verbo.  
  
 `hWndParent`  
 Identificador de la ventana primaria del control.  
  
 `lpRect`  
 Puntero al rectángulo utilizado por el control en el contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la llamada se realiza correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto tiene el mismo efecto que invocar el control `OLEIVERB_UIACTIVATE` verbo.  
  
 Esta función se utiliza normalmente como la función de controlador para un `ON_OLEVERB` entrada del mapa de mensajes. Esto hace que un verbo "Edit" disponible en el menú del control "Objeto". Por ejemplo:  
  
 [!code-cpp[NVC_MFCAxCtl&#5;](../../mfc/reference/codesnippet/cpp/colecontrol-class_6.cpp)]  
  
##  <a name="a-nameonenabledchangeda--colecontrolonenabledchanged"></a><a name="onenabledchanged"></a>COleControl::OnEnabledChanged  
 Llamado por el marco de trabajo cuando ha cambiado el valor de la propiedad Enabled del material.  
  
```  
virtual void OnEnabledChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea notificación después de los cambios de esta propiedad. La implementación predeterminada llama [InvalidateControl](#invalidatecontrol).  
  
##  <a name="a-nameonenumverbsa--colecontrolonenumverbs"></a><a name="onenumverbs"></a>COleControl::OnEnumVerbs  
 Llamado por el marco de trabajo cuando el contenedor llama el **IOleObject:: EnumVerbs** función miembro.  
  
```  
virtual BOOL OnEnumVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppenumOleVerb`  
 Un puntero a la **IEnumOLEVERB** objeto que enumera los verbos del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si verbos disponibles; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada enumera el `ON_OLEVERB` entradas del mapa de mensajes.  
  
 Reemplazar esta función para cambiar el modo predeterminado de la enumeración de verbos.  
  
##  <a name="a-nameoneventadvisea--colecontroloneventadvise"></a><a name="oneventadvise"></a>COleControl::OnEventAdvise  
 Lo llama el marco de trabajo cuando está conectado a un controlador de eventos o se desconecta un control OLE.  
  
```  
virtual void OnEventAdvise(BOOL bAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAdvise`  
 **TRUE** indica que un controlador de eventos se ha conectado al control. **FALSE** indica que se ha desconectado un controlador de eventos del control.  
  
##  <a name="a-nameonfontchangeda--colecontrolonfontchanged"></a><a name="onfontchanged"></a>COleControl::OnFontChanged  
 Llamado por el marco de trabajo cuando ha cambiado el valor de la propiedad Font estándar.  
  
```  
virtual void OnFontChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `COleControl::InvalidateControl`. Si el control es crear subclases de un control de Windows, la implementación predeterminada también envía una **WM_SETFONT** mensaje a la ventana del control.  
  
 Reemplace esta función si desea notificación después de los cambios de esta propiedad.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAxCtl Nº&6;](../../mfc/reference/codesnippet/cpp/colecontrol-class_7.cpp)]  
  
##  <a name="a-nameonforecolorchangeda--colecontrolonforecolorchanged"></a><a name="onforecolorchanged"></a>COleControl::OnForeColorChanged  
 Llamado por el marco cuando ha cambiado el valor de propiedad ForeColor existencias.  
  
```  
virtual void OnForeColorChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `InvalidateControl`.  
  
 Reemplace esta función si desea notificación después de los cambios de esta propiedad.  
  
##  <a name="a-nameonfreezeeventsa--colecontrolonfreezeevents"></a><a name="onfreezeevents"></a>COleControl::OnFreezeEvents  
 Llamado por el marco después de las llamadas de contenedor **IOleControl::FreezeEvents**.  
  
```  
virtual void OnFreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parámetros  
 `bFreeze`  
 **TRUE** si el control control de eventos está inmovilizada; de lo contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada.  
  
 Reemplace esta función si desea un comportamiento adicional al control de eventos está inmovilizado o inmovilizado.  
  
##  <a name="a-nameongetcolorseta--colecontrolongetcolorset"></a><a name="ongetcolorset"></a>COleControl::OnGetColorSet  
 Llamado por el marco de trabajo cuando el contenedor llama el **IViewObject::GetColorSet** función miembro.  
  
```  
virtual BOOL OnGetColorSet(
    DVTARGETDEVICE* ptd,  
    HDC hicTargetDev,  
    LPLOGPALETTE* ppColorSet);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptd`  
 Señala al dispositivo de destino para el que se debe representar la imagen. Si este valor es **NULL**, se debe representar la imagen para un dispositivo de destino predeterminado, normalmente un dispositivo de pantalla.  
  
 `hicTargetDev`  
 Especifica el contexto de información en el dispositivo de destino indicado por `ptd`. Este parámetro puede ser un contexto de dispositivo, pero no es necesariamente. If `ptd` is **NULL**, `hicTargetDev` should also be **NULL**.  
  
 *ppColorSet*  
 Puntero a la ubicación en la que debe copiarse el conjunto de colores que se usará. Si la función no devuelve el conjunto de colores, **NULL** se devuelve.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se devuelve un conjunto de colores válidos; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El contenedor llama a esta función para obtener todos los colores necesarios para dibujar el control OLE. El contenedor puede usar los conjuntos de color obtenidos junto con los colores que necesita para establecer la paleta de colores general. La implementación predeterminada devuelve **FALSE**.  
  
 Reemplazar esta función para realizar cualquier procesamiento especial de esta solicitud.  
  
##  <a name="a-nameongetcontrolinfoa--colecontrolongetcontrolinfo"></a><a name="ongetcontrolinfo"></a>COleControl::OnGetControlInfo  
 Llamado por el marco de trabajo cuando el contenedor del control ha solicitado información sobre el control.  
  
```  
virtual void OnGetControlInfo(LPCONTROLINFO pControlInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pControlInfo`  
 Puntero a un [CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734) estructura que deben rellenarse.  
  
### <a name="remarks"></a>Comentarios  
 Esta información está formado principalmente por una descripción de las teclas de acceso del control. Los rellenos de implementación predeterminado `pControlInfo` con información predeterminada.  
  
 Reemplace esta función si el control debe procesar teclas de acceso.  
  
##  <a name="a-nameongetdisplaystringa--colecontrolongetdisplaystring"></a><a name="ongetdisplaystring"></a>COleControl::OnGetDisplayString  
 Llamado por el marco para obtener una cadena que representa el valor actual de la propiedad identificada por `dispid`.  
  
```  
virtual BOOL OnGetDisplayString(
    DISPID dispid,  
    CString& strValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 `strValue`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que se devolverá una cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha devuelto una cadena en *strValue;* lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si el control tiene una propiedad cuyo valor no se puede convertir directamente en una cadena y desea que el valor de la propiedad que se mostrará en un explorador de propiedades proporcionado por el contenedor.  
  
##  <a name="a-nameongetinplacemenua--colecontrolongetinplacemenu"></a><a name="ongetinplacemenu"></a>COleControl::OnGetInPlaceMenu  
 Llamado por el marco de trabajo cuando el control está activado para obtener el menú que se combinarán en el menú del contenedor existente de la interfaz de usuario.  
  
```  
virtual HMENU OnGetInPlaceMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del menú del control, o **NULL** si el control no tiene ninguno. La implementación predeterminada devuelve **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la combinación de recursos OLE, vea el artículo [menús y recursos (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="a-nameongetnaturalextenta--colecontrolongetnaturalextent"></a><a name="ongetnaturalextent"></a>COleControl::OnGetNaturalExtent  
 Llamado por el marco de trabajo en respuesta a un contenedor **IViewObjectEx::GetNaturalExtent** solicitud.  
  
```  
virtual BOOL OnGetNaturalExtent(
    DWORD dwAspect,
    LONG lindex,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwAspect`  
 Especifica cómo se va a representar el objeto. Representaciones incluyen contenido, un icono, una vista en miniatura o un documento impreso. Los valores válidos proceden de la enumeración [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) o **DVASPECT2**.  
  
 *lIndex*  
 La parte del objeto que es de interés. Actualmente, sólo -1 es válido.  
  
 `ptd`  
 Apunta a la [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) estructura define el dispositivo de destino para el que se debe devolver el tamaño del objeto.  
  
 `hicTargetDev`  
 Especifica el contexto de información para el dispositivo de destino indicado por el `ptd` parámetro desde el que el objeto puede extraer las métricas del dispositivo y probar las capacidades del dispositivo. Si `ptd` es **NULL**, el objeto debe pasar por alto el valor de la `hicTargetDev` parámetro.  
  
 *pExtentInfo*  
 Apunta a la **DVEXTENTINFO** estructura que especifica los datos de ajuste de tamaño. El **DVEXTENTINFO** estructura es:  
  
 `typedef struct  tagExtentInfo`  
  
 `{`  
  
 `UINT cb;`  
  
 `DWORD dwExtentMode;`  
  
 `SIZEL sizelProposed;`  
  
 `}   DVEXTENTINFO;`  
  
 El miembro de estructura `dwExtentMode` puede adoptar uno de dos valores:  
  
- **DVEXTENT_CONTENT** consultar qué tamaño debe ser el control ajustar exactamente el contenido (complemento a tamaño)  
  
- **DVEXTENT_INTEGRAL** al cambiar el tamaño, pasar el tamaño propuesto al control  
  
 `psizel`  
 Puntos de datos devueltos por el control de tamaño. Los datos de tamaño devuelto se establecen en -1 para cualquier dimensión que no se haya ajustado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se devuelve correctamente o se ajusta el tamaño; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para devolver el tamaño de presentación del objeto más cercano al modo propuesto de tamaño y el alcance de la **DVEXTENTINFO** estructura. La implementación predeterminada devuelve **FALSE** y no se realiza ajustes en el tamaño.  
  
##  <a name="a-nameongetpredefinedstringsa--colecontrolongetpredefinedstrings"></a><a name="ongetpredefinedstrings"></a>COleControl::OnGetPredefinedStrings  
 Llamado por el marco de trabajo para obtener un conjunto de cadenas predefinidas que representa los valores posibles para una propiedad.  
  
```  
virtual BOOL OnGetPredefinedStrings(
    DISPID dispid,  
    CStringArray* pStringArray,  
    CDWordArray* pCookieArray);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 `pStringArray`  
 Una matriz de cadenas que se debe rellenar con los valores devueltos.  
  
 `pCookieArray`  
 Un `DWORD` matriz se rellena con los valores devueltos.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se han agregado elementos a `pStringArray` y `pCookieArray`.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si el control tiene una propiedad con un conjunto de valores posibles que puede representarse mediante cadenas. Cada elemento agregado a `pStringArray`, debe agregar un elemento "cookie" correspondiente a *pCookieArray.* Estos valores de "cookie" más adelante se pueden pasar el marco de trabajo para el `COleControl::OnGetPredefinedValue` (función).  
  
##  <a name="a-nameongetpredefinedvaluea--colecontrolongetpredefinedvalue"></a><a name="ongetpredefinedvalue"></a>COleControl::OnGetPredefinedValue  
 Llamado por el marco para obtener el valor correspondiente a una de las cadenas predefinidas previamente devueltos por una invalidación de `COleControl::OnGetPredefinedStrings`.  
  
```  
virtual BOOL OnGetPredefinedValue(
    DISPID dispid,  
    DWORD dwCookie,  
    VARIANT* lpvarOut);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 `dwCookie`  
 Un valor de cookie devuelto previamente por una invalidación de `COleControl::OnGetPredefinedStrings`.  
  
 `lpvarOut`  
 Puntero a un **VARIANT** estructura mediante la cual se devolverá un valor de propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha devuelto un valor de `lpvarOut`; de lo contrario, 0.  
  
##  <a name="a-nameongetviewextenta--colecontrolongetviewextent"></a><a name="ongetviewextent"></a>COleControl::OnGetViewExtent  
 Llamado por el marco de trabajo en respuesta a un contenedor [IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) solicitud.  
  
```  
virtual BOOL OnGetViewExtent(
    DWORD dwDrawAspect,
    LONG lindex,
    DVTARGETDEVICE* ptd,
    LPSIZEL lpsizel);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDrawAspect*  
 `DWORD`Describir qué formulario o aspecto, de un objeto es que se mostrará. Los valores válidos proceden de la enumeración [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) o **DVASPECT2**.  
  
 *lIndex*  
 La parte del objeto que es de interés. Actualmente, sólo -1 es válido.  
  
 `ptd`  
 Apunta a la [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) estructura define el dispositivo de destino para el que se debe devolver el tamaño del objeto.  
  
 *lpsizel*  
 Señala a la ubicación donde se devuelve el tamaño del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la información de extensión se devolvió correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si el control utiliza el dibujo de dos pasos y sus partes transparentes y opacos tienen dimensiones diferentes.  
  
##  <a name="a-nameongetviewrecta--colecontrolongetviewrect"></a><a name="ongetviewrect"></a>COleControl::OnGetViewRect  
 Llamado por el marco de trabajo en respuesta a un contenedor **IViewObjectEx::GetRect** solicitud.  
  
```  
virtual BOOL OnGetViewRect(DWORD dwAspect, LPRECTL pRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwAspect`  
 `DWORD`Describir qué formulario o aspecto, de un objeto es que se mostrará. Los valores válidos proceden de la enumeración [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) o **DVASPECT2**:  
  
- `DVASPECT_CONTENT`Rectángulo delimitador del objeto completo. La esquina superior izquierda en el origen y el tamaño igual a la medida devuelta por el objeto **GetViewExtent***.*  
  
- **DVASPECT_OPAQUE** objetos con una región rectangular opaco devolver el rectángulo. Otros no.  
  
- **DVASPECT_TRANSPARENT** rectángulo que cubre todas las partes transparentes o irregulares.  
  
 `pRect`  
 Apunta a la [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) estructura que especifica el rectángulo en el que se debe dibujar el objeto. Este parámetro controla la posición y el ajuste del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el rectángulo de tamaño para el objeto se devolvió correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño del objeto se convierte en `OnGetViewRect` en un rectángulo que comienza en una posición específica (el valor predeterminado es la esquina superior izquierda de la pantalla). Reemplace esta función si el control utiliza el dibujo de dos pasos y sus partes transparentes y opacos tienen dimensiones diferentes.  
  
##  <a name="a-nameongetviewstatusa--colecontrolongetviewstatus"></a><a name="ongetviewstatus"></a>COleControl::OnGetViewStatus  
 Llamado por el marco de trabajo en respuesta a un contenedor **IViewObjectEx::GetViewStatus** solicitud.  
  
```  
virtual DWORD OnGetViewStatus();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores de la **VIEWSTATUS** enumeración si se realiza correctamente; en caso contrario, 0. Los valores posibles son cualquier combinación de las siguientes acciones:  
  
 **VIEWSTATUS_OPAQUE**  
 Objeto es completamente opaco. Si este bit no está establecido, el objeto contiene partes transparentes. Este bit se aplica solo a los aspectos relacionados con el contenido y no a `DVASPECT_ICON` o `DVASPECT_DOCPRINT`.  
  
 **VIEWSTATUS_SOLIDBKGND**  
 Objeto tiene un fondo sólido (que consta de un color sólido, no es un motivo de pincel). Este bit es significativo únicamente si **VIEWSTATUS_OPAQUE** se establece y se aplica solo a los aspectos relacionados con el contenido y no a `DVASPECT_ICON` o `DVASPECT_DOCPRINT`.  
  
 **VIEWSTATUS_DVASPECTOPAQUE**  
 Objeto admite **DVASPECT_OPAQUE**. Todos los **IViewObjectEx** métodos que toman un aspecto de dibujo como un parámetro que se puede llamar con este aspecto.  
  
 **VIEWSTATUS_DVASPECTTRANSPARENT**  
 Objeto admite **DVASPECT_TRANSPARENT**. Todos los **IViewObjectEx** métodos que toman un aspecto de dibujo como un parámetro que se puede llamar con este aspecto.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si el control utiliza el dibujo de dos pasos. La implementación predeterminada devuelve **VIEWSTATUS_OPAQUE**.  
  
##  <a name="a-nameonhidetoolbarsa--colecontrolonhidetoolbars"></a><a name="onhidetoolbars"></a>COleControl::OnHideToolBars  
 Lo llama el marco de trabajo cuando el control está desactivado de la interfaz de usuario.  
  
```  
virtual void OnHideToolBars();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación debe ocultar todas las barras de herramientas mostradas por `OnShowToolbars`.  
  
##  <a name="a-nameoninactivemousemovea--colecontroloninactivemousemove"></a><a name="oninactivemousemove"></a>COleControl::OnInactiveMouseMove  
 Llamado por el contenedor para el objeto inactivo bajo el puntero del mouse en la recepción de un `WM_MOUSEMOVE` mensaje.  
  
```  
virtual void OnInactiveMouseMove(
    LPCRECT lprcBounds,
    long x,
    long y,
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>Parámetros  
 `lprcBounds`  
 El objeto rectángulo, en coordenadas de cliente de la ventana contenedora de límite. Indica que el objeto a su posición exacta y su tamaño en la pantalla cuando el `WM_MOUSEMOVE` se recibió el mensaje.  
  
 *x*  
 Coordenada x de la ubicación del mouse en coordenadas de cliente de la ventana contenedora.  
  
 *y*  
 Coordenada y de la ubicación del mouse en coordenadas de cliente de la ventana contenedora.  
  
 `dwKeyState`  
 Identifica el estado actual de las teclas modificadoras de teclado en el teclado. Valores válidos pueden ser una combinación de cualquiera de los indicadores **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_BUTTON**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que coordenadas de cliente de la ventana (píxeles) se utilizan para pasar la posición del cursor del mouse. Esto se consigue pasando asimismo el rectángulo delimitador del objeto en el mismo sistema de coordenadas.  
  
##  <a name="a-nameoninactivesetcursora--colecontroloninactivesetcursor"></a><a name="oninactivesetcursor"></a>COleControl::OnInactiveSetCursor  
 Llamado por el contenedor para el objeto inactivo bajo el puntero del mouse en la recepción de un `WM_SETCURSOR` mensaje.  
  
```  
virtual BOOL OnInactiveSetCursor(
    LPCRECT lprcBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL bSetAlways);
```  
  
### <a name="parameters"></a>Parámetros  
 `lprcBounds`  
 El objeto rectángulo, en coordenadas de cliente de la ventana contenedora de límite. Indica que el objeto a su posición exacta y su tamaño en la pantalla cuando el `WM_SETCURSOR` se recibió el mensaje.  
  
 *x*  
 Coordenada x de la ubicación del mouse en coordenadas de cliente de la ventana contenedora.  
  
 *y*  
 Coordenada y de la ubicación del mouse en coordenadas de cliente de la ventana contenedora.  
  
 *dwMouseMsg*  
 El identificador del mensaje del mouse para que un `WM_SETCURSOR` se ha producido.  
  
 *bSetAlways*  
 Especifica si el objeto debe establecer el cursor. Si **TRUE**, el objeto debe establecer el cursor; si **FALSE**, el cursor no está obligado a colocar el cursor y debe devolver **S_FALSE** en ese caso.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que coordenadas de cliente de la ventana (píxeles) se utilizan para pasar la posición del cursor del mouse. Esto se consigue pasando asimismo el rectángulo delimitador del objeto en el mismo sistema de coordenadas.  
  
##  <a name="a-nameonkeydowneventa--colecontrolonkeydownevent"></a><a name="onkeydownevent"></a>COleControl::OnKeyDownEvent  
 Llamado por el marco después de procesar un evento KeyDown estándar.  
  
```  
virtual void OnKeyDownEvent(
    USHORT nChar,  
    USHORT nShiftState);
```  
  
### <a name="parameters"></a>Parámetros  
 `nChar`  
 El valor de código de tecla virtual de la tecla presionada. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h  
  
 `nShiftState`  
 Contiene una combinación de los siguientes indicadores:  
  
- **SHIFT_MASK** se presionó la tecla MAYÚS durante la acción.  
  
- **CTRL_MASK** se presionó la tecla CTRL la durante la acción.  
  
- **ALT_MASK** se presionó la tecla ALT el durante la acción.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si el control necesita tener acceso a la información de clave después de que se ha desencadenado el evento.  
  
##  <a name="a-nameonkeypresseventa--colecontrolonkeypressevent"></a><a name="onkeypressevent"></a>COleControl::OnKeyPressEvent  
 Llamado por el marco después de las existencias se ha desencadenado el evento KeyPress.  
  
```  
virtual void OnKeyPressEvent(USHORT nChar);
```  
  
### <a name="parameters"></a>Parámetros  
 `nChar`  
 Contiene el valor de código de tecla virtual de la tecla presionada. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el `nChar` valor puede haber sido modificado por el contenedor.  
  
 Reemplace esta función si desea notificación cuando se produce este evento.  
  
##  <a name="a-nameonkeyupeventa--colecontrolonkeyupevent"></a><a name="onkeyupevent"></a>COleControl::OnKeyUpEvent  
 Llamado por el marco después de procesar un evento KeyDown estándar.  
  
```  
virtual void OnKeyUpEvent(
    USHORT nChar,  
    USHORT nShiftState);
```  
  
### <a name="parameters"></a>Parámetros  
 `nChar`  
 El valor de código de tecla virtual de la tecla presionada. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h  
  
 `nShiftState`  
 Contiene una combinación de los siguientes indicadores:  
  
- **SHIFT_MASK** se presionó la tecla MAYÚS durante la acción.  
  
- **CTRL_MASK** se presionó la tecla CTRL la durante la acción.  
  
- **ALT_MASK** se presionó la tecla ALT el durante la acción.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si el control necesita tener acceso a la información de clave después de que se ha desencadenado el evento.  
  
##  <a name="a-nameonmappropertytopagea--colecontrolonmappropertytopage"></a><a name="onmappropertytopage"></a>COleControl::OnMapPropertyToPage  
 Llamado por el marco de trabajo para obtener el identificador de clase de una página de propiedades que implementa la edición de la propiedad especificada.  
  
```  
virtual BOOL OnMapPropertyToPage(
    DISPID dispid,  
    LPCLSID lpclsid,  
    BOOL* pbPageOptional);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 Identificador de envío de una propiedad del control.  
  
 `lpclsid`  
 Puntero a un **CLSID** estructura mediante la cual se devolverá un identificador de clase.  
  
 *pbPageOptional*  
 Devuelve un indicador de si el uso de la página de propiedades especificado es opcional.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ha devuelto un Id. de clase de `lpclsid`; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para proporcionar un mecanismo para invocar las páginas de propiedades del control desde el Explorador de propiedades del contenedor.  
  
##  <a name="a-nameonmnemonica--colecontrolonmnemonic"></a><a name="onmnemonic"></a>COleControl::OnMnemonic  
 Llamado por el marco de trabajo cuando el contenedor ha detectado que se ha presionado una tecla de acceso del control OLE.  
  
```  
virtual void OnMnemonic(LPMSG pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Puntero al mensaje de Windows generado por la presión de una tecla mnemónica.  
  
##  <a name="a-nameonpropertiesa--colecontrolonproperties"></a><a name="onproperties"></a>COleControl::OnProperties  
 Llamado por el marco al verbo de propiedades del control se ha invocado por el contenedor.  
  
```  
virtual BOOL OnProperties(
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMsg`  
 Un puntero al mensaje de Windows que invocó el verbo.  
  
 `hWndParent`  
 Identificador de la ventana primaria del control.  
  
 `lpRect`  
 Puntero al rectángulo utilizado por el control en el contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la llamada se realiza correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada, muestra un cuadro de diálogo modal propiedad.  
  
 También puede utilizar esta función para hacer que la visualización de páginas de propiedades del control. Realizar una llamada a la `OnProperties` función, pasando el identificador del elemento primario del control en el `hWndParent` parámetro. En este caso, los valores de la `lpMsg` y `lpRect` se omiten los parámetros.  
  
##  <a name="a-nameonqueryhitpointa--colecontrolonqueryhitpoint"></a><a name="onqueryhitpoint"></a>COleControl::OnQueryHitPoint  
 Llamado por el marco de trabajo en respuesta a un contenedor **IViewObjectEx::QueryHitPoint** solicitud.  
  
```  
virtual BOOL OnQueryHitPoint(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG lCloseHint,
    DWORD* pHitResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwAspect`  
 Especifica cómo se representa el objeto. Los valores válidos proceden de la enumeración [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) o **DVASPECT2**.  
  
 `pRectBounds`  
 Puntero a un `RECT` estructura que especifica el rectángulo delimitador del área de cliente de control OLE.  
  
 `ptlLoc`  
 Puntero a la **punto** estructura que especifica el punto de comprobarse un acierto. El punto se especifica en coordenadas del área de cliente OLE.  
  
 `lCloseHint`  
 La distancia que define "cerrar" para el punto buscaba un acierto.  
  
 `pHitResult`  
 Puntero al resultado de la consulta de visita. Uno de los siguientes valores:  
  
- **HITRESULT_OUTSIDE** `ptlLoc` está fuera de OLE del objeto y se cierra.  
  
- **HITRESULT_TRANSPARENT** *ptlLoc* está dentro de los límites del objeto OLE, pero no más cerca de la imagen. Por ejemplo, podría ser un punto en medio de un círculo transparente **HITRESULT_TRANSPARENT**.  
  
- **HITRESULT_CLOSE** `ptlLoc` está dentro o fuera del objeto OLE pero suficientemente cerca al objeto que se considera dentro. Pequeños, ligeros o detallados de objetos pueden utilizar este valor. Incluso si un punto está fuera del límite rectángulo de un objeto todavía puede ser cerrar (Esto es necesario para alcanzar los objetos pequeños).  
  
- **HITRESULT_HIT** `ptlLoc` está en la imagen del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se devolvió un resultado acierto; en caso contrario, 0. Un acierto es una superposición con el área de presentación del control OLE.  
  
### <a name="remarks"></a>Comentarios  
 Si el punto especificado superpone a rectángulo de presentación de un objeto de consulta (alcanza el punto). `QueryHitPoint`se puede invalidar para probar los resultados para objetos no rectangulares.  
  
##  <a name="a-nameonqueryhitrecta--colecontrolonqueryhitrect"></a><a name="onqueryhitrect"></a>COleControl::OnQueryHitRect  
 Llamado por el marco de trabajo en respuesta a un contenedor **IViewObjectEx::QueryHitRect** solicitud.  
  
```  
virtual BOOL OnQueryHitRect(
    DWORD dwAspect,  
    LPCRECT pRectBounds,  
    LPCRECT prcLoc,  
    LONG lCloseHint,  
    DWORD* pHitResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwAspect`  
 Especifica cómo se va a representar el objeto. Los valores válidos proceden de la enumeración [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) o **DVASPECT2**.  
  
 `pRectBounds`  
 Puntero a un `RECT` estructura que especifica el rectángulo delimitador del área de cliente de control OLE.  
  
 *prcLoc*  
 Puntero a la `RECT` estructura que especifica el rectángulo que se comprobará para un acierto (superposición con el rectángulo de objeto), con respecto a la esquina superior izquierda del objeto.  
  
 `lCloseHint`  
 No usado.  
  
 `pHitResult`  
 Puntero al resultado de la consulta de visita. Uno de los siguientes valores:  
  
- **HITRESULT_OUTSIDE** ningún punto en el rectángulo que se visita el objeto OLE.  
  
- **HITRESULT_HIT** al menos un punto en el rectángulo sería un impacto en el objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se devolvió un resultado acierto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Consulta si rectángulo de presentación de un objeto superpone a cualquier punto en el rectángulo dado (alcanza el rectángulo). `QueryHitRect`se puede invalidar para probar los resultados para objetos no rectangulares.  
  
##  <a name="a-nameonrenderdataa--colecontrolonrenderdata"></a><a name="onrenderdata"></a>COleControl::OnRenderData  
 Llamado por el marco de trabajo para recuperar datos en el formato especificado.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `lpStgMedium`  
 Apunta a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura en la que se devolverán los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una colocado anteriormente en el objeto de control mediante la [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) o [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) funciones miembro para representación retrasada. La implementación predeterminada de esta función llama `OnRenderFileData` o `OnRenderGlobalData`, respectivamente, si el medio de almacenamiento proporcionado es un archivo o la memoria. Si el formato solicitado es `CF_METAFILEPICT` o la propiedad persistent establece formato, la implementación predeterminada representa los datos apropiados y devuelve distinto de cero. De lo contrario, devuelve 0 y no hace nada.  
  
 Si *lpStgMedium-> tymed* es **TYMED_NULL**, **STGMEDIUM** debe ser asignado y rellenado según lo especificado por *lpFormatEtc-> tymed*. Si no **TYMED_NULL**, **STGMEDIUM** debe rellenar con los datos.  
  
 Reemplazar esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede invalidar una de las otras versiones de esta función en su lugar. Si los datos son pequeños y un tamaño fijo, reemplace `OnRenderGlobalData`. Si los datos en un archivo, o es de tamaño variable, reemplazar `OnRenderFileData`.  
  
 Para obtener más información, consulte el **FORMATETC** y **STGMEDIUM** las estructuras de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameonrenderfiledataa--colecontrolonrenderfiledata"></a><a name="onrenderfiledata"></a>COleControl::OnRenderFileData  
 Llamado por el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento es un archivo.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `pFile`  
 Apunta a un [CFile](../../mfc/reference/cfile-class.md) objeto en el que se va a representar los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una colocado anteriormente en el objeto de control mediante la [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función de miembro para la representación aplazada. La implementación predeterminada de esta función devuelve simplemente **FALSE**.  
  
 Reemplazar esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace `OnRenderData`. Si los datos en un archivo, o es de tamaño variable, reemplazar `OnRenderFileData`.  
  
 Para obtener más información, consulte el **FORMATETC** estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameonrenderglobaldataa--colecontrolonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleControl::OnRenderGlobalData  
 Llamado por el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento especificado es una memoria global.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `phGlobal`  
 Apunta a un identificador de memoria global en el que los datos son va a devolver. Si no se ha asignado ninguna memoria, este parámetro puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una colocado anteriormente en el objeto de control mediante la [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función de miembro para la representación aplazada. La implementación predeterminada de esta función devuelve simplemente **FALSE**.  
  
 Si `phGlobal` es **NULL**, a continuación, un nuevo `HGLOBAL` se debe asignar y devueltos en `phGlobal`. De lo contrario, el `HGLOBAL` especificado por `phGlobal` debe rellenarse con los datos. La cantidad de datos se coloca en el `HGLOBAL` no debe superar el tamaño actual del bloque de memoria. Además, el bloque no se puede reasignar a un tamaño mayor.  
  
 Reemplazar esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace `OnRenderData`. Si los datos en un archivo, o es de tamaño variable, reemplazar `OnRenderFileData`.  
  
 Para obtener más información, consulte el **FORMATETC** estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameonresetstatea--colecontrolonresetstate"></a><a name="onresetstate"></a>COleControl:: OnResetState  
 Llamado por el marco de trabajo cuando las propiedades del control deben establecerse en sus valores predeterminados.  
  
```  
virtual void OnResetState();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama [DoPropExchange](#dopropexchange), pasando un `CPropExchange` objeto que hace que las propiedades se establezca en sus valores predeterminados.  
  
 El escritor de control puede insertar código de inicialización para el control OLE en este reemplazable. Esta función se invoca cuando [IPersistStream:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680568) o [IPersistStorage:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) se produce un error, o [IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) o [IPersistStorage::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194) se llama sin llamar primero a cualquiera **IPersistStream:: Load** o **IPersistStorage:: Load**.  
  
##  <a name="a-nameonsetclientsitea--colecontrolonsetclientsite"></a><a name="onsetclientsite"></a>COleControl:: OnSetClientSite  
 Llamado por el marco de trabajo cuando el contenedor denomina el control **IOleControl::SetClientSite** (función).  
  
```  
virtual void OnSetClientSite();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `OnSetClientSite` comprueba si las propiedades de ruta de acceso de datos se cargan y, si es así, llama a `DoDataPathPropExchange`.  
  
 Reemplazar esta función para realizar cualquier procesamiento especial de esta notificación. En concreto, las invalidaciones de esta función deben llamar a la clase base.  
  
##  <a name="a-nameonsetdataa--colecontrolonsetdata"></a><a name="onsetdata"></a>COleControl::OnSetData  
 Llamado por el marco de trabajo para reemplazar los datos del control con los datos especificados.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Puntero a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato de los datos.  
  
 `lpStgMedium`  
 Puntero a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura donde residen los datos.  
  
 `bRelease`  
 **TRUE** si el control debe liberar el medio de almacenamiento; **FALSE** si el control no debe liberar el medio de almacenamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si los datos se establecen en la propiedad persistente de formato, la implementación predeterminada modifica el estado del control en consecuencia. De lo contrario, la implementación predeterminada no hace nada. Si `bRelease` es **TRUE**, a continuación, una llamada a **ReleaseStgMedium** queda; en caso contrario, no.  
  
 Reemplazar esta función para reemplazar los datos del control con los datos especificados.  
  
 Para obtener más información, consulte el **FORMATETC** y **STGMEDIUM** las estructuras de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameonsetextenta--colecontrolonsetextent"></a><a name="onsetextent"></a>COleControl::OnSetExtent  
 Llamado por el marco cuando la extensión del control debe cambiarse, como resultado de una llamada a [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330).  
  
```  
virtual BOOL OnSetExtent(LPSIZEL lpSizeL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSizeL`  
 Un puntero a la **tamaño** estructura que utiliza enteros largos para representar el ancho y alto del control, expresado en **HIMETRIC** unidades.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se acepta el cambio de tamaño; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada controla el cambio de tamaño de la extensión del control. Si el control está activo en contexto, una llamada al contenedor **OnPosRectChanged** , a continuación, se realiza.  
  
 Reemplazar esta función para modificar el cambio de tamaño predeterminado del control.  
  
##  <a name="a-nameonsetobjectrectsa--colecontrolonsetobjectrects"></a><a name="onsetobjectrects"></a>COleControl::OnSetObjectRects  
 Llamado por el marco para implementar una llamada a [IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767).  
  
```  
virtual BOOL OnSetObjectRects(
    LPCRECT lpRectPos,  
    LPCRECT lpRectClip);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpRectPos*  
 Puntero a una estructura RECT que indica la nueva posición y el tamaño en relación con el contenedor del control.  
  
 `lpRectClip`  
 Un puntero a un `RECT` estructura que indica un área rectangular a la que se recorta el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se acepta el cambio de posición; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada controla el cambio de posición y cambio de tamaño de la ventana de control y devuelve automáticamente **TRUE**.  
  
 Reemplazar esta función para alterar el comportamiento predeterminado de esta función.  
  
##  <a name="a-nameonshowtoolbarsa--colecontrolonshowtoolbars"></a><a name="onshowtoolbars"></a>COleControl::OnShowToolBars  
 Lo llama el marco de trabajo cuando el control se ha activado la IU.  
  
```  
virtual void OnShowToolBars();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada.  
  
##  <a name="a-nameontextchangeda--colecontrolontextchanged"></a><a name="ontextchanged"></a>COleControl::OnTextChanged  
 Llamado por el marco de trabajo cuando ha cambiado el valor de propiedad de título o de texto estándar.  
  
```  
virtual void OnTextChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `InvalidateControl`.  
  
 Reemplace esta función si desea notificación después de los cambios de esta propiedad.  
  
##  <a name="a-nameonwindowlessmessagea--colecontrolonwindowlessmessage"></a><a name="onwindowlessmessage"></a>COleControl::OnWindowlessMessage  
 Llamado por el marco de trabajo en respuesta a un contenedor **IOleInPlaceObjectWindowless::OnWindowMessage** solicitud.  
  
```  
virtual BOOL OnWindowlessMessage(
    UINT msg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `msg`  
 Identificador de mensaje como pasan por Windows.  
  
 `wParam`  
 Como se pasan por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor de la `msg` parámetro.  
  
 `lParam`  
 Como se pasan por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor de la `msg` parámetro.  
  
 *plResult*  
 Código de resultado de Windows. Especifica el resultado del procesamiento del mensaje y depende del mensaje enviado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Procesa los mensajes de ventana para los controles sin ventana. `COleControl`de `OnWindowlessMessage` debe utilizarse para mensajes de ventana que no sean los mensajes del mouse y teclado. `COleControl`proporciona [SetCapture](#setcapture) y [SetFocus](#setfocus) específicamente a obtener el foco de teclado y la captura del mouse para los objetos OLE sin ventanas.  
  
 Dado que los objetos sin ventana no tiene una ventana, necesitan un mecanismo para permitir que los mensajes de envío de contenedor con ellos. Un objeto OLE sin ventanas obtiene mensajes de su contenedor a través del `OnWindowMessage` método en el `IOleInPlaceObjectWindowless` interfaz (una extensión de [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) de soporte sin ventanas). `OnWindowMessage`no se hace un `HWND` parámetro.  
  
##  <a name="a-nameparenttoclienta--colecontrolparenttoclient"></a><a name="parenttoclient"></a>COleControl::ParentToClient  
 Convierte las coordenadas de `pPoint` en coordenadas de cliente.  
  
```  
virtual UINT ParentToClient(
    LPCRECT lprcBounds,
    LPPOINT pPoint,
    BOOL bHitTest = FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lprcBounds`  
 Puntero a los límites del control dentro del contenedor OLE. El área de todo el control, incluidos los bordes y barras de desplazamiento, pero no en el área de cliente.  
  
 `pPoint`  
 Puntero al elemento primario (contenedor) señala a traducir las coordenadas del área cliente del control.  
  
 `bHitTest`  
 Especifica si la prueba de posicionamiento es llevar a cabo en el punto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si `bHitTest` es **FALSE**, devuelve **HTNOWHERE**. Si `bHitTest` es **TRUE**, devuelve la ubicación en la que elija el elemento primario (contenedor) descargados en el área cliente del control OLE y es uno de lo mouse siguiente valores de prueba de posicionamiento:  
  
- **HTBORDER** en el borde de una ventana que no tiene un borde de tamaño.  
  
- **HTBOTTOM** en el borde inferior horizontal de la ventana.  
  
- **HTBOTTOMLEFT** en la esquina inferior izquierda del borde de ventana.  
  
- **HTBOTTOMRIGHT** en la esquina inferior derecha del borde de ventana.  
  
- **HTCAPTION** en un área de la barra de título.  
  
- **HTCLIENT** en un área de cliente.  
  
- **HTERROR** en el fondo de la pantalla o en una línea divisoria entre windows (igual que **HTNOWHERE** excepto en que la **DefWndProc** función de Windows genera un pitido para indicar un error del sistema).  
  
- **HTGROWBOX** en un cuadro de tamaño.  
  
- **HTHSCROLL** en la barra de desplazamiento horizontal.  
  
- **HTLEFT** en el borde izquierdo de la ventana.  
  
- **HTMAXBUTTON** botón de maximizar.  
  
- **HTMENU** en un área de menú.  
  
- **HTMINBUTTON** botón de minimizar.  
  
- **HTNOWHERE** en el fondo de la pantalla o en una línea divisoria entre las ventanas.  
  
- **HTREDUCE** botón de minimizar.  
  
- **HTRIGHT** en el borde derecho de la ventana.  
  
- **HTSIZE** en un cuadro de tamaño (igual que **HTGROWBOX**).  
  
- **HTSYSMENU** en un menú de Control o en un botón de cierre de una ventana secundaria.  
  
- **HTTOP** en el borde superior horizontal de la ventana.  
  
- **HTTOPLEFT** en la esquina superior izquierda del borde de ventana.  
  
- **HTTOPRIGHT** en la esquina superior derecha del borde de ventana.  
  
- **HTTRANSPARENT** en una ventana que está cubierta por otra ventana.  
  
- **HTVSCROLL** en la barra de desplazamiento vertical.  
  
- **HTZOOM** botón de maximizar.  
  
### <a name="remarks"></a>Comentarios  
 En la entrada `pPoint` es relativo al origen del elemento primario (esquina superior izquierda del contenedor). En la salida `pPoint` es relativo al origen del área cliente del control OLE (esquina superior izquierda del área cliente del control).  
  
##  <a name="a-namepostmodaldialoga--colecontrolpostmodaldialog"></a><a name="postmodaldialog"></a>COleControl::PostModalDialog  
 Notifica al contenedor que se ha cerrado el cuadro de diálogo modal.  
  
```  
void PostModalDialog(HWND hWndParent = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la ventana primaria del cuadro de diálogo modal.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función después de mostrar cualquier cuadro de diálogo modal. Debe llamar a esta función para que el contenedor puede habilitar las ventanas de nivel superior deshabilitadas de forma `PreModalDialog`. Esta función se debe emparejar con una llamada a `PreModalDialog`.  
  
##  <a name="a-namepremodaldialoga--colecontrolpremodaldialog"></a><a name="premodaldialog"></a>COleControl::PreModalDialog  
 Notifica al contenedor que se mostrará un cuadro de diálogo modal.  
  
```  
void PreModalDialog(HWND hWndParent = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la ventana primaria del cuadro de diálogo modal.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función antes de mostrar cualquier cuadro de diálogo modal. Debe llamar a esta función para que el contenedor puede deshabilitar todas las ventanas de nivel superior. Después de mostrar el cuadro de diálogo modal, debe llamar `PostModalDialog`.  
  
##  <a name="a-namerecreatecontrolwindowa--colecontrolrecreatecontrolwindow"></a><a name="recreatecontrolwindow"></a>COleControl::RecreateControlWindow  
 Destruye y vuelve a crear la ventana del control.  
  
```  
void RecreateControlWindow();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto puede ser necesario si necesita cambiar los bits de estilo de la ventana.  
  
##  <a name="a-namerefresha--colecontrolrefresh"></a><a name="refresh"></a>COleControl::Refresh  
 Hace vuelva a dibujarse el control OLE.  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función es compatible con la `COleControl` clase base como un método estándar, denominado actualización. Esto permite a los usuarios de su control OLE para volver a dibujar el control en un momento determinado. Para obtener más información sobre este método, vea el artículo [controles ActiveX: métodos](../../mfc/mfc-activex-controls-methods.md).  
  
##  <a name="a-namereleasecapturea--colecontrolreleasecapture"></a><a name="releasecapture"></a>COleControl::ReleaseCapture  
 Libera la captura del mouse.  
  
```  
BOOL ReleaseCapture();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si el control tiene actualmente la captura del mouse, se libera la captura. De lo contrario, esta función no tiene efecto.  
  
##  <a name="a-namereleasedca--colecontrolreleasedc"></a><a name="releasedc"></a>COleControl::ReleaseDC  
 Libera el contexto de dispositivo de presentación de un contenedor de un control sin ventana, al liberar el contexto de dispositivo para su uso por otras aplicaciones.  
  
```  
int ReleaseDC(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Identifica el contexto de dispositivo de contenedor que se libere.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La aplicación debe llamar a `ReleaseDC` para cada llamada a [GetDC](#getdc).  
  
##  <a name="a-namereparentcontrolwindowa--colecontrolreparentcontrolwindow"></a><a name="reparentcontrolwindow"></a>COleControl::ReparentControlWindow  
 Establece al elemento primario del control.  
  
```  
virtual void ReparentControlWindow(
    HWND hWndOuter,  
    HWND hWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 *hWndOuter*  
 Identificador de la ventana de control.  
  
 `hWndParent`  
 El identificador de la nueva ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para restablecer al elemento primario de la ventana de control.  
  
##  <a name="a-nameresetstockpropsa--colecontrolresetstockprops"></a><a name="resetstockprops"></a>COleControl::ResetStockProps  
 Inicializa el estado de la `COleControl` propiedades a sus valores predeterminados estándar.  
  
```  
void ResetStockProps();
```  
  
### <a name="remarks"></a>Comentarios  
 Las propiedades son: apariencia, BackColor, BorderStyle, título, Enabled, fuente, color de primer plano, hWnd y texto. Para obtener una descripción de las propiedades estándar, vea [controles ActiveX: agregar propiedades estándar](../../mfc/mfc-activex-controls-adding-stock-properties.md).  
  
 Puede mejorar el rendimiento de binarios de inicialización de un control mediante el uso de `ResetStockProps` y `ResetVersion` reemplazar `COleControl::OnResetState`. Vea el ejemplo siguiente. Para obtener más información acerca de cómo optimizar la inicialización, vea [controles ActiveX: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAxCtl&#7;](../../mfc/reference/codesnippet/cpp/colecontrol-class_8.cpp)]  
  
##  <a name="a-nameresetversiona--colecontrolresetversion"></a><a name="resetversion"></a>COleControl::ResetVersion  
 Inicializa el número de versión al valor especificado.  
  
```  
void ResetVersion(DWORD dwVersionDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwVersionDefault`  
 El número de versión que se asignará al control.  
  
### <a name="remarks"></a>Comentarios  
 Puede mejorar el rendimiento de binarios de inicialización de un control mediante el uso de `ResetVersion` y `ResetStockProps` reemplazar `COleControl::OnResetState`. Consulte el ejemplo en [ResetStockProps](#resetstockprops). Para obtener más información acerca de cómo optimizar la inicialización, vea [controles ActiveX: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
##  <a name="a-namescrollwindowa--colecontrolscrollwindow"></a><a name="scrollwindow"></a>COleControl::ScrollWindow  
 Permite que un objeto OLE sin ventanas desplazar un área dentro de su imagen activo en contexto en la pantalla.  
  
```  
void ScrollWindow(
    int xAmount,
    int yAmount,
    LPCRECT lpRect = NULL,
    LPCRECT lpClipRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `xAmount`  
 Especifica la cantidad, en unidades del dispositivo, de desplazamiento horizontal. Este parámetro debe ser un valor negativo para desplazarse a la izquierda.  
  
 `yAmount`  
 Especifica la cantidad, en unidades del dispositivo, de desplazamiento vertical. Este parámetro debe ser un valor negativo para desplazar hacia arriba.  
  
 `lpRect`  
 Apunta a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o estructura RECT que especifica la parte del área de cliente del objeto OLE que desplazarse, en coordenadas de cliente de la ventana contenedora. Si `lpRect` es **NULL**, se desplaza el área de cliente del objeto OLE todo.  
  
 `lpClipRect`  
 Apunta a un `CRect` objeto o `RECT` estructura que especifica el rectángulo de recorte para. Se desplazan sólo píxeles dentro del rectángulo. Bits fuera del rectángulo no se ven afectados incluso si están en el `lpRect` rectángulo. Si `lpClipRect` es **NULL**, no se realiza ningún recorte en el rectángulo de desplazamiento.  
  
##  <a name="a-nameselectfontobjecta--colecontrolselectfontobject"></a><a name="selectfontobject"></a>COleControl::SelectFontObject  
 Selecciona una fuente en un contexto de dispositivo.  
  
```  
CFont* SelectFontObject(
    CDC* pDC,  
    CFontHolder& fontHolder);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero a un objeto de contexto de dispositivo.  
  
 `fontHolder`  
 Hacer referencia a la [CFontHolder](../../mfc/reference/cfontholder-class.md) objeto que representa la fuente que va a seleccionar.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la fuente seleccionada anteriormente. Cuando el llamador ha terminado todas las operaciones de dibujos que utilizan *fontHolder,* debe volver a la fuente seleccionada anteriormente, pasando como parámetro a [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject).  
  
##  <a name="a-nameselectstockfonta--colecontrolselectstockfont"></a><a name="selectstockfont"></a>COleControl:: SelectStockFont  
 Selecciona la propiedad Font estándar en un contexto de dispositivo.  
  
```  
CFont* SelectStockFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 El contexto de dispositivo en el que se seleccionará la fuente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la seleccionada anteriormente `CFont` objeto. Debe usar [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) para seleccionar esta fuente en el contexto de dispositivo cuando haya terminado.  
  
##  <a name="a-nameserializeextenta--colecontrolserializeextent"></a><a name="serializeextent"></a>COleControl::SerializeExtent  
 Serializa o inicializa el estado del espacio asignado al control.  
  
```  
void SerializeExtent(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` objeto que se va a serializar a o desde.  
  
### <a name="remarks"></a>Comentarios  
 Puede mejorar el rendimiento de persistencia binaria de un control mediante el uso de `SerializeExtent`, `SerializeStockProps`, y `SerializeVersion` reemplazar **COleControl::Serialize**. Vea el ejemplo siguiente. Para obtener más información acerca de cómo optimizar la inicialización, vea [controles ActiveX: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCAxCtl Nº&8;](../../mfc/reference/codesnippet/cpp/colecontrol-class_9.cpp)]  
  
##  <a name="a-nameserializestockpropsa--colecontrolserializestockprops"></a><a name="serializestockprops"></a>COleControl::SerializeStockProps  
 Serializa o se inicializa el estado de la `COleControl` propiedades estándar: apariencia, BackColor, BorderStyle, título, Enabled, fuente, color de primer plano y texto.  
  
```  
void SerializeStockProps(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` objeto que se va a serializar a o desde.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una descripción de las propiedades estándar, vea [controles ActiveX: agregar propiedades estándar](../../mfc/mfc-activex-controls-adding-stock-properties.md).  
  
 Puede mejorar el rendimiento de persistencia binaria de un control mediante el uso de `SerializeStockProps`, `SerializeExtent`, y `SerializeVersion` reemplazar **COleControl::Serialize**. Para obtener un ejemplo, vea el código de [SerializeExtent](#serializeextent). Para obtener más información acerca de cómo optimizar la inicialización, vea [controles ActiveX: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
##  <a name="a-nameserializeversiona--colecontrolserializeversion"></a><a name="serializeversion"></a>COleControl::SerializeVersion  
 Serializa o inicializa el estado de un control información de versión.  
  
```  
DWORD SerializeVersion(
    CArchive& ar,
    DWORD dwVersionDefault,
    BOOL bConvert = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Un `CArchive` objeto que se va a serializar a o desde.  
  
 `dwVersionDefault`  
 El número de versión actual del control.  
  
 `bConvert`  
 Indica si los datos persistentes deben convertirse al formato más reciente cuando se guardan, o se mantienen en el mismo formato que tenía cuando se cargó.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de versión del control. Si está cargando el archivo especificado, `SerializeVersion` devuelve la versión cargada desde ese archivo. De lo contrario, devuelve la versión cargada actualmente.  
  
### <a name="remarks"></a>Comentarios  
 Puede mejorar el rendimiento de persistencia binaria de un control mediante el uso de `SerializeVersion`, `SerializeExtent`, y `SerializeStockProps` reemplazar **COleControl::Serialize**. Para obtener un ejemplo, vea el código de [SerializeExtent](#serializeextent). Para obtener más información acerca de cómo optimizar la inicialización, vea [controles ActiveX: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
##  <a name="a-namesetappearancea--colecontrolsetappearance"></a><a name="setappearance"></a>COleControl::SetAppearance  
 Establece el valor de propiedad estándar de apariencia del control.  
  
```  
void SetAppearance (short sAppearance);
```  
  
### <a name="parameters"></a>Parámetros  
 *sAppearance*  
 Un **corto** ( `VT_I2`) valor que se usará para la apariencia del control. Un valor de cero, Establece la apariencia del control en plano y un valor de 1 establece la apariencia del control en 3D.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las propiedades estándar, consulte [controles ActiveX: propiedades](../../mfc/mfc-activex-controls-properties.md).  
  
##  <a name="a-namesetbackcolora--colecontrolsetbackcolor"></a><a name="setbackcolor"></a>COleControl::SetBackColor  
 Establece el valor de propiedad BackColor estándar del control.  
  
```  
void SetBackColor(OLE_COLOR dwBackColor);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwBackColor*  
 Un **OLE_COLOR** valor que se utilizará para el fondo de dibujo del control.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el uso de esta propiedad y otras relacionadas con propiedades, vea el artículo [controles ActiveX: propiedades](../../mfc/mfc-activex-controls-properties.md).  
  
##  <a name="a-namesetborderstylea--colecontrolsetborderstyle"></a><a name="setborderstyle"></a>COleControl::SetBorderStyle  
 Establece el valor de propiedad estándar de estilo de borde del control.  
  
```  
void SetBorderStyle(short sBorderStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 *sBorderStyle*  
 El nuevo estilo de borde para el control; 0 no indica borde y 1 indica un borde normal.  
  
### <a name="remarks"></a>Comentarios  
 A continuación, se volverá a crear la ventana de control y `OnBorderStyleChanged` llama.  
  
##  <a name="a-namesetcapturea--colecontrolsetcapture"></a><a name="setcapture"></a>COleControl::SetCapture  
 Hace que la ventana del control contenedor tomar posesión de la captura del mouse en el nombre del control.  
  
```  
CWnd* SetCapture();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la **CWnd** objeto de ventana que recibió anteriormente la entrada del mouse.  
  
### <a name="remarks"></a>Comentarios  
 Si el control está activado y sin ventana, esta función hace que la ventana del control contenedor tomar posesión de la captura del mouse, en nombre del control. De lo contrario, esta función hace que el propio control para tomar posesión de la captura del mouse (igual que `CWnd::SetCapture`).  
  
##  <a name="a-namesetcontrolsizea--colecontrolsetcontrolsize"></a><a name="setcontrolsize"></a>COleControl::SetControlSize  
 Establece el tamaño de la ventana de control OLE y notifica al contenedor que está cambiando el sitio del control.  
  
```  
BOOL SetControlSize(int cx, int cy);
```  
  
### <a name="parameters"></a>Parámetros  
 `cx`  
 Especifica el nuevo ancho del control en píxeles.  
  
 `cy`  
 Especifica el nuevo alto del control en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la llamada se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no debe usarse en el constructor del control.  
  
 Tenga en cuenta que todas las coordenadas para ventanas de control son relativas a la esquina superior izquierda del control.  
  
##  <a name="a-namesetenableda--colecontrolsetenabled"></a><a name="setenabled"></a>COleControl::SetEnabled  
 Establece el valor de la propiedad Enabled del control de existencias.  
  
```  
void SetEnabled(BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnabled`  
 **TRUE** si el control está habilitado; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Después de establecer esta propiedad, **OnEnabledChange** se llama.  
  
##  <a name="a-namesetfocusa--colecontrolsetfocus"></a><a name="setfocus"></a>COleControl::SetFocus  
 Hace que la ventana del control contenedor tomar posesión del foco de entrada en nombre del control.  
  
```  
CWnd* SetFocus();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la **CWnd** objeto window que tenía anteriormente el foco de entrada, o **NULL** si no hay ninguna ventana.  
  
### <a name="remarks"></a>Comentarios  
 Si el control está activado y sin ventana, esta función hace que la ventana del control contenedor tomar posesión del foco de entrada en nombre del control. El foco de entrada dirige entradas mediante teclado en la ventana del contenedor y el contenedor envía todos los mensajes de teclado subsiguientes al objeto OLE que se llama `SetFocus`. Lo pierde cualquier ventana que previamente tenía el foco de entrada.  
  
 Si el control no tiene ventana, esta función hace que el propio control para tomar posesión del foco de entrada (igual que `CWnd::SetFocus`).  
  
##  <a name="a-namesetfonta--colecontrolsetfont"></a><a name="setfont"></a>COleControl::SetFont  
 Establece la propiedad Font estándar del control.  
  
```  
void SetFont(LPFONTDISP pFontDisp);
```  
  
### <a name="parameters"></a>Parámetros  
 *pFontDisp*  
 Puntero a una interfaz de envío de la fuente.  
  
##  <a name="a-namesetforecolora--colecontrolsetforecolor"></a><a name="setforecolor"></a>COleControl::SetForeColor  
 Establece el valor de propiedad estándar de color de primer plano del control.  
  
```  
void SetForeColor(OLE_COLOR dwForeColor);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwForeColor*  
 Un **OLE_COLOR** valor que se utilizará para el primer plano de dibujo del control.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el uso de esta propiedad y otras relacionadas con propiedades, vea el artículo [controles ActiveX: propiedades](../../mfc/mfc-activex-controls-properties.md).  
  
##  <a name="a-namesetinitialdataformatsa--colecontrolsetinitialdataformats"></a><a name="setinitialdataformats"></a>COleControl::SetInitialDataFormats  
 Llamado por el marco para inicializar la lista de formatos de datos admitidos por el control.  
  
```  
virtual void SetInitialDataFormats();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada especifica dos formatos: `CF_METAFILEPICT` y la propiedad persistente establecida.  
  
##  <a name="a-namesetinitialsizea--colecontrolsetinitialsize"></a><a name="setinitialsize"></a>COleControl::SetInitialSize  
 Establece el tamaño de un control cuando se muestra por primera vez en un contenedor OLE.  
  
```  
void SetInitialSize(
    int cx,  
    int cy);
```  
  
### <a name="parameters"></a>Parámetros  
 `cx`  
 Ancho inicial del control OLE en píxeles.  
  
 `cy`  
 El alto inicial del control OLE en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función en el constructor para establecer el tamaño inicial del control. El tamaño inicial se mide en unidades del dispositivo o píxeles. Se recomienda realizar la llamada en el constructor del control.  
  
##  <a name="a-namesetmodifiedflaga--colecontrolsetmodifiedflag"></a><a name="setmodifiedflag"></a>COleControl::SetModifiedFlag  
 Cambia el estado modificado de un control.  
  
```  
void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bModified`  
 El nuevo valor para el control modificada de la marca. **TRUE** indica que el estado del control se ha modificado; **FALSE** indica que ha guardado el estado del control.  
  
### <a name="remarks"></a>Comentarios  
 Llamada a esta función siempre que produce un cambio que afecte a un estado permanente de su control. Por ejemplo, si cambia el valor de una propiedad persistente, llame a esta función con `bModified` **TRUE**.  
  
##  <a name="a-namesetnotpermitteda--colecontrolsetnotpermitted"></a><a name="setnotpermitted"></a>COleControl:: SetNotPermitted  
 Indica que ha fallado una solicitud de edición.  
  
```  
void SetNotPermitted();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función cuando `BoundPropertyRequestEdit` se produce un error. Esta función produce una excepción de tipo **COleDispScodeException** para indicar que no se permite la operación de establecimiento.  
  
##  <a name="a-namesetnotsupporteda--colecontrolsetnotsupported"></a><a name="setnotsupported"></a>COleControl:: SetNotSupported  
 Evita la modificación del valor de propiedad de un control por el usuario.  
  
```  
void SetNotSupported();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función en lugar de la función de conjunto de cualquier propiedad que no se admite la modificación del valor de propiedad por el usuario del control. Un ejemplo sería una propiedad que es de sólo lectura.  
  
##  <a name="a-namesetrectincontainera--colecontrolsetrectincontainer"></a><a name="setrectincontainer"></a>COleControl::SetRectInContainer  
 Establece las coordenadas de rectángulo del control en relación con el contenedor, expresado en unidades del dispositivo.  
  
```  
BOOL SetRectInContainer(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Un puntero a un rectángulo que contiene coordenadas nuevo del control en relación con el contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la llamada se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el control está abierto, que cambia de tamaño; de lo contrario, el contenedor **OnPosRectChanged** se llama la función.  
  
##  <a name="a-namesettexta--colecontrolsettext"></a><a name="settext"></a>COleControl::SetText  
 Establece el valor de propiedad estándar de leyenda o el texto del control.  
  
```  
void SetText(LPCTSTR pszText);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszText`  
 Puntero a una cadena de caracteres.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que las propiedades de título y texto estándar se asignan ambos en el mismo valor. Esto significa que los cambios realizados en cualquiera de las propiedades cambiará automáticamente ambas propiedades. En general, un control debe admitir las existencias título o propiedad de texto, pero no ambos.  
  
##  <a name="a-namethrowerrora--colecontrolthrowerror"></a><a name="throwerror"></a>COleControl:: ThrowError  
 Indica la aparición de un error en el control.  
  
```  
void ThrowError(
    SCODE sc,  
    UINT nDescriptionID,  
    UINT nHelpID = -1);

 
void ThrowError(
    SCODE sc,  
    LPCTSTR pszDescription = NULL,  
    UINT nHelpID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `sc`  
 El valor de código de estado que se notifiquen. Para obtener una lista completa de los posibles códigos, vea el artículo [controles ActiveX: temas avanzados](../../mfc/mfc-activex-controls-advanced-topics.md).  
  
 `nDescriptionID`  
 Identificador de recurso de cadena de la excepción que se notifiquen.  
  
 `nHelpID`  
 El identificador de la Ayuda del tema para crear el informe.  
  
 `pszDescription`  
 Una cadena que contiene una explicación de la excepción que se notifiquen.  
  
### <a name="remarks"></a>Comentarios  
 Esta función solo debe llamarse desde dentro de una función Get o Set para una propiedad de OLE o la implementación de un método de automatización OLE. Si necesita señalar los errores que se producen en otras ocasiones, debe desencadenar el evento de Error estándar.  
  
##  <a name="a-nametransformcoordsa--colecontroltransformcoords"></a><a name="transformcoords"></a>COleControl::TransformCoords  
 Entre los valores de coordenadas de transformaciones **HIMETRIC** unidades y las unidades nativa del contenedor.  
  
```  
void TransformCoords(
    POINTL* lpptlHimetric,  
    POINTF* lpptfContainer,  
    DWORD flags);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpptlHimetric*  
 Puntero a un **POINTL** estructura que contiene las coordenadas en **HIMETRIC** unidades.  
  
 *lpptfContainer*  
 Puntero a un **POINTF** estructura que contiene las coordenadas en el tamaño de la unidad del contenedor.  
  
 `flags`  
 Una combinación de los siguientes valores:  
  
- **XFORMCOORDS_POSITION** una posición en el contenedor.  
  
- **XFORMCOORDS_SIZE** un tamaño en el contenedor.  
  
- **XFORMCOORDS_HIMETRICTOCONTAINER** transformar **HIMETRIC** unidades a las unidades del contenedor.  
  
- **XFORMCOORDS_CONTAINERTOHIMETRIC** transformar unidades del contenedor a **HIMETRIC** unidades.  
  
### <a name="remarks"></a>Comentarios  
 Las dos primeras marcas, **XFORMCOORDS_POSITION** y **XFORMCOORDS_SIZE**, indicar si las coordenadas se deberían tratar como una posición o un tamaño. Las dos marcas restantes indican la dirección de la transformación.  
  
##  <a name="a-nametranslatecolora--colecontroltranslatecolor"></a><a name="translatecolor"></a>COleControl::TranslateColor  
 Convierte un valor de color desde la **OLE_COLOR** tipo de datos a la [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) tipo de datos.  
  
```  
COLORREF TranslateColor(
    OLE_COLOR clrColor,  
    HPALETTE hpal = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `clrColor`  
 Un **OLE_COLOR** tipo de datos. Para obtener más información, consulte Windows [OleTranslateColor](http://msdn.microsoft.com/library/windows/desktop/ms694353) (función).  
  
 `hpal`  
 Identificador de una paleta opcional; puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color de 32 bits RGB (rojo, verde, azul) que define el sólido de color más cercana a la `clrColor` valor que represente el dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función resulta útil para traducir las propiedades estándar ForeColor y BackColor a **COLORREF** tipos utilizados por [CDC](../../mfc/reference/cdc-class.md) funciones miembro.  
  
##  <a name="a-namewillambientsbevalidduringloada--colecontrolwillambientsbevalidduringload"></a><a name="willambientsbevalidduringload"></a>COleControl::WillAmbientsBeValidDuringLoad  
 Determina si el control debe usar los valores de las propiedades de ambiente como valores predeterminados, cuando se carga posteriormente desde su estado persistente.  
  
```  
BOOL WillAmbientsBeValidDuringLoad();
```  
  
### <a name="return-value"></a>Valor devuelto  
 NonZero indica que las propiedades de ambiente será válidas; de lo contrario, las propiedades de ambiente no será válidas.  
  
### <a name="remarks"></a>Comentarios  
 En algunos de los contenedores, el control no puede tener acceso a sus propiedades de ambientales durante la llamada inicial a la invalidación de `COleControl::DoPropExchange`. Este es el caso si el contenedor llama [IPersistStreamInit:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) o [IPersistStorage:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) antes de llamar a [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) (es decir, si no se cumple la **OLEMISC_SETCLIENTSITEFIRST** bits de estado).  
  
##  <a name="a-namewindowproca--colecontrolwindowproc"></a><a name="windowproc"></a>COleControl::WindowProc  
 Proporciona un procedimiento para una `COleControl` objeto.  
  
```  
virtual LRESULT WindowProc(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `message`  
 Especifica el mensaje de Windows que se va a procesar.  
  
 `wParam`  
 Proporciona información adicional que se utilizan en el procesamiento del mensaje. El valor del parámetro depende del mensaje.  
  
 `lParam`  
 Proporciona información adicional que se utilizan en el procesamiento del mensaje. El valor del parámetro depende del mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto del mensaje enviado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para enviar mensajes específicos a través del mapa de mensajes del control.  
  
## <a name="see-also"></a>Vea también  
 [CIRC3 de ejemplo MFC](../../visual-cpp-samples.md)   
 [Ejemplo de MFC TESTHELP](../../visual-cpp-samples.md)   
 [Clase de COlePropertyPage](../../mfc/reference/colepropertypage-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CFontHolder](../../mfc/reference/cfontholder-class.md)   
 [CPictureHolder (clase)](../../mfc/reference/cpictureholder-class.md)

