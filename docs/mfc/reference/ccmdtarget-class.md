---
title: CCmdTarget (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCmdTarget
dev_langs:
- C++
helpviewer_keywords:
- message maps, CCmdTarget base class
- command targets
- CCmdTarget class
- command routing, command targets
- targets, command
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0b5b7617f6b3d89e454e31c9f95b5d4455569114
ms.lasthandoff: 02/24/2017

---
# <a name="ccmdtarget-class"></a>CCmdTarget (clase)
La clase base para la arquitectura de mapa de mensajes de la biblioteca Microsoft Foundation Class.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCmdTarget : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Construye un objeto `CCmdTarget`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Muestra el cursor como un cursor de reloj de arena.|  
|[CCmdTarget::DoOleVerb](#dooleverb)|Hace que una acción especificada por un verbo OLE que se va a realizar.|  
|[CCmdTarget::EnableAutomation](#enableautomation)|Permite la automatización OLE para la `CCmdTarget` objeto.|  
|[CCmdTarget::EnableConnections](#enableconnections)|Habilita la activación de eventos a través de puntos de conexión.|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Habilita la biblioteca de tipos de un objeto.|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Devuelve el cursor anterior.|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Enumera los verbos de un objeto OLE.|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|Devuelve un puntero a la `CCmdTarget` objeto asociado con el `IDispatch` puntero.|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Obtiene el identificador de interfaz de envío principal.|  
|[CCmdTarget::GetIDispatch](#getidispatch)|Devuelve un puntero a la `IDispatch` objeto asociado a la `CCmdTarget` objeto.|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo que proporciona un objeto.|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Recupera la descripción del tipo que se corresponde con el GUID especificado.|  
|[CCmdTarget::GetTypeLib](#gettypelib)|Obtiene un puntero a una biblioteca de tipos.|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Obtiene la caché de la biblioteca de tipos.|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Permite la invocación del método de automatización.|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|Devuelve cero si una función de automatización debe devolver un valor.|  
|[CCmdTarget:: OnCmdMsg](#oncmdmsg)|Enruta y envía mensajes de comando.|  
|[CCmdTarget:: OnFinalRelease](#onfinalrelease)|Limpia después de libera la última referencia OLE.|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Restaura el cursor de reloj de arena.|  
  
## <a name="remarks"></a>Comentarios  
 Un mapa de mensajes enruta mensajes o comandos a las funciones miembro que escriba para controlarlos. (Un comando es un mensaje de un elemento de menú, un botón de comando o una tecla de aceleración).  
  
 Las clases del marco de claves derivadas de `CCmdTarget` incluyen [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), y [CFrameWnd](../../mfc/reference/cframewnd-class.md). Si desea que una nueva clase controlar los mensajes, derive la clase de uno de estos `CCmdTarget`-las clases derivadas. Rara vez se derive una clase de `CCmdTarget` directamente.  
  
 Para obtener información general de los destinos de comando y `OnCmdMsg` el enrutamiento, consulte [destinos de comando](../../mfc/command-targets.md), [enrutamiento de comandos](../../mfc/command-routing.md), y [asignar mensajes](../../mfc/mapping-messages.md).  
  
 `CCmdTarget`incluye funciones miembro que administrar la presentación de un cursor de reloj de arena. Mostrar el cursor de reloj de arena cuando se espera un comando para un intervalo de tiempo apreciable para ejecutar.  
  
 Mapas de envíos, similares a los mapas de mensajes, se utilizan para exponer la automatización OLE `IDispatch` funcionalidad. Al exponer esta interfaz, otras aplicaciones (como Visual Basic) pueden llamar a la aplicación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namebeginwaitcursora--ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor  
 Llame a esta función para mostrar el cursor como un reloj de arena cuando se espera un comando para un intervalo de tiempo apreciable para ejecutar.  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función para mostrar al usuario que está ocupado, por ejemplo, cuando un **CDocument** objeto carga o guarda a sí mismo en un archivo.  
  
 Las acciones de `BeginWaitCursor` no siempre son efectivos fuera de un controlador de mensaje único como otras acciones, como `OnSetCursor` de control, puede cambiar el cursor.  
  
 Llame a `EndWaitCursor` para restaurar el cursor anterior.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#43;](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="a-nameccmdtargeta--ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CCmdTarget::CCmdTarget  
 Construye un objeto `CCmdTarget`.  
  
```  
CCmdTarget();
```  
  
##  <a name="a-namedooleverba--ccmdtargetdooleverb"></a><a name="dooleverb"></a>CCmdTarget::DoOleVerb  
 Hace que una acción especificada por un verbo OLE que se va a realizar.  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `iVerb`  
 Identificador numérico del verbo.  
  
 `lpMsg`  
 Puntero a la [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) estructura que describe el evento (como un doble clic) que invocó el verbo.  
  
 `hWndParent`  
 Identificador de la ventana de documento que contiene el objeto.  
  
 `lpRect`  
 Puntero a la [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene las coordenadas, en píxeles, que definen un objeto de selección del rectángulo en *hwndParent*.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto, de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Básicamente, esta función miembro es una implementación de [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508). Enumeran las posibles acciones [CCmdTarget::EnumOleVerbs](#enumoleverbs).  
  
##  <a name="a-nameenableautomationa--ccmdtargetenableautomation"></a><a name="enableautomation"></a>CCmdTarget::EnableAutomation  
 Llame a esta función para habilitar la automatización OLE de un objeto.  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama desde el constructor del objeto y sólo se debe llamar si se ha declarado un mapa de envíos para la clase. Para obtener más información sobre la automatización, consulte los artículos [clientes de automatización](../../mfc/automation-clients.md) y [servidores de automatización](../../mfc/automation-servers.md).  
  
##  <a name="a-nameenableconnectionsa--ccmdtargetenableconnections"></a><a name="enableconnections"></a>CCmdTarget::EnableConnections  
 Habilita la activación de eventos a través de puntos de conexión.  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>Comentarios  
 Para habilitar los puntos de conexión, llame a esta función miembro en el constructor de la clase derivada.  
  
##  <a name="a-nameenabletypeliba--ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CCmdTarget::EnableTypeLib  
 Habilita la biblioteca de tipos de un objeto.  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro en el constructor de su `CCmdTarget`-objeto derivado si se proporciona información de tipo. Para obtener más información, consulte el artículo de Knowledge Base Q185720, "Cómo: proporcionar información de tipo de un servidor de automatización de MFC." Artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="a-nameendwaitcursora--ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor  
 Llame a esta función después de haber llamado el `BeginWaitCursor` función de miembro para devolver el cursor de reloj de arena hasta el cursor anterior.  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco también llama a esta función miembro después de haber llamado el cursor de reloj de arena.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#43;](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="a-nameenumoleverbsa--ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs  
 Enumera los verbos de un objeto OLE.  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppenumOleVerb`  
 Un puntero a un puntero a un [IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084) interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el objeto admite al menos un verbo OLE (en cuyo caso \* `ppenumOleVerb` apunta a un **IEnumOLEVERB** interfaz de enumerador), de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Básicamente, esta función miembro es una implementación de [IOleObject:: EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781).  
  
##  <a name="a-namefromidispatcha--ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>CCmdTarget::FromIDispatch  
 Llame a esta función para asignar un `IDispatch` puntero, recibido de las funciones de miembro de automatización de una clase, en la `CCmdTarget` objeto que implementa las interfaces de la `IDispatch` objeto.  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDispatch`  
 Puntero a un objeto `IDispatch`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CCmdTarget` objeto asociado con `lpDispatch`. Esta función devuelve **NULL** si la `IDispatch` objeto no se reconoce como un Microsoft Foundation Class `IDispatch` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El resultado de esta función es el inverso de una llamada a la función miembro `GetIDispatch`.  
  
##  <a name="a-namegetdispatchiida--ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID  
 Obtiene el identificador de interfaz de envío principal.  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>Parámetros  
 *pIID*  
 Un puntero a un identificador de interfaz (una [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)).  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto, de lo contrario, FALSE. Si se realiza correctamente, \* *pIID* se establece en el identificador de interfaz de envío principal.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetDispatchIID` devuelve FALSE). Consulte [COleControl](../../mfc/reference/colecontrol-class.md).  
  
 Para obtener más información, consulte el artículo de Knowledge Base Q185720, "Cómo: proporcionar información de tipo de un servidor de automatización de MFC." Artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http://support.microsoft.com](http://support.microsoft.com/).  
  
##  <a name="a-namegetidispatcha--ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CCmdTarget::GetIDispatch  
 Llame a esta función miembro para recuperar el `IDispatch` puntero desde un método de automatización que o bien devuelve un `IDispatch` puntero o toma un `IDispatch` puntero por referencia.  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAddRef*  
 Especifica si se incrementa el recuento de referencias para el objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 El `IDispatch` asociado con el objeto de puntero.  
  
### <a name="remarks"></a>Comentarios  
 Para los objetos que la llamada `EnableAutomation` en sus constructores, haciéndolos automatización habilitada, esta función devuelve un puntero a la implementación de clase base `IDispatch` utilizado por clientes que se comunican a través de la `IDispatch` interfaz. Llamar a esta función automáticamente agrega una referencia al puntero, por lo que no es necesario realizar una llamada a [IUnknown:: AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379).  
  
##  <a name="a-namegettypeinfocounta--ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount  
 Recupera el número de interfaces de información de tipo que proporciona un objeto.  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de interfaces de información de tipo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se implementa básicamente [IDispatch:: GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12).  
  
 Las clases derivadas deben reemplazar esta función para devolver el número de interfaces de información de tipo proporcionado (0 ó 1). Si no se reemplaza, **GetTypeInfoCount** devuelve 0. Para reemplazar, utilice la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) (macro), que también implementa `GetTypeLib` y `GetTypeLibCache`.  
  
##  <a name="a-namegettypeinfoofguida--ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid  
 Recupera la descripción del tipo que se corresponde con el GUID especificado.  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `lcid`  
 Identificador de configuración regional ( `LCID`).  
  
 `guid`  
 El [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931) de la descripción del tipo.  
  
 `ppTypeInfo`  
 Puntero a un puntero a la `ITypeInfo` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 HRESULT que indica el éxito o error de la llamada. Si es correcto, * `ppTypeInfo` señala a la interfaz de información de tipo.  
  
##  <a name="a-namegettypeliba--ccmdtargetgettypelib"></a><a name="gettypelib"></a>CCmdTarget::GetTypeLib  
 Obtiene un puntero a una biblioteca de tipos.  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>Parámetros  
 `lcid`  
 Identificador de configuración regional ( `LCID`).  
  
 `ppTypeLib`  
 Un puntero a un puntero a la `ITypeLib` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 HRESULT que indica el éxito o error de la llamada. Si es correcto, * `ppTypeLib` señala a la interfaz de la biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetTypeLib` devuelve TYPE_E_CANTLOADLIBRARY). Utilice la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) (macro), que también implementa `GetTypeInfoCount` y `GetTypeLibCache`.  
  
##  <a name="a-namegettypelibcachea--ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache  
 Obtiene la caché de la biblioteca de tipos.  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un **CTypeLibCache** objeto.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, **GetTypeLibCache** devuelve NULL). Utilice la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) (macro), que también implementa `GetTypeInfoCount` y `GetTypeLib`.  
  
##  <a name="a-nameisinvokealloweda--ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed  
 Esta función se invoca mediante la implementación de MFC de **IDispatch:: Invoke** para determinar si un método de automatización especificado (identificado por `dispid`) pueden invocar.  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>Parámetros  
 `dispid`  
 Un identificador de envío.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método puede ser invocado, de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Si `IsInvokeAllowed` devuelve TRUE, **Invoke** procede a llamar al método; en caso contrario, `Invoke` se produce un error, devuelve E_UNEXPECTED.  
  
 Las clases derivadas pueden reemplazar esta función para devolver los valores adecuados (si no se reemplaza, `IsInvokeAllowed` devuelve TRUE). Vea en particular [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).  
  
##  <a name="a-nameisresultexpecteda--ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>CCmdTarget::IsResultExpected  
 Utilice `IsResultExpected` para determinar si un cliente espera un valor devuelto de la llamada a una función de automatización.  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si una función de automatización debe devolver un valor; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz OLE proporciona información a MFC si el cliente está utilizando o omitiendo el resultado de una llamada de función y, a su vez, MFC utiliza esta información para determinar el resultado de una llamada a `IsResultExpected`. Si la producción de un valor devuelto mucho tiempo o recursos, puede aumentar la eficacia al llamar a esta función antes de calcular el valor devuelto.  
  
 Esta función devuelve 0, sólo una vez para que se obtengan valores devueltos válidos de otras funciones de automatización si se llaman desde la función de automatización el cliente ha llamado.  
  
 `IsResultExpected`Devuelve un valor distinto de cero si se llama cuando una llamada de función de automatización no está en curso.  
  
##  <a name="a-nameoncmdmsga--ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CCmdTarget:: OnCmdMsg  
 Llamado por el marco de trabajo para enrutar y enviar mensajes de comando y controlar la actualización de la interfaz de usuario de objetos de comando.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Contiene el identificador del comando.  
  
 `nCode`  
 Identifica el código de notificación de comando. Consulte **comentarios** para obtener más información acerca de los valores para `nCode`.  
  
 `pExtra`  
 Usar según el valor de `nCode`. Consulte **comentarios** para obtener más información acerca de `pExtra`.  
  
 `pHandlerInfo`  
 Si no **NULL**, `OnCmdMsg` rellena la **pTarget** y **pmf** los miembros de la `pHandlerInfo` estructura en lugar de enviar el comando. Normalmente, este parámetro debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controló el mensaje; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Ésta es la rutina de implementación principal de la arquitectura de comandos de framework.  
  
 En tiempo de ejecución `OnCmdMsg` envía un comando a otros objetos o controle el propio comando mediante una llamada a la clase raíz `CCmdTarget::OnCmdMsg`, que realiza la búsqueda en el mapa de mensajes real. Para obtener una descripción completa de la ruta predeterminada del comando, consulte [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
 En raras ocasiones, puede reemplazar esta función miembro para extender el marco enrutamiento de comandos estándar. Consulte [21 de nota técnica](../../mfc/tn021-command-and-message-routing.md) para detalles avanzados de la arquitectura de enrutamiento de comandos.  
  
 Si reemplaza `OnCmdMsg`, debe proporcionar el valor adecuado para `nCode`, el código de notificación de comando y `pExtra`, que depende del valor de `nCode`. En la tabla siguiente se enumera los valores correspondientes:  
  
|Valor de `nCode`|Valor de `pExtra`|  
|-------------------|--------------------|  
|PARÁMETRO CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)*|  
|CN_EVENT|AFX_EVENT *|  
|CN_UPDATE_COMMAND_UI|CCmdUI *|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#44;](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView nº&45;](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="a-nameonfinalreleasea--ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>CCmdTarget:: OnFinalRelease  
 Llamado por el marco de trabajo cuando se libera la última referencia OLE hacia o desde el objeto.  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para proporcionar un control especial para esta situación. La implementación predeterminada, elimina el objeto.  
  
##  <a name="a-namerestorewaitcursora--ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor  
 Llame a esta función para restaurar el cursor de reloj de arena apropiado después de cambia el cursor del sistema (por ejemplo, cuando se abre un cuadro de mensaje y se cierra mientras se esté realizando una operación larga).  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#43;](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo ACDUAL de MFC](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Clase COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)

