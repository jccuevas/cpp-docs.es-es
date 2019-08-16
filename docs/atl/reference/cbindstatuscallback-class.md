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
ms.openlocfilehash: 89c65ff034cf7471c379b28116a741b62269a00c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497600"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback (clase)

Esta clase implementa la interfaz `IBindStatusCallback` .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que contiene la función a la que se llamará cuando se reciban los datos.

*nBindFlags*<br/>
Especifica las marcas de enlace devueltas por [GetBindInfo](#getbindinfo). La implementación predeterminada establece que el enlace sea asincrónico, recupera la versión más reciente de los datos/objeto y no almacena los datos recuperados en la memoria caché del disco.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|El constructor.|
|[CBindStatusCallback::~CBindStatusCallback](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Método estático que inicia el proceso de descarga, crea `CBindStatusCallback` un objeto y llama `StartAsyncDownload`a.|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Lo llama el moniker asincrónico para solicitar información sobre el tipo de enlace que se va a crear.|
|[CBindStatusCallback::GetPriority](#getpriority)|Lo llama el moniker asincrónico para obtener la prioridad de la operación de enlace. La implementación de ATL `E_NOTIMPL`devuelve.|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Se llama para proporcionar datos a la aplicación cuando está disponible. Lee los datos y, a continuación, llama a la función que se le ha pasado para usar los datos.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Se llama cuando los recursos son bajos. La implementación de ATL Devuelve S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Llamado por el moniker asincrónico para pasar un puntero de interfaz de objeto a la aplicación. La implementación de ATL Devuelve S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Se llama para indicar el progreso de un proceso de descarga de datos. La implementación de ATL Devuelve S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Se llama cuando se inicia el enlace.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Se llama cuando se detiene la transferencia de datos asincrónica.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Inicializa los bytes disponibles y los bytes leídos en cero, crea un objeto de secuencia de tipo de entrada a partir de `OnDataAvailable` una dirección URL y llama a cada vez que los datos están disponibles.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Número de bytes disponibles para leer.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Número total de bytes leídos.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Puntero a la función a la que se llama cuando los datos están disponibles.|
|[CBindStatusCallback::m_pT](#m_pt)|Puntero al objeto que solicita la transferencia de datos asincrónica.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Puntero a la interfaz [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) para la operación de enlace actual.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Puntero a la `IBinding` interfaz para la operación de enlace actual.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Puntero a la interfaz [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) para la dirección URL que se va a usar.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) para la transferencia de datos.|

## <a name="remarks"></a>Comentarios

La clase `CBindStatusCallback` implementa la interfaz `IBindStatusCallback`. `IBindStatusCallback`debe ser implementada por la aplicación para que pueda recibir notificaciones de una transferencia de datos asincrónica. El moniker asincrónico proporcionado por el sistema `IBindStatusCallback` utiliza métodos para enviar y recibir información acerca de la transferencia de datos asincrónica hacia y desde el objeto.

Normalmente, el `CBindStatusCallback` objeto está asociado a una operación de enlace específica. Por ejemplo, en el ejemplo [Async](../../overview/visual-cpp-samples.md) , al establecer la propiedad URL, se crea un `CBindStatusCallback` objeto en la llamada a: `Download`

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

El moniker asincrónico usa la función `OnData` de devolución de llamada para llamar a la aplicación cuando tiene datos. El moniker asincrónico lo proporciona el sistema.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="cbindstatuscallback"></a>  CBindStatusCallback::CBindStatusCallback

El constructor.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Comentarios

Crea un objeto para recibir notificaciones relativas a la transferencia de datos asincrónica. Normalmente, se crea un objeto para cada operación de enlace.

El constructor también inicializa [m_pT](#m_pt) y [m_pFunc](#m_pfunc) en NULL.

##  <a name="dtor"></a>  CBindStatusCallback::~CBindStatusCallback

Destructor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="download"></a>  CBindStatusCallback::Download

Crea un `CBindStatusCallback` objeto y llama `StartAsyncDownload` a para iniciar la descarga asincrónica de datos de la dirección URL especificada.

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
de Puntero al objeto que solicita la transferencia de datos asincrónica. El `CBindStatusCallback` objeto es hace plantilla en la clase de este objeto.

*pFunc*<br/>
de Puntero a la función que recibe los datos que se leen. La función es un miembro de la clase del objeto de tipo `T`. Consulte [StartAsyncDownload](#startasyncdownload) para ver la sintaxis y un ejemplo.

*bstrURL*<br/>
de Dirección URL de la que se van a obtener datos. Puede ser cualquier dirección URL o nombre de archivo válido. No puede ser nulo. Por ejemplo:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
de `IUnknown` Del contenedor. NULL de forma predeterminada.

*bRelative*<br/>
de Marca que indica si la dirección URL es relativa o absoluta. FALSE de forma predeterminada, lo que significa que la dirección URL es absoluta.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Cada vez que los datos están disponibles, se envía al objeto `OnDataAvailable`a través de. `OnDataAvailable`Lee los datos y llama a la función a la que apunta *pFunc* (por ejemplo, para almacenar los datos o imprimirlos en la pantalla).

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

Se llama para indicar al moniker cómo enlazar.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parámetros

*pgrfBSCF*<br/>
enuncia Un puntero a los valores de enumeración de BINDF que indican cómo debe realizarse la operación de enlace. De forma predeterminada, establezca con los siguientes valores de enumeración:

BINDF_ASYNCHRONOUS descarga asincrónica.

BINDF_ASYNCSTORAGE `OnDataAvailable` devuelve E_PENDING cuando los datos aún no están disponibles en lugar de bloquearse hasta que los datos estén disponibles.

BINDF_GETNEWESTVERSION la operación de enlace debe recuperar la versión más reciente de los datos.

BINDF_NOWRITECACHE la operación de enlace no debe almacenar los datos recuperados en la memoria caché del disco.

*pbindinfo*<br/>
[in, out] Puntero a la `BINDINFO` estructura que aporta más información sobre el modo en que el objeto desea que se produzca el enlace.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

La implementación predeterminada establece que el enlace sea asincrónico y que se use el modelo de introducción de datos. En el modelo de extracción de datos, el moniker controla la operación de enlace asincrónica y notifica continuamente al cliente cada vez que haya nuevos datos disponibles.

##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority

Lo llama el moniker asincrónico para obtener la prioridad de la operación de enlace.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parámetros

*pnPriority*<br/>
enuncia Dirección de la variable **Long** que, si se ejecuta correctamente, recibe la prioridad.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

Se puede utilizar para almacenar el número de bytes disponibles que se van a leer.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Comentarios

Se inicializa en cero en `StartAsyncDownload`.

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

El total acumulado de bytes leídos en la transferencia de datos asincrónica.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Comentarios

Incrementado cada vez `OnDataAvailable` que se llama por el número de bytes leídos realmente. Se inicializa en cero en `StartAsyncDownload`.

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

Llama a la función a `m_pFunc` la que apunta despuésdeleerlosdatosdisponibles(porejemplo,paraalmacenarlosdatosoimprimirlosenlapantalla).`OnDataAvailable`

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Comentarios

La función a la que `m_pFunc` apunta es un miembro de la clase del objeto y tiene la siguiente sintaxis:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

Puntero al objeto que solicita la transferencia de datos asincrónica.

```
T* m_pT;
```

### <a name="remarks"></a>Comentarios

El `CBindStatusCallback` objeto es hace plantilla en la clase de este objeto.

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

Puntero a una interfaz [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) que proporciona acceso al contexto de enlace (un objeto que almacena información sobre una operación de enlace de moniker determinada).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Comentarios

Inicializado en `StartAsyncDownload`.

##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding

Puntero a la `IBinding` interfaz de la operación de enlace actual.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Comentarios

Se inicializa en `OnStartBinding` y se libera `OnStopBinding`en.

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

Puntero a la interfaz [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) para la dirección URL que se va a usar.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Comentarios

Inicializado en `StartAsyncDownload`.

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) de la operación de enlace actual.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Comentarios

Se inicializa en `OnDataAvailable` a partir `STGMEDIUM` de la estructura cuando la marca BCSF es BCSF_FIRSTDATANOTIFICATION y se libera cuando la marca BCSF es BCSF_LASTDATANOTIFICATION.

##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable

Las llamadas `OnDataAvailable` de moniker asincrónicas proporcionadas por el sistema para proporcionar datos al objeto a medida que estén disponibles.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parámetros

*grfBSCF*<br/>
de Valor de enumeración BSCF. Uno o varios de los siguientes: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION o BSCF_LASTDATANOTIFICATION.

*dwSize*<br/>
de Cantidad acumulativa (en bytes) de los datos disponibles desde el principio del enlace. Puede ser cero, lo que indica que la cantidad de datos no es relevante o que no hay ningún importe específico disponible.

*pformatetc*<br/>
de Puntero a la estructura [FORMATETC](/windows/win32/com/the-formatetc-structure) que contiene el formato de los datos disponibles. Si no hay ningún formato, puede ser CF_NULL.

*pstgmed*<br/>
de El puntero a la estructura [STGMEDIUM](/windows/win32/com/the-stgmedium-structure) que contiene los datos reales ahora está disponible.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

`OnDataAvailable`Lee los datos y, a continuación, llama a un método de la clase del objeto (por ejemplo, para almacenar los datos o imprimirlos en la pantalla). Consulte [CBindStatusCallback:: StartAsyncDownload](#startasyncdownload) para obtener más información.

##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource

Se llama cuando los recursos son bajos.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

Llamado por el moniker asincrónico para pasar un puntero de interfaz de objeto a la aplicación.

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
Entero largo sin signo sin usar.

*ulStatusCode*<br/>
Entero largo sin signo. Sin usar.

*szStatusText*<br/>
Dirección de un valor de cadena. Sin usar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding

Establece el miembro de datos [m_spBinding](#m_spbinding) en `IBinding` el puntero de *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
Reservado para un uso futuro.

*pBinding*<br/>
de Dirección de la interfaz IBinding de la operación de enlace actual. No puede ser NULL. El cliente debe llamar a AddRef en este puntero para mantener una referencia al objeto de enlace.

##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding

Libera el `IBinding` puntero en el miembro de datos [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parámetros

*hresult*<br/>
Código de estado devuelto por la operación de enlace.

*szError*<br/>
Dirección de un valor de cadena. Sin usar.

### <a name="remarks"></a>Comentarios

Lo llama el moniker asincrónico proporcionado por el sistema para indicar el final de la operación de enlace.

##  <a name="startasyncdownload"></a>  CBindStatusCallback::StartAsyncDownload

Inicia la descarga de datos de forma asincrónica desde la dirección URL especificada.

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
de Puntero al objeto que solicita la transferencia de datos asincrónica. El `CBindStatusCallback` objeto es hace plantilla en la clase de este objeto.

*pFunc*<br/>
de Puntero a la función que recibe los datos que se están leyendo. La función es un miembro de la clase del objeto de tipo `T`. Vea la **sección Comentarios** para ver la sintaxis y un ejemplo.

*bstrURL*<br/>
de Dirección URL de la que se van a obtener datos. Puede ser cualquier dirección URL o nombre de archivo válido. No puede ser nulo. Por ejemplo:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
de `IUnknown` Del contenedor. NULL de forma predeterminada.

*bRelative*<br/>
de Marca que indica si la dirección URL es relativa o absoluta. FALSE de forma predeterminada, lo que significa que la dirección URL es absoluta.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Cada vez que los datos están disponibles, se envía al objeto `OnDataAvailable`a través de. `OnDataAvailable`Lee los datos y llama a la función a la que apunta *pFunc* (por ejemplo, para almacenar los datos o imprimirlos en la pantalla).

La función a la que apunta *pFunc* es un miembro de la clase del objeto y tiene la siguiente sintaxis:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

En el ejemplo siguiente (tomado del ejemplo [Async](../../overview/visual-cpp-samples.md) ), la función `OnData` escribe los datos recibidos en un cuadro de texto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
