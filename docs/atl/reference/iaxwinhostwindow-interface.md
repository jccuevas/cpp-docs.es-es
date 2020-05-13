---
title: Interfaz IAxWinHostWindow
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
ms.openlocfilehash: ebecc611660a788ce59bb11beb95bd60eacaf01b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329999"
---
# <a name="iaxwinhostwindow-interface"></a>Interfaz IAxWinHostWindow

Esta interfaz proporciona métodos para manipular un control y su objeto host.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

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
|[CreateControlEx](#createcontrolex)|Crea un control, lo adjunta al objeto host y, opcionalmente, configura un controlador de eventos.|
|[QueryControl](#querycontrol)|Devuelve un puntero de interfaz al control hospedado.|
|[SetExternalDispatch](#setexternaldispatch)|Establece la `IDispatch` interfaz externa.|
|[SetExternalUIHandler](#setexternaluihandler)|Establece la `IDocHostUIHandlerDispatch` interfaz externa.|

## <a name="remarks"></a>Observaciones

Esta interfaz se expone mediante objetos de hospedaje de control ActiveX de ATL. Llame a los métodos de esta interfaz para crear o adjuntar un control al objeto host, para obtener una interfaz de un control hospedado o para establecer la interfaz dispinterface externa o el controlador de interfaz de usuario para su uso al hospedar el explorador web.

## <a name="requirements"></a>Requisitos

La definición de esta interfaz está disponible como IDL o C++, como se muestra a continuación.

|Tipo de definición|Archivo|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (también incluido en ATLBase.h)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Asocia un control existente (y inicializado previamente) al objeto host mediante la ventana identificada por *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*pUnkControl*<br/>
[en] Puntero a `IUnknown` la interfaz del control que se va a adjuntar al objeto host.

*hWnd*<br/>
[en] Identificador de la ventana que se usará para hospedar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Crea un control, lo inicializa y lo hospeda en la ventana identificada por *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parámetros

*lpTricsData*<br/>
[en] Cadena que identifica el control que se va a crear. Puede ser un CLSID (debe incluir las llaves), ProgID, URL o HTML sin formato (prefijado por **MSHTML:**).

*hWnd*<br/>
[en] Identificador de la ventana que se usará para hospedar.

*pStream*<br/>
[en] Puntero de interfaz para una secuencia que contiene datos de inicialización para el control. Puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta ventana será subclase por el objeto host que expone esta interfaz para que los mensajes se pueden reflejar en el control y otras características de contenedor funcionarán.

Llamar a este método equivale a llamar a [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Para crear un control ActiveX con licencia, vea [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada, similar a [IAxWinHostWindow::CreateControl](#createcontrol).

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
[en] Cadena que identifica el control que se va a crear. Puede ser un CLSID (debe incluir las llaves), ProgID, URL o HTML sin formato (prefijado con **MSHTML:**).

*hWnd*<br/>
[en] Identificador de la ventana que se usará para hospedar.

*pStream*<br/>
[en] Puntero de interfaz para una secuencia que contiene datos de inicialización para el control. Puede ser NULL.

*ppUnk*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá la interfaz del control creado. Puede ser NULL.

*riidAdvise*<br/>
[en] Identificador de interfaz de una interfaz saliente en el objeto contenido. Puede ser IID_NULL.

*punkAdvise*<br/>
[en] Puntero a `IUnknown` la interfaz del objeto receptor que se va a conectar `iidSink`al punto de conexión en el objeto contenido especificado por .

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

A `CreateControl` diferencia `CreateControlEx` del método, también permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir eventos desencadenados por el control.

Para crear un control ActiveX con licencia, vea [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Devuelve el puntero de interfaz especificado proporcionado por el control hospedado.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
[en] El identificador de una interfaz en el control que se solicita.

*ppvObject*<br/>
[fuera] La dirección de un puntero que recibirá la interfaz especificada del control creado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Establece el dispinterface externo, que está disponible para los controles contenidos a través de la [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) método.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[en] Un puntero `IDispatch` a una interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Llame a esta función para establecer la interfaz [externa IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) para el `CAxWindow` objeto.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[en] Un puntero `IDocHostUIHandlerDispatch` a una interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función la usan los controles (como el control del explorador `IDocHostUIHandlerDispatch` web) que consultan el sitio del host para la interfaz.

## <a name="see-also"></a>Consulte también

[Interfaz IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
