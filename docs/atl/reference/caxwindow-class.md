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
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423391"
---
# <a name="caxwindow-class"></a>CAxWindow (clase)

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AttachControl](#attachcontrol)|Asocia un control ActiveX existente al objeto `CAxWindow`.|
|[CAxWindow](#caxwindow)|Construye un objeto `CAxWindow`.|
|[CreateControl](#createcontrol)|Crea un control ActiveX, lo inicializa y lo hospeda en la ventana `CAxWindow`.|
|[CreateControlEx](#createcontrolex)|Crea un control ActiveX y recupera un puntero de interfaz (o punteros) del control.|
|[GetWndClassName](#getwndclassname)|Estático Recupera el nombre de clase predefinido del objeto `CAxWindow`.|
|[Consulta](#querycontrol)|Recupera el `IUnknown` del control ActiveX hospedado.|
|[QueryHost](#queryhost)|Recupera el puntero `IUnknown` del objeto `CAxWindow`.|
|[SetExternalDispatch](#setexternaldispatch)|Establece la interfaz de envío externa utilizada por el objeto `CAxWindow`.|
|[SetExternalUIHandler](#setexternaluihandler)|Establece la interfaz de `IDocHostUIHandler` externa utilizada por el objeto `CAxWindow`.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#operator_eq)|Asigna un HWND a un objeto de `CAxWindow` existente.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX. El hospedaje lo proporciona " **AtlAxWin80"** , que se ajusta mediante `CAxWindow`.

La clase `CAxWindow` se implementa como una especialización de la clase `CAxWindowT`. Esta especialización se declara como:

`typedef CAxWindowT<CWindow> CAxWindow;`

Si necesita cambiar la clase base, puede usar `CAxWindowT` y especificar la nueva clase base como un argumento de plantilla.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="attachcontrol"></a>CAxWindow:: AttachControl

Crea un nuevo objeto host si aún no existe uno y asocia el control especificado al host.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Parámetros

*pControl*<br/>
de Puntero al `IUnknown` del control.

*ppUnkContainer*<br/>
enuncia Puntero al `IUnknown` del host (el objeto `AxWin`).

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El objeto de control que se va a adjuntar debe inicializarse correctamente antes de llamar a `AttachControl`.

##  <a name="caxwindow"></a>CAxWindow:: CAxWindow

Construye un objeto `CAxWindow` mediante un identificador de objeto de ventana existente.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de un objeto de ventana existente.

##  <a name="createcontrol"></a>CAxWindow:: CreateControl

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
Puntero a una cadena para crear el control. Debe tener el formato de una de las siguientes maneras:

- Un ProgID como `"MSCAL.Calendar.7"`

- Un CLSID como `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una dirección URL como `"<https://www.microsoft.com>"`

- Referencia a un documento activo como `"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` debe preceder al fragmento HTML para que se designe como una secuencia de MSHTML. En las plataformas Windows Mobile solo se admiten ProgID y CLSID. Windows CE plataformas incrustadas, a excepción de Windows Mobile, compatible con CE IE admiten todos los tipos, incluidos ProgID, CLSID, URL, referencia al documento activo y fragmento de HTML.

*pStream*<br/>
de Un puntero a un flujo que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
enuncia La dirección de un puntero que recibirá el `IUnknown` del contenedor. Puede ser NULL.

*dwResID*<br/>
El identificador de recurso de un recurso HTML. El control WebBrowser se creará y cargará con el recurso especificado.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si se usa la segunda versión de este método, se crea un control HTML y se enlaza al recurso identificado por *dwResID*.

Este método proporciona el mismo resultado que llamar a:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Vea [CAxWindow2T:: CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) para crear, inicializar y hospedar un control ActiveX con licencia.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante la AxHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControl`.

##  <a name="createcontrolex"></a>CAxWindow:: CreateControlEx

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
Puntero a una cadena para crear el control. Debe tener el formato de una de las siguientes maneras:

- Un ProgID como `"MSCAL.Calendar.7"`

- Un CLSID como `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Una dirección URL como `"<https://www.microsoft.com>"`

- Referencia a un documento activo como `"file://\\\Documents\MyDoc.doc"`

- Un fragmento de HTML como `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` debe preceder al fragmento HTML para que se designe como una secuencia de MSHTML. En las plataformas Windows Mobile solo se admiten ProgID y CLSID. Windows CE plataformas incrustadas, a excepción de Windows Mobile, compatible con CE IE admiten todos los tipos, incluidos ProgID, CLSID, URL, referencia al documento activo y fragmento de HTML.

*pStream*<br/>
de Un puntero a un flujo que se utiliza para inicializar las propiedades del control. Puede ser NULL.

*ppUnkContainer*<br/>
enuncia La dirección de un puntero que recibirá el `IUnknown` del contenedor. Puede ser NULL.

*ppUnkControl*<br/>
enuncia Dirección de un puntero que recibirá el `IUnknown` del control. Puede ser NULL.

*iidSink*<br/>
de Identificador de interfaz de una interfaz de salida en el objeto contenido. Se puede IID_NULL.

*punkSink*<br/>
de Puntero a la interfaz `IUnknown` del objeto receptor que se va a conectar al punto de conexión en el objeto contenido especificado por *iidSink*.

*dwResID*<br/>
de El identificador de recurso de un recurso HTML. El control WebBrowser se creará y cargará con el recurso especificado.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método es similar a [CAxWindow:: CreateControl](#createcontrol), pero a diferencia de ese método, `CreateControlEx` también le permite recibir un puntero de interfaz al control recién creado y configurar un receptor de eventos para recibir los eventos desencadenados por el control.

Vea [CAxWindow2T:: CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) para crear, inicializar y hospedar un control ActiveX con licencia.

### <a name="example"></a>Ejemplo

Vea [hospedar controles ActiveX mediante la AxHost de ATL](../../atl/hosting-activex-controls-using-atl-axhost.md) para obtener un ejemplo que usa `CreateControlEx`.

##  <a name="getwndclassname"></a>CAxWindow:: GetWndClassName

Recupera el nombre de la clase de ventana.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena que contiene el nombre de la clase de ventana que puede hospedar controles ActiveX sin licencia.

##  <a name="operator_eq"></a>CAxWindow:: Operator =

Asigna un HWND a un objeto de `CAxWindow` existente.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
Identificador de una ventana existente.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al objeto `CAxWindow` actual.

##  <a name="querycontrol"></a>CAxWindow:: consulta

Recupera la interfaz especificada del control hospedado.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de Especifica el IID de la interfaz del control.

*ppUnk*<br/>
enuncia Puntero a la interfaz del control. En la versión de plantilla de este método, no es necesario un identificador de referencia siempre que se pase una interfaz con tipo con un UUID asociado.

*Q*<br/>
de La interfaz que se consulta.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="queryhost"></a>CAxWindow:: QueryHost

Devuelve la interfaz especificada del host.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de Especifica el IID de la interfaz del control.

*ppUnk*<br/>
enuncia Puntero a la interfaz en el host. En la versión de plantilla de este método, no es necesario un identificador de referencia siempre que se pase una interfaz con tipo con un UUID asociado.

*Q*<br/>
de La interfaz que se consulta.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La interfaz del host permite el acceso a la funcionalidad subyacente del código de hospedaje de ventana, implementada por `AxWin`.

##  <a name="setexternaldispatch"></a>CAxWindow:: SetExternalDispatch

Establece la interfaz de envío externa para el objeto `CAxWindow`.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
de Puntero a una interfaz de `IDispatch`.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="setexternaluihandler"></a>CAxWindow:: SetExternalUIHandler

Establece la interfaz [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) externa para el objeto `CAxWindow`.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Parámetros

*pUIHandler*<br/>
de Puntero a una interfaz de `IDocHostUIHandlerDispatch`.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

La interfaz de `IDocHostUIHandlerDispatch` externa la usan los controles que consultan el sitio del host para la interfaz de `IDocHostUIHandlerDispatch`. El control WebBrowser es un control que lo hace.

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLCON](../../overview/visual-cpp-samples.md)<br/>
[CWindow (clase)](../../atl/reference/cwindow-class.md)<br/>
[Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Preguntas más frecuentes sobre contención de controles](../../atl/atl-control-containment-faq.md)
