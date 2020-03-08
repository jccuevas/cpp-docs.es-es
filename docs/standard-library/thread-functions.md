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
ms.openlocfilehash: 8064cec7e94a909d7dc2e1b22142d362bb7b9488
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876182"
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

*Rel_time*\
Un objeto [duration](../standard-library/duration-class.md) que especifica un intervalo de tiempo.

### <a name="remarks"></a>Observaciones

La función bloquea el subproceso de llamada durante al menos el tiempo especificado por *Rel_time*. Esta función no produce ninguna excepción.

## <a name="sleep_until"></a>  sleep_until

Bloquea el subproceso de llamada al menos hasta la hora especificada.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parámetros

*Abs_time*\
Representa un punto en el tiempo.

### <a name="remarks"></a>Observaciones

Esta función no produce ninguna excepción.

## <a name="swap"></a> swap

Intercambia los Estados de dos objetos de **subproceso** .

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de **subproceso** izquierdo.

\ *derecha*
Objeto de **subproceso** correcto.

### <a name="remarks"></a>Observaciones

La función llama a `Left.swap(Right)`.

## <a name="yield"></a>  yield

Indica al sistema operativo que ejecute otros subprocesos, incluso si el subproceso actual seguiría ejecutándose en condiciones normales.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Consulte también

[\<thread>](../standard-library/thread.md)
