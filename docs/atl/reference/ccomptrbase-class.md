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
ms.openlocfilehash: 740920225fc513a869b4a92344f87004831e4768
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298621"
---
# <a name="ccomptrbase-class"></a>Clase CComPtrBase

Esta clase proporciona una base para las clases de puntero inteligente mediante rutinas de memoria basadas en COM.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parameters

*T*<br/>
Tipo de objeto al que hace referencia el puntero inteligente.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase::~CComPtrBase](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase::Advise](#advise)|Llame a este método para crear una conexión entre el punto de conexión del `CComPtrBase`y el receptor de un cliente.|
|[CComPtrBase::Attach](#attach)|Llame a este método para tomar posesión de un puntero existente.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Llame a este método para crear un objeto de la clase asociada a un identificador de clase o de programa especificado.|
|[CComPtrBase::CopyTo](#copyto)|Llame a este método para copiar el puntero `CComPtrBase` en otra variable de puntero.|
|[CComPtrBase::Detach](#detach)|Llame a este método para liberar la propiedad de un puntero.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Llame a este método para comprobar si el `IUnknown` especificado apunta al mismo objeto asociado al objeto `CComPtrBase`.|
|[CComPtrBase::QueryInterface](#queryinterface)|Llame a este método para devolver un puntero a una interfaz especificada.|
|[CComPtrBase::Release](#release)|Llame a este método para liberar la interfaz.|
|[CComPtrBase::SetSite](#setsite)|Llame a este método para establecer el sitio del objeto `CComPtrBase` en el `IUnknown` del objeto primario.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase:: Operator T *](#operator_t_star)|Operador de conversión.|
|[CComPtrBase:: Operator!](#operator_not)|Operador NOT.|
|[CComPtrBase:: operator &](#operator_amp)|El operador &.|
|[CComPtrBase::operator *](#operator_star)|El operador \*.|
|[CComPtrBase:: Operator <](#ccomptrbase__operator lt)|Operador menor que.|
|[CComPtrBase::operator ==](#operator_eq_eq)|Operador de igualdad.|
|[CComPtrBase::operator ->](#operator_ptr)|Operador de puntero a miembro.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComPtrBase::p](#p)|Variable de miembro de datos de puntero.|

## <a name="remarks"></a>Notas

Esta clase proporciona la base para otros punteros inteligentes que utilizan rutinas de administración de memoria COM, como [CComQIPtr](../../atl/reference/ccomqiptr-class.md) y [CComPtr](../../atl/reference/ccomptr-class.md). Las clases derivadas agregan sus propios constructores y operadores, pero dependen de los métodos proporcionados por `CComPtrBase`.

## <a name="requirements"></a>Requisitos de

**Encabezado:** atlcomcli. h

##  <a name="advise"></a>  CComPtrBase::Advise

Llame a este método para crear una conexión entre el punto de conexión del `CComPtrBase`y el receptor de un cliente.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parameters

*pUnk*<br/>
Puntero a la `IUnknown`del cliente.

*iid*<br/>
GUID del punto de conexión. Normalmente, es igual que la interfaz de salida administrada por el punto de conexión.

*pdw*<br/>
Puntero a la cookie que identifica de forma única la conexión.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Notas

Vea [AtlAdvise](connection-point-global-functions.md#atladvise) para obtener más información.

##  <a name="attach"></a>  CComPtrBase::Attach

Llame a este método para tomar posesión de un puntero existente.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parameters

*p2*<br/>
El objeto `CComPtrBase` tomará posesión de este puntero.

### <a name="remarks"></a>Notas

`Attach` llama a [CComPtrBase:: Release](#release) en la variable miembro [CComPtrBase::p](#p) existente y, a continuación, asigna *P2* a `CComPtrBase::p`. Cuando un objeto de `CComPtrBase` toma la propiedad de un puntero, llamará automáticamente a `Release` en el puntero, lo que eliminará el puntero y los datos asignados si el recuento de referencias del objeto va a 0.

##  <a name="dtor"></a>  CComPtrBase::~CComPtrBase

Destructor.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Notas

Libera la interfaz a la que apunta `CComPtrBase`.

##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance

Llame a este método para crear un objeto de la clase asociada a un identificador de clase o de programa especificado.

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

### <a name="parameters"></a>Parameters

*szProgID*<br/>
Puntero a un ProgID, que se usa para recuperar el CLSID.

*pUnkOuter*<br/>
Si es NULL, indica que el objeto no se crea como parte de un agregado. Si no es NULL, es un puntero a la interfaz de `IUnknown` del objeto de agregado (control de `IUnknown`).

*dwClsContext*<br/>
Contexto en el que se ejecutará el código que administra el objeto recién creado.

*rclsid*<br/>
CLSID asociado con los datos y el código que se utilizarán para crear el objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING o E_NOINTERFACE en caso de error. Vea [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) y [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) para obtener una descripción de estos errores.

### <a name="remarks"></a>Notas

Si se llama al primer formulario del método, se usa [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) para recuperar el CLSID. Ambos formularios llamarán a [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

En las compilaciones de depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.

##  <a name="copyto"></a>  CComPtrBase::CopyTo

Llame a este método para copiar el puntero `CComPtrBase` en otra variable de puntero.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parameters

*ppT*<br/>
Dirección de la variable que recibirá el puntero `CComPtrBase`.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, E_POINTER en caso de error.

### <a name="remarks"></a>Notas

Copia el puntero `CComPtrBase` en *ppT*. Se incrementa el recuento de referencias en la variable de miembro [CComPtrBase::p](#p) .

Se devolverá un error HRESULT si *ppT* es igual a NULL. En las compilaciones de depuración, se producirá un error de aserción si *ppT* es igual a NULL.

##  <a name="detach"></a>  CComPtrBase::Detach

Llame a este método para liberar la propiedad de un puntero.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del puntero.

### <a name="remarks"></a>Notas

Libera la propiedad de un puntero, establece la variable de miembro de datos [CComPtrBase::p](#p) en NULL y devuelve una copia del puntero.

##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject

Llame a este método para comprobar si el `IUnknown` especificado apunta al mismo objeto asociado al objeto `CComPtrBase`.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parameters

*pOther*<br/>
`IUnknown *` que se va comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los objetos son idénticos; en caso contrario, false.

##  <a name="operator_not"></a>CComPtrBase:: Operator!

Operador NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el puntero `CComHeapPtr` es igual a NULL y false en caso contrario.

##  <a name="operator_amp"></a>CComPtrBase:: Operator &amp;

El operador &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección del objeto al que apunta el objeto `CComPtrBase`.

##  <a name="operator_star"></a>CComPtrBase:: Operator \*

El operador \*.

```
T& operator*() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de [CComPtrBase::p](#p); es decir, un puntero al objeto al que hace referencia el objeto `CComPtrBase`.

Si se compila la depuración, se producirá un error de aserción si [CComPtrBase::p](#p) no es igual a NULL.

##  <a name="operator_eq_eq"></a>  CComPtrBase::operator ==

Operador de igualdad.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parameters

*pT*<br/>
Un puntero a un objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si `CComPtrBase` y *PT* apuntan al mismo objeto; de lo contrario, devuelve false.

##  <a name="operator_ptr"></a>  CComPtrBase::operator -&gt;

Operador de puntero a miembro.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la variable de miembro de datos [CComPtrBase::p](#p) .

### <a name="remarks"></a>Notas

Utilice este operador para llamar a un método en una clase a la que señala el objeto `CComPtrBase`. En las compilaciones de depuración, se producirá un error de aserción si el `CComPtrBase` miembro de datos señala a NULL.

##  <a name="operator_lt"></a>CComPtrBase:: Operator &lt;

Operador menor que.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parameters

*pT*<br/>
Un puntero a un objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el puntero administrado por el objeto actual es menor que el puntero con el que se está comparando.

##  <a name="operator_t_star"></a>CComPtrBase:: Operator T\*

Operador de conversión.

```
operator T*() const throw();
```

### <a name="remarks"></a>Notas

Devuelve un puntero al tipo de datos del objeto definido en la plantilla de clase.

##  <a name="p"></a>  CComPtrBase::p

Variable de miembro de datos de puntero.

```
T* p;
```

### <a name="remarks"></a>Notas

Esta variable miembro contiene la información del puntero.

##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface

Llame a este método para devolver un puntero a una interfaz especificada.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parameters

*Q*<br/>
Tipo de objeto cuyo puntero de interfaz se requiere.

*pp*<br/>
Dirección de la variable de salida que recibe el puntero de interfaz solicitado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o E_NOINTERFACE en caso de error.

### <a name="remarks"></a>Notas

Este método llama a [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

En las compilaciones de depuración, se producirá un error de aserción si *PP* no es igual a NULL.

##  <a name="release"></a>  CComPtrBase::Release

Llame a este método para liberar la interfaz.

```
void Release() throw();
```

### <a name="remarks"></a>Notas

La interfaz se libera y [CComPtrBase::p](#p) se establece en NULL.

##  <a name="setsite"></a>  CComPtrBase::SetSite

Llame a este método para establecer el sitio del objeto `CComPtrBase` en el `IUnknown` del objeto primario.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parameters

*punkParent*<br/>
Puntero a la interfaz `IUnknown` del elemento primario.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Notas

Este método llama a [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
