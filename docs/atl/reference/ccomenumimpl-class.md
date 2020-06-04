---
title: Clase CComEnumImpl
ms.date: 11/04/2016
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
ms.openlocfilehash: 965e0a8bf6c890882754b60e2785832933d1c52c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327862"
---
# <a name="ccomenumimpl-class"></a>Clase CComEnumImpl

Esta clase proporciona la implementación para una interfaz de enumerador COM donde los elementos que se enumeran se almacenan en una matriz.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
Una interfaz de enumerador COM. Consulte [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Un puntero al identificador de interfaz de la interfaz del enumerador.

*T*<br/>
El tipo de elemento expuesto por la interfaz del enumerador.

*Copiar*<br/>
Una [clase](../../atl/atl-copy-policy-classes.md)de política de copia homogénea.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|El constructor.|
|[CComEnumImpl::-CComEnumImpl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComEnumImpl::Clone](#clone)|La implementación del método de interfaz de enumeración **Clone.**|
|[CComEnumImpl::Init](#init)|Inicializa el enumerador.|
|[CComEnumImpl::Siguiente](#next)|La implementación de **Next**.|
|[CComEnumImpl::Reset](#reset)|La implementación de **Reset**.|
|[CComEnumImpl::Skip](#skip)|La implementación de **Skip**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Un puntero al primer elemento de la matriz.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Copiar las `Init`marcas pasadas a través de .|
|[CComEnumImpl::m_end](#m_end)|Un puntero a la ubicación justo más allá del último elemento de la matriz.|
|[CComEnumImpl::m_iter](#m_iter)|Un puntero al elemento actual de la matriz.|
|[CComEnumImpl::m_spUnk](#m_spunk)|Puntero `IUnknown` del objeto que proporciona la colección que se va a enumerar.|

## <a name="remarks"></a>Observaciones

Consulte [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo de implementaciones de método. `CComEnumImpl`proporciona la implementación de una interfaz de enumerador COM donde los elementos que se enumeran se almacenan en una matriz. Esta clase es análoga a la `IEnumOnSTLImpl` clase, que proporciona una implementación de una interfaz de enumerador basada en un contenedor de biblioteca estándar de C++ .

> [!NOTE]
> Para obtener más información `CComEnumImpl` `IEnumOnSTLImpl`sobre otras diferencias entre y , consulte [CComEnumImpl::Init](#init).

Normalmente, *no* necesitará crear su propia clase de enumerador derivando de esta implementación de interfaz. Si desea utilizar un enumerador proporcionado por ATL basado en una matriz, es más común crear una instancia de [CComEnum](../../atl/reference/ccomenum-class.md).

Sin embargo, si necesita proporcionar un enumerador personalizado (por ejemplo, uno que expone interfaces además de la interfaz del enumerador), puede derivar de esta clase. En esta situación, es probable que tenga que invalidar el [CComEnumImpl::Clone](#clone) método para proporcionar su propia implementación.

Para obtener más información, vea [AtL Collections and Enumerators](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomenumimplccomenumimpl"></a><a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl

El constructor.

```
CComEnumImpl();
```

## <a name="ccomenumimplccomenumimpl"></a><a name="dtor"></a>CComEnumImpl::-CComEnumImpl

Destructor.

```
~CComEnumImpl();
```

## <a name="ccomenumimplinit"></a><a name="init"></a>CComEnumImpl::Init

Debe llamar a este método antes de pasar un puntero a la interfaz del enumerador a cualquier cliente.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parámetros

*Comenzar*<br/>
Puntero al primer elemento de la matriz que contiene los elementos que se van a enumerar.

*Final*<br/>
Puntero a la ubicación justo más allá del último elemento de la matriz que contiene los elementos que se van a enumerar.

*Punk*<br/>
[en] Puntero `IUnknown` de un objeto que se debe mantener activo durante la duración del enumerador. Pase NULL si no existe tal objeto.

*Banderas*<br/>
Indicadores que especifican si el enumerador debe tomar posesión de la matriz o hacer una copia de ella. Los valores posibles se describen a continuación.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Solo llame a este método una vez: inicialice el enumerador, utilícelo y, a continuación, desátelo.

Si pasa punteros a elementos de una matriz que se encuentran en otro objeto (y no le pide al enumerador que copie los datos), puede usar el parámetro *pUnk* para asegurarse de que el objeto y la matriz que contiene están disponibles durante el tiempo que el enumerador los necesite. El enumerador simplemente contiene una referencia COM en el objeto para mantenerlo activo. La referencia COM se libera automáticamente cuando se destruye el enumerador.

El parámetro *flags* permite especificar cómo debe tratar el enumerador los elementos de matriz que se le pasan. *los indicadores* pueden tomar `CComEnumFlags` uno de los valores de la enumeración que se muestra a continuación:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`significa que la duración de la matriz no está controlada por el enumerador. En este caso, la matriz será estática o el objeto identificado por *pUnk* será responsable de liberar la matriz cuando ya no sea necesaria.

`AtlFlagTakeOwnership`significa que la destrucción de la matriz debe ser controlada por el enumerador. En este caso, la matriz debe haberse asignado dinámicamente utilizando **new**. El enumerador eliminará la matriz en su destructor. Normalmente, pasaría NULL para *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.

`AtlFlagCopy`significa que se debe crear una nueva matriz `Init`copiando la matriz que se pasa a . La duración de la nueva matriz debe ser controlada por el enumerador. El enumerador eliminará la matriz en su destructor. Normalmente, pasaría NULL para *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.

> [!NOTE]
> El prototipo de este método especifica los `T`elementos `T` de matriz como de tipo , donde se definió como un parámetro de plantilla para la clase. Este es el mismo tipo que se expone mediante el método de interfaz COM [CComEnumImpl::Next](#next). La implicación de esto es que, a diferencia de [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), esta clase no admite diferentes tipos de almacenamiento y datos expuestos. El tipo de datos de los elementos de la matriz debe ser el mismo que el tipo de datos expuesto mediante la interfaz COM.

## <a name="ccomenumimplclone"></a><a name="clone"></a>CComEnumImpl::Clone

Este método proporciona la **Clone** implementación de la `CComEnum`Clone método mediante la creación de un objeto de tipo , inicializándolo con la misma matriz e iterador utilizado por el objeto actual y devolviendo la interfaz en el objeto recién creado.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parámetros

*ppEnum*<br/>
[fuera] La interfaz del enumerador en un objeto recién creado clonado desde el enumerador actual.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que los enumeradores clonados nunca hacen su propia copia (o toman la propiedad) de los datos utilizados por el enumerador original. Si es necesario, los enumeradores clonados mantendrán vivo el enumerador original (mediante una referencia COM) para asegurarse de que los datos están disponibles durante el tiempo que los necesiten.

## <a name="ccomenumimplm_spunk"></a><a name="m_spunk"></a>CComEnumImpl::m_spUnk

Este puntero inteligente mantiene una referencia en el objeto pasado a [CComEnumImpl::Init](#init), asegurándose de que permanece activo durante la duración del enumerador.

```
CComPtr<IUnknown> m_spUnk;
```

## <a name="ccomenumimplm_begin"></a><a name="m_begin"></a>CComEnumImpl::m_begin

Puntero a la ubicación justo más allá del último elemento de la matriz que contiene los elementos que se van a enumerar.

```
T* m_begin;
```

## <a name="ccomenumimplm_end"></a><a name="m_end"></a>CComEnumImpl::m_end

Puntero al primer elemento de la matriz que contiene los elementos que se van a enumerar.

```
T* m_end;
```

## <a name="ccomenumimplm_iter"></a><a name="m_iter"></a>CComEnumImpl::m_iter

Puntero al elemento actual de la matriz que contiene los elementos que se van a enumerar.

```
T* m_iter;
```

## <a name="ccomenumimplm_dwflags"></a><a name="m_dwflags"></a>CComEnumImpl::m_dwFlags

Las marcas [pasadas a CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

## <a name="ccomenumimplnext"></a><a name="next"></a>CComEnumImpl::Siguiente

Este método proporciona la implementación de la **Next** método.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[en] El número de elementos solicitados.

*rgelt*<br/>
[fuera] Matriz que se va a rellenar con los elementos.

*pceltFetched*<br/>
[fuera] El número de elementos devueltos realmente en *rgelt*. Esto puede ser menor que *celt* si quedan menos elementos *celt* en la lista.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomenumimplreset"></a><a name="reset"></a>CComEnumImpl::Reset

Este método proporciona la implementación de la **Reset** método.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomenumimplskip"></a><a name="skip"></a>CComEnumImpl::Skip

Este método proporciona la implementación de la **Skip** método.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[en] El número de elementos que se deben omitir.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Devuelve E_INVALIDARG si *celt* es cero, devuelve S_FALSE si se devuelven menos de los elementos *celt,* devuelve S_OK en caso contrario.

## <a name="see-also"></a>Consulte también

[Clase IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Clase CComEnum](../../atl/reference/ccomenum-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
