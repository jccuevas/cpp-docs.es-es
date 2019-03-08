---
title: CBindStatusCallback (clase)
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
ms.openlocfilehash: e8c8d3f170803a792ca2ea8c7a37a18fd2cebd48
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259209"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback (clase)

Esta clase implementa la interfaz `IBindStatusCallback` .

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que contiene la función que se llamará cuando se reciben los datos.

*nBindFlags*<br/>
Especifica las marcas de enlace que se devuelven por [GetBindInfo](#getbindinfo). La implementación predeterminada establece el enlace sea asincrónico, recupera la versión más reciente de que el objeto de datos y no almacena los datos recuperados en la caché de disco.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|El constructor.|
|[CBindStatusCallback::~CBindStatusCallback](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Método estático que se inicia el proceso de descarga, se crea un `CBindStatusCallback` objeto y llama a `StartAsyncDownload`.|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Lo llama el moniker asincrónico para solicitar información sobre el tipo de enlace que se va a crear.|
|[CBindStatusCallback::GetPriority](#getpriority)|Lo llama el moniker asincrónico para obtener la prioridad de la operación de enlace. Devuelve la implementación de ATL `E_NOTIMPL`.|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a la aplicación cuando se encuentre disponible. Lee los datos y, a continuación, llama a la función que se pasa para usar los datos.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Se llama cuando hay pocos recursos. La implementación de ATL devuelve S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Lo llama el moniker asincrónico para pasar un puntero de interfaz de objeto a la aplicación. La implementación de ATL devuelve S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Se llama para indicar el progreso de un proceso de descarga de datos. La implementación de ATL devuelve S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Se llama cuando se inicia el enlace.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia de datos asincrónica.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicializa los bytes disponibles y los bytes leídos en cero, se crea un objeto de secuencia de tipo de inserción desde una dirección URL y las llamadas `OnDataAvailable` cada vez que los datos están disponibles.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Número de bytes disponibles para su lectura.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Número total de bytes leídos.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Puntero a la función se llama cuando hay datos disponibles.|
|[CBindStatusCallback::m_pT](#m_pt)|Puntero al objeto que solicita la transferencia de datos asincrónica.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Puntero a la [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) interfaz para la operación de enlace actual.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Puntero a la `IBinding` interfaz para la operación de enlace actual.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Puntero a la [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) interfaz para la dirección URL.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Puntero a la [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfaz para la transferencia de datos.|

## <a name="remarks"></a>Comentarios

La clase `CBindStatusCallback` implementa la interfaz `IBindStatusCallback`. `IBindStatusCallback` se debe implementar la aplicación para que puedan recibir notificaciones de una transferencia de datos asincrónica. El moniker asincrónico proporcionado por el sistema usa `IBindStatusCallback` métodos para enviar y recibir información sobre los datos asincrónicos se transfieren hacia y desde el objeto.

Normalmente, el `CBindStatusCallback` objeto está asociado a una operación de enlace específica. Por ejemplo, en el [ASYNC](../../visual-cpp-samples.md) ejemplo, al establecer la propiedad de dirección URL, crea un `CBindStatusCallback` objeto en la llamada a `Download`:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

El moniker asincrónico usa la función de devolución de llamada `OnData` para llamar a la aplicación cuando tiene datos. El moniker asincrónico proporcionado por el sistema.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="cbindstatuscallback"></a>  CBindStatusCallback::CBindStatusCallback

El constructor.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Comentarios

Crea un objeto para recibir las notificaciones relativas a la transferencia de datos asincrónica. Normalmente, se crea un objeto para cada operación de enlace.

El constructor inicializa también [m_pT](#m_pt) y [m_pFunc](#m_pfunc) en NULL.

##  <a name="dtor"></a>  CBindStatusCallback::~CBindStatusCallback

Destructor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="download"></a>  CBindStatusCallback::Download

Crea un `CBindStatusCallback` objeto y llama a `StartAsyncDownload` para comenzar a descargar datos de forma asincrónica desde la dirección URL especificada.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parámetros

*pT*<br/>
[in] Un puntero al objeto que solicita la transferencia de datos asincrónica. La `CBindStatusCallback` objeto se hace plantilla en la clase de este objeto.

*pFunc*<br/>
[in] Un puntero a la función que recibe los datos que se leen. La función es un miembro de clase del objeto de tipo `T`. Consulte [StartAsyncDownload](#startasyncdownload) de sintaxis y ejemplos.

*bstrURL*<br/>
[in] La dirección URL para obtener datos de. Puede ser cualquier nombre de archivo o dirección URL válida. No puede ser nulo. Por ejemplo:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] El `IUnknown` del contenedor. NULL de forma predeterminada.

*bRelative*<br/>
[in] Una marca que indica si la dirección URL es relativa o absoluta. FALSE de forma predeterminada, lo que significa que la dirección URL es absoluta.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Cada vez que hay datos se envía al objeto mediante `OnDataAvailable`. `OnDataAvailable` lee los datos y llama a la función señalada por *pFunc* (por ejemplo, para almacenar los datos o imprimirlo en la pantalla).

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

Se llama para indicar el moniker enlazado.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parámetros

*pgrfBSCF*<br/>
[out] Un puntero a los valores de enumeración BINDF que indica cómo debe tener lugar la operación de enlace. De forma predeterminada, establecer con los valores de enumeración siguientes:

Descarga BINDF_ASYNCHRONOUS asincrónica.

BINDF_ASYNCSTORAGE `OnDataAvailable` devuelve E_PENDING cuando los datos aún no están disponibles en lugar de bloquearse hasta que haya datos disponibles.

BINDF_GETNEWESTVERSION la operación de enlace debe recuperar la versión más reciente de los datos.

BINDF_NOWRITECACHE la operación de enlace no debe almacenar recuperar datos en la caché de disco.

*pbindinfo*<br/>
[in, out] Un puntero a la `BINDINFO` estructura que proporciona más información acerca de cómo desea que el objeto de enlace que se produzca.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación predeterminada establece el enlace sea asincrónico y utilizar el modelo de inserción de datos. En el modelo de inserción de datos, el moniker controla la operación de enlace asincrónica y continuamente notifica al cliente cada vez que hay nuevos datos disponibles.

##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority

Lo llama el moniker asincrónico para obtener la prioridad de la operación de enlace.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parámetros

*pnPriority*<br/>
[out] Dirección de la **largo** variable que, si se ejecuta correctamente, recibe la prioridad.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

Puede usarse para almacenar el número de bytes disponibles para su lectura.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Comentarios

Inicializado en cero en `StartAsyncDownload`.

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

El total acumulado de bytes de lectura en la transferencia de datos asincrónica.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Comentarios

Incrementa cada vez que `OnDataAvailable` es llamado por el número de bytes leídos realmente. Inicializado en cero en `StartAsyncDownload`.

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

La función señalada por `m_pFunc` llama a `OnDataAvailable` después de leer los datos disponibles (por ejemplo, para almacenar los datos o imprimirlo en la pantalla).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Comentarios

La función señalada por `m_pFunc` es un miembro de la clase del objeto y tiene la siguiente sintaxis:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

Un puntero al objeto que solicita la transferencia de datos asincrónica.

```
T* m_pT;
```

### <a name="remarks"></a>Comentarios

La `CBindStatusCallback` objeto se hace plantilla en la clase de este objeto.

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

Un puntero a un [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) interfaz que proporciona acceso al contexto de enlace (un objeto que almacena información sobre una operación de enlace de moniker determinado).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Comentarios

Inicializado en `StartAsyncDownload`.

##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding

Un puntero a la `IBinding` interfaz de la operación de enlace actual.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Comentarios

Inicializado en `OnStartBinding` y se lanzan en `OnStopBinding`.

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

Un puntero a la [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) interfaz para la dirección URL.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Comentarios

Inicializado en `StartAsyncDownload`.

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

Un puntero a la [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfaz de la operación de enlace actual.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Comentarios

Inicializado en `OnDataAvailable` desde el `STGMEDIUM` estructura cuando la marca BCSF es BCSF_FIRSTDATANOTIFICATION y se libera cuando la marca BCSF es BCSF_LASTDATANOTIFICATION.

##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable

Las llamadas de moniker asincrónico proporcionado por el sistema `OnDataAvailable` para proporcionar datos al objeto cuando se encuentre disponible.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parámetros

*grfBSCF*<br/>
[in] Un valor de enumeración BSCF. Uno o varios de los siguientes: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION o BSCF_LASTDATANOTIFICATION.

*dwSize*<br/>
[in] La cantidad acumulada (en bytes) de datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante o que ninguna cantidad específica, empezó a estar disponible.

*pformatetc*<br/>
[in] Puntero a la [FORMATETC](/windows/desktop/com/the-formatetc-structure) estructura que contiene el formato de los datos disponibles. Si no hay ningún formato, puede ser CF_NULL.

*pstgmed*<br/>
[in] Puntero a la [STGMEDIUM](/windows/desktop/com/the-stgmedium-structure) estructura que contiene los datos reales que ya está disponibles.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

`OnDataAvailable` lee los datos y, a continuación, llama a un método de clase del objeto (por ejemplo, para almacenar los datos o imprimirlo en la pantalla). Consulte [StartAsyncDownload](#startasyncdownload) para obtener más información.

##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource

Se llama cuando hay pocos recursos.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

Lo llama el moniker asincrónico para pasar un puntero de interfaz de objeto a la aplicación.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Identificador de interfaz de la interfaz solicitada. Sin usar.

*punk*<br/>
Dirección de la interfaz IUnknown. Sin usar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

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
Entero largo sin signo no utilizado.

*ulStatusCode*<br/>
Entero largo sin signo. Sin usar.

*szStatusText*<br/>
Dirección de un valor de cadena. Sin usar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding

Establece el miembro de datos [m_spBinding](#m_spbinding) a la `IBinding` puntero en *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado para un uso futuro.

*pBinding*<br/>
[in] La operación de enlace de la dirección de la interfaz IBinding del elemento actual. No puede ser NULL. El cliente debe llamar a AddRef en este puntero para mantener una referencia al objeto de enlace.

##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding

Las versiones del `IBinding` puntero en el miembro de datos [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parámetros

*hresult*<br/>
Devuelve el código de estado de la operación de enlace.

*szError*<br/>
Dirección de un valor de cadena. Sin usar.

### <a name="remarks"></a>Comentarios

Lo llama el moniker asincrónico proporcionado por el sistema para indicar el final de la operación de enlace.

##  <a name="startasyncdownload"></a>  CBindStatusCallback::StartAsyncDownload

Inicia la descarga datos asincrónicamente desde la dirección URL especificada.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parámetros

*pT*<br/>
[in] Un puntero al objeto que solicita la transferencia de datos asincrónica. La `CBindStatusCallback` objeto se hace plantilla en la clase de este objeto.

*pFunc*<br/>
[in] Un puntero a la función que recibe los datos que se va a leer. La función es un miembro de clase del objeto de tipo `T`. Consulte **comentarios** de sintaxis y ejemplos.

*bstrURL*<br/>
[in] La dirección URL para obtener datos de. Puede ser cualquier nombre de archivo o dirección URL válida. No puede ser nulo. Por ejemplo:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] El `IUnknown` del contenedor. NULL de forma predeterminada.

*bRelative*<br/>
[in] Una marca que indica si la dirección URL es relativa o absoluta. FALSE de forma predeterminada, lo que significa que la dirección URL es absoluta.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Cada vez que hay datos se envía al objeto mediante `OnDataAvailable`. `OnDataAvailable` lee los datos y llama a la función señalada por *pFunc* (por ejemplo, para almacenar los datos o imprimirlo en la pantalla).

La función señalada por *pFunc* es un miembro de la clase del objeto y tiene la siguiente sintaxis:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

En el ejemplo siguiente (procedente del [ASYNC](../../visual-cpp-samples.md) ejemplo), la función `OnData` escribe los datos recibidos en un cuadro de texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
