---
title: CCmdTarget (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
dev_langs:
- C++
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1dfc1c4d5cf753ae102d7656e94d63923004d2cc
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955666"
---
# <a name="ccmdtarget-class"></a>CCmdTarget (clase)
La clase base para la arquitectura de mapa de mensajes de la biblioteca Microsoft Foundation Class.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCmdTarget : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Construye un objeto `CCmdTarget`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Muestra el cursor como un cursor de reloj de arena.|  
|[CCmdTarget::DoOleVerb](#dooleverb)|Hace que una acción especificada por un verbo OLE que se realice.|  
|[CCmdTarget::EnableAutomation](#enableautomation)|Permite la automatización OLE para la `CCmdTarget` objeto.|  
|[CCmdTarget::EnableConnections](#enableconnections)|Habilita la activación de eventos a través de puntos de conexión.|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Habilita la biblioteca de tipos de un objeto.|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Devuelve el cursor anterior.|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Enumera los verbos de un objeto OLE.|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|Devuelve un puntero a la `CCmdTarget` objeto asociado a la `IDispatch` puntero.|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Obtiene el identificador de interfaz de envío principal.|  
|[CCmdTarget::GetIDispatch](#getidispatch)|Devuelve un puntero a la `IDispatch` objeto asociado a la `CCmdTarget` objeto.|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo que proporciona un objeto.|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Recupera la descripción del tipo que se corresponde con el GUID especificado.|  
|[CCmdTarget::GetTypeLib](#gettypelib)|Obtiene un puntero a una biblioteca de tipos.|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Obtiene la caché de la biblioteca de tipos.|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Permite la invocación del método de automatización.|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|Devuelve distinto de cero si una función de automatización debe devolver un valor.|  
|[CCmdTarget:: OnCmdMsg](#oncmdmsg)|Enruta y envía los mensajes de comando.|  
|[CCmdTarget:: OnFinalRelease](#onfinalrelease)|Limpia después del lanzamiento de la última referencia OLE.|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Restaura el cursor de reloj de arena.|  
  
## <a name="remarks"></a>Comentarios  
 Un mapa de mensajes enruta los comandos o mensajes a las funciones de miembro que se escribe para controlarlos. (Un comando es un mensaje de un elemento de menú, un botón de comando o una tecla de aceleración).  
  
 Las clases del marco de claves derivadas de `CCmdTarget` incluyen [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), y [ CFrameWnd](../../mfc/reference/cframewnd-class.md). Si tiene previsto para que una nueva clase controlar los mensajes, derive la clase de uno de estos `CCmdTarget`-las clases derivadas. Rara vez se derive una clase de `CCmdTarget` directamente.  
  
 Para obtener información general de destinos de comando y `OnCmdMsg` el enrutamiento, consulte [destinos de comando](../../mfc/command-targets.md), [enrutamiento de comandos](../../mfc/command-routing.md), y [asignar mensajes](../../mfc/mapping-messages.md).  
  
 `CCmdTarget` incluye funciones miembro que administrar la presentación de un cursor de reloj de arena. Mostrar el cursor de reloj de arena cuando creas un comando para adquirir un intervalo de tiempo notable para ejecutar.  
  
 Mapas, similares a mapas de mensajes de envío, se utilizan para exponer la automatización OLE `IDispatch` funcionalidad. Al exponer esta interfaz, otras aplicaciones (como Visual Basic) pueden llamar a la aplicación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor  
 Llame a esta función para mostrar el cursor como un reloj de arena cuando creas un comando para adquirir un intervalo de tiempo notable para ejecutar.  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función para mostrar al usuario que está ocupado, por ejemplo, cuando un `CDocument` objeto carga ni guarda propia en un archivo.  
  
 Las acciones de `BeginWaitCursor` no siempre son efectivos fuera de un controlador de mensaje único como otras acciones, como `OnSetCursor` de control, puede cambiar el cursor.  
  
 Llame a `EndWaitCursor` para restaurar el cursor anterior.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget  
 Construye un objeto `CCmdTarget`.  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb  
 Hace que una acción especificada por un verbo OLE que se realice.  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 *iVerb*  
 Identificador numérico del verbo.  
  
 *lpMsg*  
 Puntero a la [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) estructura que describe el evento (por ejemplo, un doble clic) que invocó el verbo.  
  
 *hWndParent*  
 Identificador de la ventana de documento que contiene el objeto.  
  
 *lpRect*  
 Puntero a la [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene las coordenadas, en píxeles, que definen un objeto de rectángulo en delimitador *hwndParent*.  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si se realizó correctamente, de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro básicamente es una implementación de [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508). Las posibles acciones se enumeran por [CCmdTarget::EnumOleVerbs](#enumoleverbs).  
  
##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation  
 Llame a esta función para habilitar la automatización OLE de un objeto.  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama desde el constructor del objeto y solo se debe llamar si se ha declarado un mapa de envíos para la clase. Para obtener más información acerca de la automatización, vea los artículos [los clientes de automatización](../../mfc/automation-clients.md) y [servidores de automatización](../../mfc/automation-servers.md).  
  
##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections  
 Habilita la activación de eventos a través de puntos de conexión.  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>Comentarios  
 Para habilitar los puntos de conexión, llame a esta función miembro en el constructor de la clase derivada.  
  
##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib  
 Habilita la biblioteca de tipos de un objeto.  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro en el constructor de la `CCmdTarget`-objeto derivado si proporciona información de tipo. Para obtener más información, vea el artículo de Knowledge Base Q185720, "HOWTO: proporcionar información de tipo de un servidor de automatización de MFC." Artículos de Knowledge Base están disponibles en [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor  
 Llame a esta función después de haber llamado el `BeginWaitCursor` función de miembro para devolver desde el cursor de reloj de arena hasta el cursor anterior.  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo también llama a esta función miembro después de haber llamado el cursor de reloj de arena.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs  
 Enumera los verbos de un objeto OLE.  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>Parámetros  
 *ppenumOleVerb*  
 Un puntero a un puntero a un [IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084) interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el objeto es compatible con al menos un verbo OLE (en cuyo caso \* *ppenumOleVerb* apunta a un `IEnumOLEVERB` interfaz de enumerador), en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro básicamente es una implementación de [IOleObject:: EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781).  
  
##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch  
 Llame a esta función para asignar un `IDispatch` puntero, procedente de las funciones de miembro de automatización de una clase, en la `CCmdTarget` objeto que implementa las interfaces de la `IDispatch` objeto.  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpDispatch*  
 Puntero a un objeto `IDispatch`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CCmdTarget` objeto asociado a *lpDispatch*. Esta función devuelve **NULL** si la `IDispatch` objeto no se reconoce como un Microsoft Foundation Class `IDispatch` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El resultado de esta función es el inverso de una llamada a la función miembro `GetIDispatch`.  
  
##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID  
 Obtiene el identificador de interfaz de envío principal.  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>Parámetros  
 *pIID*  
 Un puntero a un identificador de interfaz (un [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)).  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si se realizó correctamente, de lo contrario, FALSE. Si se realiza correctamente, \* *pIID* se establece en el identificador de interfaz de envío principal.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetDispatchIID` devuelve FALSE). Vea [COleControl](../../mfc/reference/colecontrol-class.md).  
  
 Para obtener más información, vea el artículo de Knowledge Base Q185720, "HOWTO: proporcionar información de tipo de un servidor de automatización de MFC." Artículos de Knowledge Base están disponibles en [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch  
 Llame a esta función miembro para recuperar el `IDispatch` puntero desde un método de automatización que devuelve un `IDispatch` puntero o toma un `IDispatch` puntero por referencia.  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAddRef*  
 Especifica si se incrementa el recuento de referencias para el objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 El `IDispatch` asociado con el objeto de puntero.  
  
### <a name="remarks"></a>Comentarios  
 Para los objetos que llaman `EnableAutomation` en sus constructores, haciéndolos automatización habilitada, esta función devuelve un puntero a la implementación de clase Foundation `IDispatch` utilizado por los clientes que se comunican a través de la `IDispatch` interfaz. Llamar a esta función automáticamente agrega una referencia al puntero, por lo que no es necesario realizar una llamada a [IUnknown:: AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379).  
  
##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount  
 Recupera el número de interfaces de información de tipo que proporciona un objeto.  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de interfaces de información de tipo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro básicamente implementa [IDispatch:: GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12).  
  
 Las clases derivadas deben invalidar esta función para devolver el número de interfaces de información de tipo proporcionado (0 ó 1). Si no se reemplaza, `GetTypeInfoCount` devuelve 0. Para invalidar, use la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, que también implementa `GetTypeLib` y `GetTypeLibCache`.  
  
##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid  
 Recupera la descripción del tipo que se corresponde con el GUID especificado.  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 *lcid*  
 Un identificador de configuración regional ( `LCID`).  
  
 *GUID*  
 El [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931) de la descripción del tipo.  
  
 *ppTypeInfo*  
 Puntero a un puntero a la `ITypeInfo` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 HRESULT que indica el éxito o fracaso de la llamada. Si es correcto, * *ppTypeInfo* señala a la interfaz de información de tipo.  
  
##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib  
 Obtiene un puntero a una biblioteca de tipos.  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>Parámetros  
 *lcid*  
 Un identificador de configuración regional ( `LCID`).  
  
 *ppTypeLib*  
 Un puntero a un puntero a la `ITypeLib` interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 HRESULT que indica el éxito o fracaso de la llamada. Si es correcto, * *ppTypeLib* señala a la interfaz de la biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetTypeLib` devuelve TYPE_E_CANTLOADLIBRARY). Use la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, que también implementa `GetTypeInfoCount` y `GetTypeLibCache`.  
  
##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache  
 Obtiene la caché de la biblioteca de tipos.  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CTypeLibCache` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetTypeLibCache` devuelve NULL). Use la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, que también implementa `GetTypeInfoCount` y `GetTypeLib`.  
  
##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed  
 Esta función se invoca mediante la implementación de MFC de `IDispatch::Invoke` para determinar si un método de automatización determinado (identificada por *dispid*) se puede invocar.  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>Parámetros  
 *DISPID*  
 Un identificador de envío.  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si el método puede ser invocado, de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Si `IsInvokeAllowed` devuelve TRUE, `Invoke` continúa para llamar al método; en caso contrario, `Invoke` producirá y devolverá E_UNEXPECTED.  
  
 Las clases derivadas pueden invalidar esta función para devolver los valores adecuados (si no se reemplaza, `IsInvokeAllowed` devuelve TRUE). Vea en particular [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).  
  
##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected  
 Utilice `IsResultExpected` para determinar si un cliente espera un valor devuelto de la llamada a una función de automatización.  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si una función de automatización debe devolver un valor; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz OLE proporciona información a MFC acerca de si el cliente está utilizando o pasando por alto el resultado de una llamada de función y, a su vez, MFC utiliza esta información para determinar el resultado de una llamada a `IsResultExpected`. Si la producción de un valor devuelto se mucho tiempo o recursos, puede aumentar la eficacia mediante una llamada a esta función antes de calcular el valor devuelto.  
  
 Esta función devuelve 0 solo una vez para que obtendrá los valores válidos de valor devueltos de otras funciones de automatización si llamarlas desde la función de automatización de la el cliente ha llamado.  
  
 `IsResultExpected` Devuelve un valor distinto de cero si se llama cuando una llamada de función de automatización no está en curso.  
  
##  <a name="oncmdmsg"></a>  CCmdTarget:: OnCmdMsg  
 Lo llama el marco de trabajo para enrutar y enviar los mensajes de comando y para controlar la actualización de los objetos de interfaz de usuario de comando.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 Contiene el identificador del comando.  
  
 *nCode*  
 Identifica el código de notificación de comando. Vea **comentarios** para obtener más información acerca de los valores para *nCode*.  
  
 *pExtra*  
 Usar según el valor de *nCode*. Vea **comentarios** para obtener más información acerca de *pExtra*.  
  
 *pHandlerInfo*  
 Si no **NULL**, `OnCmdMsg` rellena la *pTarget* y *pmf* los miembros de la *pHandlerInfo* estructura en lugar de enviar el comando. Normalmente, este parámetro debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controla el mensaje; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de la rutina de implementación principal de la arquitectura de comandos de framework.  
  
 En tiempo de ejecución `OnCmdMsg` envía un comando a otros objetos o controle el propio comando mediante una llamada a la clase raíz `CCmdTarget::OnCmdMsg`, que realiza la búsqueda en el mapa de mensajes real. Para obtener una descripción completa de la ruta predeterminada del comando, consulte [control de mensajes y los temas de asignación](../../mfc/message-handling-and-mapping.md).  
  
 En raras ocasiones, puede que desee anular esta función miembro para extender el marco enrutamiento de comandos estándar. Hacer referencia a [21 de nota técnica](../../mfc/tn021-command-and-message-routing.md) para obtener detalles avanzados sobre la arquitectura de enrutamiento de comandos.  
  
 Si invalida `OnCmdMsg`, debe proporcionar el valor adecuado para *nCode*, el código de notificación de comandos, y *pExtra*, que depende del valor de *nCode* . En la tabla siguiente se enumera sus valores correspondientes:  
  
|*nCode* valor|*pExtra* valor|  
|-------------------|--------------------|  
|PARÁMETRO CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)*|  
|CN_EVENT|AFX_EVENT *|  
|CN_UPDATE_COMMAND_UI|CCmdUI *|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>  CCmdTarget:: OnFinalRelease  
 Llamado por el marco de trabajo cuando se libera la última referencia OLE hacia o desde el objeto.  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para proporcionar un control especial para esta situación. La implementación predeterminada, elimina el objeto.  
  
##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor  
 Llame a esta función para restaurar el cursor de reloj de arena adecuado después de cambia el cursor del sistema (por ejemplo, después de un cuadro de mensaje se ha abierto y, a continuación, se cierra mientras se esté realizando una operación larga).  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo ACDUAL de MFC](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver (clase)](../../mfc/reference/coledispatchdriver-class.md)
