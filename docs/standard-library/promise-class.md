---
title: promise (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: 13818ef085492087a5f7192f6d42c31c1a5dd8ae
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

|Name|Descripción|
|----------|-----------------|
|[Promise](#promise)|Construye un objeto `promise`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_future](#get_future)|Devuelve un objeto [future](../standard-library/future-class.md) asociado a este compromiso.|
|[set_exception](#set_exception)|Establece de forma atómica el resultado de este compromiso para indicar una excepción.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Establece de forma atómica el resultado de este compromiso para indicar una excepción y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).|
|[set_value](#set_value)|Establece de forma atómica el resultado de este compromiso para indicar un valor.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Establece de forma atómica el resultado de este compromiso para indicar un valor y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).|
|[swap](#swap)|Intercambia el *estado asincrónico asociado* de este compromiso con el de un objeto promise especificado.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[promise::operator=](#op_eq)|Asignación del estado compartido de este objeto promise.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`promise`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<futura >

**Espacio de nombres:** std

## <a name="get_future"></a> promise::get_future

Devuelve un objeto [future](../standard-library/future-class.md) que tiene el mismo *estado asincrónico asociado* que este objeto promise.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Comentarios

Si el objeto promise está vacío, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un [error_code](../standard-library/error-code-class.md) de `no_state`.

Si ya se ha llamado a este método para un objeto promise que tiene el mismo estado asincrónico asociado, el método produce un `future_error` que tiene un `error_code` de `future_already_retrieved`.

## <a name="op_eq"></a> promise::operator=

Transfiere el *estado asincrónico asociado* de un objeto `promise` especificado.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

`Other` Un `promise` objeto.

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Comentarios

Este operador transfiere el estado asincrónico asociado de `Other`. Después de la transferencia, `Other` está *vacío*.

## <a name="promise"></a> promise::promise (Constructor)

Construye un objeto `promise`.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

`Al` Asignador de memoria. Para obtener más información, vea [\<allocators>](../standard-library/allocators-header.md).

`Other` Un `promise` objeto.

### <a name="remarks"></a>Comentarios

El primer constructor crea un objeto `promise` *vacío*.

El segundo constructor crea un objeto `promise` vacío y usa `Al` para la asignación de memoria.

El tercer constructor crea un objeto `promise` y transfiere el estado asincrónico asociado de `Other` y deja `Other` vacío.

## <a name="set_exception"></a> promise::set_exception

Almacena de forma atómica una excepción como resultado de este objeto `promise` y establece el *estado asincrónico asociado* en *listo*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parámetros

`Exc` Un [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que se almacena por este método como el resultado de la excepción.

### <a name="remarks"></a>Comentarios

Si el objeto `promise` no tiene ningún estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) o [set_value_at_thread_exit](#set_value_at_thread_exit) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

Como resultado de este método, se desbloquean todos los subprocesos bloqueados en el estado asincrónico asociado.

## <a name="set_exception_at_thread_exit"></a> promise::set_exception_at_thread_exit

Establece de forma atómica el resultado de este `promise` para indicar una excepción, entregando la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parámetros

`Exc` Un [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que se almacena por este método como el resultado de la excepción.

### <a name="remarks"></a>Comentarios

Si el objeto promise no tiene ningún *estado asincrónico asociado*, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value) o [set_value_at_thread_exit](#set_value_at_thread_exit) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

A diferencia de [set_exception](#set_exception), este método no establece el estado asincrónico asociado en listo hasta que no se han destruido todos los objetos locales de subprocesos del subproceso actual. Normalmente, los subprocesos que están bloqueados en el estado asincrónico asociado no se desbloquean hasta que no se sale del subproceso actual.

## <a name="set_value"></a> promise::set_value

Almacena de forma atómica un valor como resultado de este objeto `promise` y establece el *estado asincrónico asociado* en *listo*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parámetros

`Val` El valor que se almacenará como resultado.

### <a name="remarks"></a>Comentarios

Si el objeto `promise` no tiene ningún estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value` o [set_value_at_thread_exit](#set_value_at_thread_exit) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

Como resultado de este método, se desbloquean todos los subprocesos bloqueados en el estado asincrónico asociado.

El primer método también produce cualquier excepción que se produce cuando se copia `Val` en el estado asincrónico asociado. En esta situación, el estado asincrónico asociado no se establece en ready.

El segundo método también produce cualquier excepción que se produce cuando se mueve `Val` en el estado asincrónico asociado. En esta situación, el estado asincrónico asociado no se establece en ready.

Para la especialización parcial `promise<Ty&>`, el valor almacenado es una referencia a `Val`.

Para la especialización `promise<void>`, no existe ningún valor almacenado.

## <a name="set_value_at_thread_exit"></a> promise::set_value_at_thread_exit

Almacena de forma atómica un valor como resultado de este objeto `promise`.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parámetros

`Val` El valor que se almacenará como resultado.

### <a name="remarks"></a>Comentarios

Si el objeto promise no tiene ningún *estado asincrónico asociado*, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.

Si ya se ha llamado a [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) o `set_value_at_thread_exit` para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.

A diferencia de `set_value`, el estado asincrónico asociado no se establece hasta que no se han destruido todos los objetos de subproceso local del subproceso actual. Normalmente, los subprocesos que están bloqueados en el estado asincrónico asociado no se desbloquean hasta que no se sale del subproceso actual.

El primer método también produce cualquier excepción que se produce cuando se copia `Val` en el estado asincrónico asociado.

El segundo método también produce cualquier excepción que se produce cuando se mueve `Val` en el estado asincrónico asociado.

Para la especialización parcial `promise<Ty&>`, el valor almacenado es una referencia a `Val`.

Para la especialización `promise<void>`, no existe ningún valor almacenado.

## <a name="swap"></a> promise::swap

Intercambia el *estado asincrónico asociado* de este objeto promise por el de un objeto especificado.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

`Other` Un `promise` objeto.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
