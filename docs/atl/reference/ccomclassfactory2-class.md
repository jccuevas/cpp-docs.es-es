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
ms.openlocfilehash: e34ebffc937c3e4ef1272fdf13ddcde7513d28e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497458"
---
# <a name="ccomclassfactory2-class"></a>Clase CComClassFactory2

Esta clase implementa la interfaz [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .

## <a name="syntax"></a>Sintaxis

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Parámetros

*license*<br/>
Una clase que implementa las siguientes funciones estáticas:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Dada una clave de licencia, crea un objeto del CLSID especificado.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Recupera información que describe las capacidades de licencia del generador de clases.|
|[CComClassFactory2::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Crea y devuelve una clave de licencia.|

## <a name="remarks"></a>Comentarios

`CComClassFactory2`implementa la interfaz [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) , que es una extensión de [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`controla la creación de objetos a través de una licencia. Un generador de clases que se ejecute en una máquina con licencia puede proporcionar una clave de licencia en tiempo de ejecución. Esta clave de licencia permite a una aplicación crear instancias de objetos cuando no existe una licencia completa de la máquina.

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para usar `CComClassFactory2`, especifique la macro [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, el parámetro de plantilla `CComClassFactory2`en, debe implementar las funciones `VerifyLicenseKey`estáticas, `IsLicenseValid` `GetLicenseKey`y. A continuación se facilita un ejemplo de una clase de licencia simple:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`deriva de `CComClassFactory2Base` y de la *licencia*. `CComClassFactory2Base`, a su vez, se deriva `IClassFactory2` de `CComObjectRootEx< CComGlobalsThreadModel >`y.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
de Si el objeto se crea como parte de un agregado, *pUnkOuter* debe ser el desconocido externo. De lo contrario, *pUnkOuter* debe ser null.

*riid*<br/>
de IID de la interfaz solicitada. Si *pUnkOuter* no es null, *riid* debe ser `IID_IUnknown`.

*ppvObj*<br/>
enuncia Puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Requiere que el equipo tenga una licencia completa. Si no existe una licencia completa de equipo, llame a [CreateInstanceLic](#createinstancelic).

##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic

Similar a [CreateInstance](#createinstance), salvo que `CreateInstanceLic` requiere una clave de licencia.

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
de Si el objeto se crea como parte de un agregado, *pUnkOuter* debe ser el desconocido externo. De lo contrario, *pUnkOuter* debe ser null.

*pUnkReserved*<br/>
de No se usa. Debe ser NULL.

*riid*<br/>
de IID de la interfaz solicitada. Si *pUnkOuter* no es null, *riid* debe ser `IID_IUnknown`.

*bstrKey*<br/>
de La clave de licencia en tiempo de ejecución obtenida previamente a `RequestLicKey`partir de una llamada a. Esta clave es necesaria para crear el objeto.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz especificado por *riid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Puede obtener una clave de licencia mediante [RequestLicKey](#requestlickey). Para crear un objeto en un equipo sin licencia, debe llamar a `CreateInstanceLic`.

##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo

Rellena una estructura [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) con información que describe las capacidades de licencia del generador de clases.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Parámetros

*pLicInfo*<br/>
enuncia Puntero a una `LICINFO` estructura.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El `fRuntimeKeyAvail` miembro de esta estructura indica si, dada una clave de licencia, el generador de clases permite crear objetos en una máquina sin licencia. El miembro *fLicVerified* indica si existe una licencia de equipo completo.

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

Incrementa y disminuye el recuento de bloqueos del módulo `_Module::Lock` mediante `_Module::Unlock`una llamada a y, respectivamente.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*fLock*<br/>
de Si es TRUE, el recuento de bloqueos se incrementa; de lo contrario, se reduce el recuento de bloqueos.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`_Module`hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o a una clase derivada de ella.

La `LockServer` llamada a permite a un cliente mantener en un generador de clases para que se puedan crear rápidamente varios objetos.

##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey

Crea y devuelve una clave de licencia, siempre que `fRuntimeKeyAvail` el miembro de la estructura [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) sea true.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Parámetros

*dwReserved*<br/>
de No se usa. Debe ser cero.

*pbstrKey*<br/>
enuncia Puntero a la clave de licencia.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Se requiere una clave de licencia para llamar a [CreateInstanceLic](#createinstancelic) con el fin de crear un objeto en una máquina sin licencia. Si `fRuntimeKeyAvail` es false, los objetos solo se pueden crear en un equipo con licencia completa.

Llame a [GetLicInfo](#getlicinfo) para recuperar el valor `fRuntimeKeyAvail`de.

## <a name="see-also"></a>Vea también

[CComClassFactoryAutoThread (clase)](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton (clase)](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
