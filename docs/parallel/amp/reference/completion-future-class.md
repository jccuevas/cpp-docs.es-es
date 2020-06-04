---
title: completion_future (Clase)
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: 69aacad02df5290f161e9d8d311be347668be9f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127025"
---
# <a name="completion_future-class"></a>completion_future (Clase)

Representa un futuro que corresponde a C++ una operación asincrónica de amp.

## <a name="syntax"></a>Sintaxis

```cpp
class completion_future;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de completion_future](#ctor)|Inicializa una nueva instancia de la clase `completion_future`.|
|[~ completion_future destructor](#dtor)|Destruye el objeto `completion_future`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get](#get)|Espera hasta que se completa la operación asincrónica asociada.|
|[then](#then)|Encadena un objeto de función de devolución de llamada al objeto `completion_future` que se va a ejecutar cuando finalice la ejecución de la operación asincrónica asociada.|
|[to_task](#to_task)|Devuelve un objeto `task` correspondiente a la operación asincrónica asociada.|
|[válido](#valid)|Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.|
|[currir](#wait)|Se bloquea hasta que se completa la operación asincrónica asociada.|
|[wait_for](#wait_for)|Se bloquea hasta que se completa la operación asincrónica asociada o hasta que ha transcurrido el tiempo especificado por `_Rel_time`.|
|[wait_until](#wait_until)|Se bloquea hasta que se completa la operación asincrónica asociada o hasta que la hora actual supera el valor especificado por `_Abs_time`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operador STD:: shared_future\<void >](#operator_shared_future)|Convierte implícitamente el objeto de `completion_future` en un objeto `std::shared_future`.|
|[operator=](#operator_eq)|Copia el contenido del objeto `completion_future` especificado en este.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`completion_future`

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>completion_future

Inicializa una nueva instancia de la clase `completion_future`.

### <a name="syntax"></a>Sintaxis

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto `completion_future` que se va a copiar o a quitar.

### <a name="overloads-list"></a>Lista de sobrecargas

|Nombre|Descripción|
|----------|-----------------|
|`completion_future();`|Inicializa una nueva instancia de la clase `completion_future`|
|`completion_future(const completion_future& _Other);`|Inicializa una nueva instancia de la clase `completion_future` copiando un constructor.|
|`completion_future(completion_future&& _Other);`|Inicializa una nueva instancia de la clase `completion_future` moviendo un constructor.|

## <a name="get"></a>Obtener

Espera hasta que se completa la operación asincrónica asociada. Produce la excepción almacenada si se encontró una durante la operación asincrónica.

### <a name="syntax"></a>Sintaxis

```cpp
void get() const;
```

## <a name="operator_shared_future"></a>operador STD:: shared_future\<void >

Convierte implícitamente el objeto de `completion_future` en un objeto `std::shared_future`.

### <a name="syntax"></a>Sintaxis

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `std::shared_future`.

## <a name="operator_eq"></a>operador =

Copia el contenido del objeto `completion_future` especificado en este.

### <a name="syntax"></a>Sintaxis

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El objeto desde el que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `completion_future`.

## <a name="overloads-list"></a>Lista de sobrecargas

|Nombre|Descripción|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Copia el contenido del objeto `completion_future` especificado en este, utilizando una copia en profundidad.|
|`completion_future& operator=(completion_future&& _Other);`|Copia el contenido del objeto `completion_future` especificado en este, utilizando una asignación de movimiento.|

## <a name="then"></a>a

Encadena un objeto de función de devolución de llamada al objeto `completion_future` que se va a ejecutar cuando finalice la ejecución de la operación asincrónica asociada.

### <a name="syntax"></a>Sintaxis

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>Parámetros

*_Functor*<br/>
Functor de devolución de llamada.

*_Func*<br/>
Objeto de función de devolución de llamada.

## <a name="to_task"></a>to_task

Devuelve un objeto `task` correspondiente a la operación asincrónica asociada.

### <a name="syntax"></a>Sintaxis

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Valor devuelto

`task` objeto que corresponde a la operación asincrónica asociada.

## <a name="valid"></a>válido

Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.

### <a name="syntax"></a>Sintaxis

```cpp
bool valid() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el objeto está asociado a una operación asincrónica; en caso contrario, **false**.

## <a name="wait"></a>currir

Se bloquea hasta que se completa la operación asincrónica asociada.

### <a name="syntax"></a>Sintaxis

```cpp
void wait() const;
```

## <a name="wait_for"></a>wait_for

Se bloquea hasta que se completa la operación asincrónica asociada o hasta que ha transcurrido el tiempo especificado por `_Rel_time`.

### <a name="syntax"></a>Sintaxis

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>Parámetros

*_Rep*<br/>
Tipo aritmético que representa el número de pasos.

*_Period*<br/>
Un STD:: ratio que representa el número de segundos que transcurren por TIC.

*_Rel_time*<br/>
Tiempo máximo que se esperará a que se complete la operación.

### <a name="return-value"></a>Valor devuelto

Devuelve:

- `std::future_status::deferred` si la operación asincrónica asociada no se está ejecutando.

- `std::future_status::ready` si la operación asincrónica asociada ha finalizado.

- `std::future_status::timeout` si ha transcurrido el período de tiempo especificado.

## <a name="wait_until"></a>wait_until

Se bloquea hasta que se completa la operación asincrónica asociada o hasta que la hora actual supera el valor especificado por `_Abs_time`.

### <a name="syntax"></a>Sintaxis

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>Parámetros

*_Clock*<br/>
Reloj en el que se mide este punto de tiempo.

*_Duration*<br/>
El intervalo de tiempo desde el inicio del tiempo de `_Clock`, después del cual se agotará el tiempo de espera de la función.

*_Abs_time*<br/>
Punto en el tiempo después del cual se agotará el tiempo de espera de la función.

### <a name="return-value"></a>Valor devuelto

Devuelve:

1. `std::future_status::deferred` si la operación asincrónica asociada no se está ejecutando.

1. `std::future_status::ready` si la operación asincrónica asociada ha finalizado.

1. `std::future_status::timeout` si ha transcurrido el período de tiempo especificado.

## <a name="dtor"></a>~ completion_future

Destruye el objeto `completion_future`.

### <a name="syntax"></a>Sintaxis

```cpp
~completion_future();
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
