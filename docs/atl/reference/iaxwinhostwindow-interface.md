---
title: IAxWinHostWindow (interfaz)
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: 1e389dc253f24eed2fee7e1d552be931a23f5e3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637325"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow (interfaz)

Esta interfaz proporciona métodos para manipular un control y su objeto de host.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AttachControl](#attachcontrol)|Asocia un control existente al objeto host.|
|[CreateControl](#createcontrol)|Crea un control y lo adjunta al objeto host.|
|[CreateControlEx](#createcontrolex)|Crea un control, lo asocia al objeto host y, opcionalmente, configura un controlador de eventos.|
|[QueryControl](#querycontrol)|Devuelve un puntero de interfaz al control hospedado.|
|[SetExternalDispatch](#setexternaldispatch)|Establece la externa `IDispatch` interfaz.|
|[SetExternalUIHandler](#setexternaluihandler)|Establece la externa `IDocHostUIHandlerDispatch` interfaz.|

## <a name="remarks"></a>Comentarios

Esta interfaz se expone mediante los objetos que hospeda los controles ActiveX de ATL. Llamar a los métodos en esta interfaz para crear o asociar un control para el objeto de host, para obtener una interfaz de un control hospedado, o para establecer la dispinterface externo o un controlador de interfaz de usuario para su uso cuando se hospedan en el explorador Web.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible como IDL o C++, como se muestra a continuación.

|Tipo de definición|Archivo|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (que también se incluye en ATLBase.h)|

##  <a name="attachcontrol"></a>  IAxWinHostWindow:: AttachControl

Asocia un control existente (e inicializado anteriormente) al objeto host mediante la ventana identificada por *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*pUnkControl*<br/>
[in] Un puntero a la `IUnknown` interfaz del control que se adjuntará al objeto host.

*hWnd*<br/>
[in] Identificador de la ventana que se usará para hospedar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Crea un control, lo inicializa y lo hospeda en la ventana identificada por *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*lpTricsData*<br/>
[in] Cadena que identifica el control que se va a crear. Puede ser un CLSID (incluidas las llaves), ProgID, dirección URL o HTML sin formato (precedida por **MSHTML:**).

*hWnd*<br/>
[in] Identificador de la ventana que se usará para hospedar.

*pStream*<br/>
[in] Un puntero de interfaz para una secuencia que contiene los datos de inicialización para el control. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto host exponer esta interfaz para que los mensajes se pueden reflejar en el control y otras características del contenedor funcionará se pueden crear subclases de esta ventana.

Llamar a este método equivale a llamar a [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Para crear un control ActiveX con licencia, consulte [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Parámetros

*lpTricsData*<br/>
[in] Cadena que identifica el control que se va a crear. Puede ser un CLSID (incluidas las llaves), ProgID, dirección URL o HTML sin formato (con el prefijo **MSHTML:**).

*hWnd*<br/>
[in] Identificador de la ventana que se usará para hospedar.

*pStream*<br/>
[in] Un puntero de interfaz para una secuencia que contiene los datos de inicialización para el control. Puede ser NULL.

*ppUnk*<br/>
[out] La dirección de un puntero que va a recibir el `IUnknown` interfaz del control creado. Puede ser NULL.

*riidAdvise*<br/>
[in] Identificador de interfaz de una interfaz de salida en el objeto contenido. Puede ser IID_NULL.

*punkAdvise*<br/>
[in] Un puntero a la `IUnknown` interfaz del objeto receptor para estar conectado al punto de conexión en el objeto contenido especificado por `iidSink`.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

A diferencia de la `CreateControl` método `CreateControlEx` también permite recibir un puntero de interfaz al control recién creado y configurado un receptor de eventos para recibir eventos desencadenados por el control.

Para crear un control ActiveX con licencia, consulte [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Devuelve el puntero de interfaz especificado proporcionado por el control hospedado.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
[in] El identificador de una interfaz en el control que se solicita.

*ppvObject*<br/>
[out] La dirección de un puntero que va a recibir la interfaz especificada del control creado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Establece la interfaz dispinterface externa, que está disponible para los controles contenidos a través de la [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) método.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[in] Un puntero a un `IDispatch` interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Llame a esta función para establecer la externa [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfaz para el `CAxWindow` objeto.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[in] Un puntero a un `IDocHostUIHandlerDispatch` interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Esta función se usa los controles (por ejemplo, el control del explorador Web) que consulta el sitio del host para el `IDocHostUIHandlerDispatch` interfaz.

## <a name="see-also"></a>Vea también

[IAxWinAmbientDispatch (interfaz)](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow:: QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

