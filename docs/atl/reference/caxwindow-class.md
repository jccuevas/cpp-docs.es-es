---
title: Clase CAxWindow
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
ms.openlocfilehash: 6f5629370bc1f821dac0a08cc76b5df1450f7a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318718"
---
# <a name="caxwindow-class"></a>Clase CAxWindow

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AttachControl](#attachcontrol)|Asocia un control ActiveX `CAxWindow` existente al objeto.|
|[CAxWindow](#caxwindow)|Construye un objeto `CAxWindow`.|
|[CreateControl](#createcontrol)|Crea un control ActiveX, lo inicializa y `CAxWindow` lo hospeda en la ventana.|
|[CreateControlEx](#createcontrolex)|Crea un control ActiveX y recupera un puntero de interfaz (o punteros) del control.|
|[GetWndClassName](#getwndclassname)|(Estático) Recupera el nombre de clase `CAxWindow` predefinido del objeto.|
|[QueryControl](#querycontrol)|Recupera el `IUnknown` del control ActiveX hospedado.|
|[QueryHost](#queryhost)|Recupera el `IUnknown` puntero `CAxWindow` del objeto.|
|[SetExternalDispatch](#setexternaldispatch)|Establece la interfaz de `CAxWindow` envío externa utilizada por el objeto.|
|[SetExternalUIHandler](#setexternaluihandler)|Establece la `IDocHostUIHandler` interfaz `CAxWindow` externa utilizada por el objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador a la operadora de la red](#operator_eq)|Asigna un HWND a `CAxWindow` un objeto existente.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX. El alojamiento es proporcionado por **"AtlAxWin80",** que está envuelto por `CAxWindow`.

La `CAxWindow` clase se implementa como `CAxWindowT` una especialización de la clase. Esta especialización se declara como:

`typedef CAxWindowT<CWindow> CAxWindow;`

Si necesita cambiar la clase base, `CAxWindowT` puede usar y especificar la nueva clase base como argumento de plantilla.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAxWindow::AttachControl

Crea un nuevo objeto host si aún no está presente y adjunta el control especificado al host.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
[en] Un puntero `IUnknown` a la del control.

*ppUnkContainer*<br/>
[fuera] Un puntero `IUnknown` al host (el `AxWin` objeto).

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El objeto de control que se `AttachControl`va a adjuntar debe inicializarse correctamente antes de llamar a .

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a>CAxWindow::CAxWindow

Construye un `CAxWindow` objeto mediante un identificador de objeto de ventana existente.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de un objeto de ventana existente.

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::CreateControl

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
Puntero a una cadena para crear el control. Debe estar formateado de una de las siguientes maneras:

- Un ProgID como`"MSCAL.Calendar.7"`

- Un CLSID como`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una URL como`"<https://www.microsoft.com>"`

- Una referencia a un documento activo como`"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`debe preceder al fragmento HTML para que se designe como una secuencia MSHTML. Solo se admiten ProgID y CLSID en plataformas Windows Mobile. Las plataformas integradas de Windows CE, que no sean Windows Mobile con soporte para CE IE, admiten todos los tipos, incluidos ProgID, CLSID, URL, referencia al documento activo y fragmento de HTML.

*pStream*<br/>
[en] Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá el contenedor. Puede ser NULL.

*dwResID*<br/>
El identificador de recurso de un recurso HTML. El control WebBrowser se creará y cargará con el recurso especificado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si se utiliza la segunda versión de este método, se crea un control HTML y se enlaza al recurso identificado por *dwResID*.

Este método le da el mismo resultado que llamar:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Consulte [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) para crear, inicializar y hospedar un control ActiveX con licencia.

### <a name="example"></a>Ejemplo

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControl`.

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAxWindow::CreateControlEx

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
Puntero a una cadena para crear el control. Debe estar formateado de una de las siguientes maneras:

- Un ProgID como`"MSCAL.Calendar.7"`

- Un CLSID como`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una URL como`"<https://www.microsoft.com>"`

- Una referencia a un documento activo como`"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`debe preceder al fragmento HTML para que se designe como una secuencia MSHTML. Solo se admiten ProgID y CLSID en plataformas Windows Mobile. Las plataformas integradas de Windows CE, que no sean Windows Mobile con soporte para CE IE, admiten todos los tipos, incluidos ProgID, CLSID, URL, referencia al documento activo y fragmento de HTML.

*pStream*<br/>
[en] Puntero a una secuencia que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá el contenedor. Puede ser NULL.

*ppUnkControl*<br/>
[fuera] La dirección de un puntero `IUnknown` que recibirá el control. Puede ser NULL.

*iidSink*<br/>
[en] Identificador de interfaz de una interfaz saliente en el objeto contenido. Puede ser IID_NULL.

*punkSink*<br/>
[en] Puntero a `IUnknown` la interfaz del objeto receptor que se va a conectar al punto de conexión en el objeto contenido especificado por *iidSink*.

*dwResID*<br/>
[en] El identificador de recurso de un recurso HTML. El control WebBrowser se creará y cargará con el recurso especificado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método es similar a [CAxWindow::CreateControl](#createcontrol) `CreateControlEx` , pero a diferencia de ese método, también permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir eventos desencadenados por el control.

Consulte [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) para crear, inicializar y hospedar un control ActiveX con licencia.

### <a name="example"></a>Ejemplo

Consulte [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControlEx`.

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow::GetWndClassName

Recupera el nombre de la clase de ventana.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena que contiene el nombre de la clase de ventana que puede hospedar controles ActiveX sin licencia.

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::operador ?

Asigna un HWND a `CAxWindow` un objeto existente.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de una ventana existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto `CAxWindow` actual.

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a>CAxWindow::QueryControl

Recupera la interfaz especificada del control hospedado.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] Especifica el IID de la interfaz del control.

*ppUnk*<br/>
[fuera] Un puntero a la interfaz del control. En la versión de plantilla de este método, no hay necesidad de un identificador de referencia siempre y cuando se pase una interfaz con tipo con un UUID asociado.

*Q*<br/>
[en] La interfaz que se está consultando.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a>CAxWindow::QueryHost

Devuelve la interfaz especificada del host.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] Especifica el IID de la interfaz del control.

*ppUnk*<br/>
[fuera] Un puntero a la interfaz en el host. En la versión de plantilla de este método, no hay necesidad de un identificador de referencia siempre y cuando se pase una interfaz con tipo con un UUID asociado.

*Q*<br/>
[en] La interfaz que se está consultando.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La interfaz del host permite el acceso a la funcionalidad subyacente `AxWin`del código de hospedaje de ventana, implementado por .

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Establece la interfaz `CAxWindow` de envío externa para el objeto.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
[en] Un puntero `IDispatch` a una interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Establece la interfaz [externa IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) para el `CAxWindow` objeto.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parámetros

*pUIHandler*<br/>
[en] Un puntero `IDocHostUIHandlerDispatch` a una interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La `IDocHostUIHandlerDispatch` interfaz externa la usan los controles que `IDocHostUIHandlerDispatch` consultan el sitio del host para la interfaz. El control WebBrowser es un control que hace esto.

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLCON](../../overview/visual-cpp-samples.md)<br/>
[Clase CWindow](../../atl/reference/cwindow-class.md)<br/>
[Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Preguntas más frecuentes sobre contención de controles](../../atl/atl-control-containment-faq.md)
