---
title: Clase COleControlSite | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleControlSite
dev_langs:
- C++
helpviewer_keywords:
- COleControlSite class
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
caps.latest.revision: 24
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
ms.openlocfilehash: 9bae18342fe5f6aeac939c854f578cf47636fa63
ms.lasthandoff: 02/24/2017

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
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|La propiedad predeterminada del control hospedado se enlaza a un origen de datos.|  
|[COleControlSite::BindProperty](#bindproperty)|Una propiedad del control hospedado se enlaza a un origen de datos.|  
|[COleControlSite::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|  
|[COleControlSite::DestroyControl](#destroycontrol)|Destruye el control hospedado.|  
|[COleControlSite::DoVerb](#doverb)|Ejecuta un verbo específico del control hospedado.|  
|[COleControlSite::EnableDSC](#enabledsc)|Permite que los datos de origen para un sitio del control.|  
|[COleControlSite::EnableWindow](#enablewindow)|Habilita el sitio del control.|  
|[COleControlSite::FreezeEvents](#freezeevents)|Especifica si el sitio del control es aceptar eventos.|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Recupera el código de botón predeterminado para el control hospedado.|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Recupera el identificador del control.|  
|[COleControlSite::GetEventIID](#geteventiid)|Recupera el identificador de una interfaz de eventos para un control hospedado.|  
|[COleControlSite::GetExStyle](#getexstyle)|Recupera los estilos extendidos de sitio del control.|  
|[COleControlSite::GetProperty](#getproperty)|Recupera una propiedad específica del control hospedado.|  
|[COleControlSite::GetStyle](#getstyle)|Recupera los estilos de control.|  
|[COleControlSite::GetWindowText](#getwindowtext)|Recupera el texto del control hospedado.|  
|[COleControlSite::InvokeHelper](#invokehelper)|Invocar un método específico del control hospedado.|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|Invocar un método específico del control hospedado con una lista de argumentos variable.|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Determina si el control es el botón predeterminado en la ventana.|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Comprueba el estado de visibilidad del sitio del control.|  
|[COleControlSite::ModifyStyle](#modifystyle)|Modifica el actual estilos de control extendidos.|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modifica los estilos de control actuales.|  
|[COleControlSite::MoveWindow](#movewindow)|Cambia la posición del sitio del control.|  
|[COleControlSite::QuickActivate](#quickactivate)|Rápida activa el control hospedado.|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|Establece una propiedad o método del control sin posibilidad de producir una excepción.|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Establece el botón predeterminado en la ventana.|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Recupera el identificador del control.|  
|[COleControlSite::SetFocus](#setfocus)|Establece el foco en el sitio del control.|  
|[COleControlSite::SetProperty](#setproperty)|Establece una propiedad específica del control hospedado.|  
|[COleControlSite::SetPropertyV](#setpropertyv)|Establece una propiedad específica del control hospedado con una lista de argumentos variable.|  
|[COleControlSite::SetWindowPos](#setwindowpos)|Establece la posición del sitio del control.|  
|[COleControlSite::SetWindowText](#setwindowtext)|Establece el texto del control hospedado.|  
|[COleControlSite::ShowWindow](#showwindow)|Muestra u oculta el sitio del control.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Recupera información sobre el teclado y teclas de acceso para el control hospedado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Determina si el control hospedado es un control sin ventanas.|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Contiene información sobre el control para el control del teclado.|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|La cookie del control punto de conexión.|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Los varios Estados para el control hospedado.|  
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
|[COleControlSite::m_rect](#m_rect)|Las dimensiones de sitio del control.|  
  
## <a name="remarks"></a>Comentarios  
 Esta compatibilidad es el medio principal por el que un control ActiveX incrustado obtiene información sobre la ubicación y el alcance de su página de muestra, su moniker, su interfaz de usuario, sus propiedades de ambientales y otros recursos proporcionados por su contenedor. `COleControlSite`implementa totalmente el [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502), [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706), [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), **IBoundObjectSite**, **INotifyDBEvents**, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) interfaces. Además, también se implementa la interfaz IDispatch (proporcionar soporte para las propiedades de ambiente y receptores de eventos).  
  
 Para crear un sitio del control ActiveX con `COleControlSite`, derive una clase de `COleControlSite`. En su `CWnd`-clase derivada para el contenedor (por ejemplo, en el cuadro de diálogo) reemplazar la **CWnd::CreateControlSite** (función).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxocc.h  
  
##  <a name="a-namebinddefaultpropertya--colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a>COleControlSite::BindDefaultProperty  
 Enlaza simple enlazado la propiedad default del objeto de llamada, se marca en la biblioteca de tipos para el cursor subyacente que se define mediante las propiedades del origen de datos, nombre de usuario, contraseña y SQL del control de origen de datos.  
  
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
 Especifica el nombre de la columna del cursor proporcionada por el control de origen de datos al que se enlazará la propiedad.  
  
 `pDSCWnd`  
 Un puntero a la `CWnd`-objeto derivado que hospeda el control de origen de datos al que se enlazará la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 La `CWnd` objeto en el que se llama a esta función debe ser un control enlazado a datos.  
  
##  <a name="a-namebindpropertya--colecontrolsitebindproperty"></a><a name="bindproperty"></a>COleControlSite::BindProperty  
 Enlaza la propiedad enlazada simple del objeto que realiza la llamada, como se marca en la biblioteca de tipos hasta el cursor subyacente que se define mediante las propiedades del origen de datos, nombre de usuario, contraseña y SQL del control de origen de datos.  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDispId*  
 Especifica la **DISPID** de una propiedad en un control enlazado a datos que se enlaza a un control de origen de datos.  
  
 `pWndDSC`  
 Un puntero a la `CWnd`-objeto derivado que hospeda el control de origen de datos al que se enlazará la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 La `CWnd` objeto en el que se llama a esta función debe ser un control enlazado a datos.  
  
##  <a name="a-namecolecontrolsitea--colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a>COleControlSite::COleControlSite  
 Construye un nuevo objeto `COleControlSite`.  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCtrlCont`  
 Puntero al contenedor del control (que representa la ventana que hospeda el control de parte).  
  
### <a name="remarks"></a>Comentarios  
 Esta función es invocada por el [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) (función). Para obtener más información acerca de cómo personalizar la creación de contenedores, consulte [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).  
  
##  <a name="a-namecreatecontrola--colecontrolsitecreatecontrol"></a><a name="createcontrol"></a>COleControlSite::CreateControl  
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
 Puntero al texto que se mostrará en el control. Establece el valor de propiedad de título o el texto de winodw (si existe).  
  
 `dwStyle`  
 Estilos de Windows. Los estilos disponibles se enumeran en la **comentarios** sección.  
  
 `rect`  
 Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto o un `RECT` estructura.  
  
 `nID`  
 Especifica el identificador de ventana secundaria del control  
  
 `pPersist`  
 Un puntero a un `CFile` que contiene el estado persistente del control. El valor predeterminado es **NULL**, que indica que el control se inicializa sin restaurar su estado desde el almacenamiento persistente. Si no **NULL**, debe ser un puntero a un `CFile`-objeto que contiene los datos persistentes del control, en forma de una secuencia o un almacenamiento derivado. Estos datos podrían guardados en una activación anterior del cliente. El `CFile` puede contener otros datos, pero debe tener su puntero de lectura y escritura establecido en el primer byte de datos persistentes en el momento de la llamada a `CreateControl`.  
  
 `bStorage`  
 Indica si los datos de `pPersist` debe interpretarse como `IStorage` o `IStream` datos. Si los datos de `pPersist` es un almacenamiento `bStorage` debe ser **TRUE**. Si los datos de `pPersist` es una secuencia, `bStorage` debe ser **FALSE**. El valor predeterminado es **FALSE**.  
  
 `bstrLicKey`  
 Datos de clave de licencia opcional. Estos datos sólo es necesaria para crear controles que requieren una clave de licencia de tiempo de ejecución. Si el control admite licencias, debe proporcionar una clave de licencia para la creación del control que se realice correctamente. El valor predeterminado es **NULL**.  
  
 `ppt`  
 Un puntero a un **punto** estructura que contiene la esquina superior izquierda del control. El tamaño del control se determina por el valor de *psize*. El `ppt` y *psize* valores son un método opcional para especificar el tamaño y posición opf el control.  
  
 *psize*  
 Un puntero a un **tamaño** estructura que contiene el tamaño del control. La esquina superior izquierda se determina por el valor de `ppt`. El `ppt` y *psize* valores son un método opcional para especificar el tamaño y posición opf el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Sólo un subconjunto de las ventanas `dwStyle` marcas son compatibles con `CreateControl`:  
  
- **WS_VISIBLE** crea una ventana que esté visible inicialmente. Necesario si desea que el control sea visible inmediatamente, como las ventanas normales.  
  
- **WS_DISABLED** crea una ventana que está inicialmente deshabilitada. Una ventana deshabilitada no puede recibir entradas del usuario. Se puede establecer si el control tiene la propiedad Enabled.  
  
- `WS_BORDER`Crea una ventana con un borde de línea fina. Se puede establecer si el control tiene una propiedad de estilo de borde.  
  
- **WS_GROUP** especifica el primer control de un grupo de controles. El usuario puede cambiar el foco del teclado de un control en el grupo a otro mediante las teclas de dirección. Todos los controles definidos con el **WS_GROUP** después de que el primer control pertenecen al mismo grupo de estilos. El siguiente control con el **WS_GROUP** estilo finaliza el grupo y comienza el siguiente grupo.  
  
- **WS_TABSTOP** especifica un control que puede recibir el foco de teclado cuando el usuario presiona la tecla TAB. Al presionar la tecla TAB cambia el foco del teclado al siguiente control de la **WS_TABSTOP** estilo.  
  
 Usar la segunda sobrecarga para crear controles de tamaño predeterminado.  
  
##  <a name="a-namedestroycontrola--colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a>COleControlSite::DestroyControl  
 Destruye el objeto `COleControlSite`.  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una vez completado, se libera el objeto de la memoria y los punteros al objeto ya no son válidos.  
  
##  <a name="a-namedoverba--colecontrolsitedoverb"></a><a name="doverb"></a>COleControlSite::DoVerb  
 Ejecuta el verbo especificado.  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nVerb`  
 Especifica el verbo que se va a ejecutar. Puede incluir uno de los siguientes:  
  
|Valor|Significado|Símbolo|  
|-----------|-------------|------------|  
|0|verbo principal|`OLEIVERB_PRIMARY`|  
|-1|Verbo secundario|(Ninguno)|  
|1|Muestra el objeto para su edición.|`OLEIVERB_SHOW`|  
|-2|Edita el elemento en una ventana independiente.|`OLEIVERB_OPEN`|  
|-3|Oculta el objeto.|`OLEIVERB_HIDE`|  
|-4|Activa un control in situ.|`OLEIVERB_UIACTIVATE`|  
|-5|Activa un control in situ, sin elementos de la interfaz de usuario adicionales.|**OLEIVERB_INPLACEACTIVATE**|  
|-7|Mostrar las propiedades del control.|**OLEIVERB_PROPERTIES**|  
  
 `lpMsg`  
 Puntero al mensaje que produjo el elemento que se debe activar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se llama directamente a través del control `IOleObject` interfaz para ejecutar el verbo especificado. Si se produce una excepción como resultado de esta llamada de función, un `HRESULT` código de error.  
  
 Para obtener más información, consulte [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameenabledsca--colecontrolsiteenabledsc"></a><a name="enabledsc"></a>COleControlSite::EnableDSC  
 Permite que los datos de origen para el sitio del control.  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamado por el marco para habilitar e iniciar para el sitio del control de orígenes de datos. Reemplazar esta función para proporcionar un comportamiento personalizado.  
  
##  <a name="a-nameenablewindowa--colecontrolsiteenablewindow"></a><a name="enablewindow"></a>COleControlSite::EnableWindow  
 Habilita o deshabilita el mouse y teclado al sitio del control.  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 Especifica si se debe habilitar o deshabilitar la ventana: **TRUE** si la entrada de ventana está habilitada, de lo contrario, **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la ventana se deshabilitó anteriormente, de lo contrario, 0.  
  
##  <a name="a-namefreezeeventsa--colecontrolsitefreezeevents"></a><a name="freezeevents"></a>COleControlSite::FreezeEvents  
 Especifica si el sitio del control se controlar u omitir los eventos desencadenados desde un control.  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parámetros  
 `bFreeze`  
 Especifica si el sitio del control desea dejar de aceptar eventos. Distinto de cero si el control no acepta eventos; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si `bFreeze` es **TRUE**, el sitio del control solicita el control que se va a detener fring eventos. Si `bFreeze` es **FALSE**, el sitio del control solicita el control continúe desencadenar eventos.  
  
> [!NOTE]
>  El control no es necesario detener el desencadenamiento de eventos si solicitado por el sitio del control. Puede continuar la activación pero se omitirá todos los eventos posteriores en el sitio del control.  
  
##  <a name="a-namegetcontrolinfoa--colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a>COleControlSite::GetControlInfo  
 Recupera información sobre el comportamiento del teclado y teclas de acceso del teclado de un control.  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>Comentarios  
 La información se almacena en [COleControlSite::m_ctlInfo](#m_ctlinfo).  
  
##  <a name="a-namegetdefbtncodea--colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a>COleControlSite::GetDefBtnCode  
 Determina si el control es un botón de comando predeterminado.  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puede presentar uno de los siguientes valores:  
  
- **DLGC_DEFPUSHBUTTON** Control es el botón predeterminado en el cuadro de diálogo.  
  
- **DLGC_UNDEFPUSHBUTTON** Control no es el botón predeterminado en el cuadro de diálogo.  
  
- **0** control no es un botón.  
  
##  <a name="a-namegetdlgctrlida--colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a>COleControlSite::GetDlgCtrlID  
 Recupera el identificador del control.  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento de cuadro de diálogo del control.  
  
##  <a name="a-namegeteventiida--colecontrolsitegeteventiid"></a><a name="geteventiid"></a>COleControlSite::GetEventIID  
 Recupera un puntero a la interfaz de eventos del control de forma predeterminada.  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>Parámetros  
 `piid`  
 Un puntero a un identificador de interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0. Si se realiza correctamente, `piid` contiene el identificador de interfaz para la interfaz de eventos del control de forma predeterminada.  
  
##  <a name="a-namegetexstylea--colecontrolsitegetexstyle"></a><a name="getexstyle"></a>COleControlSite::GetExStyle  
 Recupera los estilos extendidos de la ventana.  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ventana de control de estilos extendidos.  
  
### <a name="remarks"></a>Comentarios  
 Para recuperar los estilos normales, llame a [COleControlSite::GetStyle](#getstyle).  
  
##  <a name="a-namegetpropertya--colecontrolsitegetproperty"></a><a name="getproperty"></a>COleControlSite::GetProperty  
 Obtiene la propiedad de control especificada por `dwDispID`.  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad, que se encuentra en predeterminado el control `IDispatch` interfaz va a recuperar.  
  
 `vtProp`  
 Especifica el tipo de la propiedad que se va a recuperar. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvProp`  
 Dirección de la variable que recibirá el valor de propiedad. Debe coincidir con el tipo especificado por `vtProp`.  
  
### <a name="remarks"></a>Comentarios  
 El valor se devuelve a través de `pvProp`.  
  
##  <a name="a-namegetstylea--colecontrolsitegetstyle"></a><a name="getstyle"></a>COleControlSite::GetStyle  
 Recupera los estilos de control.  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Estilos de ventana.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una lista de valores posibles, consulte [Windows estilos](../../mfc/reference/window-styles.md). Para recuperar los estilos extendidos de sitio del control, llame a [COleControlSite::GetExStyle](#getexstyle).  
  
##  <a name="a-namegetwindowtexta--colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a>COleControlSite::GetWindowText  
 Recupera el texto actual del control.  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 Una referencia a un `CString` objeto que contiene el texto actual del control.  
  
### <a name="remarks"></a>Comentarios  
 Si el control admite la propiedad de título estándar, se devuelve este valor. Si no se admite la propiedad de título estándar, se devuelve el valor de la propiedad Text.  
  
##  <a name="a-nameinvokehelpera--colecontrolsiteinvokehelper"></a><a name="invokehelper"></a>COleControlSite::InvokeHelper  
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
 Identifica el identificador de envío de la propiedad o método, que se encuentra en el control `IDispatch` interfaz, que se debe invocar.  
  
 `wFlags`  
 Marcas que describen el contexto de la llamada a IDispatch:: Invoke. Posibles `wFlags` valores, consulte `IDispatch::Invoke` en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `vtRet`  
 Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por `vtRet`.  
  
 `pbParamInfo`  
 Puntero a una cadena terminada en null de bytes que especifica los tipos de los parámetros que siguen a `pbParamInfo`. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Lista de variables de parámetros, de tipos especificados en `pbParamInfo`.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `pbParamInfo` especifica los tipos de los parámetros pasados al método o a la propiedad. La lista de argumentos variables se representa mediante... en la declaración de sintaxis.  
  
 Esta función convierte los parámetros de **VARIANTARG** valores, a continuación, se invoca el **IDispatch:: Invoke** método en el control. Si la llamada a **IDispatch:: Invoke** produce un error, esta función producirá una excepción. Si el código de estado devuelto por **IDispatch:: Invoke** es `DISP_E_EXCEPTION`, esta función lanza una **COleDispatchException** objeto, en caso contrario lanza una `COleException`.  
  
##  <a name="a-nameinvokehelperva--colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a>COleControlSite::InvokeHelperV  
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
 Identifica el identificador de envío de la propiedad o método, que se encuentra en el control `IDispatch` interfaz, que se debe invocar.  
  
 `wFlags`  
 Marcas que describen el contexto de la llamada a IDispatch:: Invoke.  
  
 `vtRet`  
 Especifica el tipo del valor devuelto. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `pvRet`  
 Dirección de la variable que recibirá el valor de la propiedad o el valor devuelto. Debe coincidir con el tipo especificado por `vtRet`.  
  
 `pbParamInfo`  
 Puntero a una cadena terminada en null de bytes que especifica los tipos de los parámetros que siguen a `pbParamInfo`. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Puntero a una lista de argumentos de variable.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `pbParamInfo` especifica los tipos de los parámetros pasados al método o a la propiedad. Se pueden pasar parámetros adicionales para el método o propiedad que se invoca utilizando la *va_list* parámetro.  
  
 Normalmente, esta función se invoca `COleControlSite::InvokeHelper`.  
  
##  <a name="a-nameisdefaultbuttona--colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a>COleControlSite::IsDefaultButton  
 Determina si el control es el botón predeterminado.  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control es el botón predeterminado en la ventana, en caso contrario devuelve cero.  
  
##  <a name="a-nameiswindowenableda--colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a>COleControlSite::IsWindowEnabled  
 Determina si el sitio del control está habilitado.  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control está habilitado, de lo contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El valor se recupera de la propiedad Enabled de control estándar.  
  
##  <a name="a-namembiswindowlessa--colecontrolsitembiswindowless"></a><a name="m_biswindowless"></a>COleControlSite::m_bIsWindowless  
 Determina si el objeto es un control sin ventanas.  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>Comentarios  
 Es distinto de cero si el control no tiene ninguna ventana, de lo contrario, es cero.  
  
##  <a name="a-namemctlinfoa--colecontrolsitemctlinfo"></a><a name="m_ctlinfo"></a>COleControlSite::m_ctlInfo  
 Obtener información sobre cómo trata el control de entrada de teclado.  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta información se almacena en un [CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734) estructura.  
  
##  <a name="a-namemdweventsinka--colecontrolsitemdweventsink"></a><a name="m_dweventsink"></a>COleControlSite::m_dwEventSink  
 Contiene la cookie del punto de conexión del receptor de eventos del control.  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="a-namemdwmiscstatusa--colecontrolsitemdwmiscstatus"></a><a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus  
 Contiene información adicional sobre el control.  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namemdwpropnotifysinka--colecontrolsitemdwpropnotifysink"></a><a name="m_dwpropnotifysink"></a>COleControlSite::m_dwPropNotifySink  
 Contiene el [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) cookie.  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="a-namemdwstylea--colecontrolsitemdwstyle"></a><a name="m_dwstyle"></a>COleControlSite::m_dwStyle  
 Contiene los estilos de ventana del control.  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="a-namemhwnda--colecontrolsitemhwnd"></a><a name="m_hwnd"></a>COleControlSite::m_hWnd  
 Contiene el `HWND` del control, o **NULL** si el control no tiene ventana.  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="a-namemiideventsa--colecontrolsitemiidevents"></a><a name="m_iidevents"></a>COleControlSite::m_iidEvents  
 Contiene el identificador de interfaz de la interfaz de receptor de eventos del control de forma predeterminada.  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="a-namemnida--colecontrolsitemnid"></a><a name="m_nid"></a>COleControlSite::m_nID  
 Contiene el identificador de elemento de cuadro de diálogo. del control  
  
```  
UINT m_nID;  
```  
  
##  <a name="a-namempactiveobjecta--colecontrolsitempactiveobject"></a><a name="m_pactiveobject"></a>COleControlSite::m_pActiveObject  
 Contiene el [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfaz del control.  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="a-namempctrlconta--colecontrolsitempctrlcont"></a><a name="m_pctrlcont"></a>COleControlSite::m_pCtrlCont  
 Contiene el contenedor del control (que representa el formulario).  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="a-namempinplaceobjecta--colecontrolsitempinplaceobject"></a><a name="m_pinplaceobject"></a>COleControlSite::m_pInPlaceObject  
 Contiene el `IOleInPlaceObject` [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interfaz del control.  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="a-namempobjecta--colecontrolsitempobject"></a><a name="m_pobject"></a>COleControlSite::m_pObject  
 Contiene el **IOleObjectInterface** interfaz del control.  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="a-namempwindowlessobjecta--colecontrolsitempwindowlessobject"></a><a name="m_pwindowlessobject"></a>COleControlSite::m_pWindowlessObject  
 Contiene el `IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interfaz del control.  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="a-namempwndctrla--colecontrolsitempwndctrl"></a><a name="m_pwndctrl"></a>COleControlSite::m_pWndCtrl  
 Contiene un puntero a la `CWnd` objeto que representa el control en Sí.  
  
```  
CWnd* m_pWndCtrl;  
```  
  
##  <a name="a-namemrecta--colecontrolsitemrect"></a><a name="m_rect"></a>COleControlSite::m_rect  
 Contiene los límites del control, en relación con la ventana del contenedor.  
  
```  
CRect m_rect;  
```  
  
##  <a name="a-namemodifystylea--colecontrolsitemodifystyle"></a><a name="modifystyle"></a>COleControlSite::ModifyStyle  
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
 Los estilos que agregarse de los estilos de ventana actual.  
  
 `nFlags`  
 Marcadores de posición de las ventanas. Para obtener una lista de valores posibles, vea el [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se modifican los estilos, cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Material del control propiedad Enabled se modificará para que coincida con la configuración de **WS_DISABLED**. Propiedad de estilo de borde estándar del control que se va a modificar para que coincida con el valor solicitado para `WS_BORDER`. Todos los demás estilos se aplican directamente al identificador de ventana del control, si hay alguno.  
  
 Modifica los estilos de ventana del control. Se pueden combinar estilos para agregarse o quitarse mediante el uso de la operación OR bit a bit (|) (operador). Consulte la [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener información acerca de los estilos de ventana disponibles.  
  
 Si `nFlags` es distinto de cero, `ModifyStyle` llama a la función de Win32 `SetWindowPos`y vuelve a dibujar la ventana combinando `nFlags` con los cuatro indicadores siguientes:  
  
- `SWP_NOSIZE`Conserva el tamaño actual.  
  
- `SWP_NOMOVE`Conserva la posición actual.  
  
- `SWP_NOZORDER`Conserva el orden Z actual.  
  
- `SWP_NOACTIVATE`No se activa la ventana.  
  
 Para modificar una ventana de estilos extendidos, llame a [ModifyStyleEx](#modifystyleex).  
  
##  <a name="a-namemodifystyleexa--colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a>COleControlSite::ModifyStyleEx  
 Modifica los estilos extendidos del control.  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwRemove`  
 Los estilos extendidos que se quita de los estilos de ventana actual.  
  
 `dwAdd`  
 Los estilos extendidos agregarse de los estilos de ventana actual.  
  
 `nFlags`  
 Marcadores de posición de las ventanas. Para obtener una lista de valores posibles, vea el [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se modifican los estilos, cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Propiedades de apariencia estándar del control que se va a modificar para que coincida con la configuración de **WS_EX_CLIENTEDGE**. Todos los demás estilos de ventana extendidos se aplican directamente al identificador de ventana del control, si hay alguno.  
  
 Modifica la ventana estilos del objeto de sitio control extendidos. Se pueden combinar estilos para agregarse o quitarse mediante el uso de la operación OR bit a bit (|) (operador). Consulte la [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener información acerca de los estilos de ventana disponibles.  
  
 Si `nFlags` es distinto de cero, `ModifyStyleEx` llama a la función de Win32 `SetWindowPos`y vuelve a dibujar la ventana combinando `nFlags` con los cuatro indicadores siguientes:  
  
- `SWP_NOSIZE`Conserva el tamaño actual.  
  
- `SWP_NOMOVE`Conserva la posición actual.  
  
- `SWP_NOZORDER`Conserva el orden Z actual.  
  
- `SWP_NOACTIVATE`No se activa la ventana.  
  
 Para modificar una ventana de estilos extendidos, llame a [ModifyStyle](#modifystyle).  
  
##  <a name="a-namemovewindowa--colecontrolsitemovewindow"></a><a name="movewindow"></a>COleControlSite::MoveWindow  
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
  
##  <a name="a-namequickactivatea--colecontrolsitequickactivate"></a><a name="quickactivate"></a>COleControlSite::QuickActivate  
 Rápida activa el control contenido.  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se activó el sitio del control, de lo contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse sólo si el usuario está invalidando el proceso de creación del control.  
  
 El `IPersist*::Load` y `IPersist*::InitNew` métodos deberían llamarse cuando se produce una activación rápida. El control debe establecer las conexiones a los receptores del contenedor durante la activación rápida. Sin embargo, estas conexiones no están activos hasta `IPersist*::Load` o `IPersist*::InitNew` se ha llamado.  
  
##  <a name="a-namesafesetpropertya--colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a>COleControlSite::SafeSetProperty  
 Establece la propiedad de control especificada por `dwDispID`.  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, que se encuentra en el control `IDispatch` interfaz establecerse.  
  
 `vtProp`  
 Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Un parámetro único del tipo especificado por `vtProp`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  A diferencia de `SetProperty` y `SetPropertyV`, si se produce un error (por ejemplo, al intentar establecer una propiedad que no existe), se inicia ninguna excepción.  
  
##  <a name="a-namesetdefaultbuttona--colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a>COleControlSite::SetDefaultButton  
 Establece el control del botón predeterminado.  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDefault`  
 Distinto de cero si el control debe convertirse en el botón predeterminado; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  El control debe tener la **OLEMISC_ACTSLIKEBUTTON** conjunto de bits de estado.  
  
##  <a name="a-namesetdlgctrlida--colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a>COleControlSite::SetDlgCtrlID  
 Cambia el valor de identificador de elemento de cuadro de diálogo del control.  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El nuevo valor de identificador.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el cuadro de diálogo anterior elemento de identificador de la ventana; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetfocusa--colecontrolsitesetfocus"></a><a name="setfocus"></a>COleControlSite::SetFocus  
 Establece el foco en el control.  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpmsg*  
 Un puntero a un [estructura MSG](../../mfc/reference/msg-structure1.md). Esta estructura contiene la activación de mensaje de Windows la `SetFocus` solicitud para el control contenido en el sitio del control actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana que previamente tenía el foco.  
  
##  <a name="a-namesetpropertya--colecontrolsitesetproperty"></a><a name="setproperty"></a>COleControlSite::SetProperty  
 Establece la propiedad de control especificada por `dwDispID`.  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, que se encuentra en el control `IDispatch` interfaz establecerse.  
  
 `vtProp`  
 Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Un parámetro único del tipo especificado por `vtProp`.  
  
### <a name="remarks"></a>Comentarios  
 Si `SetProperty` encuentra un error, se produce una excepción.  
  
 El tipo de excepción se determina por el valor devuelto del intento de establecer la propiedad o método. Si el valor devuelto es `DISP_E_EXCEPTION`, **COleDispatchExcpetion** se inicia; en caso contrario, un `COleException`.  
  
##  <a name="a-namesetpropertyva--colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a>COleControlSite::SetPropertyV  
 Establece la propiedad de control especificada por `dwDispID`.  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDispID`  
 Identifica el identificador de envío de la propiedad o método, que se encuentra en el control `IDispatch` interfaz establecerse.  
  
 `vtProp`  
 Especifica el tipo de propiedad que se va a establecer. Para los valores posibles, vea la sección Comentarios para [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 `argList`  
 Puntero a la lista de argumentos.  
  
### <a name="remarks"></a>Comentarios  
 Parámetros adicionales para el método o propiedad que se invoca pueden ser passeed mediante la *arg_list* parámetro. Si `SetProperty` encuentra un error, se produce una excepción.  
  
 El tipo de excepción se determina por el valor devuelto del intento de establecer la propiedad o método. Si el valor devuelto es `DISP_E_EXCEPTION`, **COleDispatchExcpetion** se inicia; en caso contrario, un `COleException`.  
  
##  <a name="a-namesetwindowposa--colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a>COleControlSite::SetWindowPos  
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
 Puntero a la ventana.  
  
 *x*  
 La nueva posición del lado izquierdo de la ventana.  
  
 *y*  
 La nueva posición de la parte superior de la ventana.  
  
 `cx`  
 El nuevo ancho de la ventana  
  
 `cy`  
 El nuevo alto de la ventana.  
  
 `nFlags`  
 Especifica la ventana de tamaño y colocación de marcas. Para los valores posibles, vea la sección Comentarios para [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, cero en caso contrario.  
  
##  <a name="a-namesetwindowtexta--colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a>COleControlSite::SetWindowText  
 Establece el texto para el sitio del control.  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszString`  
 Puntero a una cadena terminada en null que se usará como el nuevo texto de título o el control.  
  
### <a name="remarks"></a>Comentarios  
 Esta función primero intenta establecer la propiedad de título estándar. Si no se admite la propiedad de título estándar, la propiedad Text se establece en su lugar.  
  
##  <a name="a-nameshowwindowa--colecontrolsiteshowwindow"></a><a name="showwindow"></a>COleControlSite::ShowWindow  
 Establece el estado de la ventana Mostrar.  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCmdShow`  
 Especifica cómo se mostrará el sitio del control. Debe ser uno de los siguientes valores:  
  
- **SW_HIDE** oculta esta ventana y pasa la activación a otra ventana.  
  
- **SW_MINIMIZE** minimiza la ventana y activa la ventana de nivel superior en la lista del sistema.  
  
- **SW_RESTORE** activa y muestra la ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición originales.  
  
- **SW_SHOW** se activa la ventana y se muestra en su tamaño y posición actuales.  
  
- **SW_SHOWMAXIMIZED** se activa la ventana y lo muestra como una ventana maximizada.  
  
- **SW_SHOWMINIMIZED** se activa la ventana y lo muestra como un icono.  
  
- **SW_SHOWMINNOACTIVE** muestra la ventana como un icono. La ventana activa permanece activa.  
  
- **SW_SHOWNA** muestra la ventana en su estado actual. La ventana activa permanece activa.  
  
- **SW_SHOWNOACTIVATE** muestra la ventana en su tamaño y posición más recientes. La ventana activa permanece activa.  
  
- **SW_SHOWNORMAL** activa y muestra la ventana. Si la ventana está minimizada o maximizada, Windows lo restaura a su tamaño y posición originales.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la ventana era visible previamente; 0 si la ventana se ha ocultado previamente.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

