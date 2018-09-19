---
title: IEnumOnSTLImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0abc7e3b87ef23e6350b54c3f64b50fbcfdd5b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031150"
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl (clase)

Esta clase define una interfaz de enumerador basándose en una colección de la biblioteca estándar de C++.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parámetros

*base*<br/>
Un enumerador COM. Consulte [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Un puntero al identificador de interfaz de la interfaz de enumerador.

*T*<br/>
El tipo de elemento que expone la interfaz de enumerador.

*Copiar*<br/>
Un [Copiar directiva clase](../../atl/atl-copy-policy-classes.md).

*CollType*<br/>
Una clase de contenedor de la biblioteca estándar de C++.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|La implementación de **clon**.|
|[IEnumOnSTLImpl::Init](#init)|Inicializa el enumerador.|
|[IEnumOnSTLImpl::Next](#next)|La implementación de **siguiente**.|
|[IEnumOnSTLImpl::Reset](#reset)|La implementación de **restablecer**.|
|[IEnumOnSTLImpl::Skip](#skip)|La implementación de **Skip**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterador que representa la posición del enumerador actual dentro de la colección.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Un puntero para el contenedor de la biblioteca estándar de C++ que contiene los elementos que hay que enumerar.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|El `IUnknown` puntero del objeto que proporciona la colección.|

## <a name="remarks"></a>Comentarios

`IEnumOnSTLImpl` proporciona la implementación de una interfaz de enumerador COM donde se almacenan los elementos que se va a enumerar en un contenedor de la biblioteca estándar de C++ compatible. Esta clase es análoga a la [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) (clase), que proporciona una implementación de una interfaz de enumerador se basa en una matriz.

> [!NOTE]
>  Consulte [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) para obtener más información sobre aún más diferencias entre `CComEnumImpl` y `IEnumOnSTLImpl`.

Por lo general, usted podrá *no* debe crear su propia clase de enumerador derivando de esta implementación de la interfaz. Si desea usar un enumerador proporcionada por ATL basándose en un contenedor de la biblioteca estándar de C++, es más habitual para crear una instancia de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), o para crear una clase de colección que devuelve un enumerador mediante la derivación de [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).

Sin embargo, si tiene que proporcionar un enumerador personalizado (por ejemplo, uno que expone interfaces además de la interfaz de enumerador), puede derivar de esta clase. En esta situación es probable que deba reemplazar el [clon](#clone) método para proporcionar su propia implementación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="init"></a>  IEnumOnSTLImpl::Init

Inicializa el enumerador.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parámetros

*pUnkForRelease*<br/>
[in] El `IUnknown` puntero de un objeto que se debe mantener activo durante la vigencia del enumerador. Pasar valor NULL si no existe el objeto existe.

*collection*<br/>
Una referencia al contenedor de biblioteca estándar de C++ que contiene los elementos que hay que enumerar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si se pasa `Init` mantiene una referencia a una colección en otro objeto, puede usar el *pUnkForRelease* parámetro para asegurarse de que está disponible para el objeto y la colección contiene, siempre y cuando lo necesite el enumerador.

Debe llamar a este método antes de pasar un puntero a la interfaz del enumerador a los clientes.

##  <a name="clone"></a>  IEnumOnSTLImpl::Clone

Este método proporciona la implementación de la **clon** método mediante la creación de un objeto de tipo `CComEnumOnSTL`, inicializándola con la misma colección e iterador utilizados por el objeto actual y devuelve la interfaz en la recién objeto creado.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parámetros

*ppEnum*<br/>
[out] La interfaz de enumerador en un objeto recién creado clona el enumerador actual.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk

El `IUnknown` puntero del objeto que proporciona la colección.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Comentarios

Este puntero inteligente mantiene una referencia en el objeto pasado a [IEnumOnSTLImpl::Init](#init), lo que garantiza que permanece activo durante la vigencia del enumerador.

##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection

Este miembro apunta a la colección que proporciona los datos que dirigen la implementación de la interfaz de enumerador.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Comentarios

Este miembro se inicializa mediante una llamada a [IEnumOnSTLImpl::Init](#init).

##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter

Este miembro contiene el iterador que se usan para marcar la posición actual dentro de la colección y navegar por los elementos subsiguientes.

```
CollType::iterator m_iter;
```

##  <a name="next"></a>  IEnumOnSTLImpl::Next

Este método proporciona la implementación de la **siguiente** método.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[in] El número de elementos solicitados.

*rgelt*<br/>
[out] La matriz que se rellena con los elementos.

*pceltFetched*<br/>
[out] El número de elementos realmente devueltos en *rgelt*. Esto puede ser menor que *celt* si hay menos de *celt* elementos permanecen en la lista.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="reset"></a>  IEnumOnSTLImpl::Reset

Este método proporciona la implementación de la **restablecer** método.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="skip"></a>  IEnumOnSTLImpl::Skip

Este método proporciona la implementación de la **Skip** método.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[in] El número de elementos que se van a omitir.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
