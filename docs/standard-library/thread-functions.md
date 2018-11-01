---
title: Funciones de &lt;thread&gt;
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: c0a8e42cb7ee78c399459be82e50ef37ab203816
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631275"
---
# <a name="ltthreadgt-functions"></a>Funciones de &lt;thread&gt;

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[swap](#swap)|[yield](#yield)|

## <a name="get_id"></a>  get_id

Identifica de forma única el subproceso de ejecución actual.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un objeto de tipo [thread::id](../standard-library/thread-class.md) que identifica de forma única el subproceso de ejecución actual.

## <a name="sleep_for"></a>  sleep_for

Bloquea el subproceso de llamada.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parámetros

*Rel_time*<br/>
Un objeto [duration](../standard-library/duration-class.md) que especifica un intervalo de tiempo.

### <a name="remarks"></a>Comentarios

La función bloquea el subproceso que realiza la llamada para al menos el tiempo especificado por *Rel_time*. Esta función no produce ninguna excepción.

## <a name="sleep_until"></a>  sleep_until

Bloquea el subproceso de llamada al menos hasta la hora especificada.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parámetros

*Abs_time*<br/>
Representa un punto en el tiempo.

### <a name="remarks"></a>Comentarios

Esta función no produce ninguna excepción.

## <a name="swap"></a>  swap

Intercambia los Estados de dos **subproceso** objetos.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Izquierda*<br/>
La izquierda **subproceso** objeto.

*Derecha*<br/>
El derecho de **subproceso** objeto.

### <a name="remarks"></a>Comentarios

La función llama a `Left.swap(Right)`.

## <a name="yield"></a>  yield

Indica al sistema operativo que ejecute otros subprocesos, incluso si el subproceso actual seguiría ejecutándose en condiciones normales.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Vea también

[\<thread>](../standard-library/thread.md)<br/>
