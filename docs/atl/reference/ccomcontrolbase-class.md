---
title: Clase CComControlBase
ms.date: 11/04/2016
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 36afd716009848ccd2e2f0ab966f66f573acdfd8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497378"
---
# <a name="ccomcontrolbase-class"></a>Clase CComControlBase

Esta clase proporciona métodos para crear y administrar controles ATL.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Reemplace si la `m_nAppearance` propiedad estándar no es de tipo **Short**.|

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|El constructor.|
|[CComControlBase::~CComControlBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Comprueba que el parámetro *iVerb* usado por `IOleObjectImpl::DoVerb` activa la interfaz de usuario del control (*iVerb* es igual a OLEIVERB_UIACTIVATE), define la acción realizada cuando el usuario hace doble clic en el control (*iVerb* es igual a OLEIVERB_ PRINCIPAL), muestra el control (*iVerb* es igual a OLEIVERB_SHOW) o activa el control (*iVerb* es igual a OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Comprueba que el parámetro *iVerb* utilizado por `IOleObjectImpl::DoVerb` hace que la interfaz de usuario del control se active y devuelva true.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Muestra las páginas de propiedades del control.|
|[CComControlBase::FireViewChange](#fireviewchange)|Llame a este método para indicar al contenedor que vuelva a dibujar el control o notifique a los receptores de notificaciones registrados que la vista del control ha cambiado.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Recupera DISPID_AMBIENT_APPEARANCE, la configuración de aspecto actual del control: 0 para plano y 1 para 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Recupera DISPID_AMBIENT_AUTOCLIP, una marca que indica si el contenedor admite el recorte automático del área de presentación del control.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Recupera DISPID_AMBIENT_BACKCOLOR, el color de fondo ambiente de todos los controles definidos por el contenedor.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Recupera DISPID_AMBIENT_CHARSET, el juego de caracteres de ambiente para todos los controles definidos por el contenedor.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Recupera DISPID_AMBIENT_CODEPAGE, el juego de caracteres de ambiente para todos los controles definidos por el contenedor.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Recupera DISPID_AMBIENT_DISPLAYASDEFAULT, una marca que es TRUE si el contenedor marcó el control en este sitio para que sea un botón predeterminado y, por lo tanto, un control de botón debe dibujarse con un marco más grueso.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Recupera DISPID_AMBIENT_DISPLAYNAME, el nombre que el contenedor ha proporcionado al control.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Recupera un puntero a la interfaz de ambiente `IFont` del contenedor.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Recupera un puntero a la interfaz de envío ambiente `IFontDisp` del contenedor.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Recupera DISPID_AMBIENT_FORECOLOR, el color de primer plano ambiente para todos los controles definidos por el contenedor.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Recupera DISPID_AMBIENT_LOCALEID, el identificador del lenguaje que usa el contenedor.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Recupera DISPID_AMBIENT_MESSAGEREFLECT, una marca que indica si el contenedor desea recibir mensajes de ventana (por ejemplo, WM_DRAWITEM) como eventos.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Recupera DISPID_AMBIENT_PALETTE, que se usa para tener acceso al HPALETTE del contenedor.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Recupera la propiedad de contenedor especificada por el *identificador*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Recupera DISPID_AMBIENT_RIGHTTOLEFT, la dirección en la que el contenedor muestra el contenido.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Recupera DISPID_AMBIENT_SCALEUNITS, las unidades de ambiente del contenedor (por ejemplo, pulgadas o centímetros) de las visualizaciones de etiquetas.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Recupera DISPID_AMBIENT_SHOWGRABHANDLES, una marca que indica si el contenedor permite que el control muestre controladores de arrastre para sí mismo cuando esté activo.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Recupera DISPID_AMBIENT_SHOWHATCHING, una marca que indica si el contenedor permite que el control se muestre con un patrón sombreado cuando la interfaz de usuario está activa.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Recupera DISPID_AMBIENT_SUPPORTSMNEMONICS, una marca que indica si el contenedor admite teclas de tecla de teclado.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Recupera DISPID_AMBIENT_TEXTALIGN, la alineación de texto preferida por el contenedor: 0 para la alineación general (números a la derecha, texto a la izquierda), 1 para la alineación izquierda, 2 para la alineación del centro y 3 para la alineación derecha.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Recupera DISPID_AMBIENT_TOPTOBOTTOM, la dirección en la que el contenedor muestra el contenido.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Recupera DISPID_AMBIENT_UIDEAD, una marca que indica si el contenedor desea que el control responda a las acciones de la interfaz de usuario.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Recupera DISPID_AMBIENT_USERMODE, una marca que indica si el contenedor está en modo de ejecución (TRUE) o en modo de diseño (FALSE).|
|[CComControlBase::GetDirty](#getdirty)|Devuelve el valor del miembro `m_bRequiresSave`de datos.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Recupera los valores x e y del numerador y el denominador del factor de zoom de un control activado para la edición en contexto.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Hace que el control pase del estado inactivo a cualquier Estado que indique el verbo en *iVerb* .|
|[CComControlBase::InternalGetSite](#internalgetsite)|Llame a este método para consultar el sitio de control para un puntero a la interfaz identificada.|
|[CComControlBase::OnDraw](#ondraw)|Invalide este método para dibujar el control.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|El valor `OnDrawAdvanced` predeterminado prepara un contexto de dispositivo normalizado para dibujar y después llama al método de `OnDraw` la clase de control.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Comprueba que el control está activo en contexto y tiene un sitio de control válido y, a continuación, informa al contenedor de que el control ha perdido el foco.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Comprueba que la interfaz de usuario está en modo usuario y, a continuación, activa el control.|
|[CComControlBase::OnPaint](#onpaint)|Prepara el contenedor para pintar, obtiene el área cliente del control y, a continuación, llama al método `OnDraw` de la clase de control.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Comprueba que el control está activo en contexto y tiene un sitio de control válido y, a continuación, informa al contenedor de que el control ha obtenido el foco.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Invalide este método para proporcionar sus propios controladores de aceleradores de teclado.|
|[CComControlBase::SendOnClose](#sendonclose)|Notifica a todos los receptores de consulta registrados con el titular de la notificación de que el control se ha cerrado.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Notifica a todos los receptores de consulta registrados con el titular de la notificación que los datos del control han cambiado.|
|[CComControlBase::SendOnRename](#sendonrename)|Notifica a todos los receptores de consulta registrados con el titular de la notificación de que el control tiene un nuevo moniker.|
|[CComControlBase::SendOnSave](#sendonsave)|Notifica a todos los receptores de consulta registrados con el titular de la notificación de que el control se ha guardado.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Notifica a todos los receptores de consulta registrados que la vista del control ha cambiado.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Establece o quita el foco de teclado del control.|
|[CComControlBase::SetDirty](#setdirty)|Establece el miembro `m_bRequiresSave` de datos en el valor de *bDirty*.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Marca que indica que el control no puede tener ningún otro tamaño.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Marca que indica `IDataObjectImpl::GetData` que `CComControlBase::GetZoomInfo` y deben establecer el tamaño del `m_sizeNatural` control desde en `m_sizeExtent`lugar de desde.|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Marca que indica `IDataObjectImpl::GetData` que debe usar unidades HIMETRIC y no píxeles al dibujar.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Marca que indica que el control está activo en contexto.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Marca que indica que el contenedor `IOleInPlaceSiteEx` es compatible con las características de control de interfaz y OCX96, como controles sin ventanas y sin parpadeo.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Marca que indica si el control ha negociado o no el contenedor sobre la compatibilidad con las características de control de OCX96 (por ejemplo, los controles sin parpadeo y sin ventanas) y si el control está en ventana o sin ventana.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Marca que indica que el control desea recomponer su presentación cuando el contenedor cambia el tamaño de presentación del control.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Marca que indica que el control ha cambiado desde que se guardó por última vez.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Marca que indica que el control desea cambiar el tamaño de su extensión natural (su tamaño físico sin escalar) cuando el contenedor cambia el tamaño de presentación del control.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Marca que indica que la interfaz de usuario del control, como los menús y las barras de herramientas, está activa.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Marca que indica que el control usa la región de ventana proporcionada por el contenedor.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Marca que indica que el control ha estado sin ventana, pero puede o no tener ventana ahora.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Marca que indica que el control debe estar en la ventana, incluso si el contenedor admite controles sin ventanas.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Marca que indica que el control no tiene ventanas.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Contiene una referencia al identificador de ventana asociado al control.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Recuento del número de veces que el contenedor ha inmovilizado eventos (se ha rechazado la aceptación de eventos) sin que intervenga la reanudación de eventos (aceptación de eventos).|
|[CComControlBase::m_rcPos](#m_rcpos)|Posición en píxeles del control, expresada en las coordenadas del contenedor.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|La extensión del control en unidades HIMETRIC (cada unidad es de 0,01 milímetros) para una pantalla determinada.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Tamaño físico del control en unidades HIMETRIC (cada unidad es 0,01 milímetros).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Un puntero directo a la conexión de consulta en el contenedor (la [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)del contenedor).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Objeto que permite recuperar y establecer las propiedades del contenedor a través de un `IDispatch` puntero. `CComDispatchDriver`|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Puntero al sitio del cliente del control dentro del contenedor.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Proporciona un medio estándar para mantener las conexiones de consulta entre los objetos de datos y los receptores de notificación.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Puntero al puntero de la interfaz [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) del contenedor.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Proporciona una implementación estándar de una manera de mantener las conexiones de consulta.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona métodos para crear y administrar controles ATL. La [clase CComControl](../../atl/reference/ccomcontrol-class.md) se deriva `CComControlBase`de. Al crear un control estándar o DHTML mediante el Asistente para controles ATL, el asistente derivará automáticamente la clase de `CComControlBase`.

Para obtener más información sobre la creación de un control, vea el [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md). Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

Reemplace si la `m_nAppearance` propiedad estándar no es de tipo **Short**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Comentarios

El Asistente para controles ATL `m_nAppearance` agrega la propiedad stock de tipo Short. Reemplace `AppearanceType` si usa un tipo de datos diferente.

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

El constructor.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Identificador de la ventana asociada al control.

### <a name="remarks"></a>Comentarios

Inicializa el tamaño del control en unidades de HIMETRIC de 5080X5080 (2 "x2") e inicializa `CComControlBase` los valores del miembro de datos en null o false.

##  <a name="dtor"></a>  CComControlBase::~CComControlBase

Destructor.

```
~CComControlBase();
```

### <a name="remarks"></a>Comentarios

Si el control está en la ventana `~CComControlBase` , lo destruye llamando a [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

Recupera un puntero a la interfaz solicitada.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
GUID de la interfaz que se solicita.

*ppv*<br/>
Puntero al puntero de interfaz identificado por *IID*, o null si no se encuentra la interfaz.

### <a name="remarks"></a>Comentarios

Solo controla las interfaces de la tabla de asignación COM.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

Comprueba que el parámetro *iVerb* usado por `IOleObjectImpl::DoVerb` activa la interfaz de usuario del control (*iVerb* es igual a OLEIVERB_UIACTIVATE), define la acción realizada cuando el usuario hace doble clic en el control (*iVerb* es igual a OLEIVERB_ PRINCIPAL), muestra el control (*iVerb* es igual a OLEIVERB_SHOW) o activa el control (*iVerb* es igual a OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Valor que indica la acción que va a `DoVerb`realizar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si *iVerb* es igual a OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW o OLEIVERB_INPLACEACTIVATE; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

Puede invalidar este método para definir su propio verbo de activación.

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

Comprueba que el parámetro *iVerb* utilizado por `IOleObjectImpl::DoVerb` hace que la interfaz de usuario del control se active y devuelva true.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Valor que indica la acción que va a `DoVerb`realizar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si *iVerb* es igual a OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW o OLEIVERB_INPLACEACTIVATE. De lo contrario, el método devuelve FALSE.

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

Muestra las páginas de propiedades del control.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
Reservado.

*hwndParent*<br/>
Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

Llame a este método para indicar al contenedor que vuelva a dibujar el control o notifique a los receptores de notificaciones registrados que la vista del control ha cambiado.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si el control está activo (el miembro de datos de la clase de control [CComControlBase:: m_bInPlaceActive](#m_binplaceactive) es true), notifica al contenedor que desea volver a dibujar todo el control. Si el control está inactivo, notifica a los receptores de notificaciones registrados del control (a través del miembro de datos de la clase de control [CComControlBase:: m_spAdviseSink](#m_spadvisesink)) que la vista del control ha cambiado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

Recupera DISPID_AMBIENT_APPEARANCE, la configuración de aspecto actual del control: 0 para plano y 1 para 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parámetros

*nAppearance*<br/>
La propiedad DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

Recupera DISPID_AMBIENT_AUTOCLIP, una marca que indica si el contenedor admite el recorte automático del área de presentación del control.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parámetros

*bAutoClip*<br/>
La propiedad DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

Recupera DISPID_AMBIENT_BACKCOLOR, el color de fondo ambiente de todos los controles definidos por el contenedor.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parámetros

*BackColor*<br/>
La propiedad DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

Recupera DISPID_AMBIENT_CHARSET, el juego de caracteres de ambiente para todos los controles definidos por el contenedor.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parámetros

*bstrCharSet*<br/>
La propiedad DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

Recupera DISPID_AMBIENT_CODEPAGE, la página de códigos de ambiente para todos los controles, definida por el contenedor.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parámetros

*ulCodePage*<br/>
La propiedad DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

Recupera DISPID_AMBIENT_DISPLAYASDEFAULT, una marca que es TRUE si el contenedor marcó el control en este sitio para que sea un botón predeterminado y, por lo tanto, un control de botón debe dibujarse con un marco más grueso.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*bDisplayAsDefault*<br/>
La propiedad DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

Recupera DISPID_AMBIENT_DISPLAYNAME, el nombre que el contenedor ha proporcionado al control.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parámetros

*bstrDisplayName*<br/>
La propiedad DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

Recupera un puntero a la interfaz de ambiente `IFont` del contenedor.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parámetros

*ppFont*<br/>
Un puntero a la interfaz de ambiente [IFont](/windows/win32/api/ocidl/nn-ocidl-ifont) del contenedor.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la propiedad es NULL, el puntero es NULL. Si el puntero no es NULL, el llamador debe liberar el puntero.

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

Recupera un puntero a la interfaz de envío ambiente `IFontDisp` del contenedor.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parámetros

*ppFont*<br/>
Un puntero a la interfaz de envío del ambiente de [IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) del contenedor.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Si la propiedad es NULL, el puntero es NULL. Si el puntero no es NULL, el llamador debe liberar el puntero.

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

Recupera DISPID_AMBIENT_FORECOLOR, el color de primer plano ambiente para todos los controles definidos por el contenedor.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parámetros

*ForeColor*<br/>
La propiedad DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

Recupera DISPID_AMBIENT_LOCALEID, el identificador del lenguaje que usa el contenedor.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parámetros

*lcid*<br/>
La propiedad DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

El control puede usar este identificador para adaptar su interfaz de usuario a diferentes idiomas.

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

Recupera DISPID_AMBIENT_MESSAGEREFLECT, una marca que indica si el contenedor desea recibir mensajes de ventana ( `WM_DRAWITEM`como) como eventos.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parámetros

*bMessageReflect*<br/>
La propiedad DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

Recupera DISPID_AMBIENT_PALETTE, que se usa para tener acceso al HPALETTE del contenedor.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parámetros

*hPalette*<br/>
La propiedad DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

Recupera la propiedad de contenedor especificada por *DISPID*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
Identificador de la propiedad de contenedor que se va a recuperar.

*var*<br/>
Variable para recibir la propiedad.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

ATL ha proporcionado un conjunto de funciones auxiliares para recuperar propiedades específicas, por ejemplo, [CComControlBase:: GetAmbientBackColor](#getambientbackcolor). Si no hay ningún método adecuado disponible, use `GetAmbientProperty`.

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

Recupera DISPID_AMBIENT_RIGHTTOLEFT, la dirección en la que el contenedor muestra el contenido.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parámetros

*bRightToLeft*<br/>
La propiedad DISPID_AMBIENT_RIGHTTOLEFT. Establézcalo en TRUE si el contenido se muestra de derecha a izquierda, FALSE si se muestra de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

Recupera DISPID_AMBIENT_SCALEUNITS, las unidades de ambiente del contenedor (por ejemplo, pulgadas o centímetros) de las visualizaciones de etiquetas.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parámetros

*bstrScaleUnits*<br/>
La propiedad DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

Recupera DISPID_AMBIENT_SHOWGRABHANDLES, una marca que indica si el contenedor permite que el control muestre controladores de arrastre para sí mismo cuando esté activo.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parámetros

*bShowGrabHandles*<br/>
La propiedad DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

Recupera DISPID_AMBIENT_SHOWHATCHING, una marca que indica si el contenedor permite que el control se muestre con un patrón sombreado cuando la interfaz de usuario del control está activa.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parámetros

*bShowHatching*<br/>
La propiedad DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

Recupera DISPID_AMBIENT_SUPPORTSMNEMONICS, una marca que indica si el contenedor admite teclas de tecla de teclado.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parámetros

*bSupportsMnemonics*<br/>
La propiedad DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

Recupera DISPID_AMBIENT_TEXTALIGN, la alineación de texto preferida por el contenedor: 0 para la alineación general (números a la derecha, texto a la izquierda), 1 para la alineación izquierda, 2 para la alineación del centro y 3 para la alineación derecha.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parámetros

*nTextAlign*<br/>
La propiedad DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

Recupera DISPID_AMBIENT_TOPTOBOTTOM, la dirección en la que el contenedor muestra el contenido.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parámetros

*bTopToBottom*<br/>
La propiedad DISPID_AMBIENT_TOPTOBOTTOM. Establézcalo en TRUE si el texto se muestra de arriba abajo, FALSE si se muestra de abajo a arriba.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

Recupera DISPID_AMBIENT_UIDEAD, una marca que indica si el contenedor desea que el control responda a las acciones de la interfaz de usuario.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parámetros

*bUIDead*<br/>
La propiedad DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si es TRUE, el control no debe responder. Esta marca se aplica independientemente de la marca DISPID_AMBIENT_USERMODE. Vea [CComControlBase:: GetAmbientUserMode](#getambientusermode).

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

Recupera DISPID_AMBIENT_USERMODE, una marca que indica si el contenedor está en modo de ejecución (TRUE) o en modo de diseño (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parámetros

*bUserMode*<br/>
La propiedad DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="getdirty"></a>  CComControlBase::GetDirty

Devuelve el valor del miembro `m_bRequiresSave`de datos.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del miembro de datos [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Comentarios

Este valor se establece mediante [CComControlBase:: SetDirty](#setdirty).

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

Recupera los valores x e y del numerador y el denominador del factor de zoom de un control activado para la edición en contexto.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parámetros

*di*<br/>
La estructura que contendrá el numerador y el denominador del factor de zoom. Para obtener más información, vea [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Comentarios

El factor de zoom es la proporción del tamaño natural del control con respecto a su extensión actual.

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

Hace que el control pase del estado inactivo a cualquier Estado que indique el verbo en *iVerb* .

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Valor que indica la acción que va a realizar [IOleObjectImpl::D overb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Puntero a la posición del control en contexto.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Antes de la activación, este método comprueba que el control tiene un sitio de cliente, comprueba la parte del control visible y obtiene la ubicación del control en la ventana primaria. Una vez activado el control, este método activa la interfaz de usuario del control e indica al contenedor que haga visible el control.

Este método también recupera un `IOleInPlaceSite`puntero de interfaz, `IOleInPlaceSiteWindowless` `IOleInPlaceSiteEx`o para el control y lo almacena en el miembro de datos de la clase de control [CComControlBase:: m_spInPlaceSite](#m_spinplacesite). Los miembros de datos de la clase de control [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase:: m_bWndLess](#m_bwndless), [CComControlBase:: M_bWasOnceWindowless](#m_bwasoncewindowless)y [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) se establecen en true según corresponda.

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

Llame a este método para consultar el sitio de control para un puntero a la interfaz identificada.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
IID del puntero de interfaz que se debe devolver en *ppUnkSite*.

*ppUnkSite*<br/>
Dirección de la variable de puntero que recibe el puntero de interfaz solicitado en *riid*.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Si el sitio admite la interfaz solicitada en *riid*, el puntero se devuelve por medio de *ppUnkSite*. De lo contrario, *ppUnkSite* se establece en NULL.

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

Marca que indica que el control no puede tener ningún otro tamaño.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Comentarios

Esta marca está activada por `IOleObjectImpl::SetExtent` y, si es true, hace que la función devuelva E_FAIL.

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

Si agrega la opción **tamaño automático** en la pestaña [propiedades estándar](../../atl/reference/stock-properties-atl-control-wizard.md) del Asistente para controles ATL, el asistente crea automáticamente este miembro de datos en la clase de control, crea los métodos Put y Get para la propiedad y admite [IPropertyNotifySink ](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)para notificar automáticamente al contenedor cuando cambia la propiedad.

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

Marca que indica `IDataObjectImpl::GetData` que `CComControlBase::GetZoomInfo` y deben establecer el tamaño del `m_sizeNatural` control desde en `m_sizeExtent`lugar de desde.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

Marca que indica `IDataObjectImpl::GetData` que debe usar unidades HIMETRIC y no píxeles al dibujar.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Comentarios

Cada unidad lógica de HIMETRIC es de 0,01 milímetros.

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

Marca que indica que el control está activo en contexto.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Comentarios

Esto significa que el control está visible y su ventana, si la hay, está visible, pero es posible que sus menús y barras de herramientas no estén activos. La `m_bUIActive` marca indica que la interfaz de usuario del control, como los menús, también está activa.

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

Marca que indica que el contenedor `IOleInPlaceSiteEx` es compatible con las características de control de interfaz y OCX96, como controles sin ventanas y sin parpadeo.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

El miembro `m_spInPlaceSite` de datos apunta a una interfaz [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) , dependiendo del valor de las `m_bWndLess` marcas y. `m_bInPlaceSiteEx` (El miembro `m_bNegotiatedWnd` de datos debe ser true para `m_spInPlaceSite` que el puntero sea válido).

Si `m_bWndLess` es false y `m_bInPlaceSiteEx` es true, `m_spInPlaceSite` es un `IOleInPlaceSiteEx` puntero de interfaz. Consulte [m_spInPlaceSite](#m_spinplacesite) para obtener una tabla que muestra la relación entre estos tres miembros de datos.

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

Marca que indica si el control ha negociado o no el contenedor sobre la compatibilidad con las características de control de OCX96 (por ejemplo, los controles sin parpadeo y sin ventanas) y si el control está en ventana o sin ventana.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

La `m_bNegotiatedWnd` marca debe ser true para que `m_spInPlaceSite` el puntero sea válido.

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

Marca que indica que el control desea recomponer su presentación cuando el contenedor cambia el tamaño de presentación del control.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

Esta marca se comprueba por [IOleObjectImpl:: SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) y, si es true `SetExtent` , notifica al contenedor de los cambios de la vista. Si se establece esta marca, también se debe establecer el bit OLEMISC_RECOMPOSEONRESIZE en la enumeración [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) .

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

Marca que indica que el control ha cambiado desde que se guardó por última vez.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Comentarios

El valor de `m_bRequiresSave` se puede establecer con [CComControlBase:: SetDirty](#setdirty) y recuperar con [CComControlBase:: GetDirty](#getdirty).

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

Marca que indica que el control desea cambiar el tamaño de su extensión natural (su tamaño físico sin escalar) cuando el contenedor cambia el tamaño de presentación del control.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Comentarios

Esta marca está activada por `IOleObjectImpl::SetExtent` y, si es true, el tamaño que `SetExtent` se pasa a `m_sizeNatural`se asigna a.

El tamaño pasado `SetExtent` siempre se asigna a `m_sizeExtent`, independientemente del valor de `m_bResizeNatural`.

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

Marca que indica que la interfaz de usuario del control, como los menús y las barras de herramientas, está activa.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Comentarios

La `m_bInPlaceActive` marca indica que el control está activo, pero no que su interfaz de usuario está activa.

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

Marca que indica que el control usa la región de ventana proporcionada por el contenedor.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

Marca que indica que el control ha estado sin ventana, pero puede o no tener ventana ahora.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

Marca que indica que el control debe estar en la ventana, incluso si el contenedor admite controles sin ventanas.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess

Marca que indica que el control no tiene ventanas.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

El `m_spInPlaceSite` miembro de datos apunta a una interfaz [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) , en función del valor de las `m_bWndLess` marcas y [CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex) . (El miembro de datos [CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd) debe ser true para que el puntero [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) sea válido).

Si `m_bWndLess` es true, `m_spInPlaceSite` es un `IOleInPlaceSiteWindowless` puntero de interfaz. Vea [CComControlBase:: m_spInPlaceSite](#m_spinplacesite) para obtener una tabla que muestra la relación completa entre estos miembros de datos.

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

Contiene una referencia al identificador de ventana asociado al control.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

Recuento del número de veces que el contenedor ha inmovilizado eventos (se ha rechazado la aceptación de eventos) sin que intervenga la reanudación de eventos (aceptación de eventos).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

Posición en píxeles del control, expresada en las coordenadas del contenedor.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent

La extensión del control en unidades HIMETRIC (cada unidad es de 0,01 milímetros) para una pantalla determinada.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

La pantalla escala este tamaño. El tamaño físico del control se especifica en el `m_sizeNatural` miembro de datos y es fijo.

Puede convertir el tamaño en píxeles con la función global [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

Tamaño físico del control en unidades HIMETRIC (cada unidad es 0,01 milímetros).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

Este tamaño es fijo, mientras que la pantalla `m_sizeExtent` escala el tamaño de.

Puede convertir el tamaño en píxeles con la función global [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

Un puntero directo a la conexión de consulta en el contenedor (la [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)del contenedor).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

Objeto que permite recuperar y establecer las propiedades de un objeto a través de `IDispatch` un puntero. `CComDispatchDriver`

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

Puntero al sitio del cliente del control dentro del contenedor.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

Proporciona un medio estándar para mantener las conexiones de consulta entre los objetos de datos y los receptores de notificación.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

Un objeto de datos es un control que puede transferir datos y que implementa [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), cuyos métodos especifican el formato y transfieren el medio de los datos.

La interfaz `m_spDataAdviseHolder` implementa los métodos [IDataObject::D Advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) y [IDataObject::D unvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) para establecer y eliminar conexiones de consulta al contenedor. El contenedor del control debe implementar un receptor de notificaciones mediante la compatibilidad con la interfaz [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

Puntero al puntero de la interfaz [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) del contenedor.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

El `m_spInPlaceSite` puntero solo es válido si la marca [m_bNegotiatedWnd](#m_bnegotiatedwnd) es true.

En la tabla siguiente se muestra `m_spInPlaceSite` cómo el tipo de puntero depende de las marcas de miembro de datos [m_bWndLess](#m_bwndless) y [m_bInPlaceSiteEx](#m_binplacesiteex) :

|Tipo m_spInPlaceSite|Valor m_bWndLess|Valor m_bInPlaceSiteEx|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|TRUE o FALSE|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

Proporciona una implementación estándar de una manera de mantener las conexiones de consulta.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una Unión en la clase base.

La interfaz `m_spOleAdviseHolder` implementa los métodos [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) y [IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) para establecer y eliminar las conexiones de consulta con el contenedor. El contenedor del control debe implementar un receptor de notificaciones mediante la compatibilidad con la interfaz [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) .

##  <a name="ondraw"></a>  CComControlBase::OnDraw

Invalide este método para dibujar el control.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parámetros

*di*<br/>
Referencia a la estructura [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) que contiene información de dibujo, como el aspecto del dibujo, los límites del control y si el dibujo está optimizado o no.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El valor `OnDraw` predeterminado elimina o restaura el contexto del dispositivo o no hace nada, según las marcas establecidas en [CComControlBase:: OnDrawAdvanced](#ondrawadvanced).

Un `OnDraw` método se agrega automáticamente a la clase de control al crear el control con el Asistente para controles ATL. De forma predeterminada `OnDraw` , el asistente dibuja un rectángulo con la etiqueta "ATL 8,0".

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComControlBase:: GetAmbientAppearance](#getambientappearance).

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

El valor `OnDrawAdvanced` predeterminado prepara un contexto de dispositivo normalizado para dibujar y después llama al método de `OnDraw` la clase de control.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parámetros

*di*<br/>
Referencia a la estructura [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) que contiene información de dibujo, como el aspecto del dibujo, los límites del control y si el dibujo está optimizado o no.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Invalide este método si desea aceptar el contexto de dispositivo que pasa el contenedor sin normalizarlo.

Vea [CComControlBase:: OnDraw](#ondraw) para obtener más detalles.

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

Comprueba que el control está activo en contexto y tiene un sitio de control válido y, a continuación, informa al contenedor de que el control ha perdido el foco.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parámetros

*nMsg*<br/>
Reservado.

*wParam*<br/>
Reservado.

*lParam*<br/>
Reservado.

*bHandled*<br/>
Marca que indica si el mensaje de ventana se controló correctamente. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

Comprueba que la interfaz de usuario está en modo usuario y, a continuación, activa el control.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parámetros

*nMsg*<br/>
Reservado.

*wParam*<br/>
Reservado.

*lParam*<br/>
Reservado.

*bHandled*<br/>
Marca que indica si el mensaje de ventana se controló correctamente. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

##  <a name="onpaint"></a>  CComControlBase::OnPaint

Prepara el contenedor para pintar, obtiene el área cliente del control y, a continuación, llama al método `OnDrawAdvanced` de la clase de control.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parámetros

*nMsg*<br/>
Reservado.

*wParam*<br/>
Cámara existente HDC.

*lParam*<br/>
Reservado.

*lResult*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve cero.

### <a name="remarks"></a>Comentarios

Si *wParam* no es null, `OnPaint` se supone que contiene un HDC válido y lo usa en lugar de [CComControlBase:: m_hWndCD](#m_hwndcd).

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

Comprueba que el control está activo en contexto y tiene un sitio de control válido y, a continuación, informa al contenedor de que el control ha obtenido el foco.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parámetros

*nMsg*<br/>
Reservado.

*wParam*<br/>
Reservado.

*lParam*<br/>
Reservado.

*bHandled*<br/>
Marca que indica si el mensaje de ventana se controló correctamente. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Comentarios

Envía una notificación al contenedor en el que el control ha recibido el foco.

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

Invalide este método para proporcionar sus propios controladores de aceleradores de teclado.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parámetros

*pMsg*<br/>
Reservado.

*hRet*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

De forma predeterminada, devuelve FALSE.

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

Notifica a todos los receptores de consulta registrados con el titular de la notificación de que el control se ha cerrado.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Envía una notificación de que el control ha cerrado sus receptores de consulta.

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

Notifica a todos los receptores de consulta registrados con el titular de la notificación que los datos del control han cambiado.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parámetros

*advf*<br/>
Marcas de Advise que especifican cómo se realiza la llamada a [IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) . Los valores proceden de la enumeración [ADVF](/windows/win32/api/objidl/ne-objidl-advf) .

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

Notifica a todos los receptores de consulta registrados con el titular de la notificación de que el control tiene un nuevo moniker.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parámetros

*pmk*<br/>
Puntero al nuevo moniker del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Envía una notificación de que el moniker del control ha cambiado.

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

Notifica a todos los receptores de consulta registrados con el titular de la notificación de que el control se ha guardado.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Envía una notificación de que el control acaba de guardar sus datos.

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

Notifica a todos los receptores de consulta registrados que la vista del control ha cambiado.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parámetros

*dwAspect*<br/>
Aspecto o vista del control.

*lindex*<br/>
Parte de la vista que ha cambiado. Solo-1 es válido.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

`SendOnViewChange`llama a [IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). El único valor de *lIndex* que se admite actualmente es-1, que indica que toda la vista es de interés.

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

Establece o quita el foco de teclado del control.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parámetros

*bGrab*<br/>
Si es TRUE, establece el foco de teclado en el control que realiza la llamada. Si es FALSE, quita el foco de teclado del control que realiza la llamada, siempre que tenga el foco.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el control recibe correctamente el foco; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para un control con ventana, se llama a la función de la API de Windows [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) . Para un control sin ventana, se llama a [IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) . A través de esta llamada, un control sin ventanas obtiene el foco del teclado y puede responder a los mensajes de ventana.

##  <a name="setdirty"></a>  CComControlBase::SetDirty

Establece el miembro `m_bRequiresSave` de datos en el valor de *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parámetros

*bDirty*<br/>
Valor del miembro de datos [CComControlBase:: m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Comentarios

`SetDirty(TRUE)`se debe llamar a para indicar que el control ha cambiado desde que se guardó por última vez. El valor de `m_bRequiresSave` se recupera con [CComControlBase:: GetDirty](#getdirty).

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
