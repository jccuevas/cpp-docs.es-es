---
title: atomic (Estructura) | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7308c127bebd2185429509315ebafb3d83a7efea
ms.sourcegitcommit: b0d5557dbb57128da560a0a4634312ec4a050a90
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
---
# <a name="atomic-structure"></a>atomic (Estructura)

Describe un objeto que realiza operaciones atómicas sobre un valor almacenado de tipo *Ty*.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Miembros

|Miembro|Descripción|
|----------|-----------------|
|**Constructor**||
|[atomic](#atomic)|Construye un objeto atómico.|
|**Operadores**||
|[atomic:: operator Ty](#op_ty)|Lee y devuelve el valor almacenado. ([atomic:: Load](#load))|
|[atomic:: operator =](#op_eq)|Utiliza un valor especificado para reemplazar el valor almacenado. ([atomic:: Store](#store))|
|[atomic:: operator ++](#op_inc)|Incrementa el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic:: operator +=](#op_add_eq)|Suma un valor especificado al valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic:: operator--](#op_dec)|Disminuye el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic:: operator =](#op_sub_eq)|Resta un valor especificado del valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.|
|[atomic:: operator & =](#op_and_eq)|Realiza un bit a bit y en un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|
|[atomic:: operator&#124;=](#op_or_eq)|Realiza un bit a bit o en un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|
|[atomic:: operator ^ =](#op_xor_eq)|Realiza un exclusivo bit a bit o en un valor especificado y el valor almacenado. Solo lo utilizan las especializaciones de entero.|
|**Funciones**||
|[compare_exchange_strong](#compare_exchange_strong)|Realiza una *atomic_compare_and_exchange* operación en **esto** y devuelve el resultado.|
|[compare_exchange_weak](#compare_exchange_weak)|Realiza una *weak_atomic_compare_and_exchange* operación en **esto** y devuelve el resultado.|
|[fetch_add](#fetch_add)|Suma un valor especificado al valor almacenado.|
|[fetch_and](#fetch_and)|Realiza un bit a bit y en un valor especificado y el valor almacenado.|
|[fetch_or](#fetch_or)|Realiza un bit a bit o en un valor especificado y el valor almacenado.|
|[fetch_sub](#fetch_sub)|Resta un valor especificado del valor almacenado.|
|[fetch_xor](#fetch_xor)|Realiza un exclusivo bit a bit o en un valor especificado y el valor almacenado.|
|[is_lock_free](#is_lock_free)|Especifica si las operaciones atómicas de **esto** son *bloqueos*. Un tipo atómico *no tiene bloqueos* si ninguna operación atómica sobre ese tipo emplea bloqueos.|
|[Carga](#load)|Lee y devuelve el valor almacenado.|
|[store](#store)|Utiliza un valor especificado para reemplazar el valor almacenado.|

## <a name="remarks"></a>Comentarios

El tipo *Ty* debe ser *copiar de forma trivial*. Es decir, usando [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) copiar sus bytes debe generar válido *Ty* objeto que es igual al objeto original. El [compare_exchange_weak](#compare_exchange_weak) y [compare_exchange_strong](#compare_exchange_strong) funciones miembro utilizan [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) para determinar si dos *Ty* valores son iguales. Estas funciones no utilizarán un *Ty*-definido **operador ==**. Las funciones miembro de **atómica** usar **memcpy** se copian los valores de tipo *Ty*.

Una especialización parcial, **atómica\<Ty \* >** , existe para todos los tipos de puntero. La especialización permite sumar un desplazamiento al valor del puntero administrado o restar un desplazamiento del mismo. Las operaciones aritméticas toman un argumento de tipo **ptrdiff_t** y ajustan ese argumento según el tamaño de *Ty* sea coherente con la aritmética normal de dirección.

Existe una especialización para cada tipo integral excepto **bool**. Cada especialización proporciona un conjunto completo de métodos para operaciones aritméticas y lógicas atómicas.

||||
|-|-|-|
|**atomic\<char >**|**atomic\<firmado char >**|**atomic\<unsigned char >**|
|**atomic\<char16_t >**|**atomic\<char32_t >**|**atomic\<wchar_t >**|
|**atomic\<corto >**|**atomic\<entero corto sin signo >**|**atomic\<int >**|
|**atomic\<int sin signo >**|**atomic\<largo >**|**atomic\<largo sin signo >**|
|**atomic\<long long >**|**atomic\<unsigned long long >**|

Las especializaciones de entero se derivan correspondiente **atomic_integral** tipos. Por ejemplo, **atómica\<int sin signo >** se deriva de **atomic_uint**.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<atómica >

**Espacio de nombres:** std

## <a name="atomic"></a> atomic::Atomic

Construye un objeto atómico.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Valor de inicialización.

### <a name="remarks"></a>Comentarios

Los objetos atómicos no se puede copiar o mover.

Objetos que son creaciones de instancias de atomic\<*Ty*> solo puede inicializar el constructor que toma un argumento de tipo *Ty* y no mediante la inicialización de agregado. Sin embargo, se pueden inicializar objetos atomic_integral solo mediante la inicialización agregada.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> atomic:: operator *Ty*

El operador para el tipo especificado a la plantilla, de forma atómica\<*Ty*>. Recupera el valor almacenado en  **\*esto**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Comentarios

Este operador se aplica el **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_eq"></a> atomic:: operator =

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

*Valor*<br/>
A *Ty* objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve *valor*.

## <a name="op_inc"></a> atomic:: operator ++

Incrementa el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Los dos primeros operadores devuelven el valor incrementado; los dos últimos operadores devuelven el valor antes del incremento. Los operadores utilizan el **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a> atomic:: operator +=

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

*Valor*<br/>
Un valor entero o puntero.

### <a name="return-value"></a>Valor devuelto

A *Ty* objeto que contiene el resultado de la suma.

### <a name="remarks"></a>Comentarios

Este operador se utiliza el **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_dec"></a> atomic:: operator--

Disminuye el valor almacenado. Solo lo utilizan las especializaciones de entero y de puntero.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Los dos primeros operadores devuelven el valor reducido; los dos últimas operadores devuelven el valor antes de que el decremento. Los operadores utilizan el **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a> atomic:: operator =

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

*Valor*<br/>
Un valor entero o puntero.

### <a name="return-value"></a>Valor devuelto

A *Ty* objeto que contiene el resultado de la resta.

### <a name="remarks"></a>Comentarios

Este operador se utiliza el **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a> atomic:: operator & =

Realiza un bit a bit y en un valor especificado y el valor almacenado de  **\*esto**. Solo lo utilizan las especializaciones de entero.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Un valor de tipo *Ty*.

### <a name="return-value"></a>Valor devuelto

El resultado de bit a bit y.

### <a name="remarks"></a>Comentarios

Este operador realiza una operación de lectura, modificación y escritura para reemplazar el valor almacenado de  **\*esto** con un bit a bit y de *valor* y el valor actual que se almacena en  **\*esto**, dentro de las restricciones de la **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a> atomic:: operator&#124;=

Realiza un bit a bit o en un valor especificado y el valor almacenado de  **\*esto**. Solo lo utilizan las especializaciones de entero.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Un valor de tipo *Ty*.

### <a name="return-value"></a>Valor devuelto

El resultado de bit a bit o.

### <a name="remarks"></a>Comentarios

Este operador realiza una operación de lectura, modificación y escritura para reemplazar el valor almacenado de  **\*esto** con un bit a bit o de *valor* y el valor actual que se almacena en  **\*esto**, dentro de las restricciones de la **memory_order_seq_cst** [memory_order](atomic-enums.md) restricciones.

## <a name="op_xor_eq"></a> atomic:: operator ^ =

Realiza un exclusivo bit a bit o en un valor especificado y el valor almacenado de  **\*esto**. Solo lo utilizan las especializaciones de entero.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Un valor de tipo *Ty*.

### <a name="return-value"></a>Valor devuelto

El resultado de la exclusivo bit a bit o.

### <a name="remarks"></a>Comentarios

Este operador realiza una operación de lectura, modificación y escritura para reemplazar el valor almacenado de  **\*esto** con un exclusivo bit a bit o de *valor* y el valor actual que se almacena en  **\*esto**, dentro de las restricciones de la **memory_order_seq_cst** [memory_order](atomic-enums.md) restricciones.

## <a name="compare_exchange_strong"></a> atomic:: compare_exchange_strong

Realiza una operación atómica de comparación e intercambio en  **\*esto**.

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

*Exp*<br/>
Un valor de tipo *Ty*.

*Valor*<br/>
Un valor de tipo *Ty*.

*Order1*<br/>
Primer argumento **memory_order**.

*Order2*<br/>
Segundo **memory_order** argumento.

### <a name="return-value"></a>Valor devuelto

A **bool** que indica el resultado de la comparación de valores.

### <a name="remarks"></a>Comentarios

Esta operación atómica de comparación e intercambio compara el valor que se almacena en  **\*esto** con *Exp*. Si los valores son iguales, la operación reemplaza el valor que se almacena en  **\*esto** con *valor* mediante una operación de lectura, modificación y escritura y aplica las restricciones de ordenación de memoria que están especificado por *Order1*. Si los valores no son iguales, la operación utiliza el valor que se almacena en  **\*esto** para reemplazar *Exp* y aplica las restricciones de ordenación de memoria especificadas por *Order2* .

Las sobrecargas que no tienen un segundo **memory_order** usar implícita *Order2* que se basa en el valor de *Order1*. Si *Order1* es **memory_order_acq_rel**, *Order2* es **memory_order_acquire**. Si *Order1* es **memory_order_release**, *Order2* es **memory_order_relaxed**. En todos los demás casos, *Order2* es igual a *Order1*.

Para las sobrecargas que toman dos **memory_order** parámetros, el valor de *Order2* no debe ser **memory_order_release** o **memory_order_acq_rel**y no debe ser mayor que el valor de *Order1*.

## <a name="compare_exchange_weak"></a> atomic:: compare_exchange_weak

Realiza una operación de comparación e intercambio atómica débil en  **\*esto**.

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

*Exp*<br/>
Un valor de tipo *Ty*.

*Valor*<br/>
Un valor de tipo *Ty*.

*Order1*<br/>
Primer argumento **memory_order**.

*Order2*<br/>
Segundo **memory_order** argumento.

### <a name="return-value"></a>Valor devuelto

A **bool** que indica el resultado de la comparación de valores.

### <a name="remarks"></a>Comentarios

Esta operación atómica de comparación e intercambio compara el valor que se almacena en  **\*esto** con *Exp*. Si los valores son iguales, la operación reemplaza el valor que se almacena en  **\*esto** con*valor* mediante una operación de lectura, modificación y escritura y aplica las restricciones de ordenación de memoria que están especificado por *Order1*. Si los valores no son iguales, la operación utiliza el valor que se almacena en  **\*esto** para reemplazar *Exp* y aplica las restricciones de ordenación de memoria especificadas por *Order2* .

Compara una débil atómica y operación de intercambio realiza un intercambio si los valores comparados son iguales. Si los valores no son iguales, no se garantiza que la operación realice un intercambio.

Las sobrecargas que no tienen un segundo **memory_order** usar implícita *Order2* que se basa en el valor de *Order1*. Si *Order1* es **memory_order_acq_rel**, *Order2* es **memory_order_acquire**. Si *Order1* es **memory_order_release**, *Order2* es **memory_order_relaxed**. En todos los demás casos, *Order2* es igual a *Order1*.

Para las sobrecargas que toman dos **memory_order** parámetros, el valor de *Order2* no debe ser **memory_order_release** o **memory_order_acq_rel**y no debe ser mayor que el valor de *Order1*.

## <a name="exchange"></a> atomic:: Exchange

Usa un valor especificado para reemplazar el valor almacenado de  **\*esto**.

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

*Valor*<br/>
Un valor de tipo *Ty*.

*Orden*<br/>
**memory_order**.

### <a name="return-value"></a>Valor devuelto

El valor almacenado de  **\*esto** antes del intercambio.

### <a name="remarks"></a>Comentarios

Esta operación realiza una operación de lectura, modificación y escritura que se utilizará *valor* para reemplazar el valor que se almacena en  **\*esto**, dentro de las restricciones de memoria especificadas por  *Orden*.

## <a name="fetch_add"></a> atomic:: fetch_add

Obtiene el valor almacenado en  **\*esto**y, a continuación, agrega un valor especificado para el valor almacenado.

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

*Valor*<br/>
Un valor de tipo *Ty*.

*Orden*<br/>
**memory_order**.

### <a name="return-value"></a>Valor devuelto

A *Ty* objeto que contiene el valor almacenado en  **\*esto** antes de agregar.

### <a name="remarks"></a>Comentarios

El **fetch_add** método realiza una operación de lectura, modificación y escritura para agregar de forma atómica *valor* con el valor almacenado en  **\*esto**y se aplica a la memoria las restricciones que se especifican mediante *orden*.

## <a name="fetch_and"></a> atomic:: fetch_and

Realiza un bit a bit y en un valor y un valor existente en la que se almacena en  **\*esto**.

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

*Valor*<br/>
Un valor de tipo *Ty*.

*Orden*<br/>
**memory_order**.

### <a name="return-value"></a>Valor devuelto

A *Ty* objeto que contiene el resultado de bit a bit y.

### <a name="remarks"></a>Comentarios

El **fetch_and** método realiza una operación de lectura, modificación y escritura para reemplazar el valor almacenado de  **\*esto** con un bit a bit y de *valor* y actual valor que se almacena en  **\*esto**, dentro de las restricciones de memoria especificadas por *orden*.

## <a name="fetch_or"></a> atomic:: fetch_or

Realiza un bit a bit o en un valor y un valor existente en la que se almacena en  **\*esto**.

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

*Valor*<br/>
Un valor de tipo *Ty*.

*Orden*<br/>
**memory_order**.

### <a name="return-value"></a>Valor devuelto

A *Ty* objeto que contiene el resultado de bit a bit o.

### <a name="remarks"></a>Comentarios

El **fetch_or** método realiza una operación de lectura, modificación y escritura para reemplazar el valor almacenado de  **\*esto** con un bit a bit o de *valor* y el valor actual que se almacena en  **\*esto**, dentro de las restricciones de memoria especificadas por *orden*.

## <a name="fetch_sub"></a> atomic:: fetch_sub

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

*Valor*<br/>
Un valor de tipo *Ty*.

*Orden*<br/>
**memory_order**.

### <a name="return-value"></a>Valor devuelto

A *Ty* objeto que contiene el resultado de la resta.

### <a name="remarks"></a>Comentarios

El **fetch_sub** método realiza una operación de lectura, modificación y escritura que se resta de forma atómica *valor* del valor almacenado en  **\*esto**, dentro de la memoria las restricciones que se especifican mediante *orden*.

## <a name="fetch_xor"></a> atomic:: fetch_xor

Realiza un exclusivo bit a bit o en un valor y un valor existente en la que se almacena en  **\*esto**.

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

*Valor*<br/>
Un valor de tipo *Ty*.

*Orden*<br/>
**memory_order**.

### <a name="return-value"></a>Valor devuelto

A *Ty* objeto que contiene el resultado de la exclusivo bit a bit o.

### <a name="remarks"></a>Comentarios

El **fetch_xor** método realiza una operación de lectura, modificación y escritura para reemplazar el valor almacenado de  **\*esto** con un exclusivo bit a bit o de *valor* y valor actual que se almacena en  **\*esto**y aplica las restricciones de memoria especificadas por *orden*.

## <a name="is_lock_free"></a> atomic:: is_lock_free

Especifica si las operaciones atómicas de  **\*esto** son bloqueos.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Valor devuelto

True si atómica operaciones en  **\*esto** son bloqueo libre; en caso contrario, false.

### <a name="remarks"></a>Comentarios

Un tipo atómico es libre de bloqueo si ninguna operación atómica sobre ese tipo utiliza bloqueos.

## <a name="load"></a> atomic:: Load

Recupera el valor almacenado en  **\*esto**, dentro de las restricciones de memoria especificada.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*<br/>
**memory_order**. *Orden* no debe ser **memory_order_release** o **memory_order_acq_rel**.

### <a name="return-value"></a>Valor devuelto

El valor recuperado que se almacena en  **\*esto**.

## <a name="store"></a> atomic:: Store

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

*Valor*<br/>
A *Ty* objeto.

*Orden*<br/>
A **memory_order** restricción.

### <a name="remarks"></a>Comentarios

Esta función miembro almacena de forma atómica *valor* en `*this`, dentro de las restricciones de memoria especificadas por *orden*.

## <a name="see-also"></a>Vea también

[\<atomic>](../standard-library/atomic.md)<br/>
[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
