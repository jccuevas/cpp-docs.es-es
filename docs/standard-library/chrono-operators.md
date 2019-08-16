---
title: Operadores de &lt;chrono&gt;
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 398e2429c38cffb454c7b510aa5ab44fbe4cfef6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244885"
---
# <a name="ltchronogt-operators"></a>Operadores de &lt;chrono&gt;

## <a name="operator-"></a> operator-

Operador para la resta o la negación de objetos [duration](../standard-library/duration-class.md) y [time_point](../standard-library/time-point-class.md).

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);

template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

*Tiempo*\
Objeto `time_point`.

*Duración*\
Objeto `duration`.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve un objeto `duration` cuya longitud del intervalo es la diferencia entre los intervalos de tiempo de los dos argumentos.

La segunda función devuelve un `time_point` objeto que representa un punto en el tiempo que está desplazado, según la negación del intervalo de tiempo representado por *Dur*, desde el punto en el tiempo especificado por *tiempo*.

La tercera función devuelve un `duration` objeto que representa el intervalo de tiempo entre *izquierda* y *derecha*.

## <a name="op_neq"></a> operador! =

Operador de desigualdad para objetos [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md).

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `!(Left == Right)`.

## <a name="op_star"></a> operador *

Operador de multiplicación para objetos [duration](../standard-library/chrono-operators.md#op_star).

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);

template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>Parámetros

*Duración*\
Objeto `duration`.

*Mult*\
Valor entero.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve un `duration` objeto cuya longitud del intervalo es *Mult* multiplicado por la longitud de *Dur*.

A menos que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*sea True*, la primera función no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

A menos que `is_convertible<Rep1, common_type<Rep1, Rep2>>`*sea True*, la segunda función no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

## <a name="op_div"></a> operador /

Operador de división para objetos [duration](../standard-library/chrono-operators.md#op_star).

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parámetros

*Duración*\
Objeto `duration`.

*div*\
Valor entero.

*Izquierda*\
Objeto `duration` izquierdo.

*Correcto*\
Objeto `duration` derecho.

### <a name="return-value"></a>Valor devuelto

El primer operador devuelve un objeto de duración cuyo intervalo de longitud es la longitud de *Dur* dividido por el valor *Div*.

El segundo operador devuelve el cociente de las longitudes de intervalo de *izquierda* y *derecha*.

A menos que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*sea True*, y `Rep2` no sea una creación de instancia de `duration`, el primer operador no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

## <a name="op_add"></a> operator +

Suma los objetos [duration](../standard-library/duration-class.md) y [time_point](../standard-library/time-point-class.md).

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);

template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

*Tiempo*\
Objeto `time_point`.

*Duración*\
Objeto `duration`.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve un `duration` objeto que tiene un intervalo de tiempo que es igual a la suma de los intervalos de *izquierda* y *derecha*.

Las funciones segunda y terceros devuelven un `time_point` objeto que representa un punto en el tiempo que está desplazado, según el intervalo de *Dur*, desde el punto en el tiempo *tiempo*.

## <a name="op_lt"></a> operator&lt;

Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es menor que otro objeto `duration` o `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve **true** si la longitud del intervalo de *izquierda* es menor que la longitud del intervalo de *derecha*. En caso contrario, devuelve la función **false**.

La segunda función devuelve **true** si *izquierda* precede *derecha*. En caso contrario, devuelve la función **false**.

## <a name="op_lt_eq"></a> Operador&lt;=

Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es menor o igual que otro objeto `duration` o `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `!(Right < Left)`.

## <a name="op_eq_eq"></a> operador ==

Determina si dos objetos `duration` representan intervalos de tiempo de la misma longitud o si dos objetos `time_point` representan el mismo punto en el tiempo.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve **true** si *izquierda* y *derecha* representan intervalos de tiempo que tienen la misma longitud. En caso contrario, devuelve la función **false**.

La segunda función devuelve **true** si *izquierda* y *derecha* representan el mismo punto en el tiempo. En caso contrario, devuelve la función **false**.

## <a name="op_gt"></a> operator&gt;

Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es mayor que otro objeto `duration` o `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `Right < Left`.

## <a name="op_gt_eq"></a> Operador&gt;=

Determina si un objeto [duration](../standard-library/duration-class.md) o [time_point](../standard-library/time-point-class.md) es mayor o igual que otro objeto `duration` o `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `duration` o `time_point` izquierdo.

*Correcto*\
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `!(Left < Right)`.

## <a name="op_modulo"></a> operador de módulo

Operador para operaciones de módulo en objetos [duration](../standard-library/duration-class.md).

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parámetros

*Duración*\
Objeto `duration`.

*div*\
Valor entero.

*Izquierda*\
Objeto `duration` izquierdo.

*Correcto*\
Objeto `duration` derecho.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve un `duration` objeto cuya longitud del intervalo es *Dur* módulo *Div*.

La segunda función devuelve un valor que representa *izquierda* módulo *derecha*.
