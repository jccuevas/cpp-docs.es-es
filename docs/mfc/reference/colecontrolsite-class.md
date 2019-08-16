---
title: Clase COleControlSite
ms.date: 11/04/2016
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
ms.openlocfilehash: 9b9b68a001acdf4b08d9cfc01cc67c43217d9a57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504315"
---
# <a name="colecontrolsite-class"></a>Clase COleControlSite

Proporciona compatibilidad con interfaces de control de cliente personalizadas.

## <a name="syntax"></a>Sintaxis

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|Construye un objeto `COleControlSite`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Enlaza la propiedad predeterminada del control hospedado a un origen de datos.|
|[COleControlSite::BindProperty](#bindproperty)|Enlaza una propiedad del control hospedado a un origen de datos.|
|[COleControlSite::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|
|[COleControlSite::DestroyControl](#destroycontrol)|Destruye el control hospedado.|
|[COleControlSite::DoVerb](#doverb)|Ejecuta un verbo específico del control hospedado.|
|[COleControlSite::EnableDSC](#enabledsc)|Habilita el origen de datos para un sitio de control.|
|[COleControlSite::EnableWindow](#enablewindow)|Habilita el sitio de control.|
|[COleControlSite::FreezeEvents](#freezeevents)|Especifica si el sitio del control está aceptando eventos.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Recupera el código de botón predeterminado para el control hospedado.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Recupera el identificador del control.|
|[COleControlSite::GetEventIID](#geteventiid)|Recupera el identificador de una interfaz de eventos para un control hospedado.|
|[COleControlSite::GetExStyle](#getexstyle)|Recupera los estilos extendidos del sitio del control.|
|[COleControlSite::GetProperty](#getproperty)|Recupera una propiedad concreta del control hospedado.|
|[COleControlSite::GetStyle](#getstyle)|Recupera los estilos del sitio del control.|
|[COleControlSite::GetWindowText](#getwindowtext)|Recupera el texto del control hospedado.|
|[COleControlSite::InvokeHelper](#invokehelper)|Invocar un método específico del control hospedado.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|Invocar un método específico del control hospedado con una lista variable de argumentos.|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Determina si el control es el botón predeterminado en la ventana.|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Comprueba el estado visible del sitio de control.|
|[COleControlSite::ModifyStyle](#modifystyle)|Modifica los estilos extendidos actuales del sitio del control.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modifica los estilos actuales del sitio del control.|
|[COleControlSite::MoveWindow](#movewindow)|Cambia la posición del sitio del control.|
|[COleControlSite::QuickActivate](#quickactivate)|Activa de forma rápida el control hospedado.|
|[COleControlSite::SafeSetProperty](#safesetproperty)|Establece una propiedad o un método del control sin posibilidad de producir una excepción.|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Establece el botón predeterminado en la ventana.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Recupera el identificador del control.|
|[COleControlSite::SetFocus](#setfocus)|Establece el foco en el sitio del control.|
|[COleControlSite::SetProperty](#setproperty)|Establece una propiedad concreta del control hospedado.|
|[COleControlSite::SetPropertyV](#setpropertyv)|Establece una propiedad específica del control hospedado con una lista variable de argumentos.|
|[COleControlSite::SetWindowPos](#setwindowpos)|Establece la posición del sitio del control.|
|[COleControlSite::SetWindowText](#setwindowtext)|Establece el texto del control hospedado.|
|[COleControlSite::ShowWindow](#showwindow)|Muestra u oculta el sitio de control.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Recupera la información de teclado y las teclas de tecla del control hospedado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Determina si el control hospedado es un control sin ventana.|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Contiene información sobre la administración de teclado para el control.|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Cookie del punto de conexión del control.|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Estados varios para el control hospedado.|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Cookie del control.|
|[COleControlSite::m_dwStyle](#m_dwstyle)|Estilos del control hospedado.|
|[COleControlSite::m_hWnd](#m_hwnd)|Identificador del sitio del control.|
|[COleControlSite::m_iidEvents](#m_iidevents)|IDENTIFICADOR de la interfaz de eventos para el control hospedado.|
|[COleControlSite::m_nID](#m_nid)|IDENTIFICADOR del control hospedado.|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Puntero al `IOleInPlaceActiveObject` objeto del control hospedado.|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Contenedor del control hospedado.|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Puntero al `IOleInPlaceObject` objeto del control hospedado.|
|[COleControlSite::m_pObject](#m_pobject)|Puntero a la `IOleObjectInterface` interfaz del control.|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Puntero a la `IOleInPlaceObjectWindowless` interfaz del control.|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Puntero al objeto de ventana para el control hospedado.|
|[COleControlSite::m_rect](#m_rect)|Dimensiones del sitio del control.|

## <a name="remarks"></a>Comentarios

Esta compatibilidad es el medio principal por el que un control ActiveX incrustado obtiene información sobre la ubicación y la extensión de su sitio de presentación, su moniker, su interfaz de usuario, sus propiedades de ambiente y otros recursos proporcionados por su contenedor. `COleControlSite`implementa todas las interfaces [IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite), [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), `IBoundObjectSite`, `INotifyDBEvents`y [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) . Además, también se implementa la interfaz IDispatch (que proporciona compatibilidad con propiedades de ambiente y receptores de eventos).

Para crear un sitio de control ActiveX `COleControlSite`mediante, derive una clase `COleControlSite`de. En la clase derivada de para el contenedor (por ejemplo, el cuadro de diálogo), `CWnd::CreateControlSite` invalide la función. `CWnd`

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxocc. h

##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty

Enlaza la propiedad enlazada simple predeterminada del objeto que realiza la llamada, como se marca en la biblioteca de tipos, al cursor subyacente definido por las propiedades DataSource, UserName, password y SQL del control de origen de datos.

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Especifica el DISPID de una propiedad en un control enlazado a datos que se va a enlazar a un control de origen de datos.

*vtProp*<br/>
Especifica el tipo de la propiedad que se va a enlazar (por ejemplo, VT_BSTR, VT_VARIANT, etc.).

*szFieldName*<br/>
Especifica el nombre de la columna, en el cursor proporcionado por el control de origen de datos, al que se enlazará la propiedad.

*pDSCWnd*<br/>
Puntero al `CWnd`objeto derivado de que hospeda el control de origen de datos al que se enlazará la propiedad.

### <a name="remarks"></a>Comentarios

El `CWnd` objeto en el que se llama a esta función debe ser un control enlazado a datos.

##  <a name="bindproperty"></a>  COleControlSite::BindProperty

Enlaza la propiedad enlazada simple del objeto que realiza la llamada, como se marca en la biblioteca de tipos, al cursor subyacente definido por las propiedades DataSource, UserName, password y SQL del control de origen de datos.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>Parámetros

*dwDispId*<br/>
Especifica el DISPID de una propiedad en un control enlazado a datos que se va a enlazar a un control de origen de datos.

*pWndDSC*<br/>
Puntero al `CWnd`objeto derivado de que hospeda el control de origen de datos al que se enlazará la propiedad.

### <a name="remarks"></a>Comentarios

El `CWnd` objeto en el que se llama a esta función debe ser un control enlazado a datos.

##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite

Construye un nuevo objeto `COleControlSite`.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parámetros

*pCtrlCont*<br/>
Puntero al contenedor del control (que representa la ventana que hospeda el control AtiveX).

### <a name="remarks"></a>Comentarios

La función [COccManager:: CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) llama a esta función. Para obtener más información sobre la personalización de la creación de contenedores, vea [COccManager:: CreateSite](../../mfc/reference/coccmanager-class.md#createsite).

##  <a name="createcontrol"></a>  COleControlSite::CreateControl

Crea un control ActiveX, hospedado por `COleControlSite` el objeto.

```
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);

virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>Parámetros

*pWndCtrl*<br/>
Puntero al objeto Window que representa el control.

*clsid*<br/>
IDENTIFICADOR de clase único del control.

*lpszWindowName*<br/>
Puntero al texto que se va a mostrar en el control. Establece el valor de la propiedad de texto o la leyenda del winodw (si existe).

*dwStyle*<br/>
Estilos de Windows. Los estilos disponibles se enumeran en la sección **comentarios** .

*rect*<br/>
Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto o una `RECT` estructura.

*nID*<br/>
Especifica el identificador de la ventana secundaria del control.

*pPersist*<br/>
Un puntero a un `CFile` que contiene el estado persistente del control. El valor predeterminado es NULL, lo que indica que el control se inicializa sin restaurar su estado desde un almacenamiento persistente. Si no es null, debe ser un puntero a un `CFile`objeto derivado de que contenga los datos persistentes del control, en forma de una secuencia o un almacenamiento. Estos datos se podrían haber guardado en una activación anterior del cliente. Puede contener otros datos, pero debe tener su puntero de lectura y escritura establecido en el primer byte de datos persistentes en el momento de la llamada `CreateControl`a. `CFile`

*bStorage*<br/>
Indica si los datos de *pPersist* deben interpretarse como `IStorage` datos `IStream` de o. Si los datos de *pPersist* son un almacenamiento, *BSTORAGE* debe ser true. Si los datos de *pPersist* son una secuencia, *BSTORAGE* debe ser false. El valor predeterminado es FALSE.

*bstrLicKey*<br/>
Datos de clave de licencia opcionales. Estos datos solo son necesarios para crear controles que requieran una clave de licencia en tiempo de ejecución. Si el control admite las licencias, debe proporcionar una clave de licencia para que la creación del control se realice correctamente. El valor predeterminado es NULL.

*ppt*<br/>
Puntero a una `POINT` estructura que contiene la esquina superior izquierda del control. El tamaño del control viene determinado por el valor de *psize*. Los valores *PPT* y *psize* son un método opcional para especificar el tamaño y la posición las el control.

*psize*<br/>
Puntero a una `SIZE` estructura que contiene el tamaño del control. La esquina superior izquierda viene determinada por el valor de *PPT*. Los valores *PPT* y *psize* son un método opcional para especificar el tamaño y la posición las el control.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Solo se admite `CreateControl`un subconjunto de las marcas *dwStyle* de Windows:

- WS_VISIBLE crea una ventana que está inicialmente visible. Necesario si desea que el control esté visible inmediatamente, como las ventanas normales.

- WS_DISABLED crea una ventana que está deshabilitada inicialmente. Una ventana deshabilitada no puede recibir entradas del usuario. Se puede establecer si el control tiene una propiedad habilitada.

- WS_BORDER crea una ventana con un borde de línea fina. Se puede establecer si el control tiene una propiedad BorderStyle.

- WS_GROUP especifica el primer control de un grupo de controles. El usuario puede cambiar el foco del teclado de un control del grupo al siguiente mediante las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo e inicia el grupo siguiente.

- WS_TABSTOP especifica un control que puede recibir el foco del teclado cuando el usuario presiona la tecla TAB. Al presionar la tecla TAB, el foco de teclado cambia al siguiente control del estilo WS_TABSTOP.

Use la segunda sobrecarga para crear controles de tamaño predeterminado.

##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl

Destruye el objeto `COleControlSite`.

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Una vez completado, el objeto se libera de la memoria y los punteros al objeto ya no son válidos.

##  <a name="doverb"></a>  COleControlSite::DoVerb

Ejecuta el verbo especificado.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>Parámetros

*nVerb*<br/>
Especifica el verbo que se va a ejecutar. Puede incluir una de las siguientes opciones:

|Valor|Significado|Símbolo|
|-----------|-------------|------------|
|0|verbo principal|OLEIVERB_PRIMARY|
|-1|Verbo secundario|(Ninguno)|
|1|Muestra el objeto para su edición.|OLEIVERB_SHOW|
|-2|Edita el elemento en una ventana independiente.|OLEIVERB_OPEN|
|-3|Oculta el objeto.|OLEIVERB_HIDE|
|-4|Activa un control en contexto.|OLEIVERB_UIACTIVATE|
|-5|Activa un control en contexto, sin elementos de interfaz de usuario adicionales.|OLEIVERB_INPLACEACTIVATE|
|-7|Muestra las propiedades del control.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
Puntero al mensaje que hizo que se activara el elemento.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Esta función llama directamente a través de la `IOleObject` interfaz del control para ejecutar el verbo especificado. Si se produce una excepción como resultado de esta llamada de función, se devuelve un código de error HRESULT.

Para obtener más información, vea [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

##  <a name="enabledsc"></a>  COleControlSite::EnableDSC

Habilita el origen de datos para el sitio de control.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Comentarios

Lo llama el marco de trabajo para habilitar e inicializar el origen de datos para el sitio de control. Invalide esta función para proporcionar un comportamiento personalizado.

##  <a name="enablewindow"></a>COleControlSite::EnableWindow

Habilita o deshabilita la entrada del mouse y del teclado en el sitio del control.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
Especifica si se debe habilitar o deshabilitar la ventana: TRUE si la entrada de la ventana se va a habilitar; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la ventana estaba deshabilitada previamente; de lo contrario, es 0.

##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents

Especifica si el sitio de control controlará o omitirá los eventos desencadenados por un control.

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parámetros

*bFreeze*<br/>
Especifica si el sitio del control desea dejar de aceptar eventos. Distinto de cero si el control no acepta eventos; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Si *bFreeze* es true, el sitio de control solicita el control para detener los eventos de Halo. Si *bFreeze* es false, el sitio de control solicita el control para continuar con la activación de eventos.

> [!NOTE]
>  No es necesario que el control detenga los eventos de activación si lo solicita el sitio del control. Puede continuar la activación, pero el sitio de control omitirá todos los eventos subsiguientes.

##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo

Recupera información sobre las teclas de teclado y el comportamiento del teclado de un control.

```
void GetControlInfo();
```

### <a name="remarks"></a>Comentarios

La información se almacena en [COleControlSite:: m_ctlInfo](#m_ctlinfo).

##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode

Determina si el control es un botón de envío predeterminado.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>Valor devuelto

Puede presentar uno de los siguientes valores:

- El control DLGC_DEFPUSHBUTTON es el botón predeterminado del cuadro de diálogo.

- El control DLGC_UNDEFPUSHBUTTON no es el botón predeterminado del cuadro de diálogo.

- el control **0** no es un botón.

##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID

Recupera el identificador del control.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del elemento de cuadro de diálogo del control.

##  <a name="geteventiid"></a>  COleControlSite::GetEventIID

Recupera un puntero a la interfaz de eventos predeterminada del control.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>Parámetros

*piid*<br/>
Un puntero a un identificador de interfaz.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es 0. Si es correcto, *piid* contiene el identificador de interfaz para la interfaz de eventos predeterminada del control.

##  <a name="getexstyle"></a>  COleControlSite::GetExStyle

Recupera los estilos extendidos de la ventana.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Los estilos extendidos de la ventana de control.

### <a name="remarks"></a>Comentarios

Para recuperar los estilos normales, llame a [COleControlSite:: getStyle](#getstyle).

##  <a name="getproperty"></a>  COleControlSite::GetProperty

Obtiene la propiedad de control especificada por *dwDispID*.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el ID. de envío de la propiedad, que se encuentra en `IDispatch` la interfaz predeterminada del control, que se va a recuperar.

*vtProp*<br/>
Especifica el tipo de la propiedad que se va a recuperar. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvProp*<br/>
Dirección de la variable que recibirá el valor de propiedad. Debe coincidir con el tipo especificado por *vtProp*.

### <a name="remarks"></a>Comentarios

El valor se devuelve a través de *pvProp*.

##  <a name="getstyle"></a>  COleControlSite::GetStyle

Recupera los estilos del sitio del control.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Estilos de la ventana.

### <a name="remarks"></a>Comentarios

Para obtener una lista de los valores posibles, consulte [estilos de Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Para recuperar los estilos extendidos del sitio del control, llame a [COleControlSite:: GetExStyle](#getexstyle).

##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText

Recupera el texto actual del control.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Referencia a un `CString` objeto que contiene el texto actual del control.

### <a name="remarks"></a>Comentarios

Si el control admite la propiedad estándar Caption, se devuelve este valor. Si no se admite la propiedad de stock de título, se devuelve el valor de la propiedad Text.

##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper

Invoca el método o la propiedad especificados por *dwDispID*, en el contexto especificado por *wFlags*.

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el ID. de envío de la propiedad o el método, que se `IDispatch` encuentra en la interfaz del control, que se va a invocar.

*wFlags*<br/>
Marcas que describen el contexto de la llamada a IDispatch:: Invoke. Para ver los posibles valores de `IDispatch::Invoke` wFlags, consulte en el Windows SDK.

*vtRet*<br/>
Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por *vtRet*.

*pbParamInfo*<br/>
Puntero a una cadena terminada en NULL de bytes que especifica los tipos de los parámetros que siguen a *pbParamInfo*. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Lista de variables de parámetros, de tipos especificados en *pbParamInfo*.

### <a name="remarks"></a>Comentarios

El parámetro *pbParamInfo* especifica los tipos de los parámetros pasados al método o a la propiedad. La lista variable de argumentos se representa mediante... en la declaración de sintaxis.

Esta función convierte los parámetros a valores VARIANTARG y luego invoca el `IDispatch::Invoke` método en el control. Si se produce un error en la llamada a `IDispatch::Invoke` , esta función generará una excepción. Si el código de estado devuelto `DISP_E_EXCEPTION`por `IDispatch::Invoke` es, esta función produce `COleDispatchException` un objeto, en caso contrario, `COleException`produce una excepción.

##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV

Invoca el método o la propiedad especificados por *dwDispID*, en el contexto especificado por *wFlags*.

```
virtual void InvokeHelperV(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo,
    va_list argList);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el ID. de envío de la propiedad o el método, que se `IDispatch` encuentra en la interfaz del control, que se va a invocar.

*wFlags*<br/>
Marcas que describen el contexto de la llamada a IDispatch:: Invoke.

*vtRet*<br/>
Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por *vtRet*.

*pbParamInfo*<br/>
Puntero a una cadena terminada en NULL de bytes que especifica los tipos de los parámetros que siguen a *pbParamInfo*. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Puntero a una lista de argumentos de variable.

### <a name="remarks"></a>Comentarios

El parámetro *pbParamInfo* especifica los tipos de los parámetros pasados al método o a la propiedad. Los parámetros adicionales para el método o la propiedad que se va a invocar se pueden pasar mediante el parámetro *va_list* .

Normalmente, llama a `COleControlSite::InvokeHelper`esta función.

##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton

Determina si el control es el botón predeterminado.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el control es el botón predeterminado de la ventana; de lo contrario, es cero.

##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled

Determina si el sitio de control está habilitado.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el control está habilitado; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

El valor se recupera de la propiedad estándar habilitada del control.

##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless

Determina si el objeto es un control sin ventana.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Comentarios

Es distinto de cero si el control no tiene ninguna ventana, de lo contrario, es cero.

##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo

Información sobre cómo controla la entrada del teclado el control.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Comentarios

Esta información se almacena en una estructura [CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo) .

##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink

Contiene la cookie del punto de conexión del receptor de eventos del control.

```
DWORD m_dwEventSink;
```

##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus

Contiene información diversa sobre el control.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)en el Windows SDK.

##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink

Contiene la cookie de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

```
DWORD m_dwPropNotifySink;
```

##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle

Contiene los estilos de ventana del control.

```
DWORD m_dwStyle;
```

##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd

Contiene el HWND del control o NULL si el control no tiene ventanas.

```
HWND m_hWnd;
```

##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents

Contiene el identificador de interfaz de la interfaz de receptor de eventos predeterminada del control.

```
IID m_iidEvents;
```

##  <a name="m_nid"></a>  COleControlSite::m_nID

Contiene el identificador del elemento de cuadro de diálogo del control.

```
UINT m_nID;
```

##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject

Contiene la interfaz [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) del control.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont

Contiene el contenedor del control (que representa el formulario).

```
COleControlContainer* m_pCtrlCont;
```

##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject

Contiene la `IOleInPlaceObject` interfaz [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) del control.

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

##  <a name="m_pobject"></a>  COleControlSite::m_pObject

Contiene la `IOleObjectInterface` interfaz del control.

```
LPOLEOBJECT m_pObject;
```

##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject

Contiene la `IOleInPlaceObjectWindowless`interfaz [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) del control.

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl

Contiene un puntero al `CWnd` objeto que representa el propio control.

```
CWnd* m_pWndCtrl;
```

##  <a name="m_rect"></a>  COleControlSite::m_rect

Contiene los límites del control, en relación con la ventana del contenedor.

```
CRect m_rect;
```

##  <a name="modifystyle"></a>  COleControlSite::ModifyStyle

Modifica los estilos del control.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*dwRemove*<br/>
Estilos que se van a quitar de los estilos de ventana actuales.

*dwAdd*<br/>
Estilos que se van a agregar a partir de los estilos de ventana actuales.

*nFlags*<br/>
Marcas de posición de la ventana. Para obtener una lista de los valores posibles, vea la función [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si se cambian los estilos, de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

La propiedad stock Enabled del control se modificará para que coincida con la configuración de WS_DISABLED. La propiedad de estilo de borde bursátil del control se modificará para que coincida con la configuración solicitada para WS_BORDER. El resto de los estilos se aplican directamente al identificador de ventana del control, si hay alguno.

Modifica los estilos de ventana del control. Los estilos que se van a agregar o quitar se pueden combinar mediante el operador &#124; bit a bit or (). Vea la función [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK para obtener información sobre los estilos de ventana disponibles.

Si *nFlags* es distinto de cero `ModifyStyle` , llama a la `SetWindowPos`función de Win32 y vuelve a dibujar la ventana mediante la combinación de *nFlags* con las cuatro marcas siguientes:

- SWP_NOSIZE conserva el tamaño actual.

- SWP_NOMOVE conserva la posición actual.

- SWP_NOZORDER conserva el orden Z actual.

- SWP_NOACTIVATE no activa la ventana.

Para modificar los estilos extendidos de una ventana, llame a [ModifyStyleEx](#modifystyleex).

##  <a name="modifystyleex"></a>COleControlSite::ModifyStyleEx

Modifica los estilos extendidos del control.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*dwRemove*<br/>
Estilos extendidos que se van a quitar de los estilos de ventana actuales.

*dwAdd*<br/>
Estilos extendidos que se van a agregar desde los estilos de ventana actuales.

*nFlags*<br/>
Marcas de posición de la ventana. Para obtener una lista de los valores posibles, vea la función [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si se cambian los estilos, de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

La propiedad de aspecto de las acciones del control se modificará para que coincida con la configuración de WS_EX_CLIENTEDGE. El resto de los estilos de ventana extendidos se aplican directamente al identificador de ventana del control, si hay alguno.

Modifica los estilos extendidos de ventana del objeto de sitio del control. Los estilos que se van a agregar o quitar se pueden combinar mediante el operador &#124; bit a bit or (). Vea la función [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK para obtener información sobre los estilos de ventana disponibles.

Si *nFlags* es distinto de cero `ModifyStyleEx` , llama a la `SetWindowPos`función de Win32 y vuelve a dibujar la ventana mediante la combinación de *nFlags* con las cuatro marcas siguientes:

- SWP_NOSIZE conserva el tamaño actual.

- SWP_NOMOVE conserva la posición actual.

- SWP_NOZORDER conserva el orden Z actual.

- SWP_NOACTIVATE no activa la ventana.

Para modificar los estilos extendidos de una ventana, llame a [ModifyStyle](#modifystyle).

##  <a name="movewindow"></a>  COleControlSite::MoveWindow

Cambia la posición del control.

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Nueva posición del lado izquierdo de la ventana.

*y*<br/>
Nueva posición de la parte superior de la ventana.

*nWidth*<br/>
Nuevo ancho de la ventana

*nHeight*<br/>
Nuevo alto de la ventana.

##  <a name="quickactivate"></a>  COleControlSite::QuickActivate

Activa de forma rápida el control contenido.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si se activó el sitio de control; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Solo se debe llamar a esta función si el usuario está invalidando el proceso de creación del control.

Se `IPersist*::Load` debe `IPersist*::InitNew` llamar a los métodos y después de que se produzca la activación rápida. El control debe establecer sus conexiones con los receptores del contenedor durante la activación rápida. Sin embargo, estas conexiones no están activas `IPersist*::Load` hasta `IPersist*::InitNew` que se ha llamado a o.

##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty

Establece la propiedad de control especificada por *dwDispID*.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el ID. de envío de la propiedad o el método, que se `IDispatch` encuentra en la interfaz del control, que se va a establecer.

*vtProp*<br/>
Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Un parámetro único del tipo especificado por *vtProp*.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  A diferencia `SetProperty` de `SetPropertyV`y, si se detecta un error (por ejemplo, al intentar establecer una propiedad inexistente), no se produce ninguna excepción.

##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton

Establece el control como el botón predeterminado.

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>Parámetros

*bDefault*<br/>
Distinto de cero si el control debe convertirse en el botón predeterminado; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  El control debe tener establecido el bit de estado OLEMISC_ACTSLIKEBUTTON.

##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID

Cambia el valor del identificador de elemento de cuadro de diálogo del control.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Nuevo valor del identificador.

### <a name="return-value"></a>Valor devuelto

Si es correcto, el identificador del elemento de cuadro de diálogo anterior de la ventana; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

##  <a name="setfocus"></a>  COleControlSite::SetFocus

Establece el foco en el control.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>Parámetros

*lpmsg*<br/>
Puntero a una [estructura MSG](/windows/win32/api/winuser/ns-winuser-msg). Esta estructura contiene el mensaje de Windows que desencadena `SetFocus` la solicitud para el control contenido en el sitio de control actual.

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana que previamente tenía el foco.

##  <a name="setproperty"></a>  COleControlSite::SetProperty

Establece la propiedad de control especificada por *dwDispID*.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el ID. de envío de la propiedad o el método, que se `IDispatch` encuentra en la interfaz del control, que se va a establecer.

*vtProp*<br/>
Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Un parámetro único del tipo especificado por *vtProp*.

### <a name="remarks"></a>Comentarios

Si `SetProperty` encuentra un error, se produce una excepción.

El tipo de excepción viene determinado por el valor devuelto del intento de establecer la propiedad o el método. Si el valor devuelto `DISP_E_EXCEPTION`es, `COleDispatchExcpetion` `COleException`se produce una excepción; en caso contrario,.

##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV

Establece la propiedad de control especificada por *dwDispID*.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el ID. de envío de la propiedad o el método, que se `IDispatch` encuentra en la interfaz del control, que se va a establecer.

*vtProp*<br/>
Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Puntero a la lista de argumentos.

### <a name="remarks"></a>Comentarios

Los parámetros adicionales para el método o la propiedad que se va a invocar se pueden passeed mediante el parámetro *arg_list* . Si `SetProperty` encuentra un error, se produce una excepción.

El tipo de excepción viene determinado por el valor devuelto del intento de establecer la propiedad o el método. Si el valor devuelto `DISP_E_EXCEPTION`es, `COleDispatchExcpetion` `COleException`se produce una excepción; en caso contrario,.

##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos

Establece el tamaño, la posición y el orden Z del sitio del control.

```
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*pWndInsertAfter*<br/>
Puntero a la ventana.

*x*<br/>
Nueva posición del lado izquierdo de la ventana.

*y*<br/>
Nueva posición de la parte superior de la ventana.

*cx*<br/>
Nuevo ancho de la ventana

*cy*<br/>
Nuevo alto de la ventana.

*nFlags*<br/>
Especifica las marcas de ajuste de tamaño y posición de la ventana. Para ver los valores posibles, consulte la sección Comentarios de [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto; de lo contrario, es cero.

##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText

Establece el texto del sitio del control.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*lpszString*<br/>
Puntero a una cadena terminada en null que se va a usar como nuevo título o control Text.

### <a name="remarks"></a>Comentarios

Esta función primero intenta establecer la propiedad stock de Caption. Si no se admite la propiedad material de título, se establece la propiedad texto en su lugar.

##  <a name="showwindow"></a>COleControlSite:: ShowWindow

Establece el estado de presentación de la ventana.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parámetros

*nCmdShow*<br/>
Especifica cómo se va a mostrar el sitio de control. Debe ser uno de los siguientes valores:

- SW_HIDE oculta esta ventana y pasa la activación a otra ventana.

- SW_MINIMIZE minimiza la ventana y activa la ventana de nivel superior en la lista del sistema.

- SW_RESTORE se activa y muestra la ventana. Si la ventana está minimizada o maximizada, Windows la restaura a su tamaño y posición originales.

- SW_SHOW activa la ventana y la muestra en su posición y tamaño actuales.

- SW_SHOWMAXIMIZED activa la ventana y la muestra como una ventana maximizada.

- SW_SHOWMINIMIZED activa la ventana y la muestra como un icono.

- SW_SHOWMINNOACTIVE muestra la ventana como un icono. La ventana que está activa actualmente permanece activa.

- SW_SHOWNA muestra la ventana en su estado actual. La ventana que está activa actualmente permanece activa.

- SW_SHOWNOACTIVATE muestra la ventana en su tamaño y posición más recientes. La ventana que está activa actualmente permanece activa.

- SW_SHOWNORMAL se activa y muestra la ventana. Si la ventana está minimizada o maximizada, Windows la restaura a su tamaño y posición originales.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la ventana estaba visible anteriormente; 0 si la ventana estaba oculta previamente.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer (clase)](../../mfc/reference/colecontrolcontainer-class.md)
