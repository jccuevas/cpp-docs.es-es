---
title: Funciones &lt;atomic&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 3b10205d490f9ac7a4f69ef01fc0da30fe7012ed
ms.lasthandoff: 02/24/2017

---
# <a name="ltatomicgt-functions"></a>Funciones &lt;atomic&gt;
||||  
|-|-|-|  
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong_function)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit_function)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak_function)|  
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit_function)|[atomic_exchange](#atomic_exchange_function)|[atomic_exchange_explicit](#atomic_exchange_explicit_function)|  
|[atomic_fetch_add](#atomic_fetch_add_function)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit_function)|[atomic_fetch_and](#atomic_fetch_and_function)|  
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit_function)|[atomic_fetch_or](#atomic_fetch_or_function)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit_function)|  
|[atomic_fetch_sub](#atomic_fetch_sub_function)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit_function)|[atomic_fetch_xor](#atomic_fetch_xor_function)|  
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit_function)|[atomic_flag_clear](#atomic_flag_clear_function)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit_function)|  
|[atomic_flag_test_and_set](#atomic_flag_test_and_set_function)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit_function)|[atomic_init](#atomic_init_function)|  
|[atomic_is_lock_free](#atomic_is_lock_free_function)|[atomic_load](#atomic_load_function)|[atomic_load_explicit](#atomic_load_explicit_function)|  
|[atomic_signal_fence](#atomic_signal_fence_function)|[atomic_store](#atomic_store_function)|[atomic_store_explicit](#atomic_store_explicit_function)|  
|[atomic_thread_fence](#atomic_thread_fence_function)|[kill_dependency](#kill_dependency_function)|  
  
##  <a name="a-nameatomiccompareexchangestrongfunctiona--atomiccompareexchangestrong"></a><a name="atomic_compare_exchange_strong_function"></a>  atomic_compare_exchange_strong  
 Realiza una operación atómica de comparación e intercambio.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.  
  
 `Exp`  
 Puntero a un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
### <a name="return-value"></a>Valor devuelto  
 Número `bool` que indica el resultado de la comparación de valores.  
  
### <a name="remarks"></a>Comentarios  
 Este método realiza una operación atómica de comparación e intercambio mediante los argumentos implícitos `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Para más información, vea [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit_function).  
  
##  <a name="a-nameatomiccompareexchangestrongexplicitfunctiona--atomiccompareexchangestrongexplicit"></a><a name="atomic_compare_exchange_strong_explicit_function"></a>  atomic_compare_exchange_strong_explicit  
 Realiza una operación *atómica de comparación e intercambio*.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.  
  
 `Exp`  
 Puntero a un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
 `Order1`  
 Primer argumento [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
 `Order2`  
 Segundo argumento `memory_order`. El valor de `Order2` no puede ser `memory_order_release` o `memory_order_acq_rel`, ni puede ser más seguro que el valor de `Order1`.  
  
### <a name="return-value"></a>Valor devuelto  
 Número `bool` que indica el resultado de la comparación de valores.  
  
### <a name="remarks"></a>Comentarios  
 Una *operación atómica de comparación e intercambio* compara el valor almacenado en el objeto al que apunta `Atom` con el valor al que apunta `Exp`. Si los valores son iguales, el valor almacenado en el objeto al que apunta `atom` se sustituye por `Val` mediante el uso de una operación `read-modify-write` y la aplicación de las restricciones de ordenación de memoria especificadas por `Order1`. Si los valores no son iguales, la operación sustituye el valor al que apunta `Exp` por el valor almacenado en el objeto al que apunta `Atom` y aplica las restricciones de ordenación de memoria especificadas por `Order2`.  
  
##  <a name="a-nameatomiccompareexchangeweakfunctiona--atomiccompareexchangeweak"></a><a name="atomic_compare_exchange_weak_function"></a>  atomic_compare_exchange_weak  
 Realiza una operación *atómica débil de comparación e intercambio*.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.  
  
 `Exp`  
 Puntero a un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
### <a name="return-value"></a>Valor devuelto  
 Número `bool` que indica el resultado de la comparación de valores.  
  
### <a name="remarks"></a>Comentarios  
 Este método realiza una *operación atómica débil de comparación e intercambio* que tiene argumentos implícitos `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Para más información, vea [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit_function).  
  
##  <a name="a-nameatomiccompareexchangeweakexplicitfunctiona--atomiccompareexchangeweakexplicit"></a><a name="atomic_compare_exchange_weak_explicit_function"></a>  atomic_compare_exchange_weak_explicit  
 Realiza una operación *atómica débil de comparación e intercambio*.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.  
  
 `Exp`  
 Puntero a un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
 `Order1`  
 Primer argumento [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
 `Order2`  
 Segundo argumento `memory_order`. El valor de `Order2` no puede ser `memory_order_release` o `memory_order_acq_rel`, ni puede ser más seguro que el valor de `Order1`.  
  
### <a name="return-value"></a>Valor devuelto  
 Número `bool` que indica el resultado de la comparación de valores.  
  
### <a name="remarks"></a>Comentarios  
 Una *operación atómica de comparación e intercambio* compara el valor almacenado en el objeto al que apunta `Atom` con el valor al que apunta `Exp`. Si los valores son iguales, la operación reemplaza el valor almacenado en el objeto al que apunta `Atom` con `Val` mediante una operación `read-modify-write` y la aplicación de las restricciones de ordenación de memoria especificadas por `Order1`. Si los valores no son iguales, la operación reemplaza el valor al que apunta `Exp` con el valor almacenado en el objeto al que apunta `Atom` y aplica las restricciones de ordenación de memoria especificadas por `Order2`.  
  
 Una operación atómica *débil* de comparación e intercambio realiza un intercambio si los valores comparados son iguales. Sin embargo, si los valores no son iguales, no se garantiza que la operación realice un intercambio.  
  
##  <a name="a-nameatomicexchangefunctiona--atomicexchange"></a><a name="atomic_exchange_function"></a>  atomic_exchange  
 Usa `Value` para sustituir el valor almacenado de `Atom`.  
  
```
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor almacenado de `Atom` antes del intercambio.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_exchange` realiza una operación `read-modify-write` para intercambiar el valor almacenado en `Atom` con `Value` mediante `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="a-nameatomicexchangeexplicitfunctiona--atomicexchangeexplicit"></a><a name="atomic_exchange_explicit_function"></a>  atomic_exchange_explicit  
 Reemplaza el valor almacenado de `Atom` con `Value`.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Valor devuelto  
 Valor almacenado de `Atom` antes del intercambio.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_exchange_explicit` realiza una operación `read-modify-write` para intercambiar el valor almacenado en `Atom` con `Value`, dentro de las restricciones de memoria especificadas por `Order`.  
  
##  <a name="a-nameatomicfetchaddfunctiona--atomicfetchadd"></a><a name="atomic_fetch_add_function"></a>  atomic_fetch_add  
 Agrega un valor a un valor existente almacenado en un objeto `atomic`.  
  
```
template <class T>  
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>  
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.  
  
 `Value`  
 Valor de tipo `ptrdiff_t`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_add` realiza una operación `read-modify-write` para agregar de forma atómica `Value` al valor almacenado en `Atom` mediante la restricción `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
 Si el tipo atómico es `atomic_address`, `Value` tiene un tipo `ptrdiff_t` y la operación trata el puntero almacenado como `char *`.  
  
 Esta operación también está sobrecargada en los tipos de entero:  
  
```
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```  
  
##  <a name="a-nameatomicfetchaddexplicitfunctiona--atomicfetchaddexplicit"></a><a name="atomic_fetch_add_explicit_function"></a>  atomic_fetch_add_explicit  
 Agrega un valor a un valor existente almacenado en un objeto `atomic`.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.  
  
 `Value`  
 Valor de tipo `ptrdiff_t`.  
  
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
  
##  <a name="a-nameatomicfetchandfunctiona--atomicfetchand"></a><a name="atomic_fetch_and_function"></a>  atomic_fetch_and  
 Realiza una operación `and` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.  
  
```
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept; 
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept; 
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `T`.  
  
 `Value`  
 Valor de tipo `T`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_and` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `and` bit a bit de `Value` y el valor actual almacenado en `Atom` con las restricciones `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="a-nameatomicfetchandexplicitfunctiona--atomicfetchandexplicit"></a><a name="atomic_fetch_and_explicit_function"></a>  atomic_fetch_and_explicit  
 Realiza una operación `and` bit a bit de un valor y un valor existente almacenado en un objeto `atomic`.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `T`.  
  
 `Value`  
 Valor de tipo `T`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Valor devuelto  
 Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_and_explicit` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `and` bit a bit de `Value` y el valor actual almacenado en `Atom`, dentro de las restricciones de memoria especificadas por `Order`.  
  
##  <a name="a-nameatomicfetchorfunctiona--atomicfetchor"></a><a name="atomic_fetch_or_function"></a>  atomic_fetch_or  
 Realiza una operación `or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.  
  
```
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `T`.  
  
 `Value`  
 Valor de tipo `T`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_or` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `or` bit a bit de `Value` y el valor actual almacenado en `Atom` con `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="a-nameatomicfetchorexplicitfunctiona--atomicfetchorexplicit"></a><a name="atomic_fetch_or_explicit_function"></a>  atomic_fetch_or_explicit  
 Realiza una operación `or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `T`.  
  
 `Value`  
 Valor de tipo `T`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Valor devuelto  
 Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_or_explicit` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `or` bit a bit de `Value` y el valor actual almacenado en `Atom`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por `Order`.  
  
##  <a name="a-nameatomicfetchsubfunctiona--atomicfetchsub"></a><a name="atomic_fetch_sub_function"></a>  atomic_fetch_sub  
 Resta un valor de un valor existente almacenado en un objeto `atomic`.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.  
  
 `Value`  
 Valor de tipo `ptrdiff_t`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor del puntero incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_sub` realiza una operación `read-modify-write` para restar de forma atómica `Value` del valor almacenado en `Atom` mediante la restricción `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
 Si el tipo atómico es `atomic_address`, `Value` tiene un tipo `ptrdiff_t` y la operación trata el puntero almacenado como `char *`.  
  
 Esta operación también está sobrecargada en los tipos de entero:  
  
```
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```  
  
##  <a name="a-nameatomicfetchsubexplicitfunctiona--atomicfetchsubexplicit"></a><a name="atomic_fetch_sub_explicit_function"></a>  atomic_fetch_sub_explicit  
 Resta un valor de un valor existente almacenado en un objeto `atomic`.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un puntero al tipo `T`.  
  
 `Value`  
 Valor de tipo `ptrdiff_t`.  
  
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
  
##  <a name="a-nameatomicfetchxorfunctiona--atomicfetchxor"></a><a name="atomic_fetch_xor_function"></a>  atomic_fetch_xor  
 Realiza una operación `exclusive or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.  
  
```
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept; 

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `T`.  
  
 `Value`  
 Valor de tipo `T`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_xor` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `exclusive or` bit a bit de `Value` y el valor actual almacenado en `Atom` con `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="a-nameatomicfetchxorexplicitfunctiona--atomicfetchxorexplicit"></a><a name="atomic_fetch_xor_explicit_function"></a>  atomic_fetch_xor_explicit  
 Realiza una operación `exclusive or` bit a bit sobre un valor y un valor existente almacenado en un objeto `atomic`.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `T`.  
  
 `Value`  
 Valor de tipo `T`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Valor devuelto  
 Valor incluido en el objeto atómico inmediatamente antes de que se realizara la operación.  
  
### <a name="remarks"></a>Comentarios  
 La función `atomic_fetch_xor_explicit` realiza una operación `read-modify-write` para sustituir el valor almacenado de `Atom` por una operación `exclusive or` bit a bit de `Value` y el valor actual almacenado en `Atom`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas por `Order`.  
  
##  <a name="a-nameatomicflagclearfunctiona--atomicflagclear"></a><a name="atomic_flag_clear_function"></a>  atomic_flag_clear  
 Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `false`, dentro de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
```
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Flag`  
 Puntero a un objeto `atomic_flag`.  
  
##  <a name="a-nameatomicflagclearexplicitfunctiona--atomicflagclearexplicit"></a><a name="atomic_flag_clear_explicit_function"></a>  atomic_flag_clear_explicit  
 Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `false`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.  
  
```
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Flag`  
 Puntero a un objeto `atomic_flag`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="a-nameatomicflagtestandsetfunctiona--atomicflagtestandset"></a><a name="atomic_flag_test_and_set_function"></a>  atomic_flag_test_and_set  
 Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `true`, dentro de las restricciones de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
```
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Flag`  
 Puntero a un objeto `atomic_flag`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor inicial de `Flag`.  
  
##  <a name="a-nameatomicflagtestandsetexplicitfunctiona--atomicflagtestandsetexplicit"></a><a name="atomic_flag_test_and_set_explicit_function"></a>  atomic_flag_test_and_set_explicit  
 Establece la marca `bool` de un objeto [atomic_flag](../standard-library/atomic-flag-structure.md) en `true`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.  
  
```
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Flag`  
 Puntero a un objeto `atomic_flag`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Valor devuelto  
 Valor inicial de `Flag`.  
  
##  <a name="a-nameatomicinitfunctiona--atomicinit"></a><a name="atomic_init_function"></a>  atomic_init  
 Establece el valor almacenado en un objeto `atomic`.  
  
```
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
### <a name="remarks"></a>Comentarios  
 `atomic_init` no es una operación atómica. No es segura para subprocesos.  
  
##  <a name="a-nameatomicislockfreefunctiona--atomicislockfree"></a><a name="atomic_is_lock_free_function"></a>  atomic_is_lock_free  
 Especifica si las operaciones atómicas sobre un objeto `atomic` *no tienen bloqueos*.  
  
```
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que almacena un valor de tipo `T`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si las operaciones atómicas sobre `Atom` no tienen bloqueos; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Un tipo atómico no tiene bloqueos si ninguna operación atómica sobre ese tipo emplea bloqueos. Si esta función devuelve True, el tipo se puede usar con seguridad en identificadores de señales.  
  
##  <a name="a-nameatomicloadfunctiona--atomicload"></a><a name="atomic_load_function"></a>  atomic_load  
 Recupera el valor almacenado en un objeto `atomic`.  
  
```
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que contiene un valor de tipo `Ty`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor recuperado que se almacena en `Atom`.  
  
### <a name="remarks"></a>Comentarios  
 `atomic_load` usa de forma implícita `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="a-nameatomicloadexplicitfunctiona--atomicloadexplicit"></a><a name="atomic_load_explicit_function"></a>  atomic_load_explicit  
 Recupera el valor almacenado en un objeto `atomic`, dentro de un [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificado.  
  
```
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto `atomic` que contiene un valor de tipo `Ty`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_release` ni `memory_order_acq_rel`.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor recuperado que se almacena en `Atom`.  
  
##  <a name="a-nameatomicsignalfencefunctiona--atomicsignalfence"></a><a name="atomic_signal_fence_function"></a>  atomic_signal_fence  
 Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, entre otras barreras de un subproceso de llamada que tienen identificadores de señales que se ejecutan en el mismo subproceso.  
  
```
inline void atomic_signal_fence(memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Order`  
 Restricción de ordenación de memoria que determina el tipo de barrera.  
  
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
  
##  <a name="a-nameatomicstorefunctiona--atomicstore"></a><a name="atomic_store_function"></a>  atomic_store  
 Almacena de forma atómica un valor en un objeto atómico.  
  
```
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Atom`  
 Puntero a un objeto atomic que contiene un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
### <a name="remarks"></a>Comentarios  
 `atomic_store` almacena `Value` en el objeto al que apunta `Atom`, dentro de la restricción `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="a-nameatomicstoreexplicitfunctiona--atomicstoreexplicit"></a><a name="atomic_store_explicit_function"></a>  atomic_store_explicit  
 Almacena de forma atómica un valor en un objeto atómico.  
  
```
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
 `Atom`  
 Puntero a un objeto `atomic` que contiene un valor de tipo `Ty`.  
  
 `Value`  
 Valor de tipo `Ty`.  
  
 `Order`  
 [memory_order](../standard-library/atomic-enums.md#memory_order_enum). No utilice `memory_order_consume`, `memory_order_acquire` ni `memory_order_acq_rel`.  
  
### <a name="remarks"></a>Comentarios  
 `atomic_store` almacena `Value` en el objeto al que apunta `Atom`, dentro del `memory_order` especificado por `Order`.  
  
##  <a name="a-nameatomicthreadfencefunctiona--atomicthreadfence"></a><a name="atomic_thread_fence_function"></a>  atomic_thread_fence  
 Actúa como una *barrera*, que es un primitivo de sincronización de memoria que aplica ordenación entre operaciones de carga o almacenamiento, sin una operación atómica asociada.  
  
```
inline void atomic_thread_fence(memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Order`  
 Restricción de ordenación de memoria que determina el tipo de barrera.  
  
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
  
##  <a name="a-namekilldependencyfunctiona--killdependency"></a><a name="kill_dependency_function"></a>  kill_dependency  
 Quita una dependencia.  
  
```
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Arg`  
 Valor de tipo `Ty`.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto es `Arg`. La evaluación de `Arg` no tiene una dependencia a la llamada de función. Al romper una posible cadena de dependencia, la función podría permitir que el compilador generara código más eficaz.  
  
## <a name="see-also"></a>Vea también  
 [\<atomic>](../standard-library/atomic.md)




