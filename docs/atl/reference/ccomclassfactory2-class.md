---
title: Clase CComClassFactory2
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: 0cb2064cfaea6317c4522ff917f3963fca2219b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321009"
---
# <a name="ccomclassfactory2-class"></a>Clase CComClassFactory2

Esta clase implementa la interfaz [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

## <a name="syntax"></a>Sintaxis

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Parámetros

*Licencia*<br/>
Clase que implementa las siguientes funciones estáticas:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Dada una clave de licencia, crea un objeto del CLSID especificado.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Recupera información que describe las capacidades de licencia de la fábrica de clases.|
|[CComClassFactory2::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Crea y devuelve una clave de licencia.|

## <a name="remarks"></a>Observaciones

`CComClassFactory2`implementa la interfaz [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) que es una extensión de [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`controla la creación de objetos a través de una licencia. Un generador de clases que se ejecuta en un equipo con licencia puede proporcionar una clave de licencia en tiempo de ejecución. Esta clave de licencia permite a una aplicación crear instancias de objetos cuando no existe una licencia de máquina completa.

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la [macro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para `CComClassFactory2`utilizar , especifique la [macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, el parámetro `CComClassFactory2`de plantilla a `VerifyLicenseKey` `GetLicenseKey`, `IsLicenseValid`debe implementar las funciones estáticas , , y . A continuación se muestra un ejemplo de una clase de licencia simple:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`deriva tanto `CComClassFactory2Base` de la *licencia.* `CComClassFactory2Base`, a su vez, deriva de `IClassFactory2` y `CComObjectRootEx< CComGlobalsThreadModel >`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a>CComClassFactory2::CreateInstance

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
[en] Si el objeto se crea como parte de un agregado, *pUnkOuter* debe ser el desconocido externo. De lo contrario, *pUnkOuter* debe ser NULL.

*riid*<br/>
[en] El IID de la interfaz solicitada. Si *pUnkOuter* no es NULL, `IID_IUnknown` *riid* debe ser .

*ppvObj*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Requiere que la máquina tenga licencia completa. Si no existe una licencia de máquina completa, llame a [CreateInstanceLic](#createinstancelic).

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic

Similar a [CreateInstance](#createinstance) `CreateInstanceLic` , excepto que requiere una clave de licencia.

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
[en] Si el objeto se crea como parte de un agregado, *pUnkOuter* debe ser el desconocido externo. De lo contrario, *pUnkOuter* debe ser NULL.

*pUnkReserved*<br/>
[in] No se utiliza. Debe ser NULL.

*riid*<br/>
[en] El IID de la interfaz solicitada. Si *pUnkOuter* no es NULL, `IID_IUnknown` *riid* debe ser .

*bstrKey*<br/>
[en] La clave de licencia en tiempo de `RequestLicKey`ejecución obtenida previamente de una llamada a . Esta clave es necesaria para crear el objeto.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz especificado por *riid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Puede obtener una clave de licencia mediante [RequestLicKey](#requestlickey). Para crear un objeto en una máquina sin licencia, debe llamar a `CreateInstanceLic`.

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

Rellena una estructura [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) con información que describe las capacidades de licencias de la fábrica de clases.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Parámetros

*pLicInfo*<br/>
[fuera] Puntero a `LICINFO` una estructura.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El `fRuntimeKeyAvail` miembro de esta estructura indica si, dada una clave de licencia, el generador de clases permite crear objetos en un equipo sin licencia. El miembro *fLicVerified* indica si existe una licencia de máquina completa.

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a>CComClassFactory2::LockServer

Incrementa y disminuye el recuento de `_Module::Lock` bloqueos del módulo llamando y `_Module::Unlock`, respectivamente.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*Rebaño*<br/>
[en] Si es TRUE, el recuento de bloqueos se incrementa; de lo contrario, el recuento de bloqueos se reduce.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

`_Module`hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o a una clase derivada de ella.

La `LockServer` llamada permite a un cliente aferrarse a un generador de clases para que se puedan crear rápidamente varios objetos.

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a>CComClassFactory2::RequestLicKey

Crea y devuelve una clave `fRuntimeKeyAvail` de licencia, siempre que el miembro de la estructura [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) sea TRUE.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
[in] No se utiliza. Debe ser cero.

*pbstrKey*<br/>
[fuera] Puntero a la clave de licencia.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Se requiere una clave de licencia para llamar a [CreateInstanceLic](#createinstancelic) para crear un objeto en un equipo sin licencia. Si `fRuntimeKeyAvail` es FALSE, los objetos solo se pueden crear en un equipo con licencia completa.

Llame a [GetLicInfo](#getlicinfo) para `fRuntimeKeyAvail`recuperar el valor de .

## <a name="see-also"></a>Consulte también

[Clase CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Clase CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Clase CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
