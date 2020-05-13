---
title: Clase CComPtrBase
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 9c62cc912b3fea3ea68390882bdda37cbfb25a7e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747760"
---
# <a name="ccomptrbase-class"></a>Clase CComPtrBase

Esta clase proporciona una base para las clases de puntero inteligente mediante rutinas de memoria basadas en COM.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto al que va a hacer referencia el puntero inteligente.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtrBase::-CComPtrBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtrBase::Advise](#advise)|Llame a este método para `CComPtrBase`crear una conexión entre el punto de conexión 's y el receptor de un cliente.|
|[CComPtrBase::Attach](#attach)|Llame a este método para tomar la propiedad de un puntero existente.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Llame a este método para crear un objeto de la clase asociada a un identificador de clase o identificador de programa especificado.|
|[CComPtrBase::CopyTo](#copyto)|Llame a este `CComPtrBase` método para copiar el puntero a otra variable de puntero.|
|[CComPtrBase::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Llame a este método para `IUnknown` comprobar si el especificado `CComPtrBase` apunta al mismo objeto asociado con el objeto.|
|[CComPtrBase::QueryInterface](#queryinterface)|Llame a este método para devolver un puntero a una interfaz especificada.|
|[CComPtrBase::Release](#release)|Llame a este método para liberar la interfaz.|
|[CComPtrBase::SetSite](#setsite)|Llame a este método para `CComPtrBase` establecer `IUnknown` el sitio del objeto en el del objeto primario.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtrBase::operador T*](#operator_t_star)|El operador de colada.|
|[CComPtrBase::operator !](#operator_not)|El operador NOT.|
|[CComPtrBase::operator &](#operator_amp)|El operador &.|
|[CComPtrBase::operador *](#operator_star)|El operador \*.|
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|El operador menor que.|
|[CComPtrBase::operador ?](#operator_eq_eq)|El operador de igualdad.|
|[CComPtrBase::operador ->](#operator_ptr)|El operador de puntero a miembros.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPtrBase::p](#p)|La variable miembro de datos de puntero.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona la base para otros punteros inteligentes que utilizan rutinas de administración de memoria COM, como [CComQIPtr](../../atl/reference/ccomqiptr-class.md) y [CComPtr](../../atl/reference/ccomptr-class.md). Las clases derivadas agregan sus propios constructores y `CComPtrBase`operadores, pero se basan en los métodos proporcionados por .

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase::Advise

Llame a este método para `CComPtrBase`crear una conexión entre el punto de conexión 's y el receptor de un cliente.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
Un puntero a la `IUnknown`.

*Iid*<br/>
El GUID del punto de conexión. Normalmente, esto es lo mismo que la interfaz saliente administrada por el punto de conexión.

*Pdw*<br/>
Puntero a la cookie que identifica de forma única la conexión.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Consulte [AtlAdvise](connection-point-global-functions.md#atladvise) para obtener más información.

## <a name="ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase::Attach

Llame a este método para tomar la propiedad de un puntero existente.

```cpp
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parámetros

*p2*<br/>
El `CComPtrBase` objeto tomará la propiedad de este puntero.

### <a name="remarks"></a>Observaciones

`Attach`llama a [CComPtrBase::Release](#release) en la variable miembro [CComPtrBase::p](#p) existente y, a continuación, asigna *p2* a `CComPtrBase::p`. Cuando `CComPtrBase` un objeto toma la propiedad de `Release` un puntero, llamará automáticamente al puntero que eliminará el puntero y los datos asignados si el recuento de referencias en el objeto va a 0.

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase::-CComPtrBase

Destructor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Observaciones

Libera la interfaz `CComPtrBase`señalada por .

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance

Llame a este método para crear un objeto de la clase asociada a un identificador de clase o identificador de programa especificado.

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>Parámetros

*szProgID*<br/>
Puntero a un ProgID, utilizado para recuperar el CLSID.

*pUnkOuter*<br/>
Si NULL, indica que el objeto no se está creando como parte de un agregado. Si no es NULL, es un puntero `IUnknown` a la `IUnknown`interfaz del objeto agregado (el control ).

*dwClsContext*<br/>
Contexto en el que se ejecutará el código que administra el objeto recién creado.

*rclsid*<br/>
CLSID asociado a los datos y el código que se usará para crear el objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING o E_NOINTERFACE en caso de error. Consulte [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) y [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) para obtener una descripción de estos errores.

### <a name="remarks"></a>Observaciones

Si se llama a la primera forma del método, [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) se utiliza para recuperar el CLSID. A continuación, ambos formularios llaman a [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

En compilaciones de depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a>CComPtrBase::CopyTo

Llame a este `CComPtrBase` método para copiar el puntero a otra variable de puntero.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parámetros

*Ppt*<br/>
Dirección de la variable `CComPtrBase` que recibirá el puntero.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito, E_POINTER en caso de error.

### <a name="remarks"></a>Observaciones

Copia `CComPtrBase` el puntero a *ppT*. El recuento de referencias en el [CComPtrBase::p](#p) variable miembro se incrementa.

Se devolverá un error HRESULT si *ppT* es igual a NULL. En compilaciones de depuración, se producirá un error de aserción si *ppT* es igual a NULL.

## <a name="ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Observaciones

Libera la propiedad de un puntero, establece el [CComPtrBase::p](#p) variable miembro de datos en NULL y devuelve una copia del puntero.

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase::IsEqualObject

Llame a este método para `IUnknown` comprobar si el especificado `CComPtrBase` apunta al mismo objeto asociado con el objeto.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parámetros

*pOtros*<br/>
`IUnknown *` que se va comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los objetos son idénticos, false en caso contrario.

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase::operator !

El operador NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true `CComHeapPtr` si el puntero es igual a NULL, false en caso contrario.

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::operator&amp;

El operador &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección del objeto `CComPtrBase` al que apunta el objeto.

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::operator\*

El operador \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de [CComPtrBase::p](#p); es decir, un puntero al `CComPtrBase` objeto al que hace referencia el objeto.

Si se compila la depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase::operador ?

El operador de igualdad.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Puntero a un objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true `CComPtrBase` if y *pT* apuntan al mismo objeto, false en caso contrario.

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase::operador -&gt;

El operador de puntero a miembro.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la [CComPtrBase::p](#p) variable miembro de datos.

### <a name="remarks"></a>Observaciones

Utilice este operador para llamar a un `CComPtrBase` método en una clase señalada por el objeto. En compilaciones de depuración, se `CComPtrBase` producirá un error de aserción si el miembro de datos apunta a NULL.

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::operator&lt;

El operador menor que.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Puntero a un objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el puntero administrado por el objeto actual es menor que el puntero con el que se está comparando.

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::operator T\*

El operador de colada.

```
operator T*() const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.

## <a name="ccomptrbasep"></a><a name="p"></a>CComPtrBase::p

La variable miembro de datos de puntero.

```
T* p;
```

### <a name="remarks"></a>Observaciones

Esta variable miembro contiene la información del puntero.

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase::QueryInterface

Llame a este método para devolver un puntero a una interfaz especificada.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parámetros

*Q*<br/>
El tipo de objeto cuyo puntero de interfaz es necesario.

*Pp*<br/>
Dirección de la variable de salida que recibe el puntero de interfaz solicitado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o E_NOINTERFACE en caso de error.

### <a name="remarks"></a>Observaciones

Este método llama a [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

En compilaciones de depuración, se producirá un error de aserción si *pp* no es igual a NULL.

## <a name="ccomptrbaserelease"></a><a name="release"></a>CComPtrBase::Release

Llame a este método para liberar la interfaz.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Observaciones

Se libera la interfaz y [CComPtrBase::p](#p) se establece en NULL.

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase::SetSite

Llame a este método para `CComPtrBase` establecer `IUnknown` el sitio del objeto en el del objeto primario.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parámetros

*punkParent*<br/>
Un puntero `IUnknown` a la interfaz del elemento primario.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método llama a [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
