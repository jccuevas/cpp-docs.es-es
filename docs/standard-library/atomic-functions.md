---
title: Funciones &lt;atomic&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 50e70230dd5b8d9aa61f4df8c1288569192048b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848796"
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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

`Exp` Un puntero a un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

Número `bool` que indica el resultado de la comparación de valores.

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

`Exp` Un puntero a un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

`Order1` Primera [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumento.

`Order2` Segundo `memory_order` argumento. El valor de `Order2` no puede ser `memory_order_release` o `memory_order_acq_rel`, ni puede ser más seguro que el valor de `Order1`.

### <a name="return-value"></a>Valor devuelto

Número `bool` que indica el resultado de la comparación de valores.

### <a name="remarks"></a>Comentarios

Una *operación atómica de comparación e intercambio* compara el valor almacenado en el objeto al que apunta `Atom` con el valor al que apunta `Exp`. Si los valores son iguales, el valor almacenado en el objeto al que apunta `atom` se sustituye por `Val` mediante el uso de una operación `read-modify-write` y la aplicación de las restricciones de ordenación de memoria especificadas por `Order1`. Si los valores no son iguales, la operación sustituye el valor al que apunta `Exp` por el valor almacenado en el objeto al que apunta `Atom` y aplica las restricciones de ordenación de memoria especificadas por `Order2`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

`Exp` Un puntero a un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

Número `bool` que indica el resultado de la comparación de valores.

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

`Exp` Un puntero a un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

`Order1` Primera [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumento.

`Order2` Segundo `memory_order` argumento. El valor de `Order2` no puede ser `memory_order_release` o `memory_order_acq_rel`, ni puede ser más seguro que el valor de `Order1`.

### <a name="return-value"></a>Valor devuelto

Número `bool` que indica el resultado de la comparación de valores.

### <a name="remarks"></a>Comentarios

Una *operación atómica de comparación e intercambio* compara el valor almacenado en el objeto al que apunta `Atom` con el valor al que apunta `Exp`. Si los valores son iguales, la operación reemplaza el valor almacenado en el objeto al que apunta `Atom` con `Val` mediante una operación `read-modify-write` y la aplicación de las restricciones de ordenación de memoria especificadas por `Order1`. Si los valores no son iguales, la operación reemplaza el valor al que apunta `Exp` con el valor almacenado en el objeto al que apunta `Atom` y aplica las restricciones de ordenación de memoria especificadas por `Order2`.

Una operación atómica *débil* de comparación e intercambio realiza un intercambio si los valores comparados son iguales. Sin embargo, si los valores no son iguales, no se garantiza que la operación realice un intercambio.

## <a name="atomic_exchange"></a>  atomic_exchange

Usa `Value` para sustituir el valor almacenado de `Atom`.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

Valor almacenado de `Atom` antes del intercambio.

### <a name="remarks"></a>Comentarios

La función `atomic_exchange` realiza una operación `read-modify-write` para intercambiar el valor almacenado en `Atom` con `Value` mediante `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit

Reemplaza el valor almacenado de `Atom` con `Value`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor almacenado de `Atom` antes del intercambio.

### <a name="remarks"></a>Comentarios

La función `atomic_exchange_explicit` realiza una operación `read-modify-write` para intercambiar el valor almacenado en `Atom` con `Value`, dentro de las restricciones de memoria especificadas por `Order`.

## <a name="atomic_fetch_add"></a>  atomic_fetch_add

Agrega un valor a un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parámetros

`Atom` Un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

`Value` Un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_add` realiza una operación `read-modify-write` para agregar de forma atómica `Value` al valor almacenado en `Atom` mediante la restricción `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

Si el tipo atómico es `atomic_address`, `Value` tiene un tipo `ptrdiff_t` y la operación trata el puntero almacenado como `char *`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

`Value` Un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_add_explicit` realiza una operación `read-modify-write` para agregar de forma atómica `Value` al valor almacenado en `Atom`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por `Order`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

`Value` Un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_and` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `and` bit a bit de `Value` y el valor actual almacenado en `Atom` con las restricciones `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

`Value` Un valor de tipo `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_and_explicit` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `and` bit a bit de `Value` y el valor actual almacenado en `Atom`, dentro de las restricciones de memoria especificadas por `Order`.

## <a name="atomic_fetch_or"></a>  atomic_fetch_or

Realiza una operación `or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

`Value` Un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_or` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `or` bit a bit de `Value` y el valor actual almacenado en `Atom` con `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

`Value` Un valor de tipo `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_or_explicit` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `or` bit a bit de `Value` y el valor actual almacenado en `Atom`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por `Order`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

`Value` Un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_sub` realiza una operación `read-modify-write` para restar de forma atómica `Value` del valor almacenado en `Atom` mediante la restricción `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

Si el tipo atómico es `atomic_address`, `Value` tiene un tipo `ptrdiff_t` y la operación trata el puntero almacenado como `char *`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un puntero al tipo `T`.

`Value` Un valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_sub_explicit` realiza una operación `read-modify-write` para restar de forma atómica `Value` del valor almacenado en `Atom`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por `Order`.

Si el tipo atómico es `atomic_address`, `Value` tiene un tipo `ptrdiff_t` y la operación trata el puntero almacenado como `char *`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

`Value` Un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_xor` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `exclusive or` bit a bit de `Value` y el valor actual almacenado en `Atom` con `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

`Value` Un valor de tipo `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Comentarios

La función `atomic_fetch_xor_explicit` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `exclusive or` bit a bit de `Value` y el valor actual almacenado en `Atom`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por `Order`.

## <a name="atomic_flag_clear"></a>  atomic_flag_clear

Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `false`, dentro de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parámetros

`Flag` Un puntero a un `atomic_flag` objeto.

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit

Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `false`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

`Flag` Un puntero a un `atomic_flag` objeto.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set

Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `true`, dentro de las restricciones de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parámetros

`Flag` Un puntero a un `atomic_flag` objeto.

### <a name="return-value"></a>Valor devuelto

Valor inicial de `Flag`.

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `true`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

`Flag` Un puntero a un `atomic_flag` objeto.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor inicial de `Flag`.

## <a name="atomic_init"></a>  atomic_init

Establece el valor almacenado en un objeto `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

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

`Atom` Un puntero a un `atomic` objeto que almacena un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

`true` si las operaciones atómicas sobre `Atom` no tienen bloqueos; de lo contrario, `false`.

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

`Atom` Un puntero a un `atomic` objeto que contiene un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

Valor recuperado que se almacena en `Atom`.

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

`Atom` Un puntero a un `atomic` objeto que contiene un valor de tipo `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_release` ni `memory_order_acq_rel`.

### <a name="return-value"></a>Valor devuelto

Valor recuperado que se almacena en `Atom`.

## <a name="atomic_signal_fence"></a>  atomic_signal_fence

Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, entre otras barreras de un subproceso de llamada que tienen identificadores de señales que se ejecutan en el mismo subproceso.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

`Order` Ordenación de restricción que determina el tipo de barrera de memoria.

### <a name="remarks"></a>Comentarios

El argumento `Order` determina el tipo de barrera.

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

`Atom` Un puntero a un objeto atomic que contiene un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

### <a name="remarks"></a>Comentarios

`atomic_store` almacena `Value` en el objeto al que apunta `Atom`, dentro de la restricción `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

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

`Atom` Un puntero a un `atomic` objeto que contiene un valor de tipo `Ty`.

`Value` Un valor de tipo `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_consume`, `memory_order_acquire` ni `memory_order_acq_rel`.

### <a name="remarks"></a>Comentarios

`atomic_store` almacena `Value` en el objeto al que apunta `Atom`, dentro del `memory_order` especificado por `Order`.

## <a name="atomic_thread_fence"></a>  atomic_thread_fence

Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, sin una operación atómica asociada.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

`Order` Ordenación de restricción que determina el tipo de barrera de memoria.

### <a name="remarks"></a>Comentarios

El argumento `Order` determina el tipo de barrera.

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

`Arg` Un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

El valor devuelto es `Arg`. La evaluación de `Arg` no tiene una dependencia a la llamada de función. Al romper una posible cadena de dependencia, la función podría permitir que el compilador generara código más eficaz.

## <a name="see-also"></a>Vea también

[\<atomic>](../standard-library/atomic.md)<br/>
