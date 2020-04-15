---
title: promise (Clase)
ms.date: 10/18/2018
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.openlocfilehash: a6541fefb2423853f8e59a662e1c8a37777dc14c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323037"
---
# <a name="promise-class"></a>promise (Clase)

Describe un *proveedor asincrónico*.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Promesa](#promise)|Construye un objeto `promise`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_future](#get_future)|Devuelve un objeto [future](../standard-library/future-class.md) asociado a este compromiso.|
|[set_exception](#set_exception)|Establece de forma atómica el resultado de este compromiso para indicar una excepción.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Establece de forma atómica el resultado de este compromiso para indicar una excepción y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).|
|[set_value](#set_value)|Establece de forma atómica el resultado de este compromiso para indicar un valor.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Establece de forma atómica el resultado de este compromiso para indicar un valor y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).|
|[swap](#swap)|Intercambia el *estado asincrónico asociado* de este compromiso con el de un objeto promise especificado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[promesa::operador ?](#op_eq)|Asignación del estado compartido de este objeto promise.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

*Promesa*

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futuro>

**Espacio de nombres:** std

## <a name="promiseget_future"></a><a name="get_future"></a>promesa::get_future

Devuelve un objeto [future](../standard-library/future-class.md) que tiene el mismo *estado asincrónico asociado* que este objeto promise.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Observaciones

Si el objeto promise está vacío, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un [error_code](../standard-library/error-code-class.md) de `no_state`.

Si ya se ha llamado a este método para un objeto promise que tiene el mismo estado asincrónico asociado, el método produce un `future_error` que tiene un `error_code` de `future_already_retrieved`.

## <a name="promiseoperator"></a><a name="op_eq"></a>promesa::operador ?

Transfiere el *estado asincrónico asociado* de un objeto `promise` especificado.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Otro*\
Objeto `promise` .

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Observaciones

Este operador transfiere el estado asincrónico asociado desde *Otro*. Después de la transferencia, *Otro* está *vacío.*

## <a name="promisepromise-constructor"></a><a name="promise"></a>promise::promise Constructor

Construye un objeto `promise`.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Al*\
Asignador de memoria. Consulte los>de [ \<asignadores](../standard-library/allocators-header.md) para obtener más información.

*Otro*\
Objeto `promise` .

### <a name="remarks"></a>Observaciones

El primer constructor construye un objeto *vacío.* `promise`

El segundo constructor construye `promise` un objeto vacío y utiliza *Al* para la asignación de memoria.

El tercer constructor `promise` construye un objeto y transfiere el estado asincrónico asociado de *Other*y deja *Other* vacío.

## <a name="promiseset_exception"></a><a name="set_exception"></a>promesa::set_exception

Almacena de forma atómica una excepción como resultado de este objeto `promise` y establece el *estado asincrónico asociado* en *listo*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parámetros

*Exc*\
[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que este método almacena como el resultado de la excepción.

### <a name="remarks"></a>Observaciones

Si el objeto `promise` no tiene ningún estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) o [set_value_at_thread_exit](#set_value_at_thread_exit) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

Como resultado de este método, se desbloquean todos los subprocesos bloqueados en el estado asincrónico asociado.

## <a name="promiseset_exception_at_thread_exit"></a><a name="set_exception_at_thread_exit"></a>promesa::set_exception_at_thread_exit

Establece de forma atómica el resultado de este `promise` para indicar una excepción, entregando la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parámetros

*Exc*\
[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que este método almacena como el resultado de la excepción.

### <a name="remarks"></a>Observaciones

Si el objeto promise no tiene ningún *estado asincrónico asociado*, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value)o [set_value_at_thread_exit](#set_value_at_thread_exit) para `promise` un objeto `future_error` que tiene el `promise_already_satisfied`mismo estado asincrónico asociado, este método produce un que tiene un código de error de .

A diferencia de [set_exception](#set_exception), este método no establece el estado asincrónico asociado en listo hasta que no se han destruido todos los objetos locales de subprocesos del subproceso actual. Normalmente, los subprocesos que están bloqueados en el estado asincrónico asociado no se desbloquean hasta que no se sale del subproceso actual.

## <a name="promiseset_value"></a><a name="set_value"></a>promesa::set_value

Almacena de forma atómica un valor como resultado de este objeto `promise` y establece el *estado asincrónico asociado* en *listo*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parámetros

*Val*\
Valor que se va a almacenar como resultado.

### <a name="remarks"></a>Observaciones

Si el objeto `promise` no tiene ningún estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value` o [set_value_at_thread_exit](#set_value_at_thread_exit) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

Como resultado de este método, se desbloquean todos los subprocesos bloqueados en el estado asincrónico asociado.

El primer método también produce cualquier excepción que se produce cuando *Val* se copia en el estado asincrónico asociado. En esta situación, el estado asincrónico asociado no se establece en ready.

El segundo método también produce cualquier excepción que se produce cuando *Val* se mueve al estado asincrónico asociado. En esta situación, el estado asincrónico asociado no se establece en ready.

Para la `promise<Ty&>`especialización parcial, el valor almacenado es en efecto una referencia a *Val*.

Para la especialización `promise<void>`, no existe ningún valor almacenado.

## <a name="promiseset_value_at_thread_exit"></a><a name="set_value_at_thread_exit"></a>promesa::set_value_at_thread_exit

Almacena de forma atómica un valor como resultado de este objeto `promise`.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parámetros

*Val*\
Valor que se va a almacenar como resultado.

### <a name="remarks"></a>Observaciones

Si el objeto promise no tiene ningún *estado asincrónico asociado*, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) o `set_value_at_thread_exit` para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

A diferencia de `set_value`, el estado asincrónico asociado no se establece hasta que no se han destruido todos los objetos de subproceso local del subproceso actual. Normalmente, los subprocesos que están bloqueados en el estado asincrónico asociado no se desbloquean hasta que no se sale del subproceso actual.

El primer método también produce cualquier excepción que se produce cuando *Val* se copia en el estado asincrónico asociado.

El segundo método también produce cualquier excepción que se produce cuando *Val* se mueve al estado asincrónico asociado.

Para la `promise<Ty&>`especialización parcial, el valor almacenado es efectivamente una referencia a *Val*.

Para la especialización `promise<void>`, no existe ningún valor almacenado.

## <a name="promiseswap"></a><a name="swap"></a>promesa::swap

Intercambia el *estado asincrónico asociado* de este objeto promise por el de un objeto especificado.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Otro*\
Objeto `promise` .

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
