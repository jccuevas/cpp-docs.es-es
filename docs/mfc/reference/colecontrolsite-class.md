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
ms.openlocfilehash: 90c41a1be1a66cdceebb3f045a98167e56b7cf4c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753945"
---
# <a name="colecontrolsite-class"></a>Clase COleControlSite

Proporciona compatibilidad con interfaces de control de cliente personalizadas.

## <a name="syntax"></a>Sintaxis

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|Construye un objeto `COleControlSite`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Enlaza la propiedad predeterminada del control hospedado a un origen de datos.|
|[COleControlSite::BindProperty](#bindproperty)|Enlaza una propiedad del control hospedado a un origen de datos.|
|[COleControlSite::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|
|[COleControlSite::DestroyControl](#destroycontrol)|Destruye el control hospedado.|
|[COleControlSite::DoVerb](#doverb)|Ejecuta un verbo específico del control hospedado.|
|[COleControlSite::HabilitarDSC](#enabledsc)|Habilita el abastecimiento de datos para un sitio de control.|
|[COleControlSite::EnableWindow](#enablewindow)|Habilita el sitio de control.|
|[COleControlSite::FreezeEvents](#freezeevents)|Especifica si el sitio de control acepta eventos.|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Recupera el código de botón predeterminado para el control hospedado.|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Recupera el identificador del control.|
|[COleControlSite::GetEventIID](#geteventiid)|Recupera el identificador de una interfaz de eventos para un control hospedado.|
|[COleControlSite::GetExStyle](#getexstyle)|Recupera los estilos extendidos del sitio de control.|
|[COleControlSite::GetProperty](#getproperty)|Recupera una propiedad específica del control hospedado.|
|[COleControlSite::GetStyle](#getstyle)|Recupera los estilos del sitio de control.|
|[COleControlSite::GetWindowText](#getwindowtext)|Recupera el texto del control hospedado.|
|[COleControlSite::InvokeHelper](#invokehelper)|Invocar un método específico del control hospedado.|
|[COleControlSite::InvokeHelperV](#invokehelperv)|Invoque un método específico del control hospedado con una lista de variables de argumentos.|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Determina si el control es el botón predeterminado en la ventana.|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Comprueba el estado visible del sitio de control.|
|[COleControlSite::ModifyStyle](#modifystyle)|Modifica los estilos extendidos actuales del sitio de control.|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modifica los estilos actuales del sitio de control.|
|[COleControlSite::MoveWindow](#movewindow)|Cambia la posición del sitio de control.|
|[COleControlSite::QuickActivate](#quickactivate)|Activa rápidamente el control hospedado.|
|[COleControlSite::SafeSetProperty](#safesetproperty)|Establece una propiedad o método del control sin posibilidad de producir una excepción.|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Establece el botón predeterminado en la ventana.|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Recupera el identificador del control.|
|[COleControlSite::SetFocus](#setfocus)|Establece el foco en el sitio de control.|
|[COleControlSite::SetProperty](#setproperty)|Establece una propiedad específica del control hospedado.|
|[COleControlSite::SetPropertyV](#setpropertyv)|Establece una propiedad específica del control hospedado con una lista de variables de argumentos.|
|[COleControlSite::SetWindowPos](#setwindowpos)|Establece la posición del sitio de control.|
|[COleControlSite::SetWindowText](#setwindowtext)|Establece el texto del control hospedado.|
|[COleControlSite::ShowWindow](#showwindow)|Muestra u oculta el sitio de control.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Recupera información de teclado y mnemotécnicas para el control hospedado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Determina si el control hospedado es un control sin ventanas.|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Contiene información sobre el control del teclado para el control.|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|La cookie del punto de conexión del control.|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Los estados varios para el control hospedado.|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|La `IPropertyNotifySink` galleta del control.|
|[COleControlSite::m_dwStyle](#m_dwstyle)|Los estilos del control hospedado.|
|[COleControlSite::m_hWnd](#m_hwnd)|El identificador del sitio de control.|
|[COleControlSite::m_iidEvents](#m_iidevents)|El identificador de la interfaz de eventos para el control hospedado.|
|[COleControlSite::m_nID](#m_nid)|El identificador del control hospedado.|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Un puntero `IOleInPlaceActiveObject` al objeto del control hospedado.|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|El contenedor del control hospedado.|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Un puntero `IOleInPlaceObject` al objeto del control hospedado.|
|[COleControlSite::m_pObject](#m_pobject)|Un puntero `IOleObjectInterface` a la interfaz del control.|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Un puntero `IOleInPlaceObjectWindowless` a la interfaz del control.|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Un puntero al objeto de ventana para el control hospedado.|
|[COleControlSite::m_rect](#m_rect)|Las dimensiones del sitio de control.|

## <a name="remarks"></a>Observaciones

Esta compatibilidad es el medio principal mediante el cual un control ActiveX incrustado obtiene información sobre la ubicación y la extensión de su sitio de visualización, su moniker, su interfaz de usuario, sus propiedades ambientales y otros recursos proporcionados por su contenedor. `COleControlSite`implementa completamente las interfaces [IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite), [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite), [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), `IBoundObjectSite`, `INotifyDBEvents`, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) . Además, también se implementa la interfaz IDispatch (que proporciona compatibilidad con propiedades ambientales y receptores de eventos).

Para crear un sitio `COleControlSite`de control ActiveX mediante , derive una clase de `COleControlSite`. En `CWnd`la clase -derived para el contenedor (por `CWnd::CreateControlSite` ejemplo, el cuadro de diálogo) invalide la función.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxocc.h

## <a name="colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty

Enlaza la propiedad enlazada simple predeterminada del objeto de llamada, tal como se marca en la biblioteca de tipos, al cursor subyacente definido por las propiedades DataSource, UserName, Password y SQL del control de código fuente de datos.

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
Especifica el tipo de la propiedad que se va a enlazar, por ejemplo, VT_BSTR, VT_VARIANT, etc.

*szFieldName*<br/>
Especifica el nombre de la columna, en el cursor proporcionado por el control de código de datos, al que se enlazará la propiedad.

*pDSCWnd*<br/>
Puntero al `CWnd`objeto derivado que hospeda el control de origen de datos al que se enlazará la propiedad.

### <a name="remarks"></a>Observaciones

El `CWnd` objeto en el que se llama a esta función debe ser un control enlazado a datos.

## <a name="colecontrolsitebindproperty"></a><a name="bindproperty"></a>COleControlSite::BindProperty

Enlaza la propiedad enlazada simple del objeto que realiza la llamada, tal como se marca en la biblioteca de tipos, al cursor subyacente definido por las propiedades DataSource, UserName, Password y SQL del control de origen de datos.

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>Parámetros

*dwDispId*<br/>
Especifica el DISPID de una propiedad en un control enlazado a datos que se va a enlazar a un control de origen de datos.

*pWndDSC*<br/>
Puntero al `CWnd`objeto derivado que hospeda el control de origen de datos al que se enlazará la propiedad.

### <a name="remarks"></a>Observaciones

El `CWnd` objeto en el que se llama a esta función debe ser un control enlazado a datos.

## <a name="colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a>COleControlSite::COleControlSite

Construye un nuevo objeto `COleControlSite`.

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>Parámetros

*pCtrlCont*<br/>
Puntero al contenedor del control (que representa la ventana que hospeda el control AtiveX).

### <a name="remarks"></a>Observaciones

La función [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) llama a esta función. Para obtener más información sobre cómo personalizar la creación de contenedores, vea [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).

## <a name="colecontrolsitecreatecontrol"></a><a name="createcontrol"></a>COleControlSite::CreateControl

Crea un control ActiveX, `COleControlSite` hospedado por el objeto.

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
Puntero al objeto de ventana que representa el control.

*clsid*<br/>
El identificador de clase único del control.

*lpszWindowName*<br/>
Puntero al texto que se mostrará en el control. Establece el valor de la propiedad Caption o Text de winodw (si existe).

*dwStyle*<br/>
Estilos de Windows. Los estilos disponibles se enumeran en la sección **Comentarios.**

*Rect*<br/>
Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto `RECT` o una estructura.

*nID*<br/>
Especifica el identificador de ventana secundaria del control.

*pPersist*<br/>
Puntero a `CFile` un que contiene el estado persistente para el control. El valor predeterminado es NULL, lo que indica que el control se inicializa sin restaurar su estado desde cualquier almacenamiento persistente. Si no es NULL, debe `CFile`ser un puntero a un objeto derivado que contiene los datos persistentes del control, en forma de una secuencia o un almacenamiento. Estos datos podrían haberse guardado en una activación anterior del cliente. Puede `CFile` contener otros datos, pero debe tener su puntero de lectura y escritura establecido `CreateControl`en el primer byte de datos persistentes en el momento de la llamada a .

*bAlmacenamiento*<br/>
Indica si los datos de *pPersist* `IStorage` deben `IStream` interpretarse como datos o datos. Si los datos de *pPersist* es un almacenamiento, *bStorage* debe ser TRUE. Si los datos de *pPersist* es una secuencia, *bStorage* debe ser FALSE. El valor predeterminado es FALSE.

*bstrLicKey*<br/>
Datos de clave de licencia opcionales. Estos datos solo son necesarios para crear controles que requieren una clave de licencia en tiempo de ejecución. Si el control admite licencias, debe proporcionar una clave de licencia para que la creación del control se realice correctamente. El valor predeterminado es NULL.

*Ppt*<br/>
Puntero a `POINT` una estructura que contiene la esquina superior izquierda del control. El tamaño del control viene determinado por el valor de *psize*. Los valores *ppt* y *psize* son un método opcional para especificar el tamaño y la posición opf el control.

*psize*<br/>
Puntero a `SIZE` una estructura que contiene el tamaño del control. La esquina superior izquierda viene determinada por el valor de *ppt*. Los valores *ppt* y *psize* son un método opcional para especificar el tamaño y la posición opf el control.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Solo un subconjunto de las marcas `CreateControl` *dwStyle* de Windows son compatibles con:

- WS_VISIBLE Crea una ventana que está visible inicialmente. Necesario si desea que el control sea visible inmediatamente, como ventanas normales.

- WS_DISABLED Crea una ventana que está deshabilitada inicialmente. Una ventana deshabilitada no puede recibir la entrada del usuario. Se puede establecer si el control tiene un Enabled propiedad.

- WS_BORDER Crea una ventana con un borde de línea delgada. Se puede establecer si el control tiene un BorderStyle propiedad.

- WS_GROUP Especifica el primer control de un grupo de controles. El usuario puede cambiar el foco del teclado de un control del grupo al siguiente mediante las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo e inicia el siguiente grupo.

- WS_TABSTOP Especifica un control que puede recibir el foco del teclado cuando el usuario presiona la tecla TAB. Al pulsar la tecla TAB, el foco del teclado se muestra al siguiente control del estilo WS_TABSTOP.

Utilice la segunda sobrecarga para crear controles de tamaño predeterminado.

## <a name="colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a>COleControlSite::DestroyControl

Destruye el objeto `COleControlSite`.

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Una vez completado, el objeto se libera de la memoria y los punteros al objeto ya no son válidos.

## <a name="colecontrolsitedoverb"></a><a name="doverb"></a>COleControlSite::DoVerb

Ejecuta el verbo especificado.

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>Parámetros

*nVerb*<br/>
Especifica el verbo que se va a ejecutar. Puede incluir uno de los siguientes:

|Value|Significado|Símbolo|
|-----------|-------------|------------|
|0|verbo principal|OLEIVERB_PRIMARY|
|-1|Verbo secundario|(Ninguna)|
|1|Muestra el objeto para editarlo.|OLEIVERB_SHOW|
|-2|Edita el elemento en una ventana independiente.|OLEIVERB_OPEN|
|-3|Oculta el objeto.|OLEIVERB_HIDE|
|-4|Activa un control in situ.|OLEIVERB_UIACTIVATE|
|-5|Activa un control in situ, sin elementos de interfaz de usuario adicionales.|OLEIVERB_INPLACEACTIVATE|
|-7|Mostrar las propiedades del control.|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
Puntero al mensaje que provocó la activación del elemento.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función llama directamente `IOleObject` a través de la interfaz del control para ejecutar el verbo especificado. Si se produce una excepción como resultado de esta llamada de función, se devuelve un código de error HRESULT.

Para obtener más información, vea [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

## <a name="colecontrolsiteenabledsc"></a><a name="enabledsc"></a>COleControlSite::HabilitarDSC

Habilita el abastecimiento de datos para el sitio de control.

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Observaciones

Llamado por el marco de trabajo para habilitar e inicializar el abastecimiento de datos para el sitio de control. Invalide esta función para proporcionar un comportamiento personalizado.

## <a name="colecontrolsiteenablewindow"></a><a name="enablewindow"></a>COleControlSite::EnableWindow

Habilita o deshabilita la entrada del mouse y el teclado en el sitio de control.

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
Especifica si se debe habilitar o deshabilitar la ventana: TRUE si se va a habilitar la entrada de ventana, de lo contrario FALSE.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la ventana se deshabilitó anteriormente, de lo contrario 0.

## <a name="colecontrolsitefreezeevents"></a><a name="freezeevents"></a>COleControlSite::FreezeEvents

Especifica si el sitio de control controlará o omitirá los eventos desencadenados desde un control.

```cpp
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parámetros

*bFreeze*<br/>
Especifica si el sitio del control desea dejar de aceptar eventos. Distinto de cero si el control no acepta eventos; de lo contrario cero.

### <a name="remarks"></a>Observaciones

Si *bFreeze* es TRUE, el sitio de control solicita el control para detener los eventos de fring. Si *bFreeze* es FALSE, el sitio de control solicita el control para continuar desencadenando eventos.

> [!NOTE]
> El control no es necesario para detener la activación de eventos si lo solicita el sitio de control. Puede continuar la activación, pero el sitio de control ignorará todos los eventos subsiguientes.

## <a name="colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a>COleControlSite::GetControlInfo

Recupera información sobre los mnemotécnicos de teclado y el comportamiento del teclado de un control.

```cpp
void GetControlInfo();
```

### <a name="remarks"></a>Observaciones

La información se almacena en [COleControlSite::m_ctlInfo](#m_ctlinfo).

## <a name="colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode

Determina si el control es un botón pulsador predeterminado.

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>Valor devuelto

Puede ser uno de los siguientes valores:

- DLGC_DEFPUSHBUTTON Control es el botón predeterminado en el cuadro de diálogo.

- DLGC_UNDEFPUSHBUTTON Control no es el botón predeterminado en el cuadro de diálogo.

- **0** El control no es un botón.

## <a name="colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID

Recupera el identificador del control.

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de elemento de cuadro de diálogo del control.

## <a name="colecontrolsitegeteventiid"></a><a name="geteventiid"></a>COleControlSite::GetEventIID

Recupera un puntero a la interfaz de eventos predeterminada del control.

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>Parámetros

*piid*<br/>
Un puntero a un identificador de interfaz.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario 0. Si se realiza correctamente, *piid* contiene el identificador de interfaz para la interfaz de eventos predeterminada del control.

## <a name="colecontrolsitegetexstyle"></a><a name="getexstyle"></a>COleControlSite::GetExStyle

Recupera los estilos extendidos de la ventana.

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Estilos extendidos de la ventana de control.

### <a name="remarks"></a>Observaciones

Para recuperar los estilos normales, llame a [COleControlSite::GetStyle](#getstyle).

## <a name="colecontrolsitegetproperty"></a><a name="getproperty"></a>COleControlSite::GetProperty

Obtiene la propiedad de control especificada por *dwDispID*.

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el identificador de envío de la propiedad, `IDispatch` que se encuentra en la interfaz predeterminada del control, que se va a recuperar.

*vtProp*<br/>
Especifica el tipo de la propiedad que se va a recuperar. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvProp*<br/>
Dirección de la variable que recibirá el valor de propiedad. Debe coincidir con el tipo especificado por *vtProp*.

### <a name="remarks"></a>Observaciones

El valor se devuelve a través de *pvProp*.

## <a name="colecontrolsitegetstyle"></a><a name="getstyle"></a>COleControlSite::GetStyle

Recupera los estilos del sitio de control.

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Estilos de la ventana.

### <a name="remarks"></a>Observaciones

Para obtener una lista de valores posibles, consulte [Estilos de Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Para recuperar los estilos extendidos del sitio de control, llame a [COleControlSite::GetExStyle](#getexstyle).

## <a name="colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a>COleControlSite::GetWindowText

Recupera el texto actual del control.

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Una referencia `CString` a un objeto que contiene el texto actual del control.

### <a name="remarks"></a>Observaciones

Si el control admite la propiedad stock Caption, se devuelve este valor. Si no se admite la propiedad Caption stock, se devuelve el valor de la propiedad Text.

## <a name="colecontrolsiteinvokehelper"></a><a name="invokehelper"></a>COleControlSite::InvokeHelper

Invoca el método o la propiedad especificado por *dwDispID*, en el contexto especificado por *wFlags*.

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
Identifica el identificador de envío de la propiedad o `IDispatch` método, que se encuentra en la interfaz del control, que se va a invocar.

*wFlags*<br/>
Marcas que describen el contexto de la llamada a IDispatch::Invoke. Para ver los posibles `IDispatch::Invoke` valores *de wFlags,* consulte el Windows SDK.

*vtRet*<br/>
Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por *vtRet*.

*pbParamInfo*<br/>
Puntero a una cadena de bytes terminada en null que especifica los tipos de los parámetros siguientes *pbParamInfo*. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Lista variable de parámetros, de tipos especificados en *pbParamInfo*.

### <a name="remarks"></a>Observaciones

El parámetro *pbParamInfo* especifica los tipos de los parámetros pasados al método o propiedad. La lista variable de argumentos se representa mediante ... en la declaración de sintaxis.

Esta función convierte los parámetros en valores `IDispatch::Invoke` VARIANTARG y, a continuación, invoca el método en el control. Si se produce un error en la llamada a `IDispatch::Invoke` , esta función generará una excepción. Si el código `IDispatch::Invoke` de `DISP_E_EXCEPTION`estado devuelto por `COleDispatchException` es , esta `COleException`función lanza un objeto, de lo contrario, lanza un archivo .

## <a name="colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a>COleControlSite::InvokeHelperV

Invoca el método o la propiedad especificado por *dwDispID*, en el contexto especificado por *wFlags*.

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
Identifica el identificador de envío de la propiedad o `IDispatch` método, que se encuentra en la interfaz del control, que se va a invocar.

*wFlags*<br/>
Marcas que describen el contexto de la llamada a IDispatch::Invoke.

*vtRet*<br/>
Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*pvRet*<br/>
Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por *vtRet*.

*pbParamInfo*<br/>
Puntero a una cadena de bytes terminada en null que especifica los tipos de los parámetros siguientes *pbParamInfo*. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Puntero a una lista de argumentos de variable.

### <a name="remarks"></a>Observaciones

El parámetro *pbParamInfo* especifica los tipos de los parámetros pasados al método o propiedad. Los parámetros adicionales para el método o la propiedad que se invoca se pueden pasar mediante el *parámetro va_list.*

Normalmente, `COleControlSite::InvokeHelper`. llama a esta función.

## <a name="colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton

Determina si el control es el botón predeterminado.

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control es el botón predeterminado en la ventana, de lo contrario cero.

## <a name="colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled

Determina si el sitio de control está habilitado.

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control está habilitado, de lo contrario cero.

### <a name="remarks"></a>Observaciones

El valor se recupera de la propiedad Enabled stock del control.

## <a name="colecontrolsitem_biswindowless"></a><a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless

Determina si el objeto es un control sin ventanas.

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Observaciones

Distinto de cero si el control no tiene ninguna ventana, de lo contrario cero.

## <a name="colecontrolsitem_ctlinfo"></a><a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo

Información sobre cómo el control controla la entrada del teclado.

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Observaciones

Esta información se almacena en una estructura [CONTROLINFO.](/windows/win32/api/ocidl/ns-ocidl-controlinfo)

## <a name="colecontrolsitem_dweventsink"></a><a name="m_dweventsink"></a>COleControlSite::m_dwEventSink

Contiene la cookie del punto de conexión desde el receptor de eventos del control.

```
DWORD m_dwEventSink;
```

## <a name="colecontrolsitem_dwmiscstatus"></a><a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus

Contiene información diversa sobre el control.

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)en el Windows SDK.

## <a name="colecontrolsitem_dwpropnotifysink"></a><a name="m_dwpropnotifysink"></a>COleControlSite::m_dwPropNotifySink

Contiene la cookie [IPropertyNotifySink.](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)

```
DWORD m_dwPropNotifySink;
```

## <a name="colecontrolsitem_dwstyle"></a><a name="m_dwstyle"></a>COleControlSite::m_dwStyle

Contiene los estilos Window del control.

```
DWORD m_dwStyle;
```

## <a name="colecontrolsitem_hwnd"></a><a name="m_hwnd"></a>COleControlSite::m_hWnd

Contiene el HWND del control, o NULL si el control no tiene ventanas.

```
HWND m_hWnd;
```

## <a name="colecontrolsitem_iidevents"></a><a name="m_iidevents"></a>COleControlSite::m_iidEvents

Contiene el identificador de interfaz de la interfaz de receptor de eventos predeterminada del control.

```
IID m_iidEvents;
```

## <a name="colecontrolsitem_nid"></a><a name="m_nid"></a>COleControlSite::m_nID

Contiene el identificador de elemento de cuadro de diálogo del control.

```
UINT m_nID;
```

## <a name="colecontrolsitem_pactiveobject"></a><a name="m_pactiveobject"></a>COleControlSite::m_pActiveObject

Contiene el [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) interfaz del control.

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

## <a name="colecontrolsitem_pctrlcont"></a><a name="m_pctrlcont"></a>COleControlSite::m_pCtrlCont

Contiene el contenedor del control (que representa el formulario).

```
COleControlContainer* m_pCtrlCont;
```

## <a name="colecontrolsitem_pinplaceobject"></a><a name="m_pinplaceobject"></a>COleControlSite::m_pInPlaceObject

Contiene `IOleInPlaceObject` el [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) interfaz del control.

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

## <a name="colecontrolsitem_pobject"></a><a name="m_pobject"></a>COleControlSite::m_pObject

Contiene `IOleObjectInterface` la interfaz del control.

```
LPOLEOBJECT m_pObject;
```

## <a name="colecontrolsitem_pwindowlessobject"></a><a name="m_pwindowlessobject"></a>COleControlSite::m_pWindowlessObject

Contiene `IOleInPlaceObjectWindowless`el [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) interfaz del control.

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

## <a name="colecontrolsitem_pwndctrl"></a><a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl

Contiene un puntero `CWnd` al objeto que representa el propio control.

```
CWnd* m_pWndCtrl;
```

## <a name="colecontrolsitem_rect"></a><a name="m_rect"></a>COleControlSite::m_rect

Contiene los límites del control, en relación con la ventana del contenedor.

```
CRect m_rect;
```

## <a name="colecontrolsitemodifystyle"></a><a name="modifystyle"></a>COleControlSite::ModifyStyle

Modifica los estilos del control.

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*dwRemove*<br/>
Los estilos que se van a quitar de los estilos de ventana actuales.

*dwAdd*<br/>
Los estilos que se agregarán desde los estilos de ventana actuales.

*nFlags*<br/>
Indicadores de posicionamiento de ventana. Para obtener una lista de valores posibles, vea la función [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se cambian los estilos, de lo contrario cero.

### <a name="remarks"></a>Observaciones

La propiedad stock Enabled del control se modificará para que coincida con la configuración de WS_DISABLED. La propiedad Estilo de borde del control se modificará para que coincida con la configuración solicitada para WS_BORDER. Todos los demás estilos se aplican directamente al identificador de ventana del control, si uno está presente.

Modifica los estilos de ventana del control. Los estilos que se van a agregar o quitar se pueden combinar mediante el operador OR ( &#124; ) bit a bit. Consulte la función [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK para obtener información sobre los estilos de ventana disponibles.

Si *nFlags* es `ModifyStyle` distinto de cero, `SetWindowPos`llama a la función Win32 y vuelve a dibujar la ventana combinando *nFlags* con los cuatro indicadores siguientes:

- SWP_NOSIZE Conserva el tamaño actual.

- SWP_NOMOVE Conserva la posición actual.

- SWP_NOZORDER Conserva el orden Z actual.

- SWP_NOACTIVATE No activa la ventana.

Para modificar los estilos extendidos de una ventana, llame a [ModifyStyleEx](#modifystyleex).

## <a name="colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a>COleControlSite::ModifyStyleEx

Modifica los estilos extendidos del control.

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

*dwRemove*<br/>
Los estilos extendidos que se eliminarán de los estilos de ventana actuales.

*dwAdd*<br/>
Los estilos extendidos que se agregarán desde los estilos de ventana actuales.

*nFlags*<br/>
Indicadores de posicionamiento de ventana. Para obtener una lista de valores posibles, vea la función [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se cambian los estilos, de lo contrario cero.

### <a name="remarks"></a>Observaciones

La propiedad Apariencia del control se modificará para que coincida con la configuración de WS_EX_CLIENTEDGE. Todos los demás estilos de ventana extendida se aplican directamente al identificador de ventana del control, si hay uno presente.

Modifica los estilos extendidos de ventana del objeto de sitio de control. Los estilos que se van a agregar o quitar se pueden combinar mediante el operador OR ( &#124; ) bit a bit. Consulte la función [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK para obtener información sobre los estilos de ventana disponibles.

Si *nFlags* es `ModifyStyleEx` distinto de cero, `SetWindowPos`llama a la función Win32 y vuelve a dibujar la ventana combinando *nFlags* con los cuatro indicadores siguientes:

- SWP_NOSIZE Conserva el tamaño actual.

- SWP_NOMOVE Conserva la posición actual.

- SWP_NOZORDER Conserva el orden Z actual.

- SWP_NOACTIVATE No activa la ventana.

Para modificar los estilos extendidos de una ventana, llame a [ModifyStyle](#modifystyle).

## <a name="colecontrolsitemovewindow"></a><a name="movewindow"></a>COleControlSite::MoveWindow

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
La nueva posición del lado izquierdo de la ventana.

*y y*<br/>
La nueva posición de la parte superior de la ventana.

*nAncho*<br/>
El nuevo ancho de la ventana

*nAltura*<br/>
La nueva altura de la ventana.

## <a name="colecontrolsitequickactivate"></a><a name="quickactivate"></a>COleControlSite::QuickActivate

Activa rápidamente el control contenido.

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el sitio de control se activó, de lo contrario cero.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse sólo si el usuario está reemplazando el proceso de creación del control.

Se `IPersist*::Load` `IPersist*::InitNew` debe llamar a los métodos y después de que se produzca una activación rápida. El control debe establecer sus conexiones a los receptores del contenedor durante la activación rápida. Sin embargo, estas `IPersist*::Load` conexiones no están vivas hasta o `IPersist*::InitNew` se ha llamado.

## <a name="colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a>COleControlSite::SafeSetProperty

Establece la propiedad de control especificada por *dwDispID*.

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el identificador de envío de la propiedad o `IDispatch` método, que se encuentra en la interfaz del control, que se va a establecer.

*vtProp*<br/>
Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Un único parámetro del tipo especificado por *vtProp*.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> A `SetProperty` `SetPropertyV`diferencia de y , si se encuentra un error (como intentar establecer una propiedad inexistente), no se produce ninguna excepción.

## <a name="colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton

Establece el control como el botón predeterminado.

```cpp
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>Parámetros

*bPredeterminado*<br/>
Distinto de cero si el control debe convertirse en el botón predeterminado; de lo contrario cero.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> El control debe tener el OLEMISC_ACTSLIKEBUTTON de bits de estado establecido.

## <a name="colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID

Cambia el valor del identificador de elemento de cuadro de diálogo del control.

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
El nuevo valor de identificador.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador de elemento de cuadro de diálogo anterior de la ventana; de lo contrario 0.

### <a name="remarks"></a>Observaciones

## <a name="colecontrolsitesetfocus"></a><a name="setfocus"></a>COleControlSite::SetFocus

Establece el foco en el control.

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>Parámetros

*lpmsg*<br/>
Un puntero a una [estructura MSG](/windows/win32/api/winuser/ns-winuser-msg). Esta estructura contiene el mensaje `SetFocus` de Windows que desencadena la solicitud para el control contenido en el sitio de control actual.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana que anteriormente tenía el foco.

## <a name="colecontrolsitesetproperty"></a><a name="setproperty"></a>COleControlSite::SetProperty

Establece la propiedad de control especificada por *dwDispID*.

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el identificador de envío de la propiedad o `IDispatch` método, que se encuentra en la interfaz del control, que se va a establecer.

*vtProp*<br/>
Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*...*<br/>
Un único parámetro del tipo especificado por *vtProp*.

### <a name="remarks"></a>Observaciones

Si `SetProperty` encuentra un error, se produce una excepción.

El tipo de excepción viene determinado por el valor devuelto del intento de establecer la propiedad o el método. Si el valor `DISP_E_EXCEPTION`devuelto `COleDispatchExcpetion` es , a se produce; de `COleException`lo contrario un archivo .

## <a name="colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a>COleControlSite::SetPropertyV

Establece la propiedad de control especificada por *dwDispID*.

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>Parámetros

*dwDispID*<br/>
Identifica el identificador de envío de la propiedad o `IDispatch` método, que se encuentra en la interfaz del control, que se va a establecer.

*vtProp*<br/>
Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).

*argList*<br/>
Puntero a la lista de argumentos.

### <a name="remarks"></a>Observaciones

Los parámetros adicionales para el método o la propiedad que se invoca se pueden pasar mediante el parámetro *arg_list.* Si `SetProperty` encuentra un error, se produce una excepción.

El tipo de excepción viene determinado por el valor devuelto del intento de establecer la propiedad o el método. Si el valor `DISP_E_EXCEPTION`devuelto `COleDispatchExcpetion` es , a se produce; de `COleException`lo contrario un archivo .

## <a name="colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a>COleControlSite::SetWindowPos

Establece el tamaño, la posición y el orden Z del sitio de control.

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
Un puntero a la ventana.

*x*<br/>
La nueva posición del lado izquierdo de la ventana.

*y y*<br/>
La nueva posición de la parte superior de la ventana.

*Cx*<br/>
El nuevo ancho de la ventana

*Cy*<br/>
La nueva altura de la ventana.

*nFlags*<br/>
Especifica los indicadores de tamaño y posicionamiento de ventana. Para ver los valores posibles, consulte la sección Comentarios para [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente, de lo contrario cero.

## <a name="colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a>COleControlSite::SetWindowText

Establece el texto del sitio de control.

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*lpszString*<br/>
Puntero a una cadena terminada en null que se usará como nuevo título o texto de control.

### <a name="remarks"></a>Observaciones

Esta función primero intenta establecer la propiedad Stock Caption. Si no se admite la propiedad Caption stock, la propiedad Text se establece en su lugar.

## <a name="colecontrolsiteshowwindow"></a><a name="showwindow"></a>COleControlSite::ShowWindow

Establece el estado de la demostración de la ventana.

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parámetros

*nCmdShow*<br/>
Especifica cómo se va a mostrar el sitio de control. Debe ser uno de los siguientes valores:

- SW_HIDE Oculta esta ventana y pasa la activación a otra ventana.

- SW_MINIMIZE Minimiza la ventana y activa la ventana de nivel superior en la lista del sistema.

- SW_RESTORE Activa y muestra la ventana. Si la ventana se minimiza o maximiza, Windows la restaura a su tamaño y posición originales.

- SW_SHOW Activa la ventana y la muestra en su tamaño y posición actuales.

- SW_SHOWMAXIMIZED Activa la ventana y la muestra como una ventana maximizada.

- SW_SHOWMINIMIZED Activa la ventana y la muestra como un icono.

- SW_SHOWMINNOACTIVE Muestra la ventana como un icono. La ventana que está activa actualmente permanece activa.

- SW_SHOWNA Muestra la ventana en su estado actual. La ventana que está activa actualmente permanece activa.

- SW_SHOWNOACTIVATE Muestra la ventana en su tamaño y posición más recientes. La ventana que está activa actualmente permanece activa.

- SW_SHOWNORMAL Activa y muestra la ventana. Si la ventana se minimiza o maximiza, Windows la restaura a su tamaño y posición originales.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la ventana estaba visible anteriormente; 0 si la ventana estaba oculta anteriormente.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer Clase](../../mfc/reference/colecontrolcontainer-class.md)
