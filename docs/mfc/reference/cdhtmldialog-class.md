---
title: CDHtmlDialog (clase)
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: bda980c26f9791e1d4f03026f7e118e69a4ab881
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565810"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog (clase)

Se usa para crear cuadros de diálogo que utilizan HTML en lugar de los recursos de cuadro de diálogo para implementar la interfaz de usuario.

## <a name="syntax"></a>Sintaxis

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Construye un objeto CDHtmlDialog.|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|Destruye un objeto CDHtmlDialog.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Reemplazables se denomina como una comprobación de acceso para ver si los objetos de scripting en la página cargada pueden tener acceso el envío de sitio del control externo. Comprueba para asegurarse de que el envío es ser seguros para scripting o la zona actual se permite para los objetos que no son seguros para scripting.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Reemplazable usado para crear una instancia de sitio del control para hospedar el control WebBrowser en el cuadro de diálogo.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Intercambia datos entre una variable de miembro y el valor de propiedad de un control ActiveX en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Intercambia datos entre una variable de miembro y una casilla de verificación en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Intercambia datos entre una variable de miembro y cualquier propiedad de elemento HTML en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Intercambia datos entre una variable de miembro y un botón de radio en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Obtiene o establece el índice de un cuadro de lista en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Obtiene o establece el texto para mostrar de una entrada de cuadro de lista (según el índice actual) en una página HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Obtiene o establece el valor de una entrada de cuadro de lista (según el índice actual) en una página HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Destruye un cuadro de diálogo no modal.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Permite a los cuadros de diálogo no modal.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Permite que el cuadro de diálogo Filtrar los objetos del Portapapeles datos creados por el explorador hospedado.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Recupera el `IDispatch` interfaz en un control ActiveX incrustado en el documento HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Recupera la propiedad solicitada del control ActiveX especificado.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Recupera el localizador uniforme de recursos (URL) asociado con el documento actual.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Recupera la interfaz IHTMLDocument2 en el documento HTML cargado actualmente.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Lo llama el control WebBrowser independiente cuando lo está usando como un destino de colocación para permitir que el cuadro de diálogo proporcionar una alternativa [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Obtiene una interfaz en un elemento HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Recupera el `innerHTML` propiedad de un elemento HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Recupera el puntero de interfaz solicitada de un elemento HTML.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Recupera el valor de propiedad de un elemento HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Recupera el `innerText` propiedad de un elemento HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Obtiene el `IHTMLEventObj` puntero al objeto de evento actual.|
|[CDHtmlDialog::GetExternal](#getexternal)|Obtiene el host `IDispatch` interfaz.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Recupera las capacidades de la interfaz de usuario del host.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Recupera la clave del registro bajo la que se almacenan las preferencias del usuario.|
|[CDHtmlDialog::HideUI](#hideui)|Oculta la interfaz de usuario del host.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Indica si el host `IDispatch` interfaz es segura para scripting.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Carga el recurso especificado en el control WebBrowser.|
|[CDHtmlDialog::Navigate](#navigate)|Navega a la dirección URL especificada.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Lo llama el marco de trabajo antes de que se desencadena un evento de navegación.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Lo llama el marco de trabajo para notificar a una aplicación cuando un documento alcanzó el estado READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Lo llama el marco de trabajo cuando se activa o desactiva la ventana de documento.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Lo llama el marco de trabajo cuando se activa o desactiva la ventana de marco.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Se llama en respuesta al mensaje WM_INITDIALOG.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Lo llama el marco de trabajo una vez completado un evento de navegación.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Alerta al objeto que debe cambiar el tamaño de su espacio del borde.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Establece la propiedad de un control ActiveX a un nuevo valor.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Establece el `innerHTML` propiedad de un elemento HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Establece una propiedad de un elemento HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Establece el `innerText` propiedad de un elemento HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Establece el host `IDispatch` interfaz.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Establece las marcas de la interfaz de usuario del host.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Se llama cuando un menú contextual está a punto de mostrarse.|
|[CDHtmlDialog::ShowUI](#showui)|Muestra la interfaz de usuario del host.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Se llama para procesar los mensajes de tecla de aceleración de menú.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Se llama para modificar la dirección URL se va a cargar.|
|[CDHtmlDialog::UpdateUI](#updateui)|Se llama para notificar al host que ha cambiado el estado del comando.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Indica si se usa el título del documento HTML como el título del cuadro de diálogo.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Resource Id. de recurso HTML que se mostrará.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Un puntero a una aplicación de explorador Web.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Un puntero a un documento HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|La dirección URL actual.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Versión de cadena del identificador del recurso HTML.|

## <a name="remarks"></a>Comentarios

`CDHtmlDialog` puede cargar el código HTML que se muestran desde un recurso HTML o una dirección URL.

`CDHtmlDialog` pueden también hacer datos intercambiar con los controles de HTML y controlar eventos de controles HTML, como clics de botón.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdhtml.h

##  <a name="ddx_dhtml_helper_macros"></a>  DDX_DHtml auxiliar Macros

Las macros de la aplicación auxiliar DDX_DHtml permiten un acceso sencillo a las propiedades utilizadas de controles en una página HTML.

### <a name="data-exchange-macros"></a>Macros de intercambio de datos

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Establece o recupera la propiedad Value del control seleccionado.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Establece o recupera el texto entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Establece o recupera el HTML entre las etiquetas inicial y final del elemento actual.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Establece o recupera el punto de dirección URL o delimitador de destino.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Establece o recupera la ventana de destino o el marco.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Establece o recupera el nombre de una imagen o un clip de vídeo en el documento.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Establece o recupera la dirección URL del marco asociado.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Establece o recupera la dirección URL del marco asociado.|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

Reemplazables se denomina como una comprobación de acceso para ver si los objetos de scripting en la página cargada pueden tener acceso el envío de sitio del control externo. Comprueba para asegurarse de que el envío es ser seguros para scripting o la zona actual se permite para los objetos que no son seguros para scripting.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="cdhtmldialog"></a>  CDHtmlDialog::CDHtmlDialog

Construye un cuadro de diálogo basada en recursos HTML dinámico.

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
La cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*szHtmlResID*<br/>
La cadena terminada en null que es el nombre de un recurso HTML.

*pParentWnd*<br/>
Un puntero al objeto de ventana principal o propietaria (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*nIDTemplate*<br/>
Contiene el número de Id. de un recurso de plantilla de cuadro de diálogo.

*nHtmlResID*<br/>
Contiene el número de Id. de un recurso HTML.

### <a name="remarks"></a>Comentarios

El segundo formulario del constructor proporciona acceso al recurso de cuadro de diálogo a través del nombre de plantilla. El tercer formulario del constructor proporciona acceso al recurso de cuadro de diálogo por el identificador de la plantilla de recursos. Normalmente, el identificador empieza por el **IDD_** prefijo.

##  <a name="_dtorcdhtmldialog"></a>  CDHtmlDialog::~CDHtmlDialog

Destruye un objeto CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Comentarios

El [CWnd:: DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) función miembro se debe usar para destruir los cuadros de diálogo no modal que se crean mediante [CDialog::Create](../../mfc/reference/cdialog-class.md#create).

##  <a name="createcontrolsite"></a>  CDHtmlDialog::CreateControlSite

Reemplazable usado para crear una instancia de sitio del control para hospedar el control WebBrowser en el cuadro de diálogo.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Parámetros

*pContainer*<br/>
Un puntero a la [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md) objeto

*ppSite*<br/>
Un puntero a un puntero a un [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Puede reemplazar esta función miembro para devolver una instancia de su propia clase de sitio del control.

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

Intercambia datos entre una variable de miembro y el valor de propiedad de un control ActiveX en una página HTML.

```
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*szId*<br/>
El valor del parámetro de identificador de la etiqueta de objeto en el código fuente HTML para el control ActiveX.

*dispId*<br/>
El identificador de envío de la propiedad con el que desee intercambiar datos.

*szPropName*<br/>
Nombre de la propiedad.

*var*<br/>
El miembro de datos de tipo VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md), o [CComVariant](../../atl/reference/ccomvariant-class.md), que contiene el valor que se intercambian con la propiedad del control ActiveX.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

Intercambia datos entre una variable de miembro y una casilla de verificación en una página HTML.

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*szId*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*value*<br/>
El valor que se intercambian.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

Intercambia datos entre una variable de miembro y cualquier propiedad de elemento HTML en una página HTML.

```
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*szId*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*dispId*<br/>
El identificador de envío del elemento HTML con la que desea intercambiar datos.

*value*<br/>
El valor que se intercambian.

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

Intercambia datos entre una variable de miembro y un botón de radio en una página HTML.

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*szId*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*value*<br/>
El valor que se intercambian.

##  <a name="ddx_dhtml_selectindex"></a>  CDHtmlDialog::DDX_DHtml_SelectIndex

Obtiene o establece el índice de un cuadro de lista en una página HTML.

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*szId*<br/>
El valor que especificó para el control HTML `id` parámetro.

*value*<br/>
El valor que se intercambian.

##  <a name="ddx_dhtml_selectstring"></a>  CDHtmlDialog::DDX_DHtml_SelectString

Obtiene o establece el texto para mostrar de una entrada de cuadro de lista (según el índice actual) en una página HTML.

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*szId*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*value*<br/>
El valor que se intercambian.

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

Obtiene o establece el valor de una entrada de cuadro de lista (según el índice actual) en una página HTML.

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Parámetros

*pDX*<br/>
Un puntero a un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*szId*<br/>
El valor que especificó para el parámetro de Id. del control HTML.

*value*<br/>
El valor que se intercambian.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

Desasocia un cuadro de diálogo no modal desde el `CDHtmlDialog` de objetos y destruye el objeto.

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>  CDHtmlDialog::EnableModeless

Permite a los cuadros de diálogo no modal.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Parámetros

*fEnable*<br/>
Consulte *fEnable* en [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="filterdataobject"></a>  CDHtmlDialog::FilterDataObject

Permite que el cuadro de diálogo Filtrar los objetos del Portapapeles datos creados por el explorador hospedado.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Parámetros

*pDO*<br/>
Consulte *pDO* en [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) en el SDK de Windows.

*ppDORet*<br/>
Consulte *ppDORet* en `IDocHostUIHandler::FilterDataObject` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="getcontroldispatch"></a>  CDHtmlDialog::GetControlDispatch

Recupera el `IDispatch` interfaz en un control ActiveX incrustado en el documento HTML devuelve [GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Parámetros

*szId*<br/>
El identificador HTML de un control ActiveX.

*ppdisp*<br/>
El `IDispatch` interfaz del control si se encuentra en la página Web.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="getcontrolproperty"></a>  CDHtmlDialog::GetControlProperty

Recupera la propiedad solicitada del control ActiveX especificado.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>Parámetros

*szId*<br/>
El identificador HTML de un control ActiveX.

*szPropName*<br/>
El nombre de una propiedad en la configuración regional predeterminada del usuario actual.

*pdispControl*<br/>
El `IDispatch` puntero de un control ActiveX.

*dispId*<br/>
El identificador de envío de una propiedad.

### <a name="return-value"></a>Valor devuelto

Una variante que contiene la propiedad solicitada o un variante vacío si no se encontró el control o la propiedad.

### <a name="remarks"></a>Comentarios

Se enumeran las sobrecargas de menos eficiente en la parte superior a más eficaz en la parte inferior.

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

Recupera el localizador uniforme de recursos (URL) asociado con el documento actual.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Parámetros

*szUrl*<br/>
Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la dirección URL para recuperar el objeto.

##  <a name="getdhtmldocument"></a>  CDHtmlDialog::GetDHtmlDocument

Recupera el [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) interfaz en el documento HTML cargado actualmente.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Parámetros

*\*\*pphtmlDoc* un puntero a un puntero a un documento HTML.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar. Devuelve S_OK si se realiza correctamente.

##  <a name="getdroptarget"></a>  CDHtmlDialog::GetDropTarget

Lo llama el control WebBrowser independiente cuando lo está usando como un destino de colocación para permitir que el cuadro de diálogo proporcionar una alternativa [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Parámetros

*pDropTarget*<br/>
Consulte *pDropTarget* en [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) en el SDK de Windows.

*ppDropTarget*<br/>
Consulte *ppDropTarget* en `IDocHostUIHandler::GetDropTarget` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="getelement"></a>  CDHtmlDialog::GetElement

Devuelve una interfaz en el elemento HTML especificado por *szElementId*.

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

*ppdisp*<br/>
Un `IDispatch` puntero a la colección de elementos o el elemento solicitado.

*pbCollection*<br/>
Un valor booleano que indica si el objeto representado por *ppdisp* es un elemento único o una colección de elementos.

*pphtmlElement*<br/>
Un `IHTMLElement` puntero al elemento solicitado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Utilice la primera sobrecarga si necesita controlar las condiciones en las que puede haber más de un elemento con el identificador especificado. Puede usar el último parámetro para averiguar si el puntero de interfaz devuelto es una colección o un solo elemento. Si el puntero de interfaz está en una colección, puede consultar el `IHTMLElementCollection` y usar su `item` propiedad para hacer referencia a los elementos según su posición ordinal.

La segunda sobrecarga se producirá un error si hay más de un elemento con el mismo identificador en la página.

##  <a name="getelementhtml"></a>  CDHtmlDialog::GetElementHtml

Recupera el `innerHTML` propiedad del elemento HTML identificado por *szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

### <a name="return-value"></a>Valor devuelto

El `innerHTML` propiedad del elemento HTML identificado por *szElementId* o NULL si no se encontró el elemento.

##  <a name="getelementinterface"></a>  CDHtmlDialog::GetElementInterface

Recupera el puntero de interfaz solicitada del elemento HTML identificado por *szElementId*.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

*ppvObj*<br/>
Dirección de un puntero que se rellenará con el puntero de interfaz solicitada si se encuentra el elemento y la consulta se realiza correctamente.

*refiid*<br/>
La interfaz de identificador (IID) de la interfaz solicitada.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>  CDHtmlDialog::GetElementProperty

Recupera el valor de la propiedad identificada por *dispId* desde el elemento HTML identificado por *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

*dispId*<br/>
El identificador de envío de una propiedad.

### <a name="return-value"></a>Valor devuelto

El valor de la propiedad o un variante vacío si no se encontró la propiedad o el elemento.

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

Recupera el `innerText` propiedad del elemento HTML identificado por *szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

### <a name="return-value"></a>Valor devuelto

El `innerText` propiedad del elemento HTML identificado por *szElementId* o NULL si no se encontró la propiedad o el elemento.

##  <a name="getevent"></a>  CDHtmlDialog::GetEvent

Devuelve el `IHTMLEventObj` puntero al objeto de evento actual.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Parámetros

*ppEventObj*<br/>
Dirección de un puntero que se rellenará con el `IHTMLEventObj` puntero de interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Esta función solo debe llamarse desde dentro de un controlador de eventos DHTML.

##  <a name="getexternal"></a>  CDHtmlDialog::GetExternal

Obtiene el host `IDispatch` interfaz.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Parámetros

*ppDispatch*<br/>
Consulte *ppDispatch* en [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si funciona correctamente o E_NOTIMPL en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

Recupera las capacidades de la interfaz de usuario del host.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Parámetros

*pInfo*<br/>
Consulte *pInfo* en [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="getoptionkeypath"></a>  CDHtmlDialog::GetOptionKeyPath

Recupera la clave del registro bajo la que se almacenan las preferencias del usuario.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Parámetros

*pchKey*<br/>
Consulte *pchKey* en [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) en el SDK de Windows.

*dw*<br/>
Consulte *dw* en `IDocHostUIHandler::GetOptionKeyPath` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="hideui"></a>  CDHtmlDialog::HideUI

Oculta la interfaz de usuario del host.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

Indica si el host `IDispatch` interfaz es segura para scripting.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE.

##  <a name="loadfromresource"></a>  CDHtmlDialog::LoadFromResource

Carga el recurso especificado en el control WebBrowser en el cuadro de diálogo DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Parámetros

*lpszResource*<br/>
Un puntero a una cadena que contiene el nombre del recurso que quiere cargar.

*nRes*<br/>
El identificador del recurso para cargar.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

Indica si se usa el título del documento HTML como el título del cuadro de diálogo.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Comentarios

Si **m**_ **bUseHtmlTitle** es TRUE, el título del cuadro de diálogo se establece igual que el título del documento HTML; en caso contrario, se usa el título en el recurso de cuadro de diálogo.

##  <a name="m_nhtmlresid"></a>  CDHtmlDialog::m_nHtmlResID

Resource Id. de recurso HTML que se mostrará.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

Un puntero a una aplicación de explorador Web.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

Un puntero a un documento HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>  CDHtmlDialog::m_strCurrentUrl

La dirección URL actual.

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

Versión de cadena del identificador del recurso HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>  CDHtmlDialog::Navigate

Navega al recurso identificado por la dirección URL especificada por *lpszURL*.

```
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>Parámetros

*lpszURL*<br/>
Un puntero a una cadena que contiene la dirección URL de destino.

*dwFlags*<br/>
Los indicadores de una variable que especifica si se debe agregar el recurso a la lista del historial, si se debe a la memoria caché de lectura o escritura de la memoria caché y si se muestra el recurso en una nueva ventana. La variable puede ser una combinación de los valores definidos por el [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) enumeración.

*lpszTargetFrameName*<br/>
Un puntero a una cadena que contiene el nombre del marco en el que se va a mostrar el recurso.

*lpszHeaders*<br/>
Un puntero a un valor que especifica los encabezados HTTP para enviar al servidor. Estos encabezados se agregan a los encabezados de Internet Explorer de forma predeterminada. Los encabezados pueden especificar dicha información como la acción necesaria del servidor, el tipo de datos que se pasan al servidor o un código de estado. Este parámetro se omite si la dirección URL no es una dirección URL HTTP.

*lpvPostData*<br/>
Un puntero a los datos que se va a enviar con la transacción de solicitud HTTP POST. Por ejemplo, la transacción POST se usa para enviar los datos recopilados por un formulario HTML. Si este parámetro no especifica ningún dato de envío, `Navigate` emite una transacción HTTP GET. Este parámetro se omite si la dirección URL no es una dirección URL HTTP.

*dwPostDataLen*<br/>
Datos que se envían con la transacción de solicitud HTTP POST. Por ejemplo, la transacción POST se usa para enviar los datos recopilados por un formulario HTML. Si este parámetro no especifica ningún dato de envío, `Navigate` emite una transacción HTTP GET. Este parámetro se omite si la dirección URL no es una dirección URL HTTP.

##  <a name="onbeforenavigate"></a>  CDHtmlDialog::OnBeforeNavigate

Lo llama el marco de trabajo para hacer que un evento se desencadena antes de que tenga lugar la navegación.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
Puntero a un objeto `IDispatch`.

*szUrl*<br/>
Un puntero a una cadena que contiene la dirección URL de destino.

##  <a name="ondocumentcomplete"></a>  CDHtmlDialog::OnDocumentComplete

Lo llama el marco de trabajo para notificar a una aplicación cuando un documento ha logrado el estado READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
Puntero a un objeto `IDispatch`.

*szUrl*<br/>
Un puntero a una cadena que contiene la dirección URL que se navegó.

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

Lo llama el marco de trabajo cuando se activa o desactiva la ventana de documento.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parámetros

*fActivate*<br/>
Consulte *fActivate* en [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

Lo llama el marco de trabajo cuando se activa o desactiva la ventana de marco.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Parámetros

*fActivate*<br/>
Consulte *fActivate* en [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="oninitdialog"></a>  CDHtmlDialog::OnInitDialog

Se llama en respuesta al mensaje WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve TRUE.

### <a name="remarks"></a>Comentarios

Este mensaje se envía al cuadro de diálogo durante la `Create`, `CreateIndirect`, o `DoModal` llamadas, que se producen inmediatamente antes de que se muestre el cuadro de diálogo.

Reemplace esta función miembro si tiene que realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. En la versión invalidada, llame primero a la clase base `OnInitDialog` pero pasar por alto el valor devuelto. Normalmente devolverá TRUE desde la función miembro reemplazado.

Las llamadas de Windows la `OnInitDialog` funcionar a través del procedimiento de cuadro de diálogo global estándar comunes a todos los cuadros de diálogo de Microsoft Foundation Class Library, en lugar de a través de su mapa de mensajes, por lo que no necesita una entrada de mapa de mensajes para esta función miembro.

##  <a name="onnavigatecomplete"></a>  CDHtmlDialog::OnNavigateComplete

Lo llama el marco de trabajo una vez completada la navegación a la dirección URL especificada.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
Puntero a un objeto `IDispatch`.

*szUrl*<br/>
Un puntero a una cadena que contiene la dirección URL que se navegó.

##  <a name="resizeborder"></a>  CDHtmlDialog::ResizeBorder

Alerta al objeto que debe cambiar el tamaño de su espacio del borde.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Parámetros

*prcBorder*<br/>
Consulte *prcBorder* en [IDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) en el SDK de Windows.

*pUIWindow*<br/>
Consulte *pUIWindow* en `IDocHostUIHandler::ResizeBorder` en el SDK de Windows.

*fFrameWindow*<br/>
Consulte *fFrameWindow* en `IDocHostUIHandler::ResizeBorder` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="setcontrolproperty"></a>  CDHtmlDialog::SetControlProperty

Establece la propiedad de un control ActiveX a un nuevo valor.

```
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador HTML de un control ActiveX.

*dispId*<br/>
El identificador de envío de la propiedad para establecer.

*pVar*<br/>
Puntero a una variante que contiene el nuevo valor de propiedad.

*pdispControl*<br/>
Puntero a un control ActiveX `IDispatch` interfaz.

*szPropName*<br/>
Cadena que contiene el nombre de la propiedad para establecer.

##  <a name="setelementhtml"></a>  CDHtmlDialog::SetElementHtml

Establece el `innerHTML` propiedad de un elemento HTML.

```
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

*bstrText*<br/>
Nuevo valor de la propiedad `innerHTML`.

*punkElem*<br/>
El `IUnknown` puntero de un elemento HTML.

##  <a name="setelementproperty"></a>  CDHtmlDialog::SetElementProperty

Establece una propiedad de un elemento HTML.

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

*dispId*<br/>
El identificador de envío de la propiedad para establecer.

*pVar*<br/>
Nuevo valor de la propiedad.

##  <a name="setelementtext"></a>  CDHtmlDialog::SetElementText

Establece el `innerText` propiedad de un elemento HTML.

```
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Parámetros

*szElementId*<br/>
El identificador de un elemento HTML.

*bstrText*<br/>
Nuevo valor de la propiedad `innerText`.

*punkElem*<br/>
El `IUnknown` puntero de un elemento HTML.

##  <a name="setexternaldispatch"></a>  CDHtmlDialog::SetExternalDispatch

Establece el host `IDispatch` interfaz.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Parámetros

*pdispExternal*<br/>
El nuevo `IDispatch` interfaz.

##  <a name="sethostflags"></a>  CDHtmlDialog::SetHostFlags

Establece el host de marcas de la interfaz de usuario.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Para los valores posibles, vea [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) en el SDK de Windows.

##  <a name="showcontextmenu"></a>  CDHtmlDialog::ShowContextMenu

Se llama cuando un menú contextual está a punto de mostrarse.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Parámetros

*dwID*<br/>
Consulte *dwID* en [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) en el SDK de Windows.

*ppt*<br/>
Consulte *ppt* en `IDocHostUIHandler::ShowContextMenu` en el SDK de Windows.

*pcmdtReserved*<br/>
Consulte *pcmdtReserved* en `IDocHostUIHandler::ShowContextMenu` en el SDK de Windows.

*pdispReserved*<br/>
Consulte *pdispReserved* en `IDocHostUIHandler::ShowContextMenu` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="showui"></a>  CDHtmlDialog::ShowUI

Muestra la interfaz de usuario del host.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Parámetros

*dwID*<br/>
Consulte *dwID* en [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) en el SDK de Windows.

*pActiveObject*<br/>
Consulte *pActiveObject d* en `IDocHostUIHandler::ShowUI` en el SDK de Windows.

*pCommandTarget*<br/>
Consulte *pCommandTarget* en `IDocHostUIHandler::ShowUI` en el SDK de Windows.

*pFrame*<br/>
Consulte *pFrame* en `IDocHostUIHandler::ShowUI` en el SDK de Windows.

*pDoc*<br/>
Consulte *pDoc* en `IDocHostUIHandler::ShowUI` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="translateaccelerator"></a>  CDHtmlDialog::TranslateAccelerator

Se llama para procesar los mensajes de tecla de aceleración de menú.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Parámetros

*lpMsg*<br/>
Consulte *lpMsg* en [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) en el SDK de Windows.

*pguidCmdGroup*<br/>
Consulte *pguidCmdGroup* en `IDocHostUIHandler::TranslateAccelerator` en el SDK de Windows.

*nCmdID*<br/>
Consulte *nCmdID* en `IDocHostUIHandler::TranslateAccelerator` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="translateurl"></a>  CDHtmlDialog::TranslateUrl

Se llama para modificar la dirección URL se va a cargar.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Parámetros

*dwTranslate*<br/>
Consulte *dwTranslate* en [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) en el SDK de Windows.

*pchURLIn*<br/>
Consulte *pchURLIn* en `IDocHostUIHandler::TranslateUrl` en el SDK de Windows.

*ppchURLOut*<br/>
Consulte *ppchURLOut* en `IDocHostUIHandler::TranslateUrl` en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), tal y como se describe en el SDK de Windows.

##  <a name="updateui"></a>  CDHtmlDialog::UpdateUI

Se llama para notificar al host que ha cambiado el estado del comando.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Esta función miembro es la implementación de CDHtmlDialog de [IDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), tal y como se describe en el SDK de Windows.

## <a name="see-also"></a>Vea también

[DHtmlExplore de ejemplo MFC](../../visual-cpp-samples.md)<br/>
[DDX_DHtml (macros del asistente)](#ddx_dhtml_helper_macros)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
