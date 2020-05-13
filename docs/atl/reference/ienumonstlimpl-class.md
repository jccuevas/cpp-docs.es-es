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
ms.openlocfilehash: 2fbe6ccfbea2836c42a054da7ea9ebeac4e1555d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329711"
---
# <a name="ienumonstlimpl-class"></a>Clase IEnumOnSTLImpl

Esta clase define una interfaz de enumerador basada en una colección de biblioteca estándar de C++.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
Un enumerador COM. Consulte [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Un puntero al identificador de interfaz de la interfaz del enumerador.

*T*<br/>
El tipo de elemento expuesto por la interfaz del enumerador.

*Copiar*<br/>
Una clase de política de [copia](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Una clase contenedora de biblioteca estándar C++ .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|La implementación de **Clone**.|
|[IEnumOnSTLImpl::Init](#init)|Inicializa el enumerador.|
|[IEnumOnSTLImpl::Siguiente](#next)|La implementación de **Next**.|
|[IEnumOnSTLImpl::Reset](#reset)|La implementación de **Reset**.|
|[IEnumOnSTLImpl::Skip](#skip)|La implementación de **Skip**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterador que representa la posición actual del enumerador dentro de la colección.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Puntero al contenedor de la biblioteca estándar de C++ que contiene los elementos que se van a enumerar.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|Puntero `IUnknown` del objeto que proporciona la colección.|

## <a name="remarks"></a>Observaciones

`IEnumOnSTLImpl`proporciona la implementación de una interfaz de enumerador COM donde los elementos que se enumeran se almacenan en un contenedor compatible con la biblioteca estándar de C++. Esta clase es análoga a la [Clase CComEnumImpl,](../../atl/reference/ccomenumimpl-class.md) que proporciona una implementación para una interfaz de enumerador basada en una matriz.

> [!NOTE]
> Consulte [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) para obtener más `CComEnumImpl` `IEnumOnSTLImpl`información sobre las diferencias adicionales entre y .

Normalmente, *no* necesitará crear su propia clase de enumerador derivando de esta implementación de interfaz. Si desea utilizar un enumerador proporcionado por ATL basado en un contenedor de biblioteca estándar C++, es más común crear una instancia de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)o crear una clase de colección que devuelva un enumerador derivando de [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).

Sin embargo, si necesita proporcionar un enumerador personalizado (por ejemplo, uno que expone interfaces además de la interfaz del enumerador), puede derivar de esta clase. En esta situación, es probable que tenga que invalidar el método [Clone](#clone) para proporcionar su propia implementación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ienumonstlimplinit"></a><a name="init"></a>IEnumOnSTLImpl::Init

Inicializa el enumerador.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parámetros

*pUnkForRelease*<br/>
[en] Puntero `IUnknown` de un objeto que se debe mantener activo durante la duración del enumerador. Pase NULL si no existe tal objeto.

*Colección*<br/>
Una referencia al contenedor de la biblioteca estándar de C++ que contiene los elementos que se van a enumerar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si pasa `Init` una referencia a una colección retenida en otro objeto, puede usar el parámetro *pUnkForRelease* para asegurarse de que el objeto y la colección que contiene están disponibles durante el tiempo que el enumerador lo necesite.

Debe llamar a este método antes de pasar un puntero a la interfaz del enumerador a cualquier cliente.

## <a name="ienumonstlimplclone"></a><a name="clone"></a>IEnumOnSTLImpl::Clone

Este método proporciona la **Clone** implementación de la `CComEnumOnSTL`Clone método mediante la creación de un objeto de tipo , inicializándolo con la misma colección e iterador utilizado por el objeto actual y devolviendo la interfaz en el objeto recién creado.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parámetros

*ppEnum*<br/>
[fuera] La interfaz del enumerador en un objeto recién creado clonado desde el enumerador actual.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ienumonstlimplm_spunk"></a><a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk

Puntero `IUnknown` del objeto que proporciona la colección.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Observaciones

Este puntero inteligente mantiene una referencia en el objeto pasado a [IEnumOnSTLImpl::Init](#init), asegurándose de que permanece activo durante la duración del enumerador.

## <a name="ienumonstlimplm_pcollection"></a><a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection

Este miembro apunta a la colección que proporciona los datos que impulsan la implementación de la interfaz de enumerador.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Observaciones

Este miembro se inicializa mediante una llamada a [IEnumOnSTLImpl::Init](#init).

## <a name="ienumonstlimplm_iter"></a><a name="m_iter"></a>IEnumOnSTLImpl::m_iter

Este miembro contiene el iterador utilizado para marcar la posición actual dentro de la colección y navegar a los elementos posteriores.

```
CollType::iterator m_iter;
```

## <a name="ienumonstlimplnext"></a><a name="next"></a>IEnumOnSTLImpl::Siguiente

Este método proporciona la implementación de la **Next** método.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[en] El número de elementos solicitados.

*rgelt*<br/>
[fuera] Matriz que se va a rellenar con los elementos.

*pceltFetched*<br/>
[fuera] El número de elementos devueltos realmente en *rgelt*. Esto puede ser menor que *celt* si quedan menos de elementos *celt* en la lista.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ienumonstlimplreset"></a><a name="reset"></a>IEnumOnSTLImpl::Reset

Este método proporciona la implementación de la **Reset** método.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ienumonstlimplskip"></a><a name="skip"></a>IEnumOnSTLImpl::Skip

Este método proporciona la implementación de la **Skip** método.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[en] El número de elementos que se deben omitir.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
