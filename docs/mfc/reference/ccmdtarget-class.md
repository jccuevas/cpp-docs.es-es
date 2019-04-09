---
title: CCmdTarget (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 9314717fab53b1a89b87d657ec617a4c6bd45b8b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776198"
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
|[CCmdTarget::DoOleVerb](#dooleverb)|Hace que una acción especificada por un verbo OLE que se realizará.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Permite la automatización OLE para la `CCmdTarget` objeto.|
|[CCmdTarget::EnableConnections](#enableconnections)|Habilita la activación de eventos a través de puntos de conexión.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Habilita la biblioteca de tipos de un objeto.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Devuelve hasta el cursor anterior.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Enumera los verbos de un objeto OLE.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|Devuelve un puntero a la `CCmdTarget` objeto asociado con el `IDispatch` puntero.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Obtiene el identificador de interfaz de envío principal.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Devuelve un puntero a la `IDispatch` objeto asociado con el `CCmdTarget` objeto.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo que proporciona un objeto.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Recupera la descripción del tipo que se corresponde con el GUID especificado.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Obtiene un puntero a una biblioteca de tipos.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Obtiene la memoria caché de biblioteca de tipos.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Permite la invocación del método de automatización.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Devuelve cero si una función de automatización debe devolver un valor.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Las rutas y envía mensajes de comando.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Limpia después del lanzamiento de la última referencia OLE.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Restaura el cursor de reloj de arena.|

## <a name="remarks"></a>Comentarios

Un mapa de mensajes enruta los comandos o los mensajes a las funciones miembro que escribir para controlarlos. (Un comando es un mensaje de un elemento de menú, un botón de comando o una tecla de aceleración).

Las clases de marco de claves derivadas de `CCmdTarget` incluyen [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), y [ CFrameWnd](../../mfc/reference/cframewnd-class.md). Si tiene previsto para que una nueva clase controlar los mensajes, derive la clase de uno de estos `CCmdTarget`-las clases derivadas. Rara vez se derivará una clase de `CCmdTarget` directamente.

Para obtener información general de los destinos de comando y `OnCmdMsg` enrutamiento, consulte [destinos de comando](../../mfc/command-targets.md), [enrutamiento de comandos](../../mfc/command-routing.md), y [asignar mensajes](../../mfc/mapping-messages.md).

`CCmdTarget` incluye funciones de miembro que controlan la presentación de un cursor de reloj de arena. Cuando se espera que un comando para tomar un intervalo de tiempo apreciable para ejecutar, mostrar el cursor de reloj de arena.

Mapas, similares a mapas de mensajes de envío, se utilizan para exponer la automatización OLE `IDispatch` funcionalidad. Al exponer esta interfaz, otras aplicaciones (como Visual Basic) pueden llamar a la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor

Llame a esta función para mostrar el cursor como un reloj de arena cuando se espera que un comando para tomar un intervalo de tiempo apreciable para ejecutar.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Comentarios

El marco llama a esta función para mostrar al usuario que está ocupado, por ejemplo, cuando un `CDocument` objeto carga ni guarda a sí mismo a un archivo.

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

Hace que una acción especificada por un verbo OLE que se realizará.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Identificador numérico del verbo.

*lpMsg*<br/>
Puntero a la [MSG](/windows/desktop/api/winuser/ns-winuser-msg) estructura que describe el evento (por ejemplo, un doble clic) que invocó el verbo.

*hWndParent*<br/>
Identificador de la ventana de documento que contiene el objeto.

*lpRect*<br/>
Puntero a la [RECT](/previous-versions/dd162897\(v=vs.85\)) rectángulo de límite de estructura que contiene las coordenadas, en píxeles, que definen un objeto *hwndParent*.

### <a name="return-value"></a>Valor devuelto

TRUE si se realizó correctamente, de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es básicamente una implementación de [DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb). Enumeran las posibles acciones [CCmdTarget::EnumOleVerbs](#enumoleverbs).

##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation

Llame a esta función para habilitar la automatización OLE para un objeto.

```
void EnableAutomation();
```

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama desde el constructor del objeto y solo debe llamarse si se ha declarado un mapa de envíos de la clase. Para obtener más información sobre la automatización, consulte los artículos [los clientes de automatización](../../mfc/automation-clients.md) y [servidores de automatización](../../mfc/automation-servers.md).

##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections

Habilita la activación de eventos a través de puntos de conexión.

```
void EnableConnections();
```

### <a name="remarks"></a>Comentarios

Para habilitar puntos de conexión, llame a esta función miembro en el constructor de la clase derivada.

##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib

Habilita la biblioteca de tipos de un objeto.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Comentarios

Llame a esta función miembro en el constructor de su `CCmdTarget`-objeto derivado si proporciona información de tipo.

##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor

Llame a esta función después de haber llamado el `BeginWaitCursor` función miembro para devolver desde el cursor de reloj de arena hasta el cursor anterior.

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

*ppenumOleVerb*<br/>
Un puntero a un puntero a un [IEnumOLEVERB](/windows/desktop/api/oleidl/nn-oleidl-ienumoleverb) interfaz.

### <a name="return-value"></a>Valor devuelto

TRUE si el objeto es compatible con al menos un verbo OLE (en cuyo caso \* *ppenumOleVerb* apunta a un `IEnumOLEVERB` interfaz de enumerador), en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Esta función miembro es básicamente una implementación de [IOleObject:: EnumVerbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs).

##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch

Llame a esta función para asignar un `IDispatch` puntero, recibido de las funciones de miembro de automatización de una clase, en el `CCmdTarget` objeto que implementa las interfaces de la `IDispatch` objeto.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parámetros

*lpDispatch*<br/>
Puntero a un objeto `IDispatch`.

### <a name="return-value"></a>Valor devuelto

Un puntero a la `CCmdTarget` asociado con el objeto *lpDispatch*. Esta función devuelve NULL si el `IDispatch` objeto no se reconoce como un Microsoft Foundation Class `IDispatch` objeto.

### <a name="remarks"></a>Comentarios

El resultado de esta función es el inverso de una llamada a la función miembro `GetIDispatch`.

##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID

Obtiene el identificador de interfaz de envío principal.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parámetros

*pIID*<br/>
Un puntero a un identificador de interfaz (una [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931)).

### <a name="return-value"></a>Valor devuelto

TRUE si se realizó correctamente, de lo contrario, FALSE. Si es correcto, \* *pIID* se establece en el identificador de interfaz de envío principal.

### <a name="remarks"></a>Comentarios

Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetDispatchIID` devuelve FALSE). Consulte [COleControl](../../mfc/reference/colecontrol-class.md).

##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch

Llame a esta función miembro para recuperar el `IDispatch` puntero desde un método de automatización que devuelve un `IDispatch` puntero o toma un `IDispatch` puntero por referencia.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parámetros

*bAddRef*<br/>
Especifica si se va a incrementar el recuento de referencias para el objeto.

### <a name="return-value"></a>Valor devuelto

El `IDispatch` asociado con el objeto de puntero.

### <a name="remarks"></a>Comentarios

Para los objetos que llaman a `EnableAutomation` en sus constructores, haciéndolos automatización habilitada, esta función devuelve un puntero a la implementación de clase Foundation `IDispatch` utilizado por clientes que se comunican a través de la `IDispatch` interfaz. Llamar a esta función automáticamente agrega una referencia al puntero, por lo que no es necesario realizar una llamada a [IUnknown:: AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref).

##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount

Recupera el número de interfaces de información de tipo que proporciona un objeto.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Valor devuelto

El número de interfaces de información de tipo.

### <a name="remarks"></a>Comentarios

Esta función miembro se implementa básicamente [IDispatch:: GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Las clases derivadas deben invalidar esta función para devolver el número de interfaces de información de tipo proporcionado (0 o 1). Si no se reemplaza, `GetTypeInfoCount` devuelve 0. Para invalidar, use el [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, que también implementa `GetTypeLib` y `GetTypeLibCache`.

##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid

Recupera la descripción del tipo que se corresponde con el GUID especificado.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parámetros

*lcid*<br/>
Un identificador regional ( `LCID`).

*guid*<br/>
El [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) de la descripción del tipo.

*ppTypeInfo*<br/>
Puntero a un puntero a la `ITypeInfo` interfaz.

### <a name="return-value"></a>Valor devuelto

Un HRESULT que indica el éxito o fracaso de la llamada. Si es correcto, \* *ppTypeInfo* señala a la interfaz de la información de tipo.

##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib

Obtiene un puntero a una biblioteca de tipos.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>Parámetros

*lcid*<br/>
Identificador de configuración regional (LCID).

*ppTypeLib*<br/>
Un puntero a un puntero a la `ITypeLib` interfaz.

### <a name="return-value"></a>Valor devuelto

Un HRESULT que indica el éxito o fracaso de la llamada. Si es correcto, \* *ppTypeLib* apunta a la interfaz de la biblioteca de tipos.

### <a name="remarks"></a>Comentarios

Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetTypeLib` devuelve TYPE_E_CANTLOADLIBRARY). Use la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, que también implementa `GetTypeInfoCount` y `GetTypeLibCache`.

##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache

Obtiene la memoria caché de biblioteca de tipos.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CTypeLibCache` .

### <a name="remarks"></a>Comentarios

Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetTypeLibCache` devuelve NULL). Use la [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, que también implementa `GetTypeInfoCount` y `GetTypeLib`.

##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed

Esta función se invoca mediante la implementación de MFC de `IDispatch::Invoke` para determinar si un método de automatización especificado (identificado por *dispid*) se pueden invocar.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
Un identificador de envío.

### <a name="return-value"></a>Valor devuelto

TRUE si el método puede ser invocado, de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si `IsInvokeAllowed` devuelve TRUE, `Invoke` procede a llamar al método; en caso contrario, `Invoke` se producirá un error, devuelve E_UNEXPECTED.

Las clases derivadas pueden reemplazar esta función para devolver los valores adecuados (si no se reemplaza, `IsInvokeAllowed` devuelve TRUE). Vea en particular [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected

Use `IsResultExpected` para determinar si un cliente espera un valor devuelto de la llamada a una función de automatización.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si una función de automatización debe devolver un valor; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La interfaz OLE proporciona información a MFC si el cliente está usando o se omite el resultado de una llamada de función y, a su vez, MFC utiliza esta información para determinar el resultado de una llamada a `IsResultExpected`. Si la producción de un valor devuelto es mucho tiempo o recursos, puede aumentar la eficacia mediante una llamada a esta función antes de calcular el valor devuelto.

Esta función devuelve 0 solamente una vez por lo que obtendrá los valores válidos de valor devueltos de otras funciones de automatización si se llama a ellos desde la función de automatización el cliente ha llamado.

`IsResultExpected` Devuelve un valor distinto de cero si se llama cuando una llamada de función de automatización no está en curso.

##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg

Lo llama el marco de trabajo para enrutar y enviar mensajes de comando y controlar la actualización de objetos de interfaz de usuario de comandos.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Contiene el identificador de comando.

*nCode*<br/>
Identifica el código de notificación de comandos. Consulte **comentarios** para obtener más información acerca de los valores para *nCode*.

*pExtra*<br/>
Usar según el valor de *nCode*. Consulte **comentarios** para obtener más información acerca de *pExtra*.

*pHandlerInfo*<br/>
Si no es NULL, `OnCmdMsg` rellena el *pTarget* y *pmf* los miembros de la *pHandlerInfo* estructura en lugar de enviar el comando. Normalmente, este parámetro debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mensaje está controlado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Se trata de la rutina de implementación principal de la arquitectura de comandos de framework.

En tiempo de ejecución `OnCmdMsg` envía un comando a otros objetos o administre el propio comando mediante una llamada a la clase raíz `CCmdTarget::OnCmdMsg`, que realiza la búsqueda en el mapa de mensajes real. Para obtener una descripción completa de la ruta predeterminada del comando, consulte [de mensajes y asignación de temas](../../mfc/message-handling-and-mapping.md).

En raras ocasiones, es posible que desee reemplazar esta función miembro para ampliar el marco de trabajo enrutamiento de comandos estándar. Consulte [21 de nota técnica](../../mfc/tn021-command-and-message-routing.md) para detalles avanzados de la arquitectura de enrutamiento de comandos.

Si invalida `OnCmdMsg`, debe proporcionar el valor adecuado para *nCode*, el código de notificación de comandos y *pExtra*, que depende del valor de *nCode* . En la tabla siguiente se enumera sus valores correspondientes:

|*nCode* valor|*pExtra* valor|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease

Lo llama el marco de trabajo cuando se libera la última referencia OLE hacia o desde el objeto.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Comentarios

Reemplace esta función para proporcionar un control especial para esta situación. La implementación predeterminada, elimina el objeto.

##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor

Llame a esta función para restaurar el cursor de reloj de arena apropiado después de que el cursor del sistema ha cambiado (por ejemplo, después de que ha abierto un cuadro de mensaje y se cierra, a continuación, en el transcurso de una operación larga).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo ACDUAL de MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp (clase)](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver (clase)](../../mfc/reference/coledispatchdriver-class.md)
