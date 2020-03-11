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
ms.openlocfilehash: 583b685295bf77910ef134776c1c4fa39baf93ad
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867044"
---
# <a name="ccmdtarget-class"></a>CCmdTarget (clase)

La clase base para la arquitectura de mapa de mensajes de biblioteca MFC.

## <a name="syntax"></a>Sintaxis

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCmdTarget:: CCmdTarget](#ccmdtarget)|Construye un objeto `CCmdTarget`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCmdTarget:: BeginWaitCursor](#beginwaitcursor)|Muestra el cursor como un cursor de reloj de arena.|
|[CCmdTarget::D oOleVerb](#dooleverb)|Hace que se realice una acción especificada por un verbo OLE.|
|[CCmdTarget:: EnableAutomation](#enableautomation)|Permite la automatización OLE para el objeto `CCmdTarget`.|
|[CCmdTarget:: EnableConnections](#enableconnections)|Habilita la activación de eventos a través de puntos de conexión.|
|[CCmdTarget:: EnableTypeLib](#enabletypelib)|Habilita la biblioteca de tipos de un objeto.|
|[CCmdTarget:: EndWaitCursor](#endwaitcursor)|Vuelve al cursor anterior.|
|[CCmdTarget:: EnumOleVerbs](#enumoleverbs)|Enumera los verbos OLE de un objeto.|
|[CCmdTarget:: FromIDispatch](#fromidispatch)|Devuelve un puntero al objeto `CCmdTarget` asociado al puntero `IDispatch`.|
|[CCmdTarget:: GetDispatchIID](#getdispatchiid)|Obtiene el identificador de la interfaz de envío principal.|
|[CCmdTarget:: GetIDispatch](#getidispatch)|Devuelve un puntero al objeto `IDispatch` asociado al objeto `CCmdTarget`.|
|[CCmdTarget:: GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo que proporciona un objeto.|
|[CCmdTarget:: GetTypeInfoOfGuid](#gettypeinfoofguid)|Recupera la descripción de tipo que se corresponde con el GUID especificado.|
|[CCmdTarget:: GetTypeLib](#gettypelib)|Obtiene un puntero a una biblioteca de tipos.|
|[CCmdTarget:: GetTypeLibCache](#gettypelibcache)|Obtiene la memoria caché de la biblioteca de tipos.|
|[CCmdTarget:: IsInvokeAllowed](#isinvokeallowed)|Habilita la invocación de métodos de automatización.|
|[CCmdTarget:: IsResultExpected](#isresultexpected)|Devuelve un valor distinto de cero si una función de automatización debe devolver un valor.|
|[CCmdTarget:: OnCmdMsg](#oncmdmsg)|Enruta y envía mensajes de comandos.|
|[CCmdTarget:: OnFinalRelease](#onfinalrelease)|Limpia una vez que se libera la última referencia OLE.|
|[CCmdTarget:: RestoreWaitCursor](#restorewaitcursor)|Restaura el cursor de reloj de arena.|

## <a name="remarks"></a>Observaciones

Un mapa de mensajes enruta comandos o mensajes a las funciones miembro que se escriben para controlarlos. (Un comando es un mensaje de un elemento de menú, un botón de comando o una tecla de aceleración).

Las clases de marco de trabajo clave derivadas de `CCmdTarget` incluyen [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)y [CFrameWnd](../../mfc/reference/cframewnd-class.md). Si desea que una clase nueva controle los mensajes, derive la clase de una de estas clases derivadas de `CCmdTarget`. Rara vez derivará una clase de `CCmdTarget` directamente.

Para obtener información general sobre los destinos de comando y `OnCmdMsg` el enrutamiento, vea [destinos](../../mfc/command-targets.md)de comandos, [enrutamiento de comandos](../../mfc/command-routing.md)y mensajes de [asignación](../../mfc/mapping-messages.md).

`CCmdTarget` incluye funciones miembro que controlan la presentación de un cursor de reloj de arena. Muestra el cursor de reloj de arena cuando espera que un comando tome un intervalo de tiempo apreciable para ejecutarse.

Las asignaciones de envío, al igual que los mapas de mensajes, se usan para exponer la funcionalidad de `IDispatch` de automatización OLE. Al exponer esta interfaz, otras aplicaciones (como Visual Basic) pueden llamar a la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="beginwaitcursor"></a>CCmdTarget:: BeginWaitCursor

Llame a esta función para mostrar el cursor como un reloj de arena cuando espera que un comando tome un intervalo de tiempo apreciable para ejecutarse.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función para mostrar el usuario que está ocupado, como cuando un objeto de `CDocument` se carga o se guarda en un archivo.

Las acciones de `BeginWaitCursor` no siempre son efectivas fuera de un único controlador de mensajes, ya que otras acciones, como el control de `OnSetCursor`, podrían cambiar el cursor.

Llame a `EndWaitCursor` para restaurar el cursor anterior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>CCmdTarget:: CCmdTarget

Construye un objeto `CCmdTarget`.

```
CCmdTarget();
```

##  <a name="dooleverb"></a>CCmdTarget::D oOleVerb

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
Puntero a la estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene las coordenadas, en píxeles, que definen el rectángulo delimitador de un objeto en *hwndParent*.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función miembro es básicamente una implementación de [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Las acciones posibles se enumeran mediante [CCmdTarget:: EnumOleVerbs](#enumoleverbs).

##  <a name="enableautomation"></a>CCmdTarget:: EnableAutomation

Llame a esta función para habilitar la automatización OLE para un objeto.

```
void EnableAutomation();
```

### <a name="remarks"></a>Observaciones

Normalmente, se llama a esta función desde el constructor del objeto y solo se debe llamar a si se ha declarado un mapa de envío para la clase. Para obtener más información sobre automatización, vea los artículos [clientes de automatización](../../mfc/automation-clients.md) y [servidores de automatización](../../mfc/automation-servers.md).

##  <a name="enableconnections"></a>CCmdTarget:: EnableConnections

Habilita la activación de eventos a través de puntos de conexión.

```
void EnableConnections();
```

### <a name="remarks"></a>Observaciones

Para habilitar los puntos de conexión, llame a esta función miembro en el constructor de la clase derivada.

##  <a name="enabletypelib"></a>CCmdTarget:: EnableTypeLib

Habilita la biblioteca de tipos de un objeto.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Observaciones

Llame a esta función miembro en el constructor del objeto derivado de `CCmdTarget`si proporciona información de tipo.

##  <a name="endwaitcursor"></a>CCmdTarget:: EndWaitCursor

Llame a esta función después de haber llamado a la función miembro `BeginWaitCursor` para volver del cursor de reloj de arena al cursor anterior.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Observaciones

El marco también llama a esta función miembro después de haber llamado al cursor de reloj de arena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>CCmdTarget:: EnumOleVerbs

Enumera los verbos OLE de un objeto.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Parámetros

*ppenumOleVerb*<br/>
Un puntero a un puntero a una interfaz [IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb) .

### <a name="return-value"></a>Valor devuelto

TRUE si el objeto admite al menos un verbo OLE (en cuyo caso \* *ppenumOleVerb* apunta a una interfaz de enumerador de `IEnumOLEVERB`); en caso contrario, false.

### <a name="remarks"></a>Observaciones

Esta función miembro es básicamente una implementación de [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

##  <a name="fromidispatch"></a>CCmdTarget:: FromIDispatch

Llame a esta función para asignar un puntero `IDispatch`, recibido de las funciones miembro de automatización de una clase, al objeto `CCmdTarget` que implementa las interfaces del objeto `IDispatch`.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Parámetros

*lpDispatch*<br/>
Puntero a un objeto `IDispatch`.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `CCmdTarget` asociado a *lpDispatch*. Esta función devuelve NULL si el objeto `IDispatch` no se reconoce como objeto `IDispatch` de Microsoft Foundation Class.

### <a name="remarks"></a>Observaciones

El resultado de esta función es el inverso de una llamada a la función miembro `GetIDispatch`.

##  <a name="getdispatchiid"></a>CCmdTarget:: GetDispatchIID

Obtiene el identificador de la interfaz de envío principal.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Parámetros

*pIID*<br/>
Un puntero a un identificador de interfaz (un [GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; de lo contrario, FALSE. Si se realiza correctamente, \* *pIID* se establece en el identificador de la interfaz de envío principal.

### <a name="remarks"></a>Observaciones

Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetDispatchIID` devuelve FALSE). Vea [COleControl](../../mfc/reference/colecontrol-class.md).

##  <a name="getidispatch"></a>CCmdTarget:: GetIDispatch

Llame a esta función miembro para recuperar el puntero `IDispatch` desde un método de automatización que devuelva un puntero `IDispatch` o acepte un puntero `IDispatch` por referencia.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Parámetros

*bAddRef*<br/>
Especifica si se va a incrementar el recuento de referencias para el objeto.

### <a name="return-value"></a>Valor devuelto

Puntero `IDispatch` asociado al objeto.

### <a name="remarks"></a>Observaciones

En el caso de los objetos que llaman a `EnableAutomation` en sus constructores, de modo que están habilitados para automatización, esta función devuelve un puntero a la implementación de la clase Foundation de `IDispatch` que usan los clientes que se comunican a través de la interfaz `IDispatch`. Al llamar a esta función, se agrega automáticamente una referencia al puntero, por lo que no es necesario realizar una llamada a [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

##  <a name="gettypeinfocount"></a>CCmdTarget:: GetTypeInfoCount

Recupera el número de interfaces de información de tipo que proporciona un objeto.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Valor devuelto

Número de interfaces de información de tipo.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa básicamente [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Las clases derivadas deben invalidar esta función para devolver el número de interfaces de información de tipo proporcionado (0 o 1). Si no se reemplaza, `GetTypeInfoCount` devuelve 0. Para invalidar, use la macro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , que también implementa `GetTypeLib` y `GetTypeLibCache`.

##  <a name="gettypeinfoofguid"></a>CCmdTarget:: GetTypeInfoOfGuid

Recupera la descripción de tipo que se corresponde con el GUID especificado.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Parámetros

*lcid*<br/>
Identificador de configuración regional (`LCID`).

*guid*<br/>
[GUID](/previous-versions/cc317743(v%3dmsdn.10)) de la descripción de tipo.

*ppTypeInfo*<br/>
Puntero a un puntero a la interfaz `ITypeInfo`.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT que indica si la llamada se ha realizado correctamente o no. Si es correcto, \* *ppTypeInfo* apunta a la interfaz de información de tipos.

##  <a name="gettypelib"></a>CCmdTarget:: GetTypeLib

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
Un puntero a un puntero a la interfaz `ITypeLib`.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT que indica si la llamada se ha realizado correctamente o no. Si es correcto, \* *ppTypeLib* apunta a la interfaz de la biblioteca de tipos.

### <a name="remarks"></a>Observaciones

Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetTypeLib` devuelve TYPE_E_CANTLOADLIBRARY). Use la macro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , que también implementa `GetTypeInfoCount` y `GetTypeLibCache`.

##  <a name="gettypelibcache"></a>CCmdTarget:: GetTypeLibCache

Obtiene la memoria caché de la biblioteca de tipos.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CTypeLibCache` .

### <a name="remarks"></a>Observaciones

Las clases derivadas deben invalidar esta función miembro (si no se reemplaza, `GetTypeLibCache` devuelve NULL). Use la macro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , que también implementa `GetTypeInfoCount` y `GetTypeLib`.

##  <a name="isinvokeallowed"></a>CCmdTarget:: IsInvokeAllowed

La implementación de `IDispatch::Invoke` de MFC llama a esta función para determinar si se puede invocar un método de automatización determinado (identificado por *DISPID*).

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Parámetros

*DISPID*<br/>
IDENTIFICADOR de envío.

### <a name="return-value"></a>Valor devuelto

TRUE si se puede invocar el método; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si `IsInvokeAllowed` devuelve TRUE, `Invoke` continúa llamando al método; de lo contrario, `Invoke` producirá un error y devolverá E_UNEXPECTED.

Las clases derivadas pueden invalidar esta función para devolver los valores adecuados (si no se reemplaza, `IsInvokeAllowed` devuelve TRUE). Vea en particular [COleControl:: IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

##  <a name="isresultexpected"></a>CCmdTarget:: IsResultExpected

Utilice `IsResultExpected` para determinar si un cliente espera un valor devuelto de su llamada a una función de automatización.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si una función de automatización debe devolver un valor. de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La interfaz OLE proporciona información a MFC sobre si el cliente usa u omite el resultado de una llamada de función, y MFC a su vez usa esta información para determinar el resultado de una llamada a `IsResultExpected`. Si la producción de un valor devuelto tiene un uso intensivo de recursos, puede aumentar la eficacia si llama a esta función antes de calcular el valor devuelto.

Esta función devuelve 0 solo una vez para que obtenga los valores devueltos válidos de otras funciones de automatización si los llama desde la función de automatización a la que el cliente ha llamado.

`IsResultExpected` devuelve un valor distinto de cero si se llama cuando una llamada de función de automatización no está en curso.

##  <a name="oncmdmsg"></a>CCmdTarget:: OnCmdMsg

Lo llama el marco de trabajo para enrutar y enviar mensajes de comandos, y para controlar la actualización de los objetos de interfaz de usuario de comandos.

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
Identifica el código de notificación de comandos. Vea la **sección Comentarios** para obtener más información sobre los valores de *nCode*.

*pExtra*<br/>
Se usa según el valor de *nCode*. Vea la **sección Comentarios** para obtener más información sobre *pExtra*.

*pHandlerInfo*<br/>
Si no es NULL, `OnCmdMsg` rellena los miembros *pTarget* y *PMF* de la estructura *pHandlerInfo* en lugar de enviar el comando. Normalmente, este parámetro debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mensaje está controlado; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta es la rutina de implementación principal de la arquitectura de comandos de Framework.

En tiempo de ejecución, `OnCmdMsg` envía un comando a otros objetos o controla el propio comando mediante una llamada a la clase raíz `CCmdTarget::OnCmdMsg`, que realiza la búsqueda de asignación de mensaje real. Para obtener una descripción completa del enrutamiento de comandos predeterminado, vea [temas sobre el control de mensajes y la asignación](../../mfc/message-handling-and-mapping.md).

En raras ocasiones, puede que desee invalidar esta función miembro para extender el enrutamiento de comandos estándar del marco. Consulte la [Nota técnica 21](../../mfc/tn021-command-and-message-routing.md) para obtener información avanzada de la arquitectura de enrutamiento de comandos.

Si invalida `OnCmdMsg`, debe proporcionar el valor adecuado para *nCode*, el código de notificación de comando y *pExtra*, que depende del valor de *nCode*. En la tabla siguiente se muestran los valores correspondientes:

|valor *nCode*|valor *pExtra*|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|\* [COleCmdUI](../../mfc/reference/colecmdui-class.md)|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>CCmdTarget:: OnFinalRelease

Lo llama el marco de trabajo cuando se libera la última referencia OLE a o desde el objeto.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Observaciones

Invalide esta función para proporcionar un control especial para esta situación. La implementación predeterminada elimina el objeto.

##  <a name="restorewaitcursor"></a>CCmdTarget:: RestoreWaitCursor

Llame a esta función para restaurar el cursor de reloj de arena adecuado después de que haya cambiado el cursor del sistema (por ejemplo, después de que un cuadro de mensaje se haya abierto y cerrado en medio de una operación larga).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Consulte también

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
