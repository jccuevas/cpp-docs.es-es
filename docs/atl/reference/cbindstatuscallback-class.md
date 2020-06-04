---
title: Clase CBindStatusCallback
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 0ae7f4fcdba18be84d99140e395b6f2ac3db792a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748199"
---
# <a name="cbindstatuscallback-class"></a>Clase CBindStatusCallback

Esta clase implementa la interfaz `IBindStatusCallback`.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que contiene la función a la que se llamará a medida que se reciban los datos.

*nBindFlags*<br/>
Especifica los indicadores de enlace devueltos por [GetBindInfo](#getbindinfo). La implementación predeterminada establece el enlace como asincrónico, recupera la versión más reciente de los datos/objetos y no almacena los datos recuperados en la memoria caché del disco.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|El constructor.|
|[CBindStatusCallback::-CBindStatusCallback](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Método estático que inicia el `CBindStatusCallback` proceso de `StartAsyncDownload`descarga, crea un objeto y llama a .|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Llamado por el moniker asincrónico para solicitar información sobre el tipo de enlace que se va a crear.|
|[CBindStatusCallback::GetPriority](#getpriority)|Llamado por el moniker asincrónico para obtener la prioridad de la operación de enlace. La implementación `E_NOTIMPL`de ATL devuelve .|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a la aplicación a medida que esté disponible. Lee los datos y, a continuación, llama a la función que se le pasa para usar los datos.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Se llama cuando los recursos son bajos. La implementación de ATL devuelve S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Llamado por el moniker asincrónico para pasar un puntero de interfaz de objeto a la aplicación. La implementación de ATL devuelve S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Se llama para indicar el progreso de un proceso de descarga de datos. La implementación de ATL devuelve S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Se llama cuando se inicia el enlace.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia de datos asincrónica.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicializa los bytes disponibles y los bytes leídos en cero, crea `OnDataAvailable` un objeto de secuencia de tipo push a partir de una dirección URL y llama cada vez que los datos están disponibles.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Número de bytes disponibles para leer.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Número total de bytes leídos.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Puntero a la función a la que se llama cuando los datos están disponibles.|
|[CBindStatusCallback::m_pT](#m_pt)|Puntero al objeto que solicita la transferencia de datos asincrónica.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Puntero a la interfaz [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) para la operación de enlace actual.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Puntero a `IBinding` la interfaz para la operación de enlace actual.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Puntero a la interfaz [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) para que se use la dirección URL.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) para la transferencia de datos.|

## <a name="remarks"></a>Observaciones

La clase `CBindStatusCallback` implementa la interfaz `IBindStatusCallback`. `IBindStatusCallback`la aplicación debe implementarla para que pueda recibir notificaciones de una transferencia de datos asincrónica. El moniker asincrónico `IBindStatusCallback` proporcionado por el sistema utiliza métodos para enviar y recibir información sobre la transferencia de datos asincrónica hacia y desde el objeto.

Normalmente, `CBindStatusCallback` el objeto está asociado a una operación de enlace específica. Por ejemplo, en el ejemplo [ASYNC,](../../overview/visual-cpp-samples.md) cuando se `CBindStatusCallback` establece la propiedad `Download`URL, se crea un objeto en la llamada a:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

El moniker asincrónico `OnData` utiliza la función de devolución de llamada para llamar a la aplicación cuando tiene datos. El sistema proporciona el moniker asincrónico.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

El constructor.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Observaciones

Crea un objeto para recibir notificaciones relativas a la transferencia asincrónica de datos. Normalmente, se crea un objeto para cada operación de enlace.

El constructor también inicializa [m_pT](#m_pt) y [m_pFunc](#m_pfunc) en NULL.

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a>CBindStatusCallback::-CBindStatusCallback

Destructor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a>CBindStatusCallback::Download

Crea `CBindStatusCallback` un objeto `StartAsyncDownload` y llama para iniciar la descarga de datos de forma asincrónica desde la dirección URL especificada.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
[en] Puntero al objeto que solicita la transferencia de datos asincrónica. El `CBindStatusCallback` objeto se templatiza en la clase de este objeto.

*pFunc*<br/>
[en] Puntero a la función que recibe los datos que se leen. La función es un miembro de `T`la clase de tipo del objeto. Consulte [StartAsyncDownload](#startasyncdownload) para ver la sintaxis y un ejemplo.

*bstrURL*<br/>
[en] La dirección URL de la que se obtendrán datos. Puede ser cualquier URL o nombre de archivo válido. No puede ser NULL. Por ejemplo:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[en] El `IUnknown` del contenedor. NULL de forma predeterminada.

*bRelativo*<br/>
[en] Marca que indica si la dirección URL es relativa o absoluta. FALSE de forma predeterminada, lo que significa que la dirección URL es absoluta.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Cada vez que los datos están `OnDataAvailable`disponibles se envían al objeto a través de . `OnDataAvailable`lee los datos y llama a la función señalada por *pFunc* (por ejemplo, para almacenar los datos o imprimirlos en la pantalla).

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a>CBindStatusCallback::GetBindInfo

Llamé para decirle al apodo cómo atar.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parámetros

*pgrfBSCF*<br/>
[fuera] Puntero a valores de enumeración BINDF que indica cómo debe producirse la operación de enlace. De forma predeterminada, establezca con los siguientes valores de enumeración:

BINDF_ASYNCHRONOUS descarga asincrónica.

BINDF_ASYNCSTORAGE `OnDataAvailable` devuelve E_PENDING cuando los datos aún no están disponibles en lugar de bloquearse hasta que los datos estén disponibles.

BINDF_GETNEWESTVERSION La operación de enlace debe recuperar la versión más reciente de los datos.

BINDF_NOWRITECACHE La operación de enlace no debe almacenar los datos recuperados en la memoria caché del disco.

*pbindinfo*<br/>
[adentro, fuera] Puntero a `BINDINFO` la estructura que proporciona más información sobre cómo el objeto desea que se produzca el enlace.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

La implementación predeterminada establece el enlace para que sea asincrónico y para usar el modelo de inserción de datos. En el modelo de inserción de datos, el moniker controla la operación de enlace asincrónica y notifica continuamente al cliente cada vez que hay nuevos datos disponibles.

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a>CBindStatusCallback::GetPriority

Llamado por el moniker asincrónico para obtener la prioridad de la operación de enlace.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parámetros

*pnPriority*<br/>
[fuera] Dirección de la variable **LONG** que, en caso de éxito, recibe la prioridad.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

Se puede utilizar para almacenar el número de bytes disponibles para leer.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Observaciones

Inicializado a `StartAsyncDownload`cero en .

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead

El total acumulado de bytes leídos en la transferencia de datos asincrónica.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Observaciones

Incrementado `OnDataAvailable` cada vez es llamado por el número de bytes realmente leídos. Inicializado a `StartAsyncDownload`cero en .

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

La función `m_pFunc` a la `OnDataAvailable` que apunta se llama después de leer los datos disponibles (por ejemplo, para almacenar los datos o imprimirlos en la pantalla).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Observaciones

La función `m_pFunc` a la que apunta es un miembro de la clase del objeto y tiene la sintaxis siguiente:

```cpp
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a>CBindStatusCallback::m_pT

Puntero al objeto que solicita la transferencia de datos asincrónica.

```
T* m_pT;
```

### <a name="remarks"></a>Observaciones

El `CBindStatusCallback` objeto se templatiza en la clase de este objeto.

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx

Puntero a una interfaz [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) que proporciona acceso al contexto de enlace (un objeto que almacena información sobre una operación de enlace de moniker determinada).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Observaciones

Inicializado `StartAsyncDownload`en .

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

Un puntero `IBinding` a la interfaz de la operación de enlace actual.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Observaciones

Inicializado `OnStartBinding` y liberado `OnStopBinding`en .

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

Un puntero a la interfaz [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) para que la dirección URL se use.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Observaciones

Inicializado `StartAsyncDownload`en .

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a>CBindStatusCallback::m_spStream

Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) de la operación de enlace actual.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Observaciones

Inicializado `OnDataAvailable` desde `STGMEDIUM` la estructura cuando el indicador BCSF se BCSF_FIRSTDATANOTIFICATION y se libera cuando se BCSF_LASTDATANOTIFICATION el indicador BCSF.

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a>CBindStatusCallback::OnDataAvailable

El moniker asincrónico `OnDataAvailable` proporcionado por el sistema llama para proporcionar datos al objeto a medida que esté disponible.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parámetros

*grfBSCF*<br/>
[en] Un valor de enumeración BSCF. Uno o más de los siguientes: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION o BSCF_LASTDATANOTIFICATION.

*dwSize*<br/>
[en] La cantidad acumulada (en bytes) de datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante o que no se ha disponible ninguna cantidad específica.

*pformatetc*<br/>
[en] Puntero a la estructura [FORMATETC](/windows/win32/com/the-formatetc-structure) que contiene el formato de los datos disponibles. Si no hay ningún formato, se puede CF_NULL.

*pstgmed*<br/>
[en] Puntero a la estructura [STGMEDIUM](/windows/win32/com/the-stgmedium-structure) que contiene los datos reales ahora disponibles.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

`OnDataAvailable`lee los datos y, a continuación, llama a un método de la clase del objeto (por ejemplo, para almacenar los datos o imprimirlos en la pantalla). Consulte [CBindStatusCallback::StartAsyncDownload](#startasyncdownload) para obtener más información.

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a>CBindStatusCallback::OnLowResource

Se llama cuando los recursos son bajos.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable

Llamado por el moniker asincrónico para pasar un puntero de interfaz de objeto a la aplicación.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Identificador de interfaz de la interfaz solicitada. Sin usar.

*Punk*<br/>
Dirección de la interfaz IUnknown. Sin usar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a>CBindStatusCallback::OnProgress

Se llama para indicar el progreso de un proceso de descarga de datos.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parámetros

*ulProgress*<br/>
Entero largo sin signo. Sin usar.

*ulProgressMax*<br/>
Entero largo sin signo Sin usar.

*ulStatusCode*<br/>
Entero largo sin signo. Sin usar.

*szStatusText*<br/>
Dirección de un valor de cadena. Sin usar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding

Establece el [m_spBinding](#m_spbinding) de `IBinding` miembro de datos en el puntero en *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado para uso futuro.

*pBinding*<br/>
[en] Dirección de la interfaz IBinding de la operación de enlace actual. Esto no puede ser NULL. El cliente debe llamar a AddRef en este puntero para mantener una referencia al objeto de enlace.

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding

Libera `IBinding` el puntero en el miembro de datos [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parámetros

*Hresult*<br/>
Código de estado devuelto por la operación de enlace.

*szError*<br/>
Dirección de un valor de cadena. Sin usar.

### <a name="remarks"></a>Observaciones

Llamado por el moniker asincrónico proporcionado por el sistema para indicar el final de la operación de enlace.

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

Comienza a descargar datos de forma asincrónica desde la dirección URL especificada.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
[en] Puntero al objeto que solicita la transferencia de datos asincrónica. El `CBindStatusCallback` objeto se templatiza en la clase de este objeto.

*pFunc*<br/>
[en] Puntero a la función que recibe los datos que se leen. La función es un miembro de `T`la clase de tipo del objeto. Consulte **Comentarios** para ver la sintaxis y un ejemplo.

*bstrURL*<br/>
[en] La dirección URL de la que se obtendrán datos. Puede ser cualquier URL o nombre de archivo válido. No puede ser NULL. Por ejemplo:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[en] El `IUnknown` del contenedor. NULL de forma predeterminada.

*bRelativo*<br/>
[en] Marca que indica si la dirección URL es relativa o absoluta. FALSE de forma predeterminada, lo que significa que la dirección URL es absoluta.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Cada vez que los datos están `OnDataAvailable`disponibles se envían al objeto a través de . `OnDataAvailable`lee los datos y llama a la función señalada por *pFunc* (por ejemplo, para almacenar los datos o imprimirlos en la pantalla).

La función señalada por *pFunc* es un miembro de la clase del objeto y tiene la sintaxis siguiente:

```cpp
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

En el ejemplo siguiente (tomado del `OnData` ejemplo [ASYNC),](../../overview/visual-cpp-samples.md) la función escribe los datos recibidos en un cuadro de texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
