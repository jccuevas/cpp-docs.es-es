---
title: Operadores de &lt;chrono&gt;
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 398e2429c38cffb454c7b510aa5ab44fbe4cfef6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427210"
---
# <a name="ltchronogt-operators"></a>Operadores de &lt;chrono&gt;

## <a name="operator-"></a>Operator

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

*Hora*\
Objeto `time_point` .

*Dur*\
Objeto `duration` .

### <a name="return-value"></a>Valor devuelto

La primera función devuelve un objeto `duration` cuya longitud del intervalo es la diferencia entre los intervalos de tiempo de los dos argumentos.

La segunda función devuelve un objeto `time_point` que representa un punto en el tiempo que se ha desplazado, por la negación del intervalo de tiempo representado por *Dur*, desde el punto en el tiempo especificado por *Time*.

La tercera función devuelve un objeto `duration` que representa el intervalo de tiempo entre la *izquierda* y la *derecha*.

## <a name="op_neq"></a>operador! =

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `!(Left == Right)`.

## <a name="op_star"></a>Operator

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

*Dur*\
Objeto `duration` .

*Mult*\
Valor entero.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve un objeto de `duration` cuya longitud de *intervalo se multiplica* por la longitud de *Dur*.

A menos que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*sea True*, la primera función no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

A menos que `is_convertible<Rep1, common_type<Rep1, Rep2>>`*sea True*, la segunda función no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

## <a name="op_div"></a>Operator

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

*Dur*\
Objeto `duration` .

\ *div*
Valor entero.

\ *izquierda*
Objeto `duration` izquierdo.

\ *derecha*
Objeto `duration` derecho.

### <a name="return-value"></a>Valor devuelto

El primer operador devuelve un objeto Duration cuya longitud del intervalo es la longitud de *Dur* dividida por el valor *div*.

El segundo operador devuelve la relación entre las longitudes de intervalo de *izquierda* y *derecha*.

A menos que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*sea True*, y `Rep2` no sea una creación de instancia de `duration`, el primer operador no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

## <a name="op_add"></a>operador +

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

*Hora*\
Objeto `time_point` .

*Dur*\
Objeto `duration` .

### <a name="return-value"></a>Valor devuelto

La primera función devuelve un objeto `duration` que tiene un intervalo de tiempo igual a la suma de los intervalos de *izquierda* y *derecha*.

Las funciones segunda y tercera devuelven un objeto `time_point` que representa un punto en el tiempo que se ha desplazado, por el intervalo *Dur*, desde el punto *en el tiempo.*

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve **true** si la longitud del intervalo de la *izquierda* es menor que la longitud del intervalo de la *derecha*. De lo contrario, la función devuelve **false**.

La segunda función devuelve **true** si la *izquierda* precede a la *derecha*. De lo contrario, la función devuelve **false**.

## <a name="op_lt_eq"></a>operador&lt;=

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `!(Right < Left)`.

## <a name="op_eq_eq"></a>operador = =

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve **true** si la *izquierda* y la *derecha* representan intervalos de tiempo que tienen la misma longitud. De lo contrario, la función devuelve **false**.

La segunda función devuelve **true** si la *izquierda* y la *derecha* representan el mismo punto en el tiempo. De lo contrario, la función devuelve **false**.

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `Right < Left`.

## <a name="op_gt_eq"></a>operador&gt;=

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

\ *izquierda*
Objeto `duration` o `time_point` izquierdo.

\ *derecha*
Objeto `duration` o `time_point` derecho.

### <a name="return-value"></a>Valor devuelto

Cada función devuelve `!(Left < Right)`.

## <a name="op_modulo"></a>operador Operator

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

*Dur*\
Objeto `duration` .

\ *div*
Valor entero.

\ *izquierda*
Objeto `duration` izquierdo.

\ *derecha*
Objeto `duration` derecho.

### <a name="return-value"></a>Valor devuelto

La primera función devuelve un objeto `duration` cuya longitud del intervalo es el *módulo de* *Dur* .

La segunda función devuelve un valor que representa el módulo *izquierdo* *derecho*.
