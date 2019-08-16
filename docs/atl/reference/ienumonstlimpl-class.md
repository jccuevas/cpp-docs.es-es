---
title: Clase IEnumOnSTLImpl
ms.date: 11/04/2016
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
ms.openlocfilehash: 7cf777f3ff0d298f224157735a06bf57a2c10cf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495857"
---
# <a name="ienumonstlimpl-class"></a>Clase IEnumOnSTLImpl

Esta clase define una interfaz de enumerador basada C++ en una colección de biblioteca estándar.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parámetros

*Básica*<br/>
Un enumerador COM. Vea [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Puntero al identificador de interfaz de la interfaz del enumerador.

*T*<br/>
Tipo de elemento expuesto por la interfaz del enumerador.

*Copy*<br/>
Una [clase de directiva de copia](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Clase C++ contenedora de la biblioteca estándar.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|Implementación de **Clone**.|
|[IEnumOnSTLImpl::Init](#init)|Inicializa el enumerador.|
|[IEnumOnSTLImpl::Next](#next)|Implementación de **Next**.|
|[IEnumOnSTLImpl::Reset](#reset)|La implementación de **RESET**.|
|[IEnumOnSTLImpl::Skip](#skip)|Implementación de **SKIP**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterador que representa la posición actual del enumerador dentro de la colección.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Puntero al contenedor de C++ la biblioteca estándar que contiene los elementos que se van a enumerar.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown` Puntero del objeto que proporciona la colección.|

## <a name="remarks"></a>Comentarios

`IEnumOnSTLImpl`proporciona la implementación de una interfaz de enumerador COM en la que los elementos que se van C++ a enumerar se almacenan en un contenedor compatible con la biblioteca estándar. Esta clase es análoga a la clase [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) , que proporciona una implementación para una interfaz de enumerador basada en una matriz.

> [!NOTE]
>  Vea [CComEnumImpl:: init](../../atl/reference/ccomenumimpl-class.md#init) para obtener más información sobre las `CComEnumImpl` diferencias `IEnumOnSTLImpl`entre y.

Normalmente, *no* necesitará crear su propia clase de enumerador derivando de esta implementación de interfaz. Si desea usar un enumerador proporcionado por ATL basado en un C++ contenedor de biblioteca estándar, es más común crear una instancia de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)o crear una clase de colección que devuelva un enumerador mediante la derivación de [ICollectionOnSTLImpl ](../../atl/reference/icollectiononstlimpl-class.md).

Sin embargo, si necesita proporcionar un enumerador personalizado (por ejemplo, uno que exponga interfaces además de la interfaz del enumerador), puede derivar de esta clase. En esta situación, es probable que deba invalidar el método [Clone](#clone) para proporcionar su propia implementación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="init"></a>  IEnumOnSTLImpl::Init

Inicializa el enumerador.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parámetros

*pUnkForRelease*<br/>
de `IUnknown` Puntero de un objeto que debe mantenerse activo mientras dure el enumerador. Pase NULL si no existe tal objeto.

*collection*<br/>
Referencia al contenedor de C++ la biblioteca estándar que contiene los elementos que se van a enumerar.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si pasa `Init` una referencia a una colección contenida en otro objeto, puede usar el parámetro *pUnkForRelease* para asegurarse de que el objeto y la colección que contiene están disponibles mientras el enumerador lo necesite.

Debe llamar a este método antes de pasar un puntero a la interfaz del enumerador de nuevo a los clientes.

##  <a name="clone"></a>  IEnumOnSTLImpl::Clone

Este método proporciona la implementación del método **Clone** mediante la creación de un objeto de `CComEnumOnSTL`tipo, su inicialización con la misma colección y el iterador que usa el objeto actual, y la devolución de la interfaz en el objeto recién creado.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parámetros

*ppEnum*<br/>
enuncia La interfaz del enumerador en un objeto recién creado clonado desde el enumerador actual.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk

`IUnknown` Puntero del objeto que proporciona la colección.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Comentarios

Este puntero inteligente mantiene una referencia en el objeto pasado a [IEnumOnSTLImpl:: init](#init), asegurándose de que permanece activo durante la vigencia del enumerador.

##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection

Este miembro apunta a la colección que proporciona los datos que impulsan la implementación de la interfaz del enumerador.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Comentarios

Este miembro se inicializa mediante una llamada a [IEnumOnSTLImpl:: init](#init).

##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter

Este miembro contiene el iterador que se usa para marcar la posición actual dentro de la colección y navegar a los elementos siguientes.

```
CollType::iterator m_iter;
```

##  <a name="next"></a>  IEnumOnSTLImpl::Next

Este método proporciona la implementación del método **siguiente** .

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
de Número de elementos solicitados.

*rgelt*<br/>
enuncia Matriz que se va a rellenar con los elementos.

*pceltFetched*<br/>
enuncia Número de elementos devueltos realmente en *rgelt*. Puede ser menor que *Celt* si permanecen menos de *Celt* elementos en la lista.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="reset"></a>  IEnumOnSTLImpl::Reset

Este método proporciona la implementación del método **RESET** .

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="skip"></a>  IEnumOnSTLImpl::Skip

Este método proporciona la implementación del método **SKIP** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
de Número de elementos que se van a omitir.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
