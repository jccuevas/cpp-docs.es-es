---
title: Funciones de &lt;chrono&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: f6230775418aa86f39f6dc1b96c759cb602cd9d3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="ltchronogt-functions"></a>Funciones de &lt;chrono&gt;

||||
|-|-|-|
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|


## <a name="duration_cast"></a>  duration_cast

Convierte un objeto `duration` a un tipo especificado.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```

### <a name="return-value"></a>Valor devuelto

Objeto `duration` de tipo `To` que representa el intervalo de tiempo `Dur`, que se trunca si tiene que ajustarse al tipo de destino.

### <a name="remarks"></a>Comentarios

Si `To` es una creación de instancia de `duration`, esta función no participa en la resolución de sobrecarga.

## <a name="time_point_cast"></a>  time_point_cast

Convierte un objeto [time_point](../standard-library/time-point-class.md) en un tipo especificado.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```

### <a name="return-value"></a>Valor devuelto

Objeto `time_point` que tiene una duración de tipo `To`.

### <a name="remarks"></a>Comentarios

A menos que `To` sea una creación de instancia de [duration](../standard-library/duration-class.md), esta función no participa en la resolución de sobrecarga.

## <a name="see-also"></a>Vea también

[\<chrono>](../standard-library/chrono.md)<br/>
