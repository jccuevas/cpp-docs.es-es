---
title: Funciones &lt;atomic&gt; | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.topic: reference
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
author: mikeblome
ms.author: mblome
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.workload:
- cplusplus
ms.openlocfilehash: df0c7ea332cda65aa3621de581eb39419ee9b9d4
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028322"
---
# <a name="ltatomicgt-functions"></a>Funciones &lt;atomic&gt;

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a>  atomic_compare_exchange_strong

Realiza una operación atómica de comparación e intercambio.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un *atómica* objeto que almacena un valor de tipo `Ty`.

*EXP* un puntero a un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

**True** si los valores son iguales; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

Este método realiza una operación atómica de comparación e intercambio mediante los argumentos implícitos `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Para más información, vea [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a>  atomic_compare_exchange_strong_explicit

Realiza una operación *atómica de comparación e intercambio*.

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

*EXP* un puntero a un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

*Order1* primera [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumento.

*Order2* segundo `memory_order` argumento. El valor de *Order2* no puede ser `memory_order_release` o `memory_order_acq_rel`, no puede ser más seguro que el valor de *Order1*.

### <a name="return-value"></a>Valor devuelto

**True** si los valores son iguales; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

Un *operación atómica de comparación e intercambio* compara el valor que se almacena en el objeto que apunta *Atom* con el valor al que apunta *Exp*. Si los valores son iguales, el el valor que se almacena en el objeto que apunta *atom* se sustituye por `Val` utilizando un `read-modify-write` restricciones que se especifican mediante deordenacióndeoperaciónylaaplicacióndelamemoria*Order1*. Si los valores no son iguales, la operación reemplaza el valor al que apunta *Exp* con el valor que se almacena en el objeto que apunta *Atom* y aplica las restricciones de ordenación de memoria que están especificado por *Order2*.

## <a name="atomic_compare_exchange_weak"></a>  atomic_compare_exchange_weak

Realiza una operación *atómica débil de comparación e intercambio*.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

*EXP* un puntero a un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

**True** si los valores son iguales; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

Este método realiza una *operación atómica débil de comparación e intercambio* que tiene argumentos implícitos `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Para más información, vea [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a>  atomic_compare_exchange_weak_explicit

Realiza una operación *atómica débil de comparación e intercambio*.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

*EXP* un puntero a un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

*Order1* primera [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumento.

*Order2* segundo `memory_order` argumento. El valor de *Order2* no puede ser `memory_order_release` o `memory_order_acq_rel`, ni puede ser más seguro que el valor de *Order1*.

### <a name="return-value"></a>Valor devuelto

**True** si los valores son iguales; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

Los tipos fuertes y débiles de un *operación atómica de comparación e intercambio* garantía de que no contienen el nuevo valor si los valores esperados y actuales no son iguales. El tipo seguro garantiza que se van a almacenar el nuevo valor si los valores esperados y actuales son iguales. A veces, puede devolver el tipo débil **false** y no almacenar el nuevo valor incluso si el actual y los valores esperados son iguales. En otras palabras, la función devolverá **false**, pero un examen posterior del valor esperado podría revelar que no ha cambiado y, por lo tanto, se debe comparar como iguales.

## <a name="atomic_exchange"></a>  atomic_exchange

Usa *valor* para reemplazar el valor almacenado de *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

El valor almacenado de *Atom* antes del intercambio.

### <a name="remarks"></a>Comentarios

El `atomic_exchange` función realiza una `read-modify-write` operación para intercambiar el valor que se almacena en *Atom* con *valor*, usando la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit

Reemplaza el valor almacenado de *Atom* con *valor*.

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

El valor almacenado de *Atom* antes del intercambio.

### <a name="remarks"></a>Comentarios

El `atomic_exchange_explicit` función realiza una `read-modify-write` operación para intercambiar el valor que se almacena en *Atom* con *valor*, dentro de las restricciones de memoria especificadas por  *Orden*.

## <a name="atomic_fetch_add"></a>  atomic_fetch_add

Agrega un valor a un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

*Valor* un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_add` función realiza una `read-modify-write` operación para agregar de forma atómica *valor* al valor almacenado en *Atom*, usando la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)restricción.

Cuando el tipo atómico es `atomic_address`, *valor* tiene tipo `ptrdiff_t` y la operación trata el puntero almacenado como un `char *`.

Esta operación también está sobrecargada en los tipos de entero:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a>  atomic_fetch_add_explicit

Agrega un valor a un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

*Valor* un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_add_explicit` función realiza una `read-modify-write` operación para agregar de forma atómica *valor* al valor almacenado en *Atom*, en el [memory_order](../standard-library/atomic-enums.md#memory_order_enum) restricciones que se especifican mediante `Order`.

Si el tipo atómico es `atomic_address`, `Value` tiene un tipo `ptrdiff_t` y la operación trata el puntero almacenado como `char *`.

Esta operación también está sobrecargada en los tipos de entero:

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a>  atomic_fetch_and

Realiza una operación `and` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

*Valor* un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_and` función realiza una `read-modify-write` operación para reemplazar el valor almacenado de *Atom* con un bit a bit `and` de *valor* y el valor actual almacenado en *Atom*, usando la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) restricción.

## <a name="atomic_fetch_and_explicit"></a>  atomic_fetch_and_explicit

Realiza una operación `and` bit a bit de un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

*Valor* un valor de tipo `T`.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_and_explicit` función realiza una `read-modify-write` operación para reemplazar el valor almacenado de *Atom* con un bit a bit `and` de *valor* y el valor actual almacenado en *Atom*, dentro de las restricciones de memoria especificadas por *orden*.

## <a name="atomic_fetch_or"></a>  atomic_fetch_or

Realiza una operación `or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

*Valor* un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_or` función realiza una `read-modify-write` operación para reemplazar el valor almacenado de *Atom* con un bit a bit `or` de *valor* y el valor actual almacenado en *Atom*, usando la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a>  atomic_fetch_or_explicit

Realiza una operación `or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

*Valor* un valor de tipo `T`.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_or_explicit` función realiza una `read-modify-write` operación para reemplazar el valor almacenado de *Atom* con un bit a bit `or` de *valor* y el valor actual almacenado en *Atom*, en el [memory_order](../standard-library/atomic-enums.md#memory_order_enum) las restricciones especificadas por *orden*.

## <a name="atomic_fetch_sub"></a>  atomic_fetch_sub

Resta un valor de un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

*Valor* un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_sub` función realiza una `read-modify-write` operación a restar de forma atómica *valor* del valor almacenado en *Atom*, usando la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) restricción.

Cuando el tipo atómico es `atomic_address`, *valor* tiene tipo `ptrdiff_t` y la operación trata el puntero almacenado como un `char *`.

Esta operación también está sobrecargada en los tipos de entero:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>  atomic_fetch_sub_explicit

Resta un valor de un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

*Valor* un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_sub_explicit` función realiza una `read-modify-write` operación a restar de forma atómica *valor* del valor almacenado en *Atom*, en el [memory_order](../standard-library/atomic-enums.md#memory_order_enum) las restricciones especificadas por `Order`.

Cuando el tipo atómico es `atomic_address`, *valor* tiene tipo `ptrdiff_t` y la operación trata el puntero almacenado como un `char *`.

Esta operación también está sobrecargada en los tipos de entero:

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a>  atomic_fetch_xor

Realiza una operación `exclusive or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

*Valor* un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_xor` función realiza una `read-modify-write` operación para reemplazar el valor almacenado de *Atom* con un bit a bit `exclusive or` de *valor* y el valor actual almacenado en *Atom*, usando la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a>  atomic_fetch_xor_explicit

Realiza una operación `exclusive or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

*Valor* un valor de tipo `T`.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

El `atomic_fetch_xor_explicit` función realiza una `read-modify-write` operación para reemplazar el valor almacenado de *Atom* con un bit a bit `exclusive or` de *valor* y el valor actual almacenado en *Atom*, en el [memory_order](../standard-library/atomic-enums.md#memory_order_enum) las restricciones especificadas por *orden*.

## <a name="atomic_flag_clear"></a>  atomic_flag_clear

Conjuntos de la **bool** marca en una [atomic_flag](../standard-library/atomic-flag-structure.md) objeto **false**, en el `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parámetros

*Marca* un puntero a un `atomic_flag` objeto.

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit

Conjuntos de la **bool** marca en una [atomic_flag](../standard-library/atomic-flag-structure.md) objeto **false**, dentro de lo especificado [memory_order](../standard-library/atomic-enums.md#memory_order_enum) restricciones.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Marca* un puntero a un `atomic_flag` objeto.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set

Conjuntos de la **bool** marca en una [atomic_flag](../standard-library/atomic-flag-structure.md) objeto **true**, dentro de las restricciones de la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parámetros

*Marca* un puntero a un `atomic_flag` objeto.

### <a name="return-value"></a>Valor devuelto

El valor inicial de *marca*.

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

Conjuntos de la **bool** marca en una [atomic_flag](../standard-library/atomic-flag-structure.md) objeto **true**, dentro de lo especificado [memory_order](../standard-library/atomic-enums.md#memory_order_enum) restricciones.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Marca* un puntero a un `atomic_flag` objeto.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

El valor inicial de *marca*.

## <a name="atomic_init"></a>  atomic_init

Establece el valor almacenado en un objeto `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

### <a name="remarks"></a>Comentarios

`atomic_init` no es una operación atómica. No es segura para subprocesos.

## <a name="atomic_is_lock_free"></a>  atomic_is_lock_free

Especifica si las operaciones atómicas sobre un objeto `atomic` *no tienen bloqueos*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

**True** si las operaciones atómicas sobre *Atom* bloqueos; de lo contrario, **false**.

### <a name="remarks"></a>Comentarios

Un tipo atómico no tiene bloqueos si ninguna operación atómica sobre ese tipo emplea bloqueos. Si esta función devuelve True, el tipo se puede usar con seguridad en identificadores de señales.

## <a name="atomic_load"></a>  atomic_load

Recupera el valor almacenado en un objeto `atomic`.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que contiene un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

El valor recuperado que se almacena en *Atom*.

### <a name="remarks"></a>Comentarios

`atomic_load` usa de forma implícita `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a>  atomic_load_explicit

Recupera el valor almacenado en un objeto `atomic`, dentro de un [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificado.

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que contiene un valor de tipo `Ty`.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_release` ni `memory_order_acq_rel`.

### <a name="return-value"></a>Valor devuelto

El valor recuperado que se almacena en *Atom*.

## <a name="atomic_signal_fence"></a>  atomic_signal_fence

Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, entre otras barreras de un subproceso de llamada que tienen identificadores de señales que se ejecutan en el mismo subproceso.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden* ordenación restricción que determina el tipo de barrera de memoria.

### <a name="remarks"></a>Comentarios

El *orden* argumento determina el tipo de barrera.

|||
|-|-|
|`memory_order_relaxed`|La barrera no tiene ningún efecto.|
|`memory_order_consume`|Es una barrera de adquisición.|
|`memory_order_acquire`|Es una barrera de adquisición.|
|`memory_order_release`|Es una barrera de liberación.|
|`memory_order_acq_rel`|Es una barrera de adquisición y de liberación.|
|`memory_order_seq_cst`|Es una barrera de adquisición y de liberación, y es coherente secuencialmente.|

## <a name="atomic_store"></a>  atomic_store

Almacena de forma atómica un valor en un objeto atómico.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un objeto atómico que contiene un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

### <a name="remarks"></a>Comentarios

`atomic_store` almacena *valor* en el objeto que apunta *Atom*, en el `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) restricción.

## <a name="atomic_store_explicit"></a>  atomic_store_explicit

Almacena de forma atómica un valor en un objeto atómico.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Atom* un puntero a un `atomic` objeto que contiene un valor de tipo `Ty`.

*Valor* un valor de tipo `Ty`.

*Orden* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_consume`, `memory_order_acquire` ni `memory_order_acq_rel`.

### <a name="remarks"></a>Comentarios

`atomic_store` almacena *valor* en el objeto que apunta *Atom*, en el `memory_order` especificado por *orden*.

## <a name="atomic_thread_fence"></a>  atomic_thread_fence

Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, sin una operación atómica asociada.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden* ordenación restricción que determina el tipo de barrera de memoria.

### <a name="remarks"></a>Comentarios

El *orden* argumento determina el tipo de barrera.

|||
|-|-|
|`memory_order_relaxed`|La barrera no tiene ningún efecto.|
|`memory_order_consume`|Es una barrera de adquisición.|
|`memory_order_acquire`|Es una barrera de adquisición.|
|`memory_order_release`|Es una barrera de liberación.|
|`memory_order_acq_rel`|Es una barrera de adquisición y de liberación.|
|`memory_order_seq_cst`|Es una barrera de adquisición y de liberación, y es coherente secuencialmente.|

## <a name="kill_dependency"></a>  kill_dependency

Quita una dependencia.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parámetros

*Arg* un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

El valor devuelto es *Arg*. La evaluación de *Arg* no tiene una dependencia en la llamada de función. Al romper una posible cadena de dependencia, la función podría permitir que el compilador generara código más eficaz.

## <a name="see-also"></a>Vea también

[\<atomic>](../standard-library/atomic.md)<br/>
