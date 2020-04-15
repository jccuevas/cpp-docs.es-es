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
ms.openlocfilehash: 5ee4101302322a5212a80b32f095cdd13d9769e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352286"
---
# <a name="ccmdtarget-class"></a>CCmdTarget (clase)

La clase base para la arquitectura de mapa de mensajes de Microsoft Foundation Class Library.

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
|[CCmdTarget::DoOleVerb](#dooleverb)|Hace que se realice una acción especificada por un verbo OLE.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Permite la automatización OLE para el `CCmdTarget` objeto.|
|[CCmdTarget::EnableConnections](#enableconnections)|Habilita la activación de eventos a través de puntos de conexión.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Habilita la biblioteca de tipos de un objeto.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Vuelve al cursor anterior.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Enumera los verbos OLE de un objeto.|
|[CCmdTarget::FromiDispatch](#fromidispatch)|Devuelve un puntero `CCmdTarget` al objeto `IDispatch` asociado al puntero.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Obtiene el identificador de interfaz de envío principal.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Devuelve un puntero `IDispatch` al objeto `CCmdTarget` asociado al objeto.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo que proporciona un objeto.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Recupera la descripción de tipo que se corresponde con el GUID especificado.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Obtiene un puntero a una biblioteca de tipos.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Obtiene la caché de biblioteca de tipos.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Habilita la invocación de métodos de automatización.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Devuelve distinto de cero si una función de automatización debe devolver un valor.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Enruta y distribuye mensajes de comando.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Limpia después de que se libere la última referencia OLE.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Restaura el cursor del reloj de arena.|

## <a name="remarks"></a>Observaciones

Un mapa de mensajes enruta comandos o mensajes a las funciones miembro que escribe para controlarlos. (Un comando es un mensaje de un elemento de menú, botón de comando o tecla aceleradora.)

Las clases de `CCmdTarget` marco de claves derivadas de: [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)y [CFrameWnd](../../mfc/reference/cframewnd-class.md). Si tiene la intención de que una nueva clase `CCmdTarget`controle los mensajes, derive la clase de una de estas clases derivadas. Rara vez derivará una `CCmdTarget` clase de directamente.

Para obtener información general `OnCmdMsg` sobre los destinos de comandos y el enrutamiento, vea [Destinos de](../../mfc/command-targets.md)comandos , [Enrutamiento](../../mfc/command-routing.md)de comandos y Mensajes de [asignación](../../mfc/mapping-messages.md).

`CCmdTarget`incluye funciones miembro que controlan la visualización de un cursor de reloj de arena. Muestre el cursor de reloj de arena cuando espere que un comando tome un intervalo de tiempo notable para ejecutarse.

Los mapas de distribución, similares a `IDispatch` los mapas de mensajes, se usan para exponer la funcionalidad de automatización OLE. Al exponer esta interfaz, otras aplicaciones (como Visual Basic) pueden llamar a la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor

Llame a esta función para mostrar el cursor como un reloj de arena cuando espera que un comando tome un intervalo de tiempo notable para ejecutar.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función para `CDocument` mostrar al usuario que está ocupado, como cuando un objeto se carga o se guarda en un archivo.

Las acciones `BeginWaitCursor` de no siempre son eficaces fuera de `OnSetCursor` un único controlador de mensajes, ya que otras acciones, como el control, podrían cambiar el cursor.

Llame `EndWaitCursor` para restaurar el cursor anterior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CCmdTarget::CCmdTarget

Construye un objeto `CCmdTarget`.

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a>CCmdTarget::DoOleVerb

Hace que se realice una acción especificada por un verbo OLE.

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
Puntero a la estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que describe el evento (por ejemplo, un doble clic) que invocó el verbo.

*hWndParent*<br/>
Identificador de la ventana de documento que contiene el objeto.

*lpRect*<br/>
Puntero a la estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que contiene las coordenadas, en píxeles, que definen el rectángulo delimitador de un objeto en *hwndParent*.

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente, de lo contrario FALSE.

### <a name="remarks"></a>Observaciones

Esta función miembro es básicamente una implementación de [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Las acciones posibles se enumeran mediante [CCmdTarget::EnumOleVerbs](#enumoleverbs).

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a>CCmdTarget::EnableAutomation

Llame a esta función para habilitar la automatización OLE para un objeto.

```
void EnableAutomation();
```

### <a name="remarks"></a>Observaciones

Normalmente se llama a esta función desde el constructor del objeto y solo se debe llamar si se ha declarado un mapa de distribución para la clase. Para obtener más información sobre la automatización, consulte los [artículos Clientes](../../mfc/automation-clients.md) de automatización y Servidores de [automatización](../../mfc/automation-servers.md).

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a>CCmdTarget::EnableConnections

Habilita la activación de eventos a través de puntos de conexión.

```
void EnableConnections();
```

### <a name="remarks"></a>Observaciones

Para habilitar los puntos de conexión, llame a esta función miembro en el constructor de la clase derivada.

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CCmdTarget::EnableTypeLib

Habilita la biblioteca de tipos de un objeto.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Observaciones

Llame a esta función `CCmdTarget`miembro en el constructor de su -derived objeto si proporciona información de tipo.

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor

Llame a esta función `BeginWaitCursor` después de haber llamado a la función miembro para volver desde el cursor de reloj de arena al cursor anterior.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo también llama a esta función miembro después de que ha llamado al cursor de reloj de arena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs

Enumera los verbos OLE de un objeto.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parámetros

*ppenumOleVerb*<br/>
Un puntero a un puntero a una interfaz [IEnumOLEVERB.](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)

### <a name="return-value"></a>Valor devuelto

TRUESi el objeto admite al menos un \* verbo OLE (en `IEnumOLEVERB` cuyo caso *ppenumOleVerb* apunta a una interfaz de enumerador), en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función miembro es básicamente una implementación de [IOleObject::EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>CCmdTarget::FromiDispatch

Llame a esta `IDispatch` función para asignar un puntero, recibido `CCmdTarget` de las funciones miembro `IDispatch` de automatización de una clase, en el objeto que implementa las interfaces del objeto.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parámetros

*lpDispatch*<br/>
Puntero a un objeto `IDispatch` .

### <a name="return-value"></a>Valor devuelto

Puntero al `CCmdTarget` objeto asociado a *lpDispatch*. Esta función devuelve `IDispatch` NULL si el objeto `IDispatch` no se reconoce como un microsoft Foundation Class objeto.

### <a name="remarks"></a>Observaciones

El resultado de esta función es el inverso de una llamada a la función `GetIDispatch`miembro .

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID

Obtiene el identificador de interfaz de envío principal.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parámetros

*pIID*<br/>
Un puntero a un identificador de interfaz (un [GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente, de lo contrario FALSE. Si se \* realiza correctamente, *pIID* se establece en el ID de interfaz de envío principal.

### <a name="remarks"></a>Observaciones

Las clases derivadas deben invalidar esta función miembro (si no se invalida, `GetDispatchIID` devuelve FALSE). Consulte [COleControl](../../mfc/reference/colecontrol-class.md).

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CCmdTarget::GetIDispatch

Llame a esta función miembro para recuperar `IDispatch` el `IDispatch` puntero de `IDispatch` un método de automatización que devuelve un puntero o toma un puntero por referencia.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parámetros

*bAddRef*<br/>
Especifica si se debe incrementar el recuento de referencias para el objeto.

### <a name="return-value"></a>Valor devuelto

El `IDispatch` puntero asociado al objeto.

### <a name="remarks"></a>Observaciones

Para los `EnableAutomation` objetos que llaman a sus constructores, por lo que la `IDispatch` automatización está habilitada, `IDispatch` esta función devuelve un puntero a la implementación de Foundation Class que usa los clientes que se comunican a través de la interfaz. Llamar a esta función agrega automáticamente una referencia al puntero, por lo que no es necesario realizar una llamada a [IUnknown::AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount

Recupera el número de interfaces de información de tipo que proporciona un objeto.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Valor devuelto

El número de interfaces de información de tipo.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa básicamente [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Las clases derivadas deben invalidar esta función para devolver el número de interfaces de información de tipo proporcionadas (0 o 1). Si no se `GetTypeInfoCount` invalida, devuelve 0. Para invalidar, utilice la macro [IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) que también implementa `GetTypeLib` y `GetTypeLibCache`.

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid

Recupera la descripción de tipo que se corresponde con el GUID especificado.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parámetros

*lcid*<br/>
Identificador de configuración `LCID`regional ( ).

*Guid*<br/>
Guid [GUID](/previous-versions/cc317743(v%3dmsdn.10)) de la descripción del tipo.

*ppTypeInfo*<br/>
Puntero a un `ITypeInfo` puntero a la interfaz.

### <a name="return-value"></a>Valor devuelto

Un HRESULT que indica el éxito o el error de la llamada. Si se \* realiza correctamente, *ppTypeInfo* apunta a la interfaz de información de tipo.

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a>CCmdTarget::GetTypeLib

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
Un puntero a un `ITypeLib` puntero a la interfaz.

### <a name="return-value"></a>Valor devuelto

Un HRESULT que indica el éxito o el error de la llamada. Si se \* realiza correctamente, *ppTypeLib* apunta a la interfaz de biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Las clases derivadas deben invalidar esta función miembro (si no se invalida, `GetTypeLib` devuelve TYPE_E_CANTLOADLIBRARY). Utilice la macro [IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) `GetTypeInfoCount` que `GetTypeLibCache`también implementa y .

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache

Obtiene la caché de biblioteca de tipos.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CTypeLibCache` .

### <a name="remarks"></a>Observaciones

Las clases derivadas deben invalidar esta función miembro (si no se invalida, `GetTypeLibCache` devuelve NULL). Utilice la macro [IMPLEMENT_OLETYPELIB,](../../mfc/reference/type-library-access.md#implement_oletypelib) `GetTypeInfoCount` que `GetTypeLib`también implementa y .

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed

La implementación de `IDispatch::Invoke` MFC llama a esta función para determinar si se puede invocar un método de automatización determinado (identificado por *dispid*).

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
Un ID de envío.

### <a name="return-value"></a>Valor devuelto

TRUESi se puede invocar el método, de lo contrario FALSE.

### <a name="remarks"></a>Observaciones

Si `IsInvokeAllowed` devuelve `Invoke` TRUE, procede a llamar al método; de `Invoke` lo contrario, fallará, devolviendo E_UNEXPECTED.

Las clases derivadas pueden invalidar esta función para `IsInvokeAllowed` devolver los valores adecuados (si no se invalida, devuelve TRUE). Vea en particular [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>CCmdTarget::IsResultExpected

Se `IsResultExpected` usa para determinar si un cliente espera un valor devuelto de su llamada a una función de automatización.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si una función de automatización debe devolver un valor; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La interfaz OLE proporciona información a MFC acerca de si el cliente está utilizando o ignorando el resultado `IsResultExpected`de una llamada de función y MFC a su vez usa esta información para determinar el resultado de una llamada a . Si la producción de un valor devuelto consume mucho tiempo o recursos, puede aumentar la eficiencia llamando a esta función antes de calcular el valor devuelto.

Esta función devuelve 0 solo una vez para que obtendrá valores devueltos válidos de otras funciones de automatización si los llama desde la función de automatización a la que ha llamado el cliente.

`IsResultExpected`devuelve un valor distinto de cero si se llama cuando una llamada de función de automatización no está en curso.

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg

Llamado por el marco de trabajo para enrutar y enviar mensajes de comando y para controlar la actualización de los objetos de interfaz de usuario de comando.

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

*nCódigo*<br/>
Identifica el código de notificación de comandos. Consulte **Comentarios** para obtener más información sobre los valores de *nCode*.

*pExtra*<br/>
Se utiliza según el valor de *nCode*. Consulte **Comentarios** para obtener más información sobre *pExtra*.

*pHandlerInfo*<br/>
Si no `OnCmdMsg` es NULL, rellena los miembros *pTarget* y *pmf* de la estructura *pHandlerInfo* en lugar de distribuir el comando. Normalmente, este parámetro debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controla el mensaje; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta es la rutina de implementación principal de la arquitectura de comandos del marco de trabajo.

En tiempo `OnCmdMsg` de ejecución, distribuye un comando a otros objetos `CCmdTarget::OnCmdMsg`o controla el propio comando llamando a la clase raíz, que realiza la búsqueda de mapa de mensajes real. Para obtener una descripción completa del enrutamiento de comandos predeterminado, vea Temas de [asignación y control](../../mfc/message-handling-and-mapping.md)de mensajes .

En raras ocasiones, es posible que desee invalidar esta función miembro para ampliar el enrutamiento de comandos estándar del marco de trabajo. Refiera a la [nota técnica 21](../../mfc/tn021-command-and-message-routing.md) para los detalles avanzados de la arquitectura del comando routing.

Si `OnCmdMsg`invalida , debe proporcionar el valor adecuado para *nCode*, el código de notificación de comandos y *pExtra*, que depende del valor de *nCode*. En la tabla siguiente se enumeran sus valores correspondientes:

|*nValor de* código|*pValor extra*|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>CCmdTarget::OnFinalRelease

Llamado por el marco de trabajo cuando se libera la última referencia OLE al objeto o desde él.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Observaciones

Reemplace esta función para proporcionar un control especial para esta situación. La implementación predeterminada elimina el objeto.

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor

Llame a esta función para restaurar el cursor de reloj de arena adecuado después de que el cursor del sistema haya cambiado (por ejemplo, después de que se haya abierto y cerrado un cuadro de mensaje mientras se encuentra en medio de una operación prolongada).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI (clase)](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Clase CWinApp](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Clase COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)
