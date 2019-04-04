---
title: ComPtr (clase)
ms.date: 10/01/2018
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
ms.openlocfilehash: 9e5b2419f070ead17e72b1642f510f74bad8260e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785827"
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
La interfaz que el `ComPtr` representa.

*U*<br/>
Una clase a la que el actual `ComPtr` es de confianza. (La plantilla que usa este parámetro está protegida).

## <a name="remarks"></a>Comentarios

`ComPtr<>` declara un tipo que representa el puntero de interfaz subyacente. Usar `ComPtr<>` para declarar una variable y, a continuación, utilice el operador de acceso a miembros de flecha (`->`) para tener acceso a una función miembro de interfaz.

Para obtener más información sobre los punteros inteligentes, consulte la subsección "Punteros inteligentes de COM" de la [COM Coding Practices](/windows/desktop/LearnWin32/com-coding-practices) tema en MSDN Library.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name            | Descripción
--------------- | ---------------------------------------------------------------
`InterfaceType` | Un sinónimo del tipo especificado por el *T* parámetro de plantilla.

### <a name="public-constructors"></a>Constructores públicos

Name                             | Descripción
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Inicializa una nueva instancia de la clase `ComPtr`. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.
[ComPtr::~ComPtr](#tilde-comptr) | Desinicializa una instancia de `ComPtr`.

### <a name="public-methods"></a>Métodos públicos

Name                                                      | Descripción
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | Devuelve un `ComPtr` objeto que representa la interfaz identificada por el parámetro de plantilla especificado.
[ComPtr::AsIID](#asiid)                                   | Devuelve un `ComPtr` objeto que representa la interfaz identificada por el identificador de interfaz especificado.
[ComPtr::AsWeak](#asweak)                                 | Recupera una referencia débil al objeto actual.
[ComPtr::Attach](#attach)                                 | Esto asocia `ComPtr` con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.
[ComPtr::CopyTo](#copyto)                                 | Copia de la interfaz actual o especificada asociada a este `ComPtr` al puntero de salida especificado.
[ComPtr::Detach](#detach)                                 | Desasocia esta `ComPtr` desde la interfaz que representa.
[ComPtr::Get](#get)                                       | Recupera un puntero a la interfaz que está asociado a este `ComPtr`.
[ComPtr::GetAddressOf](#getaddressof)                     | Recupera la dirección de la [ptr_](#ptr) miembro de datos que contiene un puntero a la interfaz representada por este `ComPtr`.
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Libera la interfaz asociada a este `ComPtr` y, a continuación, recupera la dirección de la [ptr_](#ptr) miembro de datos que contiene un puntero a la interfaz que se publicó.
[ComPtr::Reset](#reset)                                   | Libera todas las referencias del puntero a la interfaz que está asociado a este `ComPtr`.
[ComPtr::Swap](#swap)                                     | Intercambia la interfaz administrada por el actual `ComPtr` con la interfaz administrada por especificado `ComPtr`.

### <a name="protected-methods"></a>Métodos protegidos

Name                                        | Descripción
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Incrementa el recuento de referencias de la interfaz asociada a este `ComPtr`.
[ComPtr::InternalRelease](#internalrelease) | Realiza una operación de liberación de COM en la interfaz asociada a este `ComPtr`.

### <a name="public-operators"></a>Operadores públicos

Name                                                                                           | Descripción
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator&](#operator-ampersand)                                                       | Recupera la dirección del elemento actual `ComPtr`.
[ComPtr::operator->](#operator-arrow)                                                          | Recupera un puntero al tipo especificado por el parámetro de plantilla actual.
[ComPtr::operator=](#operator-assign)                                                          | Asigna un valor a la actual `ComPtr`.
[ComPtr::operator==](#operator-equality)                                                       | Indica si dos objetos `ComPtr` son iguales.
[ComPtr::operator!=](#operator-inequality)                                                     | Indica si dos objetos `ComPtr` no son iguales.
[ComPtr::operator Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Indica si un `ComPtr` administra la duración del objeto de una interfaz.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Name                 | Descripción
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Contiene un puntero a la interfaz que está asociado y administrado por este `ComPtr`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres**: Microsoft::WRL

## <a name="tilde-comptr"></a>ComPtr::~ComPtr

Desinicializa una instancia de `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr::As

Devuelve un `ComPtr` objeto que representa la interfaz identificada por el parámetro de plantilla especificado.

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
La interfaz para ser representado por el parámetro *p*.

*p*<br/>
Un `ComPtr` objeto que representa la interfaz especificada por el parámetro *U*. Parámetro *p* no debe hacer referencia a la actual `ComPtr` objeto.

### <a name="remarks"></a>Comentarios

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización del asistente interno, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../../cpp/auto-cpp.md) .

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="asiid"></a>ComPtr::AsIID

Devuelve un `ComPtr` objeto que representa la interfaz identificada por el identificador de interfaz especificado.

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
Si el objeto tiene una interfaz cuyo identificador es igual a *riid*, un puntero indirecto doble para la interfaz especificada por el *riid* parámetro; en caso contrario, un puntero a `IUnknown`.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="asweak"></a>ComPtr::AsWeak

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

## <a name="attach"></a>ComPtr::Attach

Esto asocia `ComPtr` con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Un tipo de interfaz.

## <a name="comptr"></a>ComPtr::ComPtr

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
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>Parámetros

*U*<br/>
El tipo de la *otros* parámetro.

*other*<br/>
Un objeto de tipo *U*.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

El primer constructor es el constructor predeterminado, que implícitamente crea un objeto vacío. Especifica el segundo constructor [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), que crea explícitamente un objeto vacío.

El tercer constructor crea un objeto desde el objeto especificado por un puntero.

Los constructores cuarto y quinto son constructores de copia. El quinto constructor copia un objeto si es convertible al tipo actual.

Los constructores sexto y séptimo son constructores de movimiento. El séptimo constructor mueve un objeto si es convertible al tipo actual.

## <a name="copyto"></a>ComPtr::CopyTo

Copia de la interfaz actual o especificada asociada a este `ComPtr` para el puntero especificado.

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

S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que indica por qué implícito `QueryInterface` error en la operación.

### <a name="remarks"></a>Comentarios

La primera función devuelve una copia de un puntero a la interfaz asociada a este `ComPtr`. Esta función siempre devuelve S_OK.

La segunda función realiza una `QueryInterface` operación en la interfaz asociada a este `ComPtr` para la interfaz especificada por el *riid* parámetro.

La tercera función realiza una `QueryInterface` operación en la interfaz asociada a este `ComPtr` para la interfaz subyacente de la *U* parámetro.

## <a name="detach"></a>ComPtr::Detach

Desasocia esta `ComPtr` objeto desde la interfaz que representa.

```cpp
T* Detach();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz que se ha representado por este `ComPtr` objeto.

## <a name="get"></a>ComPtr::Get

Recupera un puntero a la interfaz que está asociado a este `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz que está asociada a este `ComPtr`.

## <a name="getaddressof"></a>ComPtr::GetAddressOf

Recupera la dirección de la [ptr_](#ptr) miembro de datos que contiene un puntero a la interfaz representada por este `ComPtr`.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

La dirección de una variable.

## <a name="internaladdref"></a>ComPtr::InternalAddRef

Incrementa el recuento de referencias de la interfaz asociada a este `ComPtr`.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Comentarios

Este método está protegido.

## <a name="internalrelease"></a>ComPtr::InternalRelease

Realiza una operación de liberación de COM en la interfaz asociada a este `ComPtr`.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Comentarios

Este método está protegido.

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

Libera la interfaz asociada a este `ComPtr` de objetos y, a continuación, recupera la dirección de la `ComPtr` objeto.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Valor devuelto

Una referencia débil a la actual `ComPtr`.

### <a name="remarks"></a>Comentarios

Este método difiere [Getaddressof](#getaddressof) en que este método libera una referencia al puntero de interfaz. Use `ComPtr::GetAddressOf` cuando se requiere la dirección del puntero de interfaz, pero no desea liberar esa interfaz.

## <a name="operator-arrow"></a>ComPtr::operator-&gt;

Recupera un puntero al tipo especificado por el parámetro de plantilla actual.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al tipo especificado por el nombre de tipo de plantilla actual.

### <a name="remarks"></a>Comentarios

Esta función auxiliar quita deberse al uso de la macro STDMETHOD una sobrecarga innecesaria. Esta función realiza `IUnknown` tipos `private` en lugar de `virtual`.

## <a name="operator-assign"></a>ComPtr::operator=

Asigna un valor a la actual `ComPtr`.

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
Una clase.

*other*<br/>
Un puntero, referencia o referencia de valor r a un tipo u otro `ComPtr`.

### <a name="return-value"></a>Valor devuelto

Una referencia a la actual `ComPtr`.

### <a name="remarks"></a>Comentarios

La primera versión de este operador asigna un valor vacío a la actual `ComPtr`.

En la segunda versión, si el puntero de interfaz de asignación no es el mismo que el actual `ComPtr` puntero de interfaz, el segundo puntero de interfaz se asigna a la actual `ComPtr`.

En la tercera versión, el puntero de interfaz de asignación se asigna a la actual `ComPtr`.

En la cuarta versión, si el puntero de interfaz de la asignación de valor no es el mismo que el actual `ComPtr` puntero de interfaz, el segundo puntero de interfaz se asigna a la actual `ComPtr`.

La quinta versión es un operador de copia. una referencia a un `ComPtr` se asigna a la actual `ComPtr`.

La sexta versión es un operador de copia que usa la semántica; de transferencia una referencia rvalue para un `ComPtr` si es estático cualquier tipo de conversión y, a continuación, se asigna a la actual `ComPtr`.

La séptima versión es un operador de copia que usa la semántica; de transferencia una referencia rvalue para un `ComPtr` typu *U* es estático, a continuación, convertir y asignado al actual `ComPtr`.

## <a name="operator-equality"></a>ComPtr::operator==

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
Una referencia a otro `ComPtr` objeto.

### <a name="return-value"></a>Valor devuelto

El primer rendimientos de operador `true` si objeto *un* es igual al objeto *b*; en caso contrario, `false`.

Los operadores de la segundo y terceros yield `true` si objeto *un* es igual a `nullptr`; en caso contrario, `false`.

## <a name="operator-inequality"></a>ComPtr::operator!=

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
Una referencia a otro `ComPtr` objeto.

### <a name="return-value"></a>Valor devuelto

El primer rendimientos de operador `true` si objeto *un* no es igual al objeto *b*; en caso contrario, `false`.

Los operadores de la segundo y terceros yield `true` si objeto *un* no es igual a `nullptr`; en caso contrario, `false`.

## <a name="operator-microsoft-wrl-details-booltype"></a>Comptr:: operator booltype

Indica si un `ComPtr` administra la duración del objeto de una interfaz.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Valor devuelto

Si una interfaz que está asociada a este `ComPtr`, la dirección de la [Boolstruct](boolstruct-structure.md#member) miembro de datos; de lo contrario, `nullptr`.

## <a name="ptr"></a>ComPtr::ptr_

Contiene un puntero a la interfaz que está asociado y administrado por este `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Comentarios

`ptr_` es un miembro de datos protegido, interno.

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Libera la interfaz asociada a este `ComPtr` y, a continuación, recupera la dirección de la [ptr_](#ptr) miembro de datos que contiene un puntero a la interfaz que se publicó.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

La dirección de la [ptr_](#ptr) miembro de datos de este `ComPtr`.

## <a name="reset"></a>ComPtr::Reset

Libera todas las referencias del puntero a la interfaz que está asociado a este `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Valor devuelto

El número de referencias liberado, si existe.

## <a name="swap"></a>ComPtr::Swap

Intercambia la interfaz administrada por el actual `ComPtr` con la interfaz administrada por especificado `ComPtr`.

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
Objeto `ComPtr`.

