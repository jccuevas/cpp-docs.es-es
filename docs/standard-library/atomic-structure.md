---
title: atomic (Estructura)
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 1b3b60d71fcdf68fdf215820535c3bfb3d4dfb2b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456732"
---
# <a name="atomic-structure"></a>atomic (Estructura)

Describe un objeto que realiza operaciones atómicas en un valor almacenado de tipo *Ty*.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Miembros

|Member|DESCRIPCIÓN|
|----------|-----------------|
|**Constructor**||
|[atomic](#atomic)|Construye un objeto atómico.|
|**Operadores**||
|[Atomic:: Operator Ty](#op_ty)|Lee y devuelve el valor almacenado. ([Atomic:: Load](#load))|
|[atomic::operator=](#op_eq)|Utiliza un valor especificado para reemplazar el valor almacenado. ([atomic::store](#store))|
|[atomic::operator++](#op_inc)|Incrementa el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic::operator+=](#op_add_eq)|Suma un valor especificado al valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic::operator--](#op_dec)|Disminuye el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic::operator-=](#op_sub_eq)|Resta un valor especificado del valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic::operator&=](#op_and_eq)|Realiza una operación and bit a bit en un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|
|[atomic::operator&#124;=](#op_or_eq)|Realiza una operación OR bit a bit en un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|
|[atomic::operator^=](#op_xor_eq)|Realiza una operación exclusiva OR bit a bit en un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|
|**Funciones**||
|[compare_exchange_strong](#compare_exchange_strong)|Realiza una operación *atomic_compare_and_exchange* en **este** y devuelve el resultado.|
|[compare_exchange_weak](#compare_exchange_weak)|Realiza una operación *weak_atomic_compare_and_exchange* en **este** y devuelve el resultado.|
|[fetch_add](#fetch_add)|Suma un valor especificado al valor almacenado.|
|[fetch_and](#fetch_and)|Realiza una operación and bit a bit en un valor especificado y el valor almacenado.|
|[fetch_or](#fetch_or)|Realiza una operación OR bit a bit en un valor especificado y el valor almacenado.|
|[fetch_sub](#fetch_sub)|Resta un valor especificado del valor almacenado.|
|[fetch_xor](#fetch_xor)|Realiza una operación exclusiva OR bit a bit en un valor especificado y el valor almacenado.|
|[is_lock_free](#is_lock_free)|Especifica si las operaciones atómicas en **esto** son *sin bloqueos*. Un tipo atómico *no tiene bloqueos* si ninguna operación atómica sobre ese tipo emplea bloqueos.|
|[load](#load)|Lee y devuelve el valor almacenado.|
|[store](#store)|Utiliza un valor especificado para reemplazar el valor almacenado.|

## <a name="remarks"></a>Comentarios

El tipo *Ty* se debe poder copiar de forma *trivial*. Es decir, el uso de [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) para copiar sus bytes debe generar un objeto *Ty* válido que compare igual al objeto original. Las funciones miembro [compare_exchange_weak](#compare_exchange_weak) y [compare_exchange_strong](#compare_exchange_strong) usan [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) para determinar si dos valores *Ty* son iguales. Estas funciones no utilizarán un definido por `operator==`Ty. Las funciones miembro de `atomic` utilizan `memcpy` para copiar valores de tipo *Ty*.

Existe una especialización parcial **,\<Atomic \*Ty >** , para todos los tipos de puntero. La especialización permite sumar un desplazamiento al valor del puntero administrado o restar un desplazamiento del mismo. Las operaciones aritméticas toman un argumento de `ptrdiff_t` tipo y ajustan ese argumento según el tamaño de *Ty* para ser coherente con la aritmética de dirección normal.

Existe una especialización para cada tipo entero excepto **bool**. Cada especialización proporciona un conjunto completo de métodos para operaciones aritméticas y lógicas atómicas.

||||
|-|-|-|
|**carácter\<atómico >**|**carácter\<> con signo atómico**|**carácter\<atómico sin signo >**|
|**atomic\<char16_t>**|**atomic\<char32_t>**|**atomic\<wchar_t>**|
|**atomic\<short>**|**>\<corto sin signo atómico**|**atomic\<int>**|
|**int\<sin signo atómico >**|**atomic\<long>**|**Atomic\<unsigned Long >**|
|**larga\<> atómica**|**Atomic\<unsigned Long Long >**|

Las especializaciones de entero se derivan de los tipos `atomic_integral` correspondientes. Por ejemplo, el valor **int sin signo\<atómico >** se deriva `atomic_uint`de.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> atómico

**Espacio de nombres:** std

## <a name="atomic"></a>Atomic:: Atomic

Construye un objeto atómico.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de inicialización.

### <a name="remarks"></a>Comentarios

Los objetos atómicos no se puede copiar o mover.

Los objetos que son instancias de >\<atómicas de*Ty*solo se pueden inicializar mediante el constructor que toma un argumento de tipo *Ty* y no mediante la inicialización de agregado. Sin embargo, los objetos atomic_integral solo se pueden inicializar mediante la inicialización de agregado.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a>Atomic:: Operator *Ty*

Operador del tipo especificado en la plantilla\<, >*atómico*. Recupera el valor almacenado en  **\*este**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Comentarios

Este operador aplica `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_eq"></a>Atomic:: Operator =

Almacena un valor especificado.

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Objeto *Ty* .

### <a name="return-value"></a>Valor devuelto

Devuelve el *valor*.

## <a name="op_inc"></a>Atomic:: Operator + +

Incrementa el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Los dos primeros operadores devuelven el valor incrementado; los dos últimos operadores devuelven el valor anterior al incremento. Los operadores usan `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a>Atomic:: Operator + =

Suma un valor especificado al valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Un valor entero o de puntero.

### <a name="return-value"></a>Valor devuelto

Objeto *Ty* que contiene el resultado de la suma.

### <a name="remarks"></a>Comentarios

Este operador usa `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_dec"></a>Atomic:: Operator--

Disminuye el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Los dos primeros operadores devuelven el valor disminuido; los dos últimos operadores devuelven el valor antes de la reducción. Los operadores usan `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a>Atomic:: Operator-=

Resta un valor especificado del valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Un valor entero o de puntero.

### <a name="return-value"></a>Valor devuelto

Objeto *Ty* que contiene el resultado de la resta.

### <a name="remarks"></a>Comentarios

Este operador usa `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a>Atomic:: operator & =

Realiza una operación and bit a bit en un valor especificado y el valor almacenado de  **\*este**. Solo lo utilizan las especializaciones de entero.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

### <a name="return-value"></a>Valor devuelto

Resultado de la operación and bit a bit.

### <a name="remarks"></a>Comentarios

Este operador realiza una operación de lectura y modificación y escritura para reemplazar el valor almacenado de  **\*este** con un operador and bit a bit de *valor* y el valor actual almacenado en  **\*este**, dentro de las restricciones de la `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a>Atomic:: Operator&#124;=

Realiza una operación OR bit a bit en un valor especificado y el valor almacenado de  **\*este**. Solo lo utilizan las especializaciones de entero.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

### <a name="return-value"></a>Valor devuelto

Resultado de la operación OR bit a bit.

### <a name="remarks"></a>Comentarios

Este operador realiza una operación de lectura y modificación y escritura para reemplazar el valor almacenado de  **\*este** con una operación OR bit a bit de *valor* y el valor actual almacenado en  **\*este**, dentro de las restricciones de la `memory_order_seq_cst`restricciones de [memory_order](atomic-enums.md) .

## <a name="op_xor_eq"></a>Atomic:: Operator ^ =

Realiza una operación exclusiva OR bit a bit en un valor especificado y el valor almacenado de  **\*este**. Solo lo utilizan las especializaciones de entero.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

### <a name="return-value"></a>Valor devuelto

Resultado de la operación OR exclusiva bit a bit.

### <a name="remarks"></a>Comentarios

Este operador realiza una operación de lectura y modificación y escritura para reemplazar el valor almacenado de  **\*este** con un *valor* or exclusivo bit a bit y el valor actual almacenado en  **\*este**, dentro de las restricciones de la restricciones de [memory_order.](atomic-enums.md) `memory_order_seq_cst`

## <a name="compare_exchange_strong"></a>Atomic:: compare_exchange_strong

Realiza una operación atómica de comparación e intercambio en  **\*este**.

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Consumo*\
Valor de tipo *Ty*.

*Valor*\
Valor de tipo *Ty*.

*Order1*\
Primer `memory_order` argumento.

*Order2*\
Segundo argumento `memory_order`.

### <a name="return-value"></a>Valor devuelto

Un valor **booleano** que indica el resultado de la comparación de valores.

### <a name="remarks"></a>Comentarios

Esta operación atómica de comparación e intercambio compara el valor almacenado en  **\*este** con *exp*. Si los valores son iguales, la operación reemplaza el valor almacenado en  **\*este** con el *valor* mediante una operación de lectura-modificación y escritura y aplica las restricciones de orden de memoria especificadas por *Order1*. Si los valores no son iguales, la operación utiliza el valor almacenado en  **\*este** para reemplazar *exp* y aplica las restricciones de orden de memoria especificadas por *Order2*.

Las sobrecargas que no tienen un segundo `memory_order` usan un *Order2* implícito que se basa en el valor de *Order1*. Si *Order1* es `memory_order_acq_rel`, *Order2* es `memory_order_acquire`. Si *Order1* es `memory_order_release`, *Order2* es `memory_order_relaxed`. En todos los demás casos, *Order2* es igual a *Order1*.

En el caso de las sobrecargas que toman `memory_order` dos parámetros, el valor de `memory_order_release` *Order2* no debe ser o `memory_order_acq_rel`y no debe ser más seguro que el valor de *Order1*.

## <a name="compare_exchange_weak"></a>Atomic:: compare_exchange_weak

Realiza una operación atómica débil de comparación e intercambio en  **\*este**.

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Consumo*\
Valor de tipo *Ty*.

*Valor*\
Valor de tipo *Ty*.

*Order1*\
Primer `memory_order` argumento.

*Order2*\
Segundo argumento `memory_order`.

### <a name="return-value"></a>Valor devuelto

Un valor **booleano** que indica el resultado de la comparación de valores.

### <a name="remarks"></a>Comentarios

Esta operación atómica de comparación e intercambio compara el valor almacenado en  **\*este** con *exp*. Si los valores son iguales, la operación reemplaza el valor almacenado en  **\*este** con el*valor* mediante una operación de lectura-modificación y escritura y aplica las restricciones de orden de memoria especificadas por *Order1*. Si los valores no son iguales, la operación utiliza el valor almacenado en  **\*este** para reemplazar *exp* y aplica las restricciones de orden de memoria especificadas por *Order2*.

Una operación atómica débil de comparación e intercambio realiza un intercambio si los valores comparados son iguales. Si los valores no son iguales, no se garantiza que la operación realice un intercambio.

Las sobrecargas que no tienen un segundo `memory_order` usan un *Order2* implícito que se basa en el valor de *Order1*. Si *Order1* es `memory_order_acq_rel`, *Order2* es `memory_order_acquire`. Si *Order1* es `memory_order_release`, *Order2* es `memory_order_relaxed`. En todos los demás casos, *Order2* es igual a *Order1*.

En el caso de las sobrecargas que toman `memory_order` dos parámetros, el valor de `memory_order_release` *Order2* no debe ser o `memory_order_acq_rel`y no debe ser más seguro que el valor de *Order1*.

## <a name="exchange"></a>Atomic:: Exchange

Utiliza un valor especificado para reemplazar el valor almacenado de  **\*este**.

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

*Orden*\
Objeto `memory_order`.

### <a name="return-value"></a>Valor devuelto

Valor almacenado de  **\*este** antes del intercambio.

### <a name="remarks"></a>Comentarios

Esta operación realiza una operación de lectura-modificación-escritura para usar el *valor* para reemplazar el valor almacenado en  **\*este**, dentro de las restricciones de memoria especificadas por *orden*.

## <a name="fetch_add"></a>Atomic:: fetch_add

Recupera el valor almacenado en  **\*este**y, a continuación, agrega un valor especificado al valor almacenado.

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

*Orden*\
Objeto `memory_order`.

### <a name="return-value"></a>Valor devuelto

Objeto *Ty* que contiene el valor almacenado en  **\*esta** antes de la suma.

### <a name="remarks"></a>Comentarios

El `fetch_add` método realiza una operación de lectura y modificación y escritura para agregar de forma atómica *valor* al valor almacenado en  **\*este**objeto y aplica las restricciones de memoria especificadas por el *orden*.

## <a name="fetch_and"></a>Atomic:: fetch_and

Realiza una operación and bit a bit en un valor y un valor existente almacenado en  **\*este**.

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

*Orden*\
Objeto `memory_order`.

### <a name="return-value"></a>Valor devuelto

Objeto *Ty* que contiene el resultado de la operación and bit a bit.

### <a name="remarks"></a>Comentarios

El `fetch_and` método realiza una operación de lectura y modificación y escritura para reemplazar el valor almacenado de  **\*este** con un operador and bit a bit de *valor* y el valor actual almacenado en  **\*este**, dentro de la memoria. restricciones que se especifican por *orden*.

## <a name="fetch_or"></a>Atomic:: fetch_or

Realiza una operación OR bit a bit en un valor y un valor existente almacenado en  **\*este**.

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

*Orden*\
Objeto `memory_order`.

### <a name="return-value"></a>Valor devuelto

Objeto *Ty* que contiene el resultado de la operación OR bit a bit.

### <a name="remarks"></a>Comentarios

El `fetch_or` método realiza una operación de lectura y modificación y escritura para reemplazar el valor almacenado de  **\*este** con una operación OR bit a bit de un *valor* y el valor actual almacenado en  **\*este**, dentro de la memoria. restricciones que se especifican por *orden*.

## <a name="fetch_sub"></a>Atomic:: fetch_sub

Resta un valor especificado del valor almacenado.

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

*Orden*\
Objeto `memory_order`.

### <a name="return-value"></a>Valor devuelto

Objeto *Ty* que contiene el resultado de la resta.

### <a name="remarks"></a>Comentarios

El `fetch_sub` método realiza una operación de lectura-modificación-escritura para restar de forma atómica el *valor* del valor almacenado en  **\*este**, dentro de las restricciones de memoria especificadas por el *orden*.

## <a name="fetch_xor"></a>Atomic:: fetch_xor

Realiza una operación OR exclusiva bit a bit en un valor y un valor existente almacenado en  **\*este**.

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Valor de tipo *Ty*.

*Orden*\
Objeto `memory_order`.

### <a name="return-value"></a>Valor devuelto

Objeto *Ty* que contiene el resultado de la operación OR exclusiva bit a bit.

### <a name="remarks"></a>Comentarios

El `fetch_xor` método realiza una operación de lectura y modificación y escritura para reemplazar el valor almacenado de  **\*este** con un *valor* or exclusivo bit a bit y el valor actual almacenado en  **\*este**, y aplica el restricciones de memoria especificadas por el *orden*.

## <a name="is_lock_free"></a>Atomic:: is_lock_free

Especifica si las operaciones atómicas en  **\*esto** son sin bloqueos.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Valor devuelto

True si las operaciones atómicas en  **\*esto** no tienen bloqueos; en caso contrario, false.

### <a name="remarks"></a>Comentarios

Un tipo atómico no tiene bloqueos si ninguna operación atómica sobre ese tipo utiliza bloqueos.

## <a name="load"></a>Atomic:: Load

Recupera el valor almacenado en  **\*este**, dentro de las restricciones de memoria especificadas.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*\
Objeto `memory_order`. El *orden* no debe `memory_order_release` ser `memory_order_acq_rel`ni.

### <a name="return-value"></a>Valor devuelto

Valor recuperado que se almacena en  **\*este**.

## <a name="store"></a>Atomic:: Store

Almacena un valor especificado.

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*\
Objeto *Ty* .

*Orden*\
`memory_order` Restricción.

### <a name="remarks"></a>Comentarios

Esta función miembro almacena de forma  atómica el `*this`valor en, dentro de las restricciones de memoria especificadas por *orden*.

## <a name="see-also"></a>Vea también

[\<atomic>](../standard-library/atomic.md)\
[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
