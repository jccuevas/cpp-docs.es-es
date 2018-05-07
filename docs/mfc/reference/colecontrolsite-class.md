---
title: Clase COleControlSite | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4dcb17c2650bf8b56702241a0ab4e77a3e2fc48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="colecontrolsite-class"></a>Clase COleControlSite
Proporciona compatibilidad con interfaces de control de cliente personalizadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::COleControlSite](#colecontrolsite)|Construye un objeto `COleControlSite`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|La propiedad predeterminada del control hospedado se enlaza a un origen de datos.|  
|[COleControlSite::BindProperty](#bindproperty)|Enlaza una propiedad del control hospedado en un origen de datos.|  
|[COleControlSite::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|  
|[COleControlSite::DestroyControl](#destroycontrol)|Destruye el control hospedado.|  
|[COleControlSite::DoVerb](#doverb)|Ejecuta un verbo específico del control hospedado.|  
|[COleControlSite::EnableDSC](#enabledsc)|Permite que los datos de origen para un sitio del control.|  
|[COleControlSite::EnableWindow](#enablewindow)|Permite que el sitio del control.|  
|[COleControlSite::FreezeEvents](#freezeevents)|Especifica si el sitio del control es aceptar eventos.|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Recupera el código del botón predeterminado para el control hospedado.|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Recupera el identificador del control.|  
|[COleControlSite::GetEventIID](#geteventiid)|Recupera el identificador de una interfaz de eventos para un control hospedado.|  
|[COleControlSite::GetExStyle](#getexstyle)|Recupera los estilos extendidos de sitio del control.|  
|[COleControlSite::GetProperty](#getproperty)|Recupera una propiedad específica del control hospedado.|  
|[COleControlSite::GetStyle](#getstyle)|Recupera los estilos de sitio del control.|  
|[COleControlSite::GetWindowText](#getwindowtext)|Recupera el texto del control hospedado.|  
|[COleControlSite::InvokeHelper](#invokehelper)|Invocar un método específico del control hospedado.|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|Invocar un método específico del control hospedado con una lista variable de argumentos.|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Determina si el control es el botón predeterminado en la ventana.|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Comprueba el estado de visibilidad de sitio del control.|  
|[COleControlSite::ModifyStyle](#modifystyle)|Modifica el actual extendidos estilos de sitio del control.|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modifica los estilos de sitio del control actuales.|  
|[COleControlSite::MoveWindow](#movewindow)|Cambia la posición del sitio del control.|  
|[COleControlSite::QuickActivate](#quickactivate)|Rápida activa el control hospedado.|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|Establece una propiedad o método del control sin posibilidad de producir una excepción.|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Establece el botón predeterminado en la ventana.|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Recupera el identificador del control.|  
|[COleControlSite::SetFocus](#setfocus)|Establece el foco en el sitio del control.|  
|[COleControlSite::SetProperty](#setproperty)|Establece una propiedad específica del control hospedado.|  
|[COleControlSite::SetPropertyV](#setpropertyv)|Establece una propiedad específica del control hospedado con una lista variable de argumentos.|  
|[COleControlSite::SetWindowPos](#setwindowpos)|Establece la posición del sitio del control.|  
|[COleControlSite::SetWindowText](#setwindowtext)|Establece el texto del control hospedado.|  
|[COleControlSite::ShowWindow](#showwindow)|Muestra u oculta el sitio del control.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Recupera información sobre el teclado y teclas de acceso para el control hospedado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Determina si el control hospedado es un control sin ventana.|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Contiene información sobre el control para el control del teclado.|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|La cookie de punto de conexión del control.|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Los diversos estados para el control hospedado.|  
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|El `IPropertyNotifySink` cookie del control.|  
|[COleControlSite::m_dwStyle](#m_dwstyle)|Los estilos del control hospedado.|  
|[COleControlSite::m_hWnd](#m_hwnd)|El identificador de sitio del control.|  
|[COleControlSite::m_iidEvents](#m_iidevents)|El identificador de la interfaz de eventos para el control hospedado.|  
|[COleControlSite::m_nID](#m_nid)|El identificador del control hospedado.|  
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Un puntero a la `IOleInPlaceActiveObject` objeto del control hospedado.|  
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|El contenedor del control hospedado.|  
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Un puntero a la `IOleInPlaceObject` objeto del control hospedado.|  
|[COleControlSite::m_pObject](#m_pobject)|Un puntero a la `IOleObjectInterface` interfaz del control.|  
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Un puntero a la `IOleInPlaceObjectWindowless` interfaz del control.|  
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Un puntero al objeto de ventana para el control hospedado.|  
|[COleControlSite::m_rect](#m_rect)|Las dimensiones del sitio del control.|  
  
## <a name="remarks"></a>Comentarios  
 Esta compatibilidad es el medio principal por el que un control ActiveX incrustado obtiene información sobre la ubicación y el alcance de su página de muestra, su moniker, su interfaz de usuario, sus propiedades de ambiente y otros recursos proporcionados por su contenedor. `COleControlSite` implementa por completo el [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502), [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706), [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638),  **IBoundObjectSite**, **INotifyDBEvents**, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) interfaces. Además, también se implementa la interfaz de IDispatch (proporcionar soporte técnico para las propiedades de ambiente y receptores de eventos).  
  
 Para crear un sitio del control ActiveX con `COleControlSite`, derive una clase de `COleControlSite`. En su `CWnd`-clase derivada para el contenedor (por ejemplo, en el cuadro de diálogo) reemplazar la **CWnd::CreateControlSite** (función).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxocc.h  
  
##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty  
 Propiedad enlazada simple predeterminada del objeto que realiza la llamada, como se marca en la biblioteca de tipos, se enlaza al cursor subyacente que se define mediante las propiedades DataSource, UserName, Password y SQL del control de origen de datos.  
  
```  
virtual void BindDefaultProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    LPCTSTR szFieldName,  
    CWnd* pDSCWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Especifica la **DISPID** de una propiedad en un control enlazado a datos que se enlaza a un control de origen de datos.  
  
 `vtProp`  
 Especifica el tipo de la propiedad que se va a enlazar, por ejemplo, `VT_BSTR`, **VT_VARIANT**, y así sucesivamente.  
  
 `szFieldName`  
 Especifica el nombre de la columna del cursor proporcionados por el control de origen de datos, al que se enlazará la propiedad.  
  
 `pDSCWnd`  
 Un puntero a la `CWnd`-objeto derivado que hospeda el control de origen de datos a la que se enlazará la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 La `CWnd` objeto en el que se llame a esta función debe ser un control enlazado a datos.  
  
##  <a name="bindproperty"></a>  COleControlSite::BindProperty  
 Enlaza la propiedad enlazada simple del objeto que realiza la llamada, como se marca en la biblioteca de tipos, hasta el cursor subyacente que se define mediante las propiedades DataSource, UserName, Password y SQL del control de origen de datos.  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDispId*  
 Especifica la **DISPID** de una propiedad en un control enlazado a datos que se enlaza a un control de origen de datos.  
  
 `pWndDSC`  
 Un puntero a la `CWnd`-objeto derivado que hospeda el control de origen de datos a la que se enlazará la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 La `CWnd` objeto en el que se llame a esta función debe ser un control enlazado a datos.  
  
##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite  
 Construye un nuevo objeto `COleControlSite`.  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCtrlCont`  
 Un puntero al contenedor del control (que representa la ventana que hospeda el control de parte).  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca la [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) (función). Para obtener más información acerca de cómo personalizar la creación de contenedores, consulte [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).  
  
##  <a name="createcontrol"></a>  COleControlSite::CreateControl  
 Crea un control ActiveX, hospedado por la `COleControlSite` objeto.  
  
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
 `pWndCtrl`  
 Un puntero al objeto window que representa el control.  
  
 `clsid`  
 El identificador de clase único del control.  
  
 `lpszWindowName`  
 Un puntero al texto que se mostrará en el control. Establece el valor de propiedad de leyenda o el texto del winodw (si existe).  
  
 `dwStyle`  
 Estilos de Windows. Los estilos disponibles aparecen en la **comentarios** sección.  
  
 `rect`  
 Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto o un `RECT` estructura.  
  
 `nID`  
 Especifica la ventana de identificador secundario. del control  
  
 `pPersist`  
 Un puntero a un `CFile` que contiene el estado persistente del control. El valor predeterminado es **NULL**, que indica que el control se inicializa sin necesidad de restaurar su estado de todo el almacenamiento persistente. Si no **NULL**, debe ser un puntero a un `CFile`: objeto que contiene los datos del control persistente, en forma de una secuencia o un almacenamiento derivado. Estos datos se ha guardado en una activación anterior del cliente. El `CFile` puede contener otros datos, pero debe tener el puntero de lectura y escritura establecido en el primer byte de datos persistentes en el momento de la llamada a `CreateControl`.  
  
 `bStorage`  
 Indica si los datos de `pPersist` deben interpretarse como `IStorage` o `IStream` datos. Si los datos de `pPersist` es un almacenamiento `bStorage` debe ser **TRUE**. Si los datos de `pPersist` es una secuencia, `bStorage` debe ser **FALSE**. El valor predeterminado es **FALSE**.  
  
 `bstrLicKey`  
 Datos de clave de licencia opcional. Estos datos sólo es necesaria para crear los controles que requieren una clave de licencia de tiempo de ejecución. Si el control admite las licencias, debe proporcionar una clave de licencia para la creación del control que se realice correctamente. El valor predeterminado es **NULL**.  
  
 `ppt`  
 Un puntero a un **punto** estructura que contiene la esquina superior izquierda del control. El tamaño del control se determina por el valor de *psize*. El `ppt` y *psize* valores son un método opcional para especificar el tamaño y colocar opf el control.  
  
 *psize*  
 Un puntero a un **tamaño** estructura que contiene el tamaño del control. La esquina superior izquierda viene determinada por el valor de `ppt`. El `ppt` y *psize* valores son un método opcional para especificar el tamaño y colocar opf el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Solo un subconjunto de las ventanas `dwStyle` marcas son compatibles con `CreateControl`:  
  
- **WS_VISIBLE** crea una ventana que esté visible inicialmente. Necesario si desea que el control sea visible inmediatamente, como las ventanas normales.  
  
- **WS_DISABLED** crea una ventana que está inicialmente deshabilitada. Una ventana deshabilitada no puede recibir la entrada del usuario. Puede establecerse si el control tiene una propiedad Enabled.  
  
- `WS_BORDER` Crea una ventana con un borde de línea fino. Puede establecerse si el control tiene una propiedad de estilo de borde.  
  
- **WS_GROUP** especifica el primer control de un grupo de controles. El usuario puede cambiar el foco del teclado de un control en el grupo a otro utilizando las teclas de dirección. Todos los controles definidos con el **WS_GROUP** después de que el primer control pertenecen al mismo grupo de estilo. El siguiente control con el **WS_GROUP** estilo finaliza el grupo e inicia el grupo siguiente.  
  
- **WS_TABSTOP** especifica un control que puede recibir el foco de teclado cuando el usuario presiona la tecla TAB. Al presionar la tecla TAB cambia el foco del teclado al siguiente control de la **WS_TABSTOP** estilo.  
  
 Usar la segunda sobrecarga para crear controles de tamaño predeterminado.  
  
##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl  
 Destruye el objeto `COleControlSite`.  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una vez completado, se libera el objeto de la memoria y los punteros en el objeto ya no son válidos.  
  
##  <a name="doverb"></a>  COleControlSite::DoVerb  
 Ejecuta el verbo especificado.  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nVerb`  
 Especifica el verbo que se ejecute. Puede incluir uno de los siguientes:  
  
|Valor|Significado|Símbolo|  
|-----------|-------------|------------|  
|0|verbo principal|`OLEIVERB_PRIMARY`|  
|-1|Verbo secundario|(Ninguno)|  
|1|Muestra el objeto para su edición.|`OLEIVERB_SHOW`|  
|-2|Modifica el elemento en una ventana independiente.|`OLEIVERB_OPEN`|  
|-3|Oculta el objeto.|`OLEIVERB_HIDE`|  
|-4|Activa un control in situ.|`OLEIVERB_UIACTIVATE`|  
|-5|Activa un control in situ, sin elementos de la interfaz de usuario adicionales.|**OLEIVERB_INPLACEACTIVATE**|  
|-7|Mostrar las propiedades del control.|**OLEIVERB_PROPERTIES**|  
  
 `lpMsg`  
 Puntero al mensaje que provocó el elemento que se debe activar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función llama directamente a través del control `IOleObject` interfaz para ejecutar el verbo especificado. Si se produce una excepción como resultado de esta llamada de función, un `HRESULT` código de error devuelto.  
  
 Para obtener más información, consulte [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) del SDK de Windows.  
  
##  <a name="enabledsc"></a>  COleControlSite::EnableDSC  
 Permite que los datos de origen para el sitio del control.  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>Comentarios  
 Lo llama el marco para habilitar e iniciar para el sitio del control de origen de datos. Reemplace esta función para proporcionar un comportamiento personalizado.  
  
##  <a name="enablewindow"></a>  COleControlSite::EnableWindow  
 Habilita o deshabilita el mouse y teclado como entrada para el sitio del control.  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 Especifica si se debe habilitar o deshabilitar la ventana: **TRUE** si la entrada de ventana está habilitado, en caso contrario, **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la ventana se deshabilitó anteriormente, en caso contrario, 0.  
  
##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents  
 Especifica si el sitio del control se controlar u omitir los eventos desencadenados desde un control.  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parámetros  
 `bFreeze`  
 Especifica si el sitio del control desea dejar de aceptar eventos. Es distinto de cero si el control no acepta eventos; cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Si `bFreeze` es **TRUE**, el sitio del control solicita el control detener fring eventos. Si `bFreeze` es **FALSE**, el sitio del control solicita el control para continuar desencadenar eventos.  
  
> [!NOTE]
>  El control no es necesario detener desencadenar eventos si lo solicita el sitio del control. Puede continuar la activación pero se pasará por alto todos los eventos posteriores por el sitio del control.  
  
##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo  
 Recupera información sobre el comportamiento del teclado y teclas de acceso de teclado de un control.  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>Comentarios  
 La información se almacena en [COleControlSite::m_ctlInfo](#m_ctlinfo).  
  
##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode  
 Determina si el control es un botón de comando predeterminado.  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puede presentar uno de los siguientes valores:  
  
- **DLGC_DEFPUSHBUTTON** Control es el botón predeterminado en el cuadro de diálogo.  
  
- **DLGC_UNDEFPUSHBUTTON** Control no es el botón predeterminado en el cuadro de diálogo.  
  
- **0** control no es un botón.  
  
##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID  
 Recupera el identificador del control.  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento de cuadro de diálogo del control.  
  
##  <a name="geteventiid"></a>  COleControlSite::GetEventIID  
 Recupera un puntero a interfaz de eventos del control de forma predeterminada.  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>Parámetros  
 `piid`  
 Un puntero a un identificador de interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, en caso contrario, 0. Si se realiza correctamente, `piid` contiene el identificador de interfaz para la interfaz de evento predeterminado del control.  
  
##  <a name="getexstyle"></a>  COleControlSite::GetExStyle  
 Recupera los estilos de ventana extendidos.  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ventana de control del estilos extendidos.  
  
### <a name="remarks"></a>Comentarios  
 Para recuperar los estilos normales, llame a [COleControlSite::GetStyle](#getstyle).  
  
##  <a name="getproperty"></a>  COleControlSite::GetProperty  
 Obtiene la propiedad de control especificada por `dwDispID`.  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad, se encuentra en el valor predeterminado del control `IDispatch` interfaz, va a recuperar.  
  
 `vtProp`  
 Especifica el tipo de la propiedad que se va a recuperar. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvProp`  
 Dirección de la variable que recibirá el valor de propiedad. Debe coincidir con el tipo especificado por `vtProp`.  
  
### <a name="remarks"></a>Comentarios  
 El valor se devuelve a través de `pvProp`.  
  
##  <a name="getstyle"></a>  COleControlSite::GetStyle  
 Recupera los estilos de sitio del control.  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los estilos de ventana.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una lista de valores posibles, consulte [Windows estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles). Para recuperar los estilos extendidos de sitio del control, llame a [COleControlSite::GetExStyle](#getexstyle).  
  
##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText  
 Recupera el texto actual del control.  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 Una referencia a un `CString` objeto que contiene el texto actual del control.  
  
### <a name="remarks"></a>Comentarios  
 Si el control admite la propiedad estándar del título, se devuelve este valor. Si no se admite la propiedad estándar del título, se devuelve el valor de la propiedad de texto.  
  
##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper  
 Invoca el método o la propiedad especificada por `dwDispID`, en el contexto especificado por `wFlags`.  
  
```  
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, se encuentra en el control `IDispatch` interfaz, que se debe invocar.  
  
 `wFlags`  
 Marcas que describen el contexto de la llamada a IDispatch:: Invoke. Posibles `wFlags` valores, vea `IDispatch::Invoke` en el SDK de Windows.  
  
 `vtRet`  
 Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por `vtRet`.  
  
 `pbParamInfo`  
 Puntero a una cadena terminada en null de bytes que especifica los tipos de los parámetros que siguen a `pbParamInfo`. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Lista de variables de parámetros, de tipos especificados en `pbParamInfo`.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `pbParamInfo` especifica los tipos de los parámetros pasados al método o a la propiedad. La lista variable de argumentos se representa mediante... en la declaración de sintaxis.  
  
 Esta función convierte los parámetros de **VARIANTARG** valores, a continuación, se invoca el **IDispatch:: Invoke** método en el control. Si la llamada a **IDispatch:: Invoke** se produce un error, esta función iniciará una excepción. Si el código de estado devuelto por **IDispatch:: Invoke** es `DISP_E_EXCEPTION`, esta función genera un **COleDispatchException** objeto, en caso contrario produce un `COleException`.  
  
##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV  
 Invoca el método o la propiedad especificada por `dwDispID`, en el contexto especificado por `wFlags`.  
  
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
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, se encuentra en el control `IDispatch` interfaz, que se debe invocar.  
  
 `wFlags`  
 Marcas que describen el contexto de la llamada a IDispatch:: Invoke.  
  
 `vtRet`  
 Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por `vtRet`.  
  
 `pbParamInfo`  
 Puntero a una cadena terminada en null de bytes que especifica los tipos de los parámetros que siguen a `pbParamInfo`. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Puntero a una lista de argumentos de variable.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `pbParamInfo` especifica los tipos de los parámetros pasados al método o a la propiedad. Se pueden pasar parámetros adicionales para el método o propiedad que se va a invocar utilizando la *va_list* parámetro.  
  
 Normalmente, esta función se invoca `COleControlSite::InvokeHelper`.  
  
##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton  
 Determina si el control es el botón predeterminado.  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control es el botón predeterminado en la ventana, en caso contrario, devuelve cero.  
  
##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled  
 Determina si el sitio del control está habilitado.  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control está habilitado, en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El valor se recupera de la propiedad Enabled de control estándar.  
  
##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless  
 Determina si el objeto es un control sin ventana.  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>Comentarios  
 Es distinto de cero si el control no tiene ninguna ventana, en caso contrario, es cero.  
  
##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo  
 Obtener información sobre cómo se controla la entrada de teclado por el control.  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta información se almacena en un [CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734) estructura.  
  
##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink  
 Contiene "cookie" del punto de conexión del receptor de eventos del control.  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus  
 Contiene información adicional sobre el control.  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)del SDK de Windows.  
  
##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink  
 Contiene el [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) cookie.  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle  
 Contiene los estilos de ventana del control.  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd  
 Contiene el `HWND` del control, o **NULL** si el control no tiene ventana.  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents  
 Contiene el identificador de interfaz de la interfaz de receptor de eventos del control de forma predeterminada.  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="m_nid"></a>  COleControlSite::m_nID  
 Contiene el identificador de elemento de cuadro de diálogo. del control  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject  
 Contiene el [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfaz del control.  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont  
 Contiene el contenedor del control (que representa el formulario).  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject  
 Contiene el `IOleInPlaceObject` [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interfaz del control.  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="m_pobject"></a>  COleControlSite::m_pObject  
 Contiene el **IOleObjectInterface** interfaz del control.  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject  
 Contiene el `IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interfaz del control.  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl  
 Contiene un puntero a la `CWnd` objeto que representa el propio control.  
  
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
 `dwRemove`  
 Los estilos que se va a quitar de los estilos de ventana actual.  
  
 `dwAdd`  
 Los estilos que se va a agregar desde los estilos de ventana actual.  
  
 `nFlags`  
 Marcadores de posición de las ventanas. Para obtener una lista de valores posibles, vea el [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) función en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se cambian los estilos, cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Existencias del control propiedad Enabled se modificarán para que coincida con la configuración de **WS_DISABLED**. Propiedades de estilo de borde estándar del control que se va a modificar para que coincida con la configuración solicitada para `WS_BORDER`. Todos los demás estilos se aplican directamente al identificador de ventana del control, si hay alguno.  
  
 Modifica los estilos de ventana del control. Se pueden combinar estilos para agregarse o quitarse mediante el uso de la operación OR bit a bit ( &#124; ) operador. Consulte la [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) función en el SDK de Windows para obtener información acerca de los estilos de ventana disponibles.  
  
 Si `nFlags` es distinto de cero, `ModifyStyle` llama a la función de Win32 `SetWindowPos`y vuelve a dibujar la ventana mediante la combinación `nFlags` con las marcas de cuatro siguientes:  
  
- `SWP_NOSIZE` Conserva el tamaño actual.  
  
- `SWP_NOMOVE` Conserva la posición actual.  
  
- `SWP_NOZORDER` Conserva el orden Z actual.  
  
- `SWP_NOACTIVATE` No se activa la ventana.  
  
 Para modificar una ventana de estilos extendidos, llame a [ModifyStyleEx](#modifystyleex).  
  
##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx  
 Modifica los estilos extendidos del control.  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwRemove`  
 Los estilos extendidos va a quitar de los estilos de ventana actual.  
  
 `dwAdd`  
 Los estilos extendidos agregarse de los estilos de ventana actual.  
  
 `nFlags`  
 Marcadores de posición de las ventanas. Para obtener una lista de valores posibles, vea el [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) función en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se cambian los estilos, cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Propiedades de apariencia estándar del control que se va a modificar para que coincida con la configuración de **WS_EX_CLIENTEDGE**. Todos los demás estilos de ventana extendidos se aplican directamente al identificador de ventana del control, si hay alguno.  
  
 Modifica la ventana estilos del objeto de sitio de control extendidos. Se pueden combinar estilos para agregarse o quitarse mediante el uso de la operación OR bit a bit ( &#124; ) operador. Consulte la [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) función en el SDK de Windows para obtener información acerca de los estilos de ventana disponibles.  
  
 Si `nFlags` es distinto de cero, `ModifyStyleEx` llama a la función de Win32 `SetWindowPos`y vuelve a dibujar la ventana mediante la combinación `nFlags` con las marcas de cuatro siguientes:  
  
- `SWP_NOSIZE` Conserva el tamaño actual.  
  
- `SWP_NOMOVE` Conserva la posición actual.  
  
- `SWP_NOZORDER` Conserva el orden Z actual.  
  
- `SWP_NOACTIVATE` No se activa la ventana.  
  
 Para modificar una ventana de estilos extendidos, llame a [ModifyStyle](#modifystyle).  
  
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
 *x*  
 La nueva posición del lado izquierdo de la ventana.  
  
 *y*  
 La nueva posición de la parte superior de la ventana.  
  
 `nWidth`  
 El nuevo ancho de la ventana  
  
 `nHeight`  
 El nuevo alto de la ventana.  
  
##  <a name="quickactivate"></a>  COleControlSite::QuickActivate  
 Rápida activa el control contenido.  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se activó el sitio del control, en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse únicamente si el usuario está reemplazando el proceso de creación del control.  
  
 El `IPersist*::Load` y `IPersist*::InitNew` métodos deben llamarse una vez que se produce una activación rápida. El control debe establecer las conexiones a los receptores del contenedor durante una activación rápida. Sin embargo, estas conexiones no son dinámicas hasta `IPersist*::Load` o `IPersist*::InitNew` se ha llamado.  
  
##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty  
 Establece la propiedad de control especificada por `dwDispID`.  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, se encuentra en el control `IDispatch` interfaz establecerse.  
  
 `vtProp`  
 Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Un parámetro único del tipo especificado por `vtProp`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  A diferencia de `SetProperty` y `SetPropertyV`, si se produce un error (por ejemplo, al intentar establecer una propiedad que no existe), se inicia ninguna excepción.  
  
##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton  
 Establece el control del botón predeterminado.  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDefault`  
 Es distinto de cero si el control debe convertirse en el botón predeterminado; cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El control debe tener la **OLEMISC_ACTSLIKEBUTTON** conjunto de bits de estado.  
  
##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID  
 Cambia el valor de identificador de elemento de cuadro de diálogo del control.  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El nuevo valor de identificador.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el cuadro de diálogo anterior elemento de identificador de la ventana; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setfocus"></a>  COleControlSite::SetFocus  
 Establece el foco en el control.  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpmsg*  
 Un puntero a un [estructura MSG](../../mfc/reference/msg-structure1.md). Esta estructura contiene la activación de mensaje de Windows la `SetFocus` solicitud para el control contenido en el sitio del control actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana que previamente tenía el foco.  
  
##  <a name="setproperty"></a>  COleControlSite::SetProperty  
 Establece la propiedad de control especificada por `dwDispID`.  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, se encuentra en el control `IDispatch` interfaz establecerse.  
  
 `vtProp`  
 Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Un parámetro único del tipo especificado por `vtProp`.  
  
### <a name="remarks"></a>Comentarios  
 Si `SetProperty` encuentra un error, se produce una excepción.  
  
 El tipo de excepción se determina por el valor devuelto del intento de establecer la propiedad o método. Si el valor devuelto es `DISP_E_EXCEPTION`, **COleDispatchExcpetion** se inicia; en caso contrario un `COleException`.  
  
##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV  
 Establece la propiedad de control especificada por `dwDispID`.  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, se encuentra en el control `IDispatch` interfaz establecerse.  
  
 `vtProp`  
 Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Puntero a la lista de argumentos.  
  
### <a name="remarks"></a>Comentarios  
 Parámetros adicionales para el método o propiedad que se va a invocar pueden ser passeed mediante la *arg_list* parámetro. Si `SetProperty` encuentra un error, se produce una excepción.  
  
 El tipo de excepción se determina por el valor devuelto del intento de establecer la propiedad o método. Si el valor devuelto es `DISP_E_EXCEPTION`, **COleDispatchExcpetion** se inicia; en caso contrario un `COleException`.  
  
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
 `pWndInsertAfter`  
 Un puntero a la ventana.  
  
 *x*  
 La nueva posición del lado izquierdo de la ventana.  
  
 *y*  
 La nueva posición de la parte superior de la ventana.  
  
 `cx`  
 El nuevo ancho de la ventana  
  
 `cy`  
 El nuevo alto de la ventana.  
  
 `nFlags`  
 Especifica la ventana de tamaño y la posición de marcas. Para los valores posibles, vea la sección Comentarios para [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) del SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, cero en caso contrario.  
  
##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText  
 Establece el texto para el sitio del control.  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Puntero a una cadena terminada en null que se usará como el nuevo texto de título o el control.  
  
### <a name="remarks"></a>Comentarios  
 Esta función primero intenta establecer la propiedad estándar del título. Si no se admite la propiedad estándar del título, la propiedad de texto se establece en su lugar.  
  
##  <a name="showwindow"></a>  COleControlSite::ShowWindow  
 Establece el estado de visualización de la ventana.  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCmdShow`  
 Especifica cómo se mostrará el sitio del control. Debe ser uno de los siguientes valores:  
  
- **SW_HIDE** oculta esta ventana y pasa la activación a otra ventana.  
  
- **SW_MINIMIZE** minimiza la ventana y activa la ventana de nivel superior en la lista del sistema.  
  
- **SW_RESTORE** activa y muestra la ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición originales.  
  
- **SW_SHOW** activa la ventana y lo muestra en su tamaño y posición actuales.  
  
- **SW_SHOWMAXIMIZED** activa la ventana y lo muestra como una ventana maximizada.  
  
- **SW_SHOWMINIMIZED** activa la ventana y lo muestra como un icono.  
  
- **SW_SHOWMINNOACTIVE** muestra la ventana como un icono. La ventana que está actualmente activa permanece activa.  
  
- **SW_SHOWNA** muestra la ventana en su estado actual. La ventana que está actualmente activa permanece activa.  
  
- **SW_SHOWNOACTIVATE** muestra la ventana en su tamaño y posición más recientes. La ventana que está actualmente activa permanece activa.  
  
- **SW_SHOWNORMAL** activa y muestra la ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición originales.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la ventana era visible previamente; 0 si la ventana se ocultó anteriormente.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleControlContainer (clase)](../../mfc/reference/colecontrolcontainer-class.md)
