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
ms.openlocfilehash: 2420e1643444e6cbbf8edff90bbd3ecb1eac8534
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320783"
---
# <a name="ccomcontrolbase-class"></a>Clase CComControlBase

Esta clase proporciona métodos para crear y administrar controles ATL.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Reemplazar si `m_nAppearance` la propiedad de stock no es de tipo **short**.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|El constructor.|
|[CComControlBase::-CComControlBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Comprueba que el parámetro *iVerb* `IOleObjectImpl::DoVerb` utilizado por activa la interfaz de usuario del control *(iVerb* es igual OLEIVERB_UIACTIVATE), define la acción realizada cuando el usuario hace doble clic en el control (*iVerb* es igual a OLEIVERB_PRIMARY), muestra el control (*iVerb* es igual a OLEIVERB_SHOW) o activa el control (*iVerb* es igual a OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Comprueba que el parámetro *iVerb* utilizado por `IOleObjectImpl::DoVerb` hace que la interfaz de usuario del control se active y devuelve TRUE.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Muestra las páginas de propiedades del control.|
|[CComControlBase::FireViewChange](#fireviewchange)|Llame a este método para indicar al contenedor que vuelva a dibujar el control o notifique a los receptores de notificaciones registrados que la vista del control ha cambiado.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Recupera DISPID_AMBIENT_APPEARANCE, la configuración de apariencia actual para el control: 0 para flat y 1 para 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Recupera DISPID_AMBIENT_AUTOCLIP, una marca que indica si el contenedor admite el recorte automático del área de visualización del control.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Recupera DISPID_AMBIENT_BACKCOLOR, el color de fondo ambiente para todos los controles, definido por el contenedor.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Recupera DISPID_AMBIENT_CHARSET, el juego de caracteres ambientales para todos los controles, definido por el contenedor.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Recupera DISPID_AMBIENT_CODEPAGE, el juego de caracteres ambientales para todos los controles, definido por el contenedor.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Recupera DISPID_AMBIENT_DISPLAYASDEFAULT, una marca que es TRUE si el contenedor ha marcado el control en este sitio para que sea un botón predeterminado y, por lo tanto, un control de botón debe dibujarse con un marco más grueso.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Recupera DISPID_AMBIENT_DISPLAYNAME, el nombre que el contenedor ha proporcionado al control.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Recupera un puntero a la `IFont` interfaz ambiental del contenedor.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Recupera un puntero a la `IFontDisp` interfaz de distribución ambiental del contenedor.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Recupera DISPID_AMBIENT_FORECOLOR, el color de primer plano ambiente para todos los controles, definido por el contenedor.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Recupera DISPID_AMBIENT_LOCALEID, el identificador del idioma utilizado por el contenedor.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Recupera DISPID_AMBIENT_MESSAGEREFLECT, una marca que indica si el contenedor desea recibir mensajes de ventana (como WM_DRAWITEM) como eventos.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Recupera DISPID_AMBIENT_PALETTE, utilizadas para tener acceso a HPALETTE del contenedor.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Recupera la propiedad contenedorespecificada por *id*.|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Recupera DISPID_AMBIENT_RIGHTTOLEFT, la dirección en la que el contenedor muestra el contenido.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Recupera DISPID_AMBIENT_SCALEUNITS, las unidades ambientales del contenedor (como pulgadas o centímetros) para las pantallas de etiquetado.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Recupera DISPID_AMBIENT_SHOWGRABHANDLES, una marca que indica si el contenedor permite que el control muestre identificadores de agarre por sí mismo cuando está activo.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Recupera DISPID_AMBIENT_SHOWHATCHING, una marca que indica si el contenedor permite que el control se muestre con un patrón sombreado cuando la interfaz de usuario está activa.|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Recupera DISPID_AMBIENT_SUPPORTSMNEMONICS, una marca que indica si el contenedor admite mnemotécnicas de teclado.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Recupera DISPID_AMBIENT_TEXTALIGN, la alineación de texto preferida por el contenedor: 0 para la alineación general (números a la derecha, texto a la izquierda), 1 para la alineación izquierda, 2 para la alineación central y 3 para la alineación derecha.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Recupera DISPID_AMBIENT_TOPTOBOTTOM, la dirección en la que el contenedor muestra el contenido.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Recupera DISPID_AMBIENT_UIDEAD, una marca que indica si el contenedor desea que el control responda a las acciones de interfaz de usuario.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Recupera DISPID_AMBIENT_USERMODE, un indicador que indica si el contenedor está en modo de ejecución (TRUE) o en modo de diseño (FALSE).|
|[CComControlBase::GetDirty](#getdirty)|Devuelve el valor `m_bRequiresSave`del miembro de datos .|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Recupera los valores x e y del numerador y el denominador del factor de zoom para un control activado para la edición in situ.|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Hace que el control pase del estado inactivo al estado que indique el verbo de *iVerb.*|
|[CComControlBase::InternalGetSite](#internalgetsite)|Llame a este método para consultar el sitio de control para un puntero a la interfaz identificada.|
|[CComControlBase::OnDraw](#ondraw)|Invalide este método para dibujar el control.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|El `OnDrawAdvanced` valor predeterminado prepara un contexto de dispositivo normalizado `OnDraw` para dibujar y, a continuación, llama al método de la clase de control.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Comprueba que el control está activo en el lugar y tiene un sitio de control válido y, a continuación, informa al contenedor de que el control ha perdido el foco.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Comprueba que la interfaz de usuario está en modo de usuario y, a continuación, activa el control.|
|[CComControlBase::OnPaint](#onpaint)|Prepara el contenedor para pintar, obtiene el área de cliente del `OnDraw` control y, a continuación, llama al método de la clase de control.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Comprueba que el control está activo en el lugar y tiene un sitio de control válido y, a continuación, informa al contenedor que el control ha ganado el foco.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Invalide este método para proporcionar sus propios controladores de acelerador de teclado.|
|[CComControlBase::SendOnClose](#sendonclose)|Notifica a todos los sumideros consultivos registrados ante el titular de la avisación que el control se ha cerrado.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Notifica a todos los receptores de asesoramiento registrados con el titular de la notificación que los datos de control han cambiado.|
|[CComControlBase::SendOnRename](#sendonrename)|Notifica a todos los sumideros consultivos registrados ante el titular de la avisación que el control tiene un nuevo apodo.|
|[CComControlBase::SendOnSave](#sendonsave)|Notifica a todos los sumideros consultivos registrados con el titular de la avisa de que se ha guardado el control.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Notifica a todos los receptores de asesoramiento registrados que la vista del control ha cambiado.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Establece o quita el foco del teclado hacia o desde el control.|
|[CComControlBase::SetDirty](#setdirty)|Establece el `m_bRequiresSave` miembro de datos en el valor en *bDirty*.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Marcador que indica que el control no puede tener ningún otro tamaño.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Marcador que `IDataObjectImpl::GetData` indica `CComControlBase::GetZoomInfo` eso y debe `m_sizeNatural` establecer `m_sizeExtent`el tamaño del control desde en lugar de desde .|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Marcador que `IDataObjectImpl::GetData` indica que debe utilizar unidades HIMETRIC y no píxeles al dibujar.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Marcador que indica que el control está activo en el lugar.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Marcador que indica que `IOleInPlaceSiteEx` el contenedor admite la interfaz y las características de control OCX96, como controles sin ventanas y sin parpadeos.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Marcador que indica si el control ha negociado con el contenedor sobre la compatibilidad con las características de control OCX96 (como controles sin parpadeos y sin ventanas) y si el control está en ventanas o sin ventanas.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Marcador que indica que el control desea recomponer su presentación cuando el contenedor cambia el tamaño de presentación del control.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Marcador que indica que el control ha cambiado desde la última vez que se guardó.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Marcador que indica que el control desea cambiar el tamaño de su extensión natural (su tamaño físico sin escala) cuando el contenedor cambia el tamaño de visualización del control.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Marcador que indica la interfaz de usuario del control, como menús y barras de herramientas, está activo.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Marcador que indica que el control está utilizando la región de ventana proporcionada por el contenedor.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Marcador que indica que el control ha estado sin ventanas, pero puede o no puede ser sin ventanas ahora.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Marca que indica el control debe tener ventanas, incluso si el contenedor admite controles sin ventanas.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Marcador que indica que el control no tiene ventanas.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Contiene una referencia al identificador de ventana asociado al control.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Un recuento del número de veces que el contenedor ha congelado eventos (se ha negado a aceptar eventos) sin un deshielo de eventos (aceptación de eventos).|
|[CComControlBase::m_rcPos](#m_rcpos)|La posición en píxeles del control, expresada en las coordenadas del contenedor.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|La extensión del control en unidades HIMETRIC (cada unidad es 0,01 milímetros) para una pantalla determinada.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|El tamaño físico del control en unidades HIMETRIC (cada unidad es 0,01 milímetros).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Un puntero directo a la conexión de asesoramiento en el contenedor [(IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)del contenedor).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Objeto `CComDispatchDriver` que permite recuperar y establecer las propiedades `IDispatch` del contenedor a través de un puntero.|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Puntero al sitio cliente del control dentro del contenedor.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Proporciona un medio estándar para mantener conexiones de asesoramiento entre objetos de datos y aconsejar receptores.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Puntero al puntero al puntero de interfaz [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) del contenedor.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Proporciona una implementación estándar de una manera de mantener conexiones de asesoramiento.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos para crear y administrar controles ATL. [CComControl (clase)](../../atl/reference/ccomcontrol-class.md) deriva de `CComControlBase`. Al crear un control Standard Control o DHTML mediante el Asistente para `CComControlBase`controles ATL, el asistente derivará automáticamente la clase de .

Para obtener más información sobre la creación de un control, vea el Tutorial de [ATL](../../atl/active-template-library-atl-tutorial.md). Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a>CComControlBase::AppearanceType

Reemplazar si `m_nAppearance` la propiedad de stock no es de tipo **short**.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Observaciones

El Asistente para controles `m_nAppearance` ATL agrega la propiedad stock de tipo short. Invalide `AppearanceType` si utiliza un tipo de datos diferente.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

El constructor.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
El identificador de la ventana asociada al control.

### <a name="remarks"></a>Observaciones

Inicializa el tamaño del control en 5080X5080 unidades HIMETRIC `CComControlBase` (2"X2") e inicializa los valores de miembro de datos en NULL o FALSE.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a>CComControlBase::-CComControlBase

Destructor.

```
~CComControlBase();
```

### <a name="remarks"></a>Observaciones

Si el control está `~CComControlBase` en ventana, lo destruye llamando a [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow).

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

Recupera un puntero a la interfaz solicitada.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
GUID de la interfaz que se solicita.

*Ppv*<br/>
Un puntero al puntero de interfaz identificado por *iid*, o NULL si no se encuentra la interfaz.

### <a name="remarks"></a>Observaciones

Solo controla las interfaces de la tabla de mapas COM.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate

Comprueba que el parámetro *iVerb* `IOleObjectImpl::DoVerb` utilizado por activa la interfaz de usuario del control *(iVerb* es igual OLEIVERB_UIACTIVATE), define la acción realizada cuando el usuario hace doble clic en el control (*iVerb* es igual a OLEIVERB_PRIMARY), muestra el control (*iVerb* es igual a OLEIVERB_SHOW) o activa el control (*iVerb* es igual a OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Valor que indica la acción `DoVerb`que debe realizar .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si *iVerb* es igual a OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW o OLEIVERB_INPLACEACTIVATE; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Observaciones

Puede invalidar este método para definir su propio verbo de activación.

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate

Comprueba que el parámetro *iVerb* utilizado por `IOleObjectImpl::DoVerb` hace que la interfaz de usuario del control se active y devuelve TRUE.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Valor que indica la acción `DoVerb`que debe realizar .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si *iVerb* es igual a OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW o OLEIVERB_INPLACEACTIVATE. De lo contrario, el método devuelve FALSE.

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a>CComControlBase::DoVerbProperties

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

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a>CComControlBase::FireViewChange

Llame a este método para indicar al contenedor que vuelva a dibujar el control o notifique a los receptores de notificaciones registrados que la vista del control ha cambiado.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si el control está activo (el miembro de datos de clase de control [CComControlBase::m_bInPlaceActive](#m_binplaceactive) es TRUE), notifica al contenedor que desea volver a dibujar todo el control. Si el control está inactivo, notifica a los receptores de notificaciones registrados del control (a través del miembro de datos de clase de control [CComControlBase::m_spAdviseSink](#m_spadvisesink)) que la vista del control ha cambiado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

Recupera DISPID_AMBIENT_APPEARANCE, la configuración de apariencia actual para el control: 0 para flat y 1 para 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parámetros

*nApariencia*<br/>
La propiedad DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

Recupera DISPID_AMBIENT_AUTOCLIP, una marca que indica si el contenedor admite el recorte automático del área de visualización del control.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parámetros

*bAutoClip*<br/>
La propiedad DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

Recupera DISPID_AMBIENT_BACKCOLOR, el color de fondo ambiente para todos los controles, definido por el contenedor.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parámetros

*BackColor*<br/>
La propiedad DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

Recupera DISPID_AMBIENT_CHARSET, el juego de caracteres ambientales para todos los controles, definido por el contenedor.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parámetros

*bstrCharSet*<br/>
La propiedad DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

Recupera DISPID_AMBIENT_CODEPAGE, la página de códigos ambientales para todos los controles, definida por el contenedor.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parámetros

*ulCodePage*<br/>
La propiedad DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

Recupera DISPID_AMBIENT_DISPLAYASDEFAULT, una marca que es TRUE si el contenedor ha marcado el control en este sitio para que sea un botón predeterminado y, por lo tanto, un control de botón debe dibujarse con un marco más grueso.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parámetros

*bDisplayAsDefault*<br/>
La propiedad DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

Recupera DISPID_AMBIENT_DISPLAYNAME, el nombre que el contenedor ha proporcionado al control.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parámetros

*bstrDisplayName*<br/>
La propiedad DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a>CComControlBase::GetAmbientFont

Recupera un puntero a la `IFont` interfaz ambiental del contenedor.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parámetros

*ppFont*<br/>
Un puntero a la interfaz [IFont](/windows/win32/api/ocidl/nn-ocidl-ifont) ambiente del contenedor.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si la propiedad es NULL, el puntero es NULL. Si el puntero no es NULL, el llamador debe liberar el puntero.

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

Recupera un puntero a la `IFontDisp` interfaz de distribución ambiental del contenedor.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parámetros

*ppFont*<br/>
Un puntero a la interfaz de envío [IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) ambiente del contenedor.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Si la propiedad es NULL, el puntero es NULL. Si el puntero no es NULL, el llamador debe liberar el puntero.

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

Recupera DISPID_AMBIENT_FORECOLOR, el color de primer plano ambiente para todos los controles, definido por el contenedor.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parámetros

*Forecolor*<br/>
La propiedad DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

Recupera DISPID_AMBIENT_LOCALEID, el identificador del idioma utilizado por el contenedor.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parámetros

*lcid*<br/>
La propiedad DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

El control puede utilizar este identificador para adaptar su interfaz de usuario a diferentes idiomas.

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

Recupera DISPID_AMBIENT_MESSAGEREFLECT, una marca que indica si el contenedor `WM_DRAWITEM`desea recibir mensajes de ventana (como ) como eventos.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parámetros

*bMessageReflect*<br/>
La propiedad DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

Recupera DISPID_AMBIENT_PALETTE, utilizadas para tener acceso a HPALETTE del contenedor.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parámetros

*hPalette*<br/>
La propiedad DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

Recupera la propiedad contenedorespecificada por *dispid*.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
Identificador de la propiedad contenedora que se va a recuperar.

*Var*<br/>
Variable para recibir la propiedad.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

ATL ha proporcionado un conjunto de funciones auxiliares para recuperar propiedades específicas, por ejemplo, [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Si no hay un método `GetAmbientProperty`adecuado disponible, utilice .

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft

Recupera DISPID_AMBIENT_RIGHTTOLEFT, la dirección en la que el contenedor muestra el contenido.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parámetros

*bRightToLeft*<br/>
La propiedad DISPID_AMBIENT_RIGHTTOLEFT. Establezca en TRUE si el contenido se muestra de derecha a izquierda, FALSE si se muestra de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits

Recupera DISPID_AMBIENT_SCALEUNITS, las unidades ambientales del contenedor (como pulgadas o centímetros) para las pantallas de etiquetado.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parámetros

*bstrScaleUnits*<br/>
La propiedad DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

Recupera DISPID_AMBIENT_SHOWGRABHANDLES, una marca que indica si el contenedor permite que el control muestre identificadores de agarre por sí mismo cuando está activo.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parámetros

*bShowGrabHandles*<br/>
La propiedad DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

Recupera DISPID_AMBIENT_SHOWHATCHING, un indicador que indica si el contenedor permite que el control se muestre con un patrón sombreado cuando la interfaz de usuario del control está activa.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parámetros

*bShowHatching*<br/>
La propiedad DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

Recupera DISPID_AMBIENT_SUPPORTSMNEMONICS, una marca que indica si el contenedor admite mnemotécnicas de teclado.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parámetros

*bSupportsMnemonics*<br/>
La propiedad DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

Recupera DISPID_AMBIENT_TEXTALIGN, la alineación de texto preferida por el contenedor: 0 para la alineación general (números a la derecha, texto a la izquierda), 1 para la alineación izquierda, 2 para la alineación central y 3 para la alineación derecha.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parámetros

*nTextAlign*<br/>
La propiedad DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

Recupera DISPID_AMBIENT_TOPTOBOTTOM, la dirección en la que el contenedor muestra el contenido.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parámetros

*bTopToBottom*<br/>
La propiedad DISPID_AMBIENT_TOPTOBOTTOM. Establezca en TRUE si el texto se muestra de arriba a abajo, FALSE si se muestra de abajo a arriba.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

Recupera DISPID_AMBIENT_UIDEAD, una marca que indica si el contenedor desea que el control responda a las acciones de interfaz de usuario.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parámetros

*bUIDead*<br/>
La propiedad DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si es TRUE, el control no debe responder. Esta marca se aplica independientemente de la DISPID_AMBIENT_USERMODE marca. Vea [CComControlBase::GetAmbientUserMode](#getambientusermode).

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

Recupera DISPID_AMBIENT_USERMODE, un indicador que indica si el contenedor está en modo de ejecución (TRUE) o en modo de diseño (FALSE).

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parámetros

*bUserMode*<br/>
La propiedad DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a>CComControlBase::GetDirty

Devuelve el valor `m_bRequiresSave`del miembro de datos .

```
BOOL GetDirty();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del miembro de datos [m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Observaciones

Este valor se establece mediante [CComControlBase::SetDirty](#setdirty).

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a>CComControlBase::GetZoomInfo

Recupera los valores x e y del numerador y el denominador del factor de zoom para un control activado para la edición in situ.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parámetros

*Di*<br/>
Estructura que contendrá el numerador y el denominador del factor de zoom. Para obtener más información, consulte [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Observaciones

El factor de zoom es la proporción del tamaño natural del control a su extensión actual.

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a>CComControlBase::InPlaceActivate

Hace que el control pase del estado inactivo al estado que indique el verbo de *iVerb.*

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Valor que indica la acción que debe realizar [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).

*prcPosRect*<br/>
Puntero a la posición del control in situ.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Antes de la activación, este método comprueba que el control tiene un sitio cliente, comprueba cuánto del control está visible y obtiene la ubicación del control en la ventana primaria. Después de activar el control, este método activa la interfaz de usuario del control e indica al contenedor que haga visible el control.

Este método también `IOleInPlaceSite`recupera `IOleInPlaceSiteEx`un `IOleInPlaceSiteWindowless` puntero de interfaz , o para el control y lo almacena en el miembro de datos de la clase de control [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Los miembros de datos de clase de control [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)y [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) se establecen en true según corresponda.

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a>CComControlBase::InternalGetSite

Llame a este método para consultar el sitio de control para un puntero a la interfaz identificada.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
El IID del puntero de interfaz que se debe devolver en *ppUnkSite*.

*ppUnkSite*<br/>
Dirección de la variable de puntero que recibe el puntero de interfaz solicitado en *riid*.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Si el sitio admite la interfaz solicitada en *riid*, el puntero se devuelve mediante *ppUnkSite*. De lo contrario, *ppUnkSite* se establece en NULL.

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a>CComControlBase::m_bAutoSize

Marcador que indica que el control no puede tener ningún otro tamaño.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Observaciones

Esta marca se `IOleObjectImpl::SetExtent` comprueba mediante y, si es TRUE, hace que la función devuelva E_FAIL.

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

Si agrega la opción **Tamaño automático** en la pestaña [Propiedades](../../atl/reference/stock-properties-atl-control-wizard.md) de stock del Asistente para controles ATL, el asistente crea automáticamente este miembro de datos en la clase de control, crea métodos put y get para la propiedad y admite [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) para notificar automáticamente al contenedor cuando cambia la propiedad.

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

Marcador que `IDataObjectImpl::GetData` indica `CComControlBase::GetZoomInfo` eso y debe `m_sizeNatural` establecer `m_sizeExtent`el tamaño del control desde en lugar de desde .

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

Marcador que `IDataObjectImpl::GetData` indica que debe utilizar unidades HIMETRIC y no píxeles al dibujar.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Observaciones

Cada unidad HIMETRIC lógica es de 0,01 milímetros.

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive

Marcador que indica que el control está activo en el lugar.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Observaciones

Esto significa que el control está visible y su ventana, si existe, está visible, pero sus menús y barras de herramientas pueden no estar activos. El `m_bUIActive` indicador indica que la interfaz de usuario del control, como los menús, también está activa.

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

Marcador que indica que `IOleInPlaceSiteEx` el contenedor admite la interfaz y las características de control OCX96, como controles sin ventanas y sin parpadeos.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

El miembro `m_spInPlaceSite` de datos apunta a un [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex), o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interfaz, dependiendo del valor de la `m_bWndLess` y `m_bInPlaceSiteEx` marcas. (El miembro `m_bNegotiatedWnd` de datos `m_spInPlaceSite` debe ser TRUE para que el puntero sea válido.)

Si `m_bWndLess` es `m_bInPlaceSiteEx` FALSE y `m_spInPlaceSite` es `IOleInPlaceSiteEx` TRUE, es un puntero de interfaz. Consulte [m_spInPlaceSite](#m_spinplacesite) para obtener una tabla que muestra la relación entre estos tres miembros de datos.

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

Marcador que indica si el control ha negociado con el contenedor sobre la compatibilidad con las características de control OCX96 (como controles sin parpadeos y sin ventanas) y si el control está en ventanas o sin ventanas.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

El `m_bNegotiatedWnd` indicador debe ser `m_spInPlaceSite` TRUE para que el puntero sea válido.

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

Marcador que indica que el control desea recomponer su presentación cuando el contenedor cambia el tamaño de presentación del control.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

[IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) comprueba esta marca y, `SetExtent` si es TRUE, notifica al contenedor de cambios de vista. si se establece esta marca, también se debe establecer el bit OLEMISC_RECOMPOSEONRESIZE de la enumeración [OLEMISC.](/windows/win32/api/oleidl/ne-oleidl-olemisc)

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

Marcador que indica que el control ha cambiado desde la última vez que se guardó.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Observaciones

El valor `m_bRequiresSave` de se puede establecer con [CComControlBase::SetDirty](#setdirty) y recuperar con [CComControlBase::GetDirty](#getdirty).

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

Marcador que indica que el control desea cambiar el tamaño de su extensión natural (su tamaño físico sin escala) cuando el contenedor cambia el tamaño de visualización del control.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Observaciones

Esta marca se `IOleObjectImpl::SetExtent` comprueba mediante y, si `SetExtent` es `m_sizeNatural`TRUE, el tamaño pasado se asigna a .

El tamaño `SetExtent` pasado siempre `m_sizeExtent`se asigna a , `m_bResizeNatural`independientemente del valor de .

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a>CComControlBase::m_bUIActive

Marcador que indica la interfaz de usuario del control, como menús y barras de herramientas, está activo.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Observaciones

El `m_bInPlaceActive` indicador indica que el control está activo, pero no que su interfaz de usuario está activa.

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

Marcador que indica que el control está utilizando la región de ventana proporcionada por el contenedor.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless

Marcador que indica que el control ha estado sin ventanas, pero puede o no puede ser sin ventanas ahora.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

Marca que indica el control debe tener ventanas, incluso si el contenedor admite controles sin ventanas.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a>CComControlBase::m_bWndLess

Marcador que indica que el control no tiene ventanas.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

El miembro `m_spInPlaceSite` de datos apunta a un [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex), o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) interfaz, dependiendo del valor de la `m_bWndLess` y [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) marcas. (El miembro de datos [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) debe ser TRUE para el [CComControlBase::m_spInPlaceSite](#m_spinplacesite) puntero sea válido.)

Si `m_bWndLess` es `m_spInPlaceSite` TRUE, `IOleInPlaceSiteWindowless` es un puntero de interfaz. Vea [CComControlBase::m_spInPlaceSite](#m_spinplacesite) para obtener una tabla que muestra la relación completa entre estos miembros de datos.

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a>CComControlBase::m_hWndCD

Contiene una referencia al identificador de ventana asociado al control.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

Un recuento del número de veces que el contenedor ha congelado eventos (se ha negado a aceptar eventos) sin un deshielo de eventos (aceptación de eventos).

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a>CComControlBase::m_rcPos

La posición en píxeles del control, expresada en las coordenadas del contenedor.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

La extensión del control en unidades HIMETRIC (cada unidad es 0,01 milímetros) para una pantalla determinada.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

Este tamaño es escalado por la pantalla. El tamaño físico del control se `m_sizeNatural` especifica en el miembro de datos y es fijo.

Puede convertir el tamaño en píxeles con la función global [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

El tamaño físico del control en unidades HIMETRIC (cada unidad es 0,01 milímetros).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

Este tamaño es fijo, `m_sizeExtent` mientras que el tamaño en es escalado por la pantalla.

Puede convertir el tamaño en píxeles con la función global [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

Un puntero directo a la conexión de asesoramiento en el contenedor [(IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)del contenedor).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

Objeto `CComDispatchDriver` que permite recuperar y establecer las propiedades `IDispatch` de un objeto a través de un puntero.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a>CComControlBase::m_spClientSite

Puntero al sitio cliente del control dentro del contenedor.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

Proporciona un medio estándar para mantener conexiones de asesoramiento entre objetos de datos y aconsejar receptores.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

Un objeto de datos es un control que puede transferir datos y que implementa [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), cuyos métodos especifican el formato y el medio de transferencia de los datos.

La `m_spDataAdviseHolder` interfaz implementa los métodos [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) e [IDataObject::DUnadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) para establecer y eliminar conexiones de asesoramiento al contenedor. El contenedor del control debe implementar un receptor advise mediante la compatibilidad con el [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) interfaz.

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

Puntero al puntero al puntero de interfaz [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)o [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) del contenedor.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

El `m_spInPlaceSite` puntero solo es válido si el [indicador m_bNegotiatedWnd](#m_bnegotiatedwnd) es TRUE.

En la tabla `m_spInPlaceSite` siguiente se muestra cómo el tipo de puntero depende de los [m_bWndLess](#m_bwndless) y [m_bInPlaceSiteEx](#m_binplacesiteex) marcas de miembro de datos:

|Tipo de m_spInPlaceSite|valor m_bWndLess|Valor m_bInPlaceSiteEx|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|VERDADERO o FALSO|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

Proporciona una implementación estándar de una manera de mantener conexiones de asesoramiento.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Para usar este miembro de datos dentro de la clase de control, debe declararlo como miembro de datos en la clase de control. La clase de control no heredará este miembro de datos de la clase base porque se declara dentro de una unión en la clase base.

La `m_spOleAdviseHolder` interfaz implementa los métodos [IOleObject::Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) y [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) para establecer y eliminar conexiones de asesoramiento al contenedor. El contenedor del control debe implementar un receptor advise mediante la compatibilidad con el [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) interfaz.

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a>CComControlBase::OnDraw

Invalide este método para dibujar el control.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parámetros

*Di*<br/>
Referencia a la [estructura ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) que contiene información de dibujo, como el aspecto de dibujo, los límites de control y si el dibujo está optimizado o no.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El `OnDraw` valor predeterminado elimina o restaura el contexto del dispositivo o no hace nada, dependiendo de los indicadores establecidos en [CComControlBase::OnDrawAdvanced](#ondrawadvanced).

Un `OnDraw` método se agrega automáticamente a la clase de control al crear el control con el Asistente para controles ATL. El valor predeterminado `OnDraw` del asistente dibuja un rectángulo con la etiqueta "ATL 8.0".

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComControlBase::GetAmbientAppearance](#getambientappearance).

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

El `OnDrawAdvanced` valor predeterminado prepara un contexto de dispositivo normalizado `OnDraw` para dibujar y, a continuación, llama al método de la clase de control.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parámetros

*Di*<br/>
Referencia a la [estructura ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) que contiene información de dibujo, como el aspecto de dibujo, los límites de control y si el dibujo está optimizado o no.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Invalide este método si desea aceptar el contexto de dispositivo pasado por el contenedor sin normalizarlo.

Consulte [CComControlBase::OnDraw](#ondraw) para obtener más detalles.

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a>CComControlBase::OnKillFocus

Comprueba que el control está activo en el lugar y tiene un sitio de control válido y, a continuación, informa al contenedor de que el control ha perdido el foco.

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
Marcador que indica si el mensaje de ventana se ha controlado correctamente. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

Comprueba que la interfaz de usuario está en modo de usuario y, a continuación, activa el control.

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
Marcador que indica si el mensaje de ventana se ha controlado correctamente. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a>CComControlBase::OnPaint

Prepara el contenedor para pintar, obtiene el área de cliente del `OnDrawAdvanced` control y, a continuación, llama al método de la clase de control.

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
Un HDC existente.

*lParam*<br/>
Reservado.

*lResult*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve cero.

### <a name="remarks"></a>Observaciones

Si *wParam* no `OnPaint` es NULL, supone que contiene un HDC válido y lo utiliza en lugar de [CComControlBase::m_hWndCD](#m_hwndcd).

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a>CComControlBase::OnSetFocus

Comprueba que el control está activo en el lugar y tiene un sitio de control válido y, a continuación, informa al contenedor que el control ha ganado el foco.

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
Marcador que indica si el mensaje de ventana se ha controlado correctamente. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Observaciones

Envía una notificación al contenedor de que el control ha recibido el foco.

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator

Invalide este método para proporcionar sus propios controladores de acelerador de teclado.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
Reservado.

*hRet*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

De forma predeterminada, devuelve FALSE.

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a>CComControlBase::SendOnClose

Notifica a todos los sumideros consultivos registrados ante el titular de la avisación que el control se ha cerrado.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Envía una notificación de que el control ha cerrado sus receptores de aviso.

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a>CComControlBase::SendOnDataChange

Notifica a todos los receptores de asesoramiento registrados con el titular de la notificación que los datos de control han cambiado.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parámetros

*advf*<br/>
Indicadores advise que especifican cómo se realiza la llamada a [IAdviseSink::OnDataChange.](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) Los valores proceden de la enumeración [ADVF.](/windows/win32/api/objidl/ne-objidl-advf)

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a>CComControlBase::SendOnRename

Notifica a todos los sumideros consultivos registrados ante el titular de la avisación que el control tiene un nuevo apodo.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parámetros

*pmk*<br/>
Puntero al nuevo apodo del control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Envía una notificación de que el moniker del control ha cambiado.

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a>CComControlBase::SendOnSave

Notifica a todos los sumideros consultivos registrados con el titular de la avisa de que se ha guardado el control.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Envía una notificación de que el control acaba de guardar sus datos.

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

Notifica a todos los receptores de asesoramiento registrados que la vista del control ha cambiado.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parámetros

*dwAspect*<br/>
El aspecto o la vista del control.

*Lindex*<br/>
Parte de la vista que ha cambiado. Solo -1 es válido.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

`SendOnViewChange`llama a [IAdviseSink::OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange). El único valor de *lindex* admitido actualmente es -1, lo que indica que toda la vista es de interés.

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

Establece o quita el foco del teclado hacia o desde el control.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parámetros

*bGrab*<br/>
Si TRUE, establece el foco del teclado en el control de llamada. Si FALSE, quita el foco del teclado del control de llamada, siempre que tenga el foco.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el control recibe correctamente el foco; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Para un control con ventanas, se llama a la función [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) de la API de Windows. Para un control sin ventanas, [IOleInPlaceSiteWindowless::SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) se llama. A través de esta llamada, un control sin ventanas obtiene el foco del teclado y puede responder a los mensajes de ventana.

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a>CComControlBase::SetDirty

Establece el `m_bRequiresSave` miembro de datos en el valor en *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parámetros

*bDirty*<br/>
Valor del miembro de datos [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Observaciones

`SetDirty(TRUE)`debe llamarse para marcar que el control ha cambiado desde la última vez que se guardó. El valor `m_bRequiresSave` de se recupera con [CComControlBase::GetDirty](#getdirty).

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
