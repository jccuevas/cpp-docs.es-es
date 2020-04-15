---
title: Funciones &lt;atomic&gt;
ms.date: 07/11/2018
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
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376896"
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

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

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

*Átomo*\
Puntero a un objeto *atómico* que almacena un valor de tipo `Ty`.

*Exp*\
Puntero a un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

**true** si los valores son iguales, de lo contrario **false**.

### <a name="remarks"></a>Observaciones

Este método realiza una operación atómica de comparación e intercambio mediante los argumentos implícitos `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Para más información, vea [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.

*Exp*\
Puntero a un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

*Pedido1*\
Primer argumento [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

*Pedido2*\
Segundo argumento `memory_order`. El valor de *Order2* no puede ser `memory_order_release` o `memory_order_acq_rel`, no puede ser más fuerte que el valor de *Order1*.

### <a name="return-value"></a>Valor devuelto

**true** si los valores son iguales, de lo contrario **false**.

### <a name="remarks"></a>Observaciones

Una operación atómica de *comparación e intercambio* compara el valor almacenado en el objeto al que apunta *Atom* con el valor al que apunta *Exp*. Si los valores son iguales, el valor que se almacena en el objeto `read-modify-write` al que apunta el *átomo* se sustituye por *Value* mediante una operación y aplicando las restricciones de orden de memoria especificadas por *Order1*. Si los valores no son iguales, la operación reemplaza el valor al que apunta *Exp* por el valor almacenado en el objeto al que apunta *Atom* y aplica las restricciones de orden de memoria especificadas por *Order2*.

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.

*Exp*\
Puntero a un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

**true** si los valores son iguales, de lo contrario **false**.

### <a name="remarks"></a>Observaciones

Este método realiza una *operación atómica débil de comparación e intercambio* que tiene argumentos implícitos `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Para más información, vea [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.

*Exp*\
Puntero a un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

*Pedido1*\
Primer argumento [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

*Pedido2*\
Segundo argumento `memory_order`. El valor de *Order2* no puede ser `memory_order_release` o `memory_order_acq_rel`, ni puede ser más fuerte que el valor de *Order1*.

### <a name="return-value"></a>Valor devuelto

**true** si los valores son iguales, de lo contrario **false**.

### <a name="remarks"></a>Observaciones

Los sabores fuertes y débiles de una *operación de comparación e intercambio atómica* garantizan que no almacenan el nuevo valor si los valores esperados y actuales no son iguales. El sabor fuerte garantiza que almacenará el nuevo valor si los valores esperados y actuales son iguales. El sabor débil a veces puede devolver **false** y no almacenar el nuevo valor incluso si los valores actuales y esperados son iguales. En otras palabras, la función devolverá **false**, pero un examen posterior del valor esperado podría revelar que no cambió y, por lo tanto, debería haber comparado como igual.

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

Utiliza *Value* para reemplazar el valor almacenado de *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

El valor almacenado de *Atom* antes del intercambio.

### <a name="remarks"></a>Observaciones

La `atomic_exchange` función `read-modify-write` realiza una operación para intercambiar el valor `memory_order_seq_cst`almacenado en *Atom* con *Value*, utilizando el [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Reemplaza el valor almacenado de *Atom* por *Value*.

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

El valor almacenado de *Atom* antes del intercambio.

### <a name="remarks"></a>Observaciones

La `atomic_exchange_explicit` función `read-modify-write` realiza una operación para intercambiar el valor almacenado en *Atom* con *Value*, dentro de las restricciones de memoria especificadas por *Order*.

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

Agrega un valor a un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.

*Valor*\
Valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_add` función `read-modify-write` realiza una operación para agregar atómicamente *Value* `memory_order_seq_cst`al valor almacenado en *Atom*, utilizando la restricción [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

Cuando el tipo `atomic_address`atómico es , *Value* tiene `ptrdiff_t` `char *`type y la operación trata el puntero almacenado como un archivo .

Esta operación también está sobrecargada en los tipos de entero:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.

*Valor*\
Valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_add_explicit` función `read-modify-write` realiza una operación para agregar atómicamente *Value* al valor almacenado en `Order` *Atom*, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por .

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

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

Realiza una operación `and` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `T`.

*Valor*\
Valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_and` función `read-modify-write` realiza una operación para reemplazar el `and` valor almacenado de *Atom* con un valor `memory_order_seq_cst`bit a bit de *Value* y el valor actual que se almacena en *Atom*, utilizando la restricción [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `T`.

*Valor*\
Valor de tipo `T`.

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_and_explicit` función `read-modify-write` realiza una operación para reemplazar el `and` valor almacenado de *Atom* con un valor bit a bit de *Value* y el valor actual que se almacena en *Atom*, dentro de las restricciones de memoria especificadas por *Order*.

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

Realiza una operación `or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `T`.

*Valor*\
Valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_or` función `read-modify-write` realiza una operación para reemplazar el `or` valor almacenado de *Atom* con un valor `memory_order_seq_cst`bit a bit de *Value* y el valor actual que se almacena en *Atom*, utilizando el [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `T`.

*Valor*\
Valor de tipo `T`.

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_or_explicit` función `read-modify-write` realiza una operación para reemplazar el `or` valor almacenado de *Atom* con un valor bit a bit de *Value* y el valor actual que se almacena en *Atom*, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por *Order*.

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.

*Valor*\
Valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_sub` función `read-modify-write` realiza una operación *Value* para restar atómicamente Value `memory_order_seq_cst`del valor almacenado en *Atom*, utilizando la restricción [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

Cuando el tipo `atomic_address`atómico es , *Value* tiene `ptrdiff_t` `char *`type y la operación trata el puntero almacenado como un archivo .

Esta operación también está sobrecargada en los tipos de entero:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.

*Valor*\
Valor de tipo `ptrdiff_t`.

### <a name="return-value"></a>Valor devuelto

Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_sub_explicit` función `read-modify-write` realiza una operación para restar atómicamente *Value* del valor almacenado en `Order` *Atom*, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por .

Cuando el tipo `atomic_address`atómico es , *Value* tiene `ptrdiff_t` `char *`type y la operación trata el puntero almacenado como un archivo .

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

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

Realiza una operación `exclusive or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `T`.

*Valor*\
Valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_xor` función `read-modify-write` realiza una operación para reemplazar el `exclusive or` valor almacenado de *Atom* con un valor `memory_order_seq_cst`bit a bit de *Value* y el valor actual que se almacena en *Atom*, utilizando el [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `T`.

*Valor*\
Valor de tipo `T`.

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.

### <a name="remarks"></a>Observaciones

La `atomic_fetch_xor_explicit` función `read-modify-write` realiza una operación para reemplazar el `exclusive or` valor almacenado de *Atom* con un valor bit a bit de *Value* y el valor actual que se almacena en *Atom*, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por *Order*.

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

Establece la marca **bool** en un objeto `memory_order_seq_cst` [atomic_flag](../standard-library/atomic-flag-structure.md) en **false**, dentro del [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parámetros

*Bandera*\
Puntero a un objeto `atomic_flag` .

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Establece el indicador **bool** en un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en **false**, dentro de las restricciones [de memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Bandera*\
Puntero a un objeto `atomic_flag` .

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Establece el indicador **bool** en un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `memory_order_seq_cst` **true**, dentro de las restricciones del [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parámetros

*Bandera*\
Puntero a un objeto `atomic_flag` .

### <a name="return-value"></a>Valor devuelto

El valor inicial de *Flag*.

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Establece el indicador **bool** en un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en **true**, dentro de las restricciones [de memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Bandera*\
Puntero a un objeto `atomic_flag` .

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

El valor inicial de *Flag*.

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

Establece el valor almacenado en un objeto `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

### <a name="remarks"></a>Observaciones

`atomic_init` no es una operación atómica. No es segura para subprocesos.

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

Especifica si las operaciones atómicas sobre un objeto `atomic`*no tienen bloqueos*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que almacena un valor de tipo `T`.

### <a name="return-value"></a>Valor devuelto

**cierto** si las operaciones atómicas en *Atom* no tienen cerradura; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Un tipo atómico no tiene bloqueos si ninguna operación atómica sobre ese tipo emplea bloqueos. Si esta función devuelve True, el tipo se puede usar con seguridad en identificadores de señales.

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

Recupera el valor almacenado en un objeto `atomic`.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que contiene un valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

El valor recuperado que se almacena en *Atom*.

### <a name="remarks"></a>Observaciones

`atomic_load` usa de forma implícita `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

Recupera el valor almacenado en un objeto `atomic`, dentro de un [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificado.

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto `atomic` que contiene un valor de tipo `Ty`.

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_release` ni `memory_order_acq_rel`.

### <a name="return-value"></a>Valor devuelto

El valor recuperado que se almacena en *Atom*.

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, entre otras barreras de un subproceso de llamada que tienen identificadores de señales que se ejecutan en el mismo subproceso.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*\
Restricción de ordenación de memoria que determina el tipo de barrera.

### <a name="remarks"></a>Observaciones

El Order argumento determina el tipo *de* valla.

|||
|-|-|
|`memory_order_relaxed`|La barrera no tiene ningún efecto.|
|`memory_order_consume`|Es una barrera de adquisición.|
|`memory_order_acquire`|Es una barrera de adquisición.|
|`memory_order_release`|Es una barrera de liberación.|
|`memory_order_acq_rel`|Es una barrera de adquisición y de liberación.|
|`memory_order_seq_cst`|Es una barrera de adquisición y de liberación, y es coherente secuencialmente.|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

Almacena de forma atómica un valor en un objeto atómico.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parámetros

*Átomo*\
Puntero a un objeto atomic que contiene un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

### <a name="remarks"></a>Observaciones

`atomic_store`almacena *Value* en el objeto al que `memory_order_seq_cst`apunta *Atom*, dentro de la restricción [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

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

*Átomo*\
Puntero a un objeto `atomic` que contiene un valor de tipo `Ty`.

*Valor*\
Valor de tipo `Ty`.

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_consume`, `memory_order_acquire` ni `memory_order_acq_rel`.

### <a name="remarks"></a>Observaciones

`atomic_store`almacena *Value* en el objeto al que `memory_order` apunta *Atom*, dentro del especificado por *Order*.

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, sin una operación atómica asociada.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*\
Restricción de ordenación de memoria que determina el tipo de barrera.

### <a name="remarks"></a>Observaciones

El Order argumento determina el tipo *de* valla.

|||
|-|-|
|`memory_order_relaxed`|La barrera no tiene ningún efecto.|
|`memory_order_consume`|Es una barrera de adquisición.|
|`memory_order_acquire`|Es una barrera de adquisición.|
|`memory_order_release`|Es una barrera de liberación.|
|`memory_order_acq_rel`|Es una barrera de adquisición y de liberación.|
|`memory_order_seq_cst`|Es una barrera de adquisición y de liberación, y es coherente secuencialmente.|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

Quita una dependencia.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parámetros

*Arg*\
Valor de tipo `Ty`.

### <a name="return-value"></a>Valor devuelto

El valor devuelto es *Arg*. La evaluación de *Arg* no lleva una dependencia a la llamada de función. Al romper una posible cadena de dependencia, la función podría permitir que el compilador generara código más eficaz.

## <a name="see-also"></a>Consulte también

[\<>atómica](../standard-library/atomic.md)
