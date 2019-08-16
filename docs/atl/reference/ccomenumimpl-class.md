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
ms.openlocfilehash: 7d26c59a38bfe43e49215fbb6108453e10ca6dea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497175"
---
# <a name="ccomenumimpl-class"></a>Clase CComEnumImpl

Esta clase proporciona la implementación de una interfaz de enumerador COM en la que los elementos que se van a enumerar se almacenan en una matriz.

## <a name="syntax"></a>Sintaxis

```
template <class Base,
    const IID* piid, class T, class Copy>
class ATL_NO_VTABLE CComEnumImpl : public Base
```

#### <a name="parameters"></a>Parámetros

*Básica*<br/>
Interfaz de enumerador COM. Vea [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo.

*piid*<br/>
Puntero al identificador de interfaz de la interfaz del enumerador.

*T*<br/>
Tipo de elemento expuesto por la interfaz del enumerador.

*Copy*<br/>
Una [clase de directiva de copia](../../atl/atl-copy-policy-classes.md)homogénea.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|El constructor.|
|[CComEnumImpl::~CComEnumImpl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComEnumImpl::Clone](#clone)|Implementación del método de interfaz de enumeración de clonación.|
|[CComEnumImpl::Init](#init)|Inicializa el enumerador.|
|[CComEnumImpl::Next](#next)|Implementación de **Next**.|
|[CComEnumImpl::Reset](#reset)|La implementación de **RESET**.|
|[CComEnumImpl::Skip](#skip)|Implementación de **SKIP**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComEnumImpl::m_begin](#m_begin)|Puntero al primer elemento de la matriz.|
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Copiar las marcas que `Init`se han pasado.|
|[CComEnumImpl::m_end](#m_end)|Puntero a la ubicación situada más allá del último elemento de la matriz.|
|[CComEnumImpl::m_iter](#m_iter)|Puntero al elemento actual de la matriz.|
|[CComEnumImpl::m_spUnk](#m_spunk)|`IUnknown` Puntero del objeto que proporciona la colección que se va a enumerar.|

## <a name="remarks"></a>Comentarios

Vea [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo de implementaciones de método. `CComEnumImpl`proporciona la implementación de una interfaz de enumerador COM en la que los elementos que se van a enumerar se almacenan en una matriz. Esta clase es análoga a la `IEnumOnSTLImpl` clase, que proporciona una implementación de una interfaz de enumerador basada C++ en un contenedor de biblioteca estándar.

> [!NOTE]
>  Para obtener más información sobre las `CComEnumImpl` diferencias `IEnumOnSTLImpl`entre y, vea [CComEnumImpl:: init](#init).

Normalmente, *no* necesitará crear su propia clase de enumerador derivando de esta implementación de interfaz. Si desea utilizar un enumerador proporcionado por ATL basado en una matriz, es más común crear una instancia de [CComEnum](../../atl/reference/ccomenum-class.md).

Sin embargo, si necesita proporcionar un enumerador personalizado (por ejemplo, uno que exponga interfaces además de la interfaz del enumerador), puede derivar de esta clase. En esta situación, es probable que deba invalidar el método [CComEnumImpl:: Clone](#clone) para proporcionar su propia implementación.

Para obtener más información, vea [colecciones y enumeradores de ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComEnumImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

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

Debe llamar a este método antes de pasar un puntero a la interfaz del enumerador de nuevo a los clientes.

```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```

### <a name="parameters"></a>Parámetros

*begin*<br/>
Puntero al primer elemento de la matriz que contiene los elementos que se van a enumerar.

*end*<br/>
Puntero a la ubicación situada más allá del último elemento de la matriz que contiene los elementos que se van a enumerar.

*pUnk*<br/>
de `IUnknown` Puntero de un objeto que debe mantenerse activo mientras dure el enumerador. Pase NULL si no existe tal objeto.

*flags*<br/>
Marcas que especifican si el enumerador debe tomar posesión de la matriz o realizar una copia de él. A continuación se describen los valores posibles.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Solo llame a este método una vez: inicialice el enumerador, úselo y, a continuación, colóquelo fuera de él.

Si pasa punteros a elementos de una matriz que se mantiene en otro objeto (y no pide al enumerador que copie los datos), puede usar el parámetro *pUnk* para asegurarse de que el objeto y la matriz que contiene están disponibles mientras el enumerador los necesite. El enumerador simplemente contiene una referencia COM en el objeto para mantenerlo activo. La referencia COM se libera automáticamente cuando se destruye el enumerador.

El parámetro flags le permite especificar cómo debe tratar el enumerador los elementos de matriz que se le pasan. las *marcas* pueden tomar uno de los valores de `CComEnumFlags` la enumeración que se muestra a continuación:

```
enum CComEnumFlags
   {
   AtlFlagNoCopy = 0,
   AtlFlagTakeOwnership = 2, // BitOwn
   AtlFlagCopy = 3           // BitOwn | BitCopy
   };
```

`AtlFlagNoCopy`significa que el enumerador no controla la duración de la matriz. En este caso, la matriz será estática o el objeto identificado por *pUnk* será el responsable de liberar la matriz cuando ya no se necesite.

`AtlFlagTakeOwnership`significa que el enumerador controlará la destrucción de la matriz. En este caso, la matriz se debe haber asignado dinámicamente mediante **New**. El enumerador eliminará la matriz en su destructor. Normalmente, pasaría NULL para *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.

`AtlFlagCopy`significa que se va a crear una nueva matriz copiando la matriz pasada a `Init`. El enumerador controlará la duración de la nueva matriz. El enumerador eliminará la matriz en su destructor. Normalmente, pasaría NULL para *pUnk*, aunque todavía puede pasar un puntero válido si necesita recibir una notificación de la destrucción del enumerador por algún motivo.

> [!NOTE]
>  El prototipo de este método especifica los elementos de la matriz como de `T`tipo, `T` donde se definió como un parámetro de plantilla para la clase. Este es el mismo tipo que se expone mediante el método de interfaz COM [CComEnumImpl:: Next](#next). La implicación de esto es que, a diferencia de [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), esta clase no admite distintos tipos de datos expuestos y de almacenamiento. El tipo de datos de los elementos de la matriz debe ser el mismo que el tipo de datos expuesto por medio de la interfaz COM.

##  <a name="clone"></a>  CComEnumImpl::Clone

Este método proporciona la implementación del método **Clone** creando un objeto de tipo `CComEnum`, inicializándose con la misma matriz e iterador que usa el objeto actual y devolviendo la interfaz en el objeto recién creado.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parámetros

*ppEnum*<br/>
enuncia La interfaz del enumerador en un objeto recién creado clonado desde el enumerador actual.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que los enumeradores clonados nunca realizan su propia copia (o toman posesión) de los datos utilizados por el enumerador original. Si es necesario, los enumeradores clonados mantendrán el enumerador original activo (mediante una referencia COM) para asegurarse de que los datos estén disponibles mientras lo necesiten.

##  <a name="m_spunk"></a>  CComEnumImpl::m_spUnk

Este puntero inteligente mantiene una referencia en el objeto pasado a [CComEnumImpl:: init](#init), asegurándose de que permanece activo durante la vigencia del enumerador.

```
CComPtr<IUnknown> m_spUnk;
```

##  <a name="m_begin"></a>  CComEnumImpl::m_begin

Puntero a la ubicación situada más allá del último elemento de la matriz que contiene los elementos que se van a enumerar.

```
T* m_begin;
```

##  <a name="m_end"></a>  CComEnumImpl::m_end

Puntero al primer elemento de la matriz que contiene los elementos que se van a enumerar.

```
T* m_end;
```

##  <a name="m_iter"></a>  CComEnumImpl::m_iter

Puntero al elemento actual de la matriz que contiene los elementos que se van a enumerar.

```
T* m_iter;
```

##  <a name="m_dwflags"></a>  CComEnumImpl::m_dwFlags

Marcas pasadas a [CComEnumImpl:: init](#init).

```
DWORD m_dwFlags;
```

##  <a name="next"></a>  CComEnumImpl::Next

Este método proporciona la implementación del método **siguiente** .

```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
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

##  <a name="reset"></a>  CComEnumImpl::Reset

Este método proporciona la implementación del método **RESET** .

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="skip"></a>  CComEnumImpl::Skip

Este método proporciona la implementación del método **SKIP** .

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parámetros

*celt*<br/>
de Número de elementos que se van a omitir.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Devuelve E_INVALIDARG si *Celt* es cero, devuelve S_FALSE si se devuelven menos elementos *Celt* , Devuelve S_OK de lo contrario.

## <a name="see-also"></a>Vea también

[IEnumOnSTLImpl (clase)](../../atl/reference/ienumonstlimpl-class.md)<br/>
[CComEnum (clase)](../../atl/reference/ccomenum-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
