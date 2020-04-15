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
ms.openlocfilehash: 89c09ede972f5bdd5da1dde810cad31733bdf338
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372640"
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
La interfaz `ComPtr` que representa.

*U*<br/>
Una clase a `ComPtr` la que la corriente es un amigo. (La plantilla que usa este parámetro está protegida).

## <a name="remarks"></a>Observaciones

`ComPtr<>`declara un tipo que representa el puntero de interfaz subyacente. Se `ComPtr<>` utiliza para declarar una variable y,`->`a continuación, utilice el operador de acceso de miembro de flecha ( ) para tener acceso a una función miembro de interfaz.

Para obtener más información acerca de los punteros inteligentes, consulte la subsección "Punteros inteligentes COM" del tema Prácticas de [codificación COM](/windows/win32/LearnWin32/com-coding-practices) en MSDN Library.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre            | Descripción
--------------- | ---------------------------------------------------------------
`InterfaceType` | Sinónimo del tipo especificado por el parámetro de plantilla *T.*

### <a name="public-constructors"></a>Constructores públicos

Nombre                             | Descripción
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::Comptr](#comptr)        | Inicializa una nueva instancia de la clase `ComPtr`. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.
[ComPtr::-Comptr](#tilde-comptr) | Desinicializa una `ComPtr`instancia de .

### <a name="public-methods"></a>Métodos públicos

Nombre                                                      | Descripción
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | Devuelve `ComPtr` un objeto que representa la interfaz identificada por el parámetro de plantilla especificado.
[ComPtr::AsIID](#asiid)                                   | Devuelve `ComPtr` un objeto que representa la interfaz identificada por el identificador de interfaz especificado.
[ComPtr::AsWeak](#asweak)                                 | Recupera una referencia débil al objeto actual.
[ComPtr::Adjuntar](#attach)                                 | Asocia `ComPtr` esto con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.
[ComPtr::CopyTo](#copyto)                                 | Copia la interfaz actual o `ComPtr` especificada asociada a esto en el puntero de salida especificado.
[ComPtr::Detach](#detach)                                 | Desasocia `ComPtr` esto de la interfaz que representa.
[ComPtr::Get](#get)                                       | Recupera un puntero a la interfaz `ComPtr`asociada a esto .
[ComPtr::GetAddressOf](#getaddressof)                     | Recupera la dirección del [ptr_](#ptr) miembro de datos, que contiene `ComPtr`un puntero a la interfaz representada por este .
[ComPtr::ReleaseAndGetAddressof](#releaseandgetaddressof) | Libera la interfaz `ComPtr` asociada a esto y, a continuación, recupera la dirección del [ptr_](#ptr) miembro de datos, que contiene un puntero a la interfaz que se publicó.
[ComPtr::Reset](#reset)                                   | Libera todas las referencias para el puntero `ComPtr`a la interfaz asociada a esto .
[ComPtr::Swap](#swap)                                     | Intercambia la interfaz `ComPtr` administrada por la actual `ComPtr`con la interfaz administrada por el archivo .

### <a name="protected-methods"></a>Métodos protegidos

Nombre                                        | Descripción
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Incrementa el recuento de referencias `ComPtr`de la interfaz asociada a esto.
[ComPtr::InternalRelease](#internalrelease) | Realiza una operación de la versión COM en la interfaz asociada a esto. `ComPtr`

### <a name="public-operators"></a>Operadores públicos

Nombre                                                                                           | Descripción
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operador&](#operator-ampersand)                                                       | Recupera la dirección del `ComPtr`archivo .
[ComPtr::operator->](#operator-arrow)                                                          | Recupera un puntero al tipo especificado por el parámetro de plantilla actual.
[ComPtr::operador ?](#operator-assign)                                                          | Asigna un valor al `ComPtr`archivo .
[ComPtr::operador](#operator-equality)                                                       | Indica si dos objetos `ComPtr` son iguales.
[ComPtr::operador!](#operator-inequality)                                                     | Indica si dos objetos `ComPtr` no son iguales.
[ComPtr::operador Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Indica si a `ComPtr` está administrando o no la duración del objeto de una interfaz.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                 | Descripción
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Contiene un puntero a la interfaz asociada `ComPtr`y administrado por este archivo .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ComPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr::-Comptr

Desinicializa una `ComPtr`instancia de .

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr::As

Devuelve `ComPtr` un objeto que representa la interfaz identificada por el parámetro de plantilla especificado.

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

*P*<br/>
Objeto `ComPtr` que representa la interfaz especificada por el parámetro *U*. El parámetro *p* no `ComPtr` debe hacer referencia al objeto actual.

### <a name="remarks"></a>Observaciones

La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización del asistente interno, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../../cpp/auto-cpp.md) .

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr::AsIID

Devuelve `ComPtr` un objeto que representa la interfaz identificada por el identificador de interfaz especificado.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*P*<br/>
Si el objeto tiene una interfaz cuyo ID es igual a *riid*, un puntero doblemente indirecto a la interfaz especificada por el parámetro *riid;* de lo contrario, un puntero a `IUnknown`.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr::AsWeak

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

## <a name="comptrattach"></a><a name="attach"></a>ComPtr::Adjuntar

Asocia `ComPtr` esto con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Un tipo de interfaz.

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr::Comptr

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
El tipo del *otro* parámetro.

*Otro*<br/>
Objeto de tipo *U*.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

El primer constructor es el constructor predeterminado, que crea impliclicly un objeto vacío. El segundo constructor especifica [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), que crea explícitamente un objeto vacío.

El tercer constructor crea un objeto a partir del objeto especificado por un puntero. El ComPtr ahora posee la memoria señalada y mantiene un recuento de referencias a ella.

Los constructores cuarto y quinto son constructores de copias. El quinto constructor copia un objeto si es convertible al tipo actual.

Los constructores sexto y séptimo son constructores de movimiento. El séptimo constructor mueve un objeto si es convertible al tipo actual.

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr::CopyTo

Copia la interfaz actual o `ComPtr` especificada asociada a esto en el puntero especificado.

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

*Ptr*<br/>
Cuando se completa esta operación, un puntero a la interfaz solicitada.

*riid*<br/>
Id. de interfaz.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT `QueryInterface` que indica por qué falló la operación implícita.

### <a name="remarks"></a>Observaciones

La primera función devuelve una copia de `ComPtr`un puntero a la interfaz asociada a este archivo . Esta función siempre devuelve S_OK.

La segunda función `QueryInterface` realiza una operación `ComPtr` en la interfaz asociada a esto para la interfaz especificada por el parámetro *riid.*

La tercera función `QueryInterface` realiza una operación `ComPtr` en la interfaz asociada a esto para la interfaz subyacente del parámetro *U.*

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr::Detach

Desasocia `ComPtr` este objeto de la interfaz que representa.

```cpp
T* Detach();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz `ComPtr` representada por este objeto.

## <a name="comptrget"></a><a name="get"></a>ComPtr::Get

Recupera un puntero a la interfaz `ComPtr`asociada a esto .

```cpp
T* Get() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz `ComPtr`asociada a esto .

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr::GetAddressOf

Recupera la dirección del [ptr_](#ptr) miembro de datos, que contiene `ComPtr`un puntero a la interfaz representada por este .

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

La dirección de una variable.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr::InternalAddRef

Incrementa el recuento de referencias `ComPtr`de la interfaz asociada a esto.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Observaciones

Este método está protegido.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr::InternalRelease

Realiza una operación de la versión COM en la interfaz asociada a esto. `ComPtr`

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Observaciones

Este método está protegido.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr::operador&amp;

Libera la interfaz `ComPtr` asociada a este objeto `ComPtr` y, a continuación, recupera la dirección del objeto.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Valor devuelto

Una referencia débil `ComPtr`a la corriente .

### <a name="remarks"></a>Observaciones

Este método difiere de [ComPtr::GetAddressOf](#getaddressof) en que este método libera una referencia al puntero de interfaz. Utilícelo `ComPtr::GetAddressOf` cuando necesite la dirección del puntero de interfaz pero no desee liberar esa interfaz.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr::operador-&gt;

Recupera un puntero al tipo especificado por el parámetro de plantilla actual.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al tipo especificado por el nombre de tipo de plantilla actual.

### <a name="remarks"></a>Observaciones

Esta función auxiliar elimina la sobrecarga innecesaria causada por el uso de la macro STDMETHOD. Esta función `private` hace `virtual` `IUnknown` tipos en lugar de .

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr::operador ?

Asigna un valor al `ComPtr`archivo .

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

*Otro*<br/>
Una referencia de puntero, referencia o valor `ComPtr`r a un tipo u otro archivo .

### <a name="return-value"></a>Valor devuelto

Una referencia a `ComPtr`la corriente .

### <a name="remarks"></a>Observaciones

La primera versión de este operador asigna `ComPtr`un valor vacío al archivo .

En la segunda versión, si el puntero de `ComPtr` interfaz de asignación no es `ComPtr`el mismo que el puntero de interfaz actual, el segundo puntero de interfaz se asigna al puntero actual.

En la tercera versión, el puntero `ComPtr`de interfaz de asignación se asigna al archivo .

En la cuarta versión, si el puntero de interfaz `ComPtr` del valor de asignación no `ComPtr`es el mismo que el puntero de interfaz actual, el segundo puntero de interfaz se asigna al puntero actual.

La quinta versión es un operador de copia; se asigna `ComPtr` una referencia a `ComPtr`al archivo .

La sexta versión es un operador de copia que utiliza la semántica de movimiento; una referencia rvalue `ComPtr` a a si cualquier tipo es `ComPtr`colada estática y, a continuación, se asigna a la versión actual.

La séptima versión es un operador de copia que utiliza la semántica de movimiento; una referencia rvalue `ComPtr` a un de tipo *U* es `ComPtr`la conversión estática y asignada al archivo .

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr::operador

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

*Un*<br/>
Referencia a un objeto `ComPtr`.

*B*<br/>
Una referencia `ComPtr` a otro objeto.

### <a name="return-value"></a>Valor devuelto

El primer operador `true` produce si el objeto *a* es igual al objeto *b*; de `false`lo contrario, .

Los operadores segundo `true` y tercero producen `nullptr`si el objeto *a* es igual a ; de `false`lo contrario, .

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr::operador!

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

*Un*<br/>
Referencia a un objeto `ComPtr`.

*B*<br/>
Una referencia `ComPtr` a otro objeto.

### <a name="return-value"></a>Valor devuelto

El primer operador `true` produce si el objeto *a* no es igual al objeto *b*; de `false`lo contrario, .

Los operadores segundo `true` y tercero producen `nullptr`si el objeto *a* no es igual a ; de `false`lo contrario, .

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::operador Microsoft::WRL::Details::BoolType

Indica si a `ComPtr` está administrando o no la duración del objeto de una interfaz.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Valor devuelto

Si una interfaz `ComPtr`está asociada a esto , la dirección de la [BoolStruct::Member](boolstruct-structure.md#member) miembro de datos; de `nullptr`lo contrario, .

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr::ptr_

Contiene un puntero a la interfaz asociada `ComPtr`y administrado por este archivo .

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Observaciones

`ptr_`es un miembro de datos interno y protegido.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressof

Libera la interfaz `ComPtr` asociada a esto y, a continuación, recupera la dirección del [ptr_](#ptr) miembro de datos, que contiene un puntero a la interfaz que se publicó.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valor devuelto

La dirección del [ptr_](#ptr) miembro `ComPtr`de datos de este archivo .

## <a name="comptrreset"></a><a name="reset"></a>ComPtr::Reset

Libera todas las referencias para el puntero `ComPtr`a la interfaz asociada a esto .

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Valor devuelto

El número de referencias liberado, si existe.

## <a name="comptrswap"></a><a name="swap"></a>ComPtr::Swap

Intercambia la interfaz `ComPtr` administrada por la actual `ComPtr`con la interfaz administrada por el archivo .

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parámetros

*R*<br/>
`ComPtr`.
