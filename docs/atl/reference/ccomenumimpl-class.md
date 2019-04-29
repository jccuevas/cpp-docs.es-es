---
title: CComEnumImpl (clase)
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
ms.openlocfilehash: ccd083f3bfd9ae694c97e466fcb40b348fec0c27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259866"
---
# <a name="ccomenumimpl-class"></a>CComEnumImpl (clase)

Esta clase proporciona la implementación de una interfaz de enumerador COM donde se almacenan los elementos que se va a enumerar en una matriz.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
Una interfaz de enumerador COM. Consulte [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Un puntero al identificador de interfaz de la interfaz de enumerador.

*T*<br/>
El tipo de elemento que expone la interfaz de enumerador.

*Copiar*<br/>
Un homogéneos [Copiar directiva clase](../../atl/atl-copy-policy-classes.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|El constructor.|
|[CComEnumImpl::~CComEnumImpl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComEnumImpl::Clone](#clone)|La implementación de la **clon** método de interfaz de enumeración.|
|[CComEnumImpl::Init](#init)|Inicializa el enumerador.|
|[CComEnumImpl::Next](#next)|La implementación de **siguiente**.|
|[CComEnumImpl::Reset](#reset)|La implementación de **restablecer**.|
|[CComEnumImpl::Skip](#skip)|La implementación de **Skip**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Un puntero al primer elemento de la matriz.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Copiar marcadores pasados a través de `Init`.|
|[CComEnumImpl::m_end](#m_end)|Un puntero a la ubicación situada más allá del último elemento de la matriz.|
|[CComEnumImpl::m_iter](#m_iter)|Un puntero al elemento actual de la matriz.|
|[CComEnumImpl::m_spUnk](#m_spunk)|El `IUnknown` puntero del objeto que proporciona la colección que se va a enumerar.|

## <a name="remarks"></a>Comentarios

Consulte [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo de las implementaciones de método. `CComEnumImpl` proporciona la implementación de una interfaz de enumerador COM donde se almacenan los elementos que se va a enumerar en una matriz. Esta clase es análoga a la `IEnumOnSTLImpl` (clase), que proporciona una implementación de una interfaz de enumerador se basa en un contenedor de la biblioteca estándar de C++.

> [!NOTE]
>  Para obtener más información sobre aún más diferencias entre `CComEnumImpl` y `IEnumOnSTLImpl`, consulte [CComEnumImpl::Init](#init).

Por lo general, usted podrá *no* debe crear su propia clase de enumerador derivando de esta implementación de la interfaz. Si desea usar un enumerador proporcionada por ATL basándose en una matriz, es más habitual para crear una instancia de [CComEnum](../../atl/reference/ccomenum-class.md).

Sin embargo, si tiene que proporcionar un enumerador personalizado (por ejemplo, uno que expone interfaces además de la interfaz de enumerador), puede derivar de esta clase. En esta situación, es probable que deba reemplazar el [CComEnumImpl::Clone](#clone) método para proporcionar su propia implementación.

Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="ccomenumimpl"></a>  CComEnumImpl::CComEnumImpl

El constructor.

```
CComEnumImpl();
```

##  <a name="dtor"></a>  CComEnumImpl::~CComEnumImpl

Destructor.

```
~CComEnumImpl();
```

##  <a name="init"></a>  CComEnumImpl::Init

Debe llamar a este método antes de pasar un puntero a la interfaz del enumerador a los clientes.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parámetros

*begin*<br/>
Un puntero al primer elemento de la matriz que contiene los elementos que hay que enumerar.

*end*<br/>
Un puntero a la ubicación situada más allá del último elemento de la matriz que contiene los elementos que hay que enumerar.

*pUnk*<br/>
[in] El `IUnknown` puntero de un objeto que se debe mantener activo durante la vigencia del enumerador. Pasar valor NULL si no existe el objeto existe.

*flags*<br/>
Marcas que especifican si el enumerador debe tomar posesión de la matriz o realizar una copia de ella. Los valores posibles se describen a continuación.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Solo llame a este método una vez, inicializar el enumerador, usarlo y luego deshacerse de él.

Si pasar punteros a los elementos de una matriz que se mantienen en otro objeto (y no preguntar el enumerador para copiar los datos), puede usar el *pUnk* parámetro para asegurarse de que el objeto y la matriz contiene están disponibles para siempre que el enumerador lo necesite. El enumerador simplemente mantiene una referencia COM en el objeto para mantener activa. La referencia COM se libera automáticamente cuando se destruye el enumerador.

El *marcas* parámetro le permite especificar cómo el enumerador debe tratar los elementos de matriz que se pasa a él. *marcas* puede tomar uno de los valores de la `CComEnumFlags` enumeración se muestra a continuación:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy` significa que la duración de la matriz no está controlada por el enumerador. En este caso, será la matriz estática o el objeto identificado por *pUnk* será responsable de liberar la matriz cuando ya no es necesario.

`AtlFlagTakeOwnership` significa que la destrucción de la matriz está controlado por el enumerador. En este caso, la matriz debe haberse dinámicamente asignada mediante **nuevo**. El enumerador eliminará de la matriz en su destructor. Por lo general, deberá pasar NULL *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.

`AtlFlagCopy` significa que se crea mediante la copia de la matriz pasada a una nueva matriz `Init`. Duración de la nueva matriz es que estén controladas por el enumerador. El enumerador eliminará de la matriz en su destructor. Por lo general, deberá pasar NULL *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.

> [!NOTE]
>  El prototipo de este método especifica los elementos de matriz son de tipo `T`, donde `T` se definió como un parámetro de plantilla a la clase. Este es el mismo tipo que se expone mediante el método de interfaz COM [CComEnumImpl::Next](#next). Esto implica que, a diferencia de [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), esta clase no admite el almacenamiento diferente y expone los tipos de datos. El tipo de datos de elementos de la matriz debe ser el mismo que el tipo de datos expuesto por medio de la interfaz COM.

##  <a name="clone"></a>  CComEnumImpl::Clone

Este método proporciona la implementación de la **clon** método mediante la creación de un objeto de tipo `CComEnum`, inicializándola con la misma matriz e iterador utilizados por el objeto actual y devuelve la interfaz en el recién creado objeto.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parámetros

*ppEnum*<br/>
[out] La interfaz de enumerador en un objeto recién creado clona el enumerador actual.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que los enumeradores clonados nunca realizar sus propia copia o tomar posesión de los datos utilizados por el enumerador original. Si es necesario, los enumeradores clonados mantendrá el enumerador original activa (mediante una referencia COM) para asegurarse de que los datos están disponibles para siempre y cuando lo necesiten.

##  <a name="m_spunk"></a>  CComEnumImpl::m_spUnk

Este puntero inteligente mantiene una referencia en el objeto pasado a [CComEnumImpl::Init](#init), lo que garantiza que permanece activo durante la vigencia del enumerador.

```
CComPtr<IUnknown> m_spUnk;
```

##  <a name="m_begin"></a>  CComEnumImpl::m_begin

Un puntero a la ubicación situada más allá del último elemento de la matriz que contiene los elementos que hay que enumerar.

```
T* m_begin;
```

##  <a name="m_end"></a>  CComEnumImpl::m_end

Un puntero al primer elemento de la matriz que contiene los elementos que hay que enumerar.

```
T* m_end;
```

##  <a name="m_iter"></a>  CComEnumImpl::m_iter

Un puntero al elemento actual de la matriz que contiene los elementos que hay que enumerar.

```
T* m_iter;
```

##  <a name="m_dwflags"></a>  CComEnumImpl::m_dwFlags

Las marcas se pasan a [CComEnumImpl::Init](#init).

```
DWORD m_dwFlags;
```

##  <a name="next"></a>  CComEnumImpl::Next

Este método proporciona la implementación de la **siguiente** método.

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[in] El número de elementos solicitados.

*rgelt*<br/>
[out] La matriz que se va a rellenar con los elementos.

*pceltFetched*<br/>
[out] El número de elementos realmente devueltos en *rgelt*. Esto puede ser menor que *celt* si hay menos de *celt* elementos permanecen en la lista.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="reset"></a>  CComEnumImpl::Reset

Este método proporciona la implementación de la **restablecer** método.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="skip"></a>  CComEnumImpl::Skip

Este método proporciona la implementación de la **Skip** método.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
[in] El número de elementos que se van a omitir.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Devuelve E_INVALIDARG si *celt* es cero, devuelve S_FALSE si es menor que *celt* se devuelven los elementos, lo contrario, devuelve S_OK.

## <a name="see-also"></a>Vea también

[IEnumOnSTLImpl (clase)](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum (clase)](../../atl/reference/ccomenum-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
