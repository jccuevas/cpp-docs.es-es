---
title: Funciones de &lt;chrono&gt;
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 85fdd413354b3f310d3315a80cf7da983cf6621d
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244915"
---
# <a name="ltchronogt-functions"></a>Funciones de &lt;chrono&gt;

## <a name="duration_cast"></a> duration_cast)

Convierte un objeto `duration` a un tipo especificado.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);

template <class ToDuration, class Rep, class Period>
constexpr ToDuration floor(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration ceil(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration round(const duration<Rep, Period>& d);
```

### <a name="return-value"></a>Valor devuelto

Objeto `duration` de tipo `To` que representa el intervalo de tiempo `Dur`, que se trunca si tiene que ajustarse al tipo de destino.

### <a name="remarks"></a>Comentarios

Si `To` es una creación de instancia de `duration`, esta función no participa en la resolución de sobrecarga.

## <a name="time_point_cast"></a> time_point_cast)

Convierte un objeto [time_point](../standard-library/time-point-class.md) en un tipo especificado.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);

template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
floor(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
ceil(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
round(const time_point<Clock, Duration>& tp);
```

### <a name="return-value"></a>Valor devuelto

Objeto `time_point` que tiene una duración de tipo `To`.

### <a name="remarks"></a>Comentarios

A menos que `To` sea una creación de instancia de [duration](../standard-library/duration-class.md), esta función no participa en la resolución de sobrecarga.
