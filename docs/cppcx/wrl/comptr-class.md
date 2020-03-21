---
title: ComPtr (clase)
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: 2881d25434291aebff6a2d3a542044e58e0e81f2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077888"
---
# <a name="comptr-class"></a>ComPtr (clase)

Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. `ComPtr` mantiene automáticamente un recuento de referencias para el puntero de la interfaz subyacente y la libera cuando el recuento de referencias llega a cero.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Interfaz que representa el `ComPtr`.

*U*<br/>
Clase a la que el `ComPtr` actual es un amigo. (La plantilla que usa este parámetro está protegida).

## <a name="remarks"></a>Observaciones

`ComPtr<>` declara un tipo que representa el puntero de interfaz subyacente. Utilice `ComPtr<>` para declarar una variable y, a continuación, utilice el operador de acceso de miembro de flecha (`->`) para tener acceso a una función miembro de interfaz.

Para obtener más información sobre los punteros inteligentes, consulte la subsección "punteros inteligentes de COM" del tema [prácticas de codificación com](/windows/win32/LearnWin32/com-coding-practices) en MSDN Library.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

Nombre            | Descripción
--------------- | ---------------------------------------------------------------
`InterfaceType` | Sinónimo del tipo especificado por el parámetro de plantilla *T* .

### <a name="public-constructors"></a>Constructores públicos

Nombre                             | Descripción
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr:: ComPtr](#comptr)        | Inicializa una nueva instancia de la clase `ComPtr`. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.
[ComPtr:: ~ ComPtr](#tilde-comptr) | Desinicializa una instancia de `ComPtr`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                      | Descripción
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: as](#as)                                         | Devuelve un objeto `ComPtr` que representa la interfaz identificada por el parámetro de plantilla especificado.
[ComPtr:: Asiid (](#asiid)                                   | Devuelve un objeto `ComPtr` que representa la interfaz identificada por el identificador de interfaz especificado.
[ComPtr:: asweak](#asweak)                                 | Recupera una referencia débil al objeto actual.
[ComPtr:: Attach](#attach)                                 | Asocia este `ComPtr` con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.
[ComPtr:: CopyTo](#copyto)                                 | Copia la interfaz actual o especificada asociada a esta `ComPtr` al puntero de salida especificado.
[ComPtr::D Etach](#detach)                                 | Desasocia esta `ComPtr` de la interfaz que representa.
[ComPtr:: get](#get)                                       | Recupera un puntero a la interfaz que está asociada a este `ComPtr`.
[ComPtr:: Getaddressof (](#getaddressof)                     | Recupera la dirección del miembro de datos [ptr_](#ptr) , que contiene un puntero a la interfaz representada por este `ComPtr`.
[ComPtr:: Releaseandgetaddressof (](#releaseandgetaddressof) | Libera la interfaz asociada a este `ComPtr` y, a continuación, recupera la dirección del miembro de datos [ptr_](#ptr) , que contiene un puntero a la interfaz que se liberó.
[ComPtr::Reset](#reset)                                   | Libera todas las referencias del puntero a la interfaz que está asociada a este `ComPtr`.
[ComPtr:: swap](#swap)                                     | Intercambia la interfaz administrada por el `ComPtr` actual con la interfaz administrada por el `ComPtr`especificado.

### <a name="protected-methods"></a>Métodos protegidos

Nombre                                        | Descripción
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr:: Internaladdref (](#internaladdref)   | Incrementa el recuento de referencias de la interfaz asociada a este `ComPtr`.
[ComPtr:: Internalrelease (](#internalrelease) | Realiza una operación de liberación de COM en la interfaz asociada a este `ComPtr`.

### <a name="public-operators"></a>Operadores públicos

Nombre                                                                                           | Descripción
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator &](#operator-ampersand)                                                       | Recupera la dirección del `ComPtr`actual.
[ComPtr:: Operator->](#operator-arrow)                                                          | Recupera un puntero al tipo especificado por el parámetro de plantilla actual.
[ComPtr:: Operator =](#operator-assign)                                                          | Asigna un valor al `ComPtr`actual.
[ComPtr:: Operator = =](#operator-equality)                                                       | Indica si dos objetos `ComPtr` son iguales.
[ComPtr:: Operator! =](#operator-inequality)                                                     | Indica si dos objetos `ComPtr` no son iguales.
[ComPtr:: Operator Microsoft:: WRL::D etalles:: Booltype (](#operator-microsoft-wrl-details-booltype) | Indica si un `ComPtr` está administrando o no la duración del objeto de una interfaz.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                 | Descripción
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::p tr_](#ptr) | Contiene un puntero a la interfaz asociada a y administrada por este `ComPtr`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

Desinicializa una instancia de `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr:: as

Devuelve un objeto `ComPtr` que representa la interfaz identificada por el parámetro de plantilla especificado.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>Parámetros

*U*<br/>
La interfaz que se va a representar mediante el parámetro *p*.

*p*<br/>
Objeto `ComPtr` que representa la interfaz especificada por el parámetro *U*. El parámetro *p* no debe hacer referencia al objeto `ComPtr` actual.

### <a name="remarks"></a>Observaciones

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización del asistente interno, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../../cpp/auto-cpp.md) .

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr:: Asiid (

Devuelve un objeto `ComPtr` que representa la interfaz identificada por el identificador de interfaz especificado.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*p*<br/>
Si el objeto tiene una interfaz cuyo identificador es igual a *riid*, un puntero de doble indirecto a la interfaz especificada por el parámetro *riid* ; de lo contrario, un puntero a `IUnknown`.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr:: asweak

Recupera una referencia débil al objeto actual.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parámetros

*pWeakRef*<br/>
Cuando se completa esta operación, un puntero a un objeto de referencia débil.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="comptrattach"></a><a name="attach"></a>ComPtr:: Attach

Asocia este `ComPtr` con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Un tipo de interfaz.

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr:: ComPtr

Inicializa una nueva instancia de la clase `ComPtr`. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.

```cpp
WRL_NOTHROW ComPtr();

WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);

template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);

WRL_NOTHROW ComPtr(
   const ComPtr& other
);

template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>Parámetros

*U*<br/>
Tipo del *otro* parámetro.

*other*<br/>
Objeto de tipo *U*.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

El primer constructor es el constructor predeterminado, que implícita crea un objeto vacío. El segundo constructor especifica [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), que crea explícitamente un objeto vacío.

El tercer constructor crea un objeto a partir del objeto especificado por un puntero. El ComPtr ahora posee la memoria señalada y mantiene un recuento de referencias.

Los constructores cuarto y quinto son constructores de copias. El quinto constructor copia un objeto si se pueden convertir al tipo actual.

Los constructores sexto y séptimo son constructores de movimiento. El séptimo constructor mueve un objeto si se pueden convertir al tipo actual.

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr:: CopyTo

Copia la interfaz actual o especificada asociada a este `ComPtr` en el puntero especificado.

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Parámetros

*U*<br/>
Nombre de tipo.

*ptr*<br/>
Cuando se completa esta operación, un puntero a la interfaz solicitada.

*riid*<br/>
Id. de interfaz.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica por qué se produjo un error en la operación de `QueryInterface` implícita.

### <a name="remarks"></a>Observaciones

La primera función devuelve una copia de un puntero a la interfaz asociada a este `ComPtr`. Esta función siempre Devuelve S_OK.

La segunda función realiza una operación de `QueryInterface` en la interfaz asociada a este `ComPtr` para la interfaz especificada por el parámetro *riid* .

La tercera función realiza una operación de `QueryInterface` en la interfaz asociada a este `ComPtr` para la interfaz subyacente del parámetro *U* .

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr::D Etach

Desasocia este objeto `ComPtr` de la interfaz que representa.

```cpp
T* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz representada por este objeto `ComPtr`.

## <a name="comptrget"></a><a name="get"></a>ComPtr:: get

Recupera un puntero a la interfaz que está asociada a este `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz que está asociada a este `ComPtr`.

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr:: Getaddressof (

Recupera la dirección del miembro de datos [ptr_](#ptr) , que contiene un puntero a la interfaz representada por este `ComPtr`.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

Dirección de una variable.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr:: Internaladdref (

Incrementa el recuento de referencias de la interfaz asociada a este `ComPtr`.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Observaciones

Este método está protegido.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr:: Internalrelease (

Realiza una operación de liberación de COM en la interfaz asociada a este `ComPtr`.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Observaciones

Este método está protegido.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr:: Operator&amp;

Libera la interfaz asociada a este objeto `ComPtr` y, a continuación, recupera la dirección del objeto `ComPtr`.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Valor devuelto

Referencia débil al `ComPtr`actual.

### <a name="remarks"></a>Observaciones

Este método difiere de [ComPtr:: getaddressof (](#getaddressof) en que este método libera una referencia al puntero de interfaz. Use `ComPtr::GetAddressOf` cuando necesite la dirección del puntero de interfaz pero no desee liberar esa interfaz.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr:: Operator-&gt;

Recupera un puntero al tipo especificado por el parámetro de plantilla actual.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al tipo especificado por el nombre del tipo de plantilla actual.

### <a name="remarks"></a>Observaciones

Esta función auxiliar quita la sobrecarga innecesaria causada por el uso de la macro STDMETHOD. Esta función realiza `private` de `IUnknown` tipos en lugar de `virtual`.

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr:: Operator =

Asigna un valor al `ComPtr`actual.

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>Parámetros

*U*<br/>
Clase.

*other*<br/>
Un puntero, una referencia o una referencia rvalue a un tipo u otro `ComPtr`.

### <a name="return-value"></a>Valor devuelto

Referencia al `ComPtr`actual.

### <a name="remarks"></a>Observaciones

La primera versión de este operador asigna un valor vacío al `ComPtr`actual.

En la segunda versión, si el puntero de la interfaz de asignación no es el mismo que el puntero de interfaz `ComPtr` actual, el segundo puntero de interfaz se asigna al `ComPtr`actual.

En la tercera versión, el puntero de interfaz de asignación se asigna al `ComPtr`actual.

En la cuarta versión, si el puntero de interfaz del valor de asignación no es el mismo que el puntero de interfaz `ComPtr` actual, el segundo puntero de interfaz se asigna al `ComPtr`actual.

La quinta versión es un operador de copia; se asigna una referencia a un `ComPtr` a la `ComPtr`actual.

La sexta versión es un operador de copia que utiliza la semántica de movimiento. referencia a un valor r a un `ComPtr` si algún tipo es una conversión estática y, a continuación, se asigna a la `ComPtr`actual.

La séptima versión es un operador de copia que utiliza la semántica de movimiento. una referencia de valor r a un `ComPtr` de tipo *U* es una conversión estática y se asigna a la `ComPtr`actual.

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr:: Operator = =

Indica si dos objetos `ComPtr` son iguales.

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Referencia a un objeto `ComPtr`.

*b*<br/>
Referencia a otro objeto de `ComPtr`.

### <a name="return-value"></a>Valor devuelto

El primer operador produce `true` si el objeto *a* es igual al objeto *b*; de lo contrario, `false`.

Los operadores segundo y tercero producen `true` si el objeto *a* es igual a `nullptr`; de lo contrario, `false`.

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr:: Operator! =

Indica si dos objetos `ComPtr` no son iguales.

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parámetros

*a*<br/>
Referencia a un objeto `ComPtr`.

*b*<br/>
Referencia a otro objeto de `ComPtr`.

### <a name="return-value"></a>Valor devuelto

El primer operador produce `true` si el objeto *a* no es igual al objeto *b*; de lo contrario, `false`.

Los operadores segundo y tercero producen `true` si el objeto *a* no es igual a `nullptr`; de lo contrario, `false`.

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: Operator Microsoft:: WRL::D etalles:: Booltype (

Indica si un `ComPtr` está administrando o no la duración del objeto de una interfaz.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Valor devuelto

Si una interfaz está asociada a esta `ComPtr`, la dirección del miembro de datos [boolstruct (:: Member](boolstruct-structure.md#member) ; de lo contrario, `nullptr`.

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr::p tr_

Contiene un puntero a la interfaz asociada a y administrada por este `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Observaciones

`ptr_` es un miembro de datos interno protegido.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr:: Releaseandgetaddressof (

Libera la interfaz asociada a este `ComPtr` y, a continuación, recupera la dirección del miembro de datos [ptr_](#ptr) , que contiene un puntero a la interfaz que se liberó.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

Dirección del miembro de datos [ptr_](#ptr) de este `ComPtr`.

## <a name="comptrreset"></a><a name="reset"></a>ComPtr:: RESET

Libera todas las referencias del puntero a la interfaz que está asociada a este `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Valor devuelto

El número de referencias liberado, si existe.

## <a name="comptrswap"></a><a name="swap"></a>ComPtr:: swap

Intercambia la interfaz administrada por el `ComPtr` actual con la interfaz administrada por el `ComPtr`especificado.

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parámetros

*r*<br/>
`ComPtr`.
