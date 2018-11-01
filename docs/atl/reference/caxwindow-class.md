---
title: CAxWindow (clase)
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6e8ebad0f99e086387bf9946323a2c1ef864f391
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523816"
---
# <a name="caxwindow-class"></a>CAxWindow (clase)

Esta clase proporciona métodos para manipular una ventana de hospedar un control ActiveX.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AttachControl](#attachcontrol)|Asocia un control ActiveX existente a la `CAxWindow` objeto.|
|[CAxWindow](#caxwindow)|Construye un objeto `CAxWindow`.|
|[CreateControl](#createcontrol)|Crea un control ActiveX, lo inicializa y lo hospeda en el `CAxWindow` ventana.|
|[CreateControlEx](#createcontrolex)|Crea un control ActiveX y recupera un puntero de interfaz (o punteros) del control.|
|[GetWndClassName](#getwndclassname)|(Estático) Recupera el nombre de clase predefinido la `CAxWindow` objeto.|
|[QueryControl](#querycontrol)|Recupera el `IUnknown` del control ActiveX hospedado.|
|[QueryHost](#queryhost)|Recupera el `IUnknown` puntero de la `CAxWindow` objeto.|
|[SetExternalDispatch](#setexternaldispatch)|Establece la interfaz de envío externo utilizada por el `CAxWindow` objeto.|
|[SetExternalUIHandler](#setexternaluihandler)|Establece la externa `IDocHostUIHandler` interfaz utilizada por el `CAxWindow` objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#operator_eq)|Asigna un HWND para existente `CAxWindow` objeto.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX. El proceso de hospedaje proporcionado por " **AtlAxWin80"**, que es ajustado por `CAxWindow`.

Clase `CAxWindow` se implementa como una especialización de la `CAxWindowT` clase. Esta especialización se declara como:

`typedef CAxWindowT<CWindow> CAxWindow;`

Si necesita cambiar la clase base, puede usar `CAxWindowT` y especifique la nueva clase base como un argumento de plantilla.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="attachcontrol"></a>  CAxWindow::AttachControl

Crea un nuevo objeto de host si uno no está presente y el control especificado asocia al host.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
[in] Un puntero a la `IUnknown` del control.

*ppUnkContainer*<br/>
[out] Un puntero a la `IUnknown` del host (el `AxWin` objeto).

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto de control que se va a asociar debe inicializarse correctamente antes de llamar a `AttachControl`.

##  <a name="caxwindow"></a>  CAxWindow::CAxWindow

Construye un `CAxWindow` objeto utilizando un identificador de objeto de ventana existente.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de un objeto de ventana existente.

##  <a name="createcontrol"></a>  CAxWindow::CreateControl

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una cadena para crear el control. Debe tener el formato de una de las maneras siguientes:

- Un identificador de programa, como "MSCAL. Calendar.7 "

- CLSID, como "{8E27C92B-1264-101C-8A2F-040224009C02}"

- Una dirección URL como "http://www.microsoft.com"

- Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"

- Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\</cuerpo >\</HTML >"

   > [!NOTE]
   > "MSHTML:" debe preceder el fragmento de HTML para que se designa como un flujo de MSHTML. Solo los ProgID y CLSID se admiten en plataformas Windows Mobile. Plataformas de Windows CE insertadas, que no sean de Windows Mobile con el soporte técnico de soporte técnico de IE CE todos los tipos incluidos ProgID, CLSID, URL, hacer referencia al documento activo y el fragmento de HTML.

*pStream*<br/>
[in] Un puntero a una secuencia que se usa para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
[out] La dirección de un puntero que va a recibir el `IUnknown` del contenedor. Puede ser NULL.

*dwResID*<br/>
El identificador de recurso de un recurso HTML. El control WebBrowser se creará y se cargan con el recurso especificado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si se usa la segunda versión de este método, se crea y se enlaza al recurso identificado por un control HTML *dwResID*.

Este método le ofrece el mismo resultado que la llamada:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Consulte [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) para crear, inicializar y hospedar un control ActiveX con licencia.

### <a name="example"></a>Ejemplo

Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControl`.

##  <a name="createcontrolex"></a>  CAxWindow::CreateControlEx

Crea un control ActiveX, lo inicializa y lo hospeda en la ventana especificada.

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una cadena para crear el control. Debe tener el formato de una de las maneras siguientes:

- Un identificador de programa, como "MSCAL. Calendar.7 "

- CLSID, como "{8E27C92B-1264-101C-8A2F-040224009C02}"

- Una dirección URL como "http://www.microsoft.com"

- Una referencia a un documento activo como "file://\\\Documents\MyDoc.doc"

- Un fragmento de HTML, como "MSHTML:\<HTML >\<cuerpo > se trata de una línea de texto\</cuerpo >\</HTML >"

   > [!NOTE]
   > "MSHTML:" debe preceder el fragmento de HTML para que se designa como un flujo de MSHTML. Solo los ProgID y CLSID se admiten en plataformas Windows Mobile. Plataformas de Windows CE insertadas, que no sean de Windows Mobile con el soporte técnico de soporte técnico de IE CE todos los tipos incluidos ProgID, CLSID, URL, hacer referencia al documento activo y el fragmento de HTML.

*pStream*<br/>
[in] Un puntero a una secuencia que se usa para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
[out] La dirección de un puntero que va a recibir el `IUnknown` del contenedor. Puede ser NULL.

*ppUnkControl*<br/>
[out] La dirección de un puntero que va a recibir el `IUnknown` del control. Puede ser NULL.

*iidSink*<br/>
[in] Identificador de interfaz de una interfaz de salida en el objeto contenido. Puede ser IID_NULL.

*punkSink*<br/>
[in] Un puntero a la `IUnknown` interfaz del objeto receptor para estar conectado al punto de conexión en el objeto contenido especificado por *iidSink*.

*dwResID*<br/>
[in] El identificador de recurso de un recurso HTML. El control WebBrowser se creará y se cargan con el recurso especificado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Este método es similar a [CAxWindow::CreateControl](#createcontrol), pero a diferencia de ese método, `CreateControlEx` también permite recibir un puntero de interfaz al control recién creado y configurado un receptor de eventos para recibir eventos desencadenados por el control.

Consulte [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) para crear, inicializar y hospedar un control ActiveX con licencia.

### <a name="example"></a>Ejemplo

Consulte [hospeda controles de ActiveX mediante AXHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControlEx`.

##  <a name="getwndclassname"></a>  CAxWindow::GetWndClassName

Recupera el nombre de la clase de ventana.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a una cadena que contiene el nombre de la clase de ventana que puede hospedar controles ActiveX sin licencia.

##  <a name="operator_eq"></a>  CAxWindow::operator =

Asigna un HWND para existente `CAxWindow` objeto.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de una ventana existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto `CAxWindow` actual.

##  <a name="querycontrol"></a>  :: QueryControl

Recupera la interfaz especificada del control hospedado.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parámetros

*IID*<br/>
[in] Especifica el IID de la interfaz del control.

*ppUnk*<br/>
[out] Un puntero a la interfaz del control. En la versión de la plantilla de este método, no hay ninguna necesidad de un Id. de referencia, siempre se pasa una interfaz con tipo con un UUID asociado.

*Q*<br/>
[in] La interfaz que se está consultando para.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="queryhost"></a>  CAxWindow:: QueryHost

Devuelve la interfaz del host especificada.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parámetros

*IID*<br/>
[in] Especifica el IID de la interfaz del control.

*ppUnk*<br/>
[out] Un puntero a la interfaz en el host. En la versión de la plantilla de este método, no hay ninguna necesidad de un Id. de referencia, siempre se pasa una interfaz con tipo con un UUID asociado.

*Q*<br/>
[in] La interfaz que se está consultando para.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

La interfaz del host permite el acceso a la funcionalidad subyacente del código de ventana que hospeda, implementado por `AxWin`.

##  <a name="setexternaldispatch"></a>  CAxWindow::SetExternalDispatch

Establece la interfaz de envío externo la `CAxWindow` objeto.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[in] Un puntero a un `IDispatch` interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="setexternaluihandler"></a>  CAxWindow::SetExternalUIHandler

Establece la externa [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interfaz para el `CAxWindow` objeto.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parámetros

*pUIHandler*<br/>
[in] Un puntero a un `IDocHostUIHandlerDispatch` interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Externo `IDocHostUIHandlerDispatch` interfaz se usa los controles que consultar el sitio del host para el `IDocHostUIHandlerDispatch` interfaz. El control WebBrowser es un control que lo haga.

## <a name="see-also"></a>Vea también

[Ejemplo ATLCON](../../visual-cpp-samples.md)<br/>
[CWindow (clase)](../../atl/reference/cwindow-class.md)<br/>
[Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Preguntas más frecuentes sobre la contención de controles](../../atl/atl-control-containment-faq.md)

