---
title: duration (Clase)
ms.date: 03/27/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 3669935bf094f476ca24a8170a0388dff29e0a0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368750"
---
# <a name="duration-class"></a>duration (Clase)

Describe un tipo que contiene un *intervalo de tiempo*, que es el tiempo transcurrido entre dos puntos en el tiempo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>Observaciones

El argumento de plantilla `Rep` describe el tipo que se utiliza para almacenar el número de ciclos de reloj del intervalo. El argumento de plantilla `Period` es una creación de instancias de [ratio](../standard-library/ratio.md) que describe el tamaño del intervalo que representa cada ciclo.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|duration::period (Typedef)|Representa un sinónimo para el parámetro de plantilla `Period`.|
|duration::rep (Typedef)|Representa un sinónimo para el parámetro de plantilla `Rep`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[duration](#duration)|Construye un objeto `duration`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[count](#count)|Devuelve el número de pasos del reloj del intervalo de tiempo.|
|[máximo](#max)|Estática. Devuelve el valor máximo permitido del parámetro de plantilla `Ref`.|
|[Min](#min)|Estática. Devuelve el valor mínimo permitido del parámetro de plantilla `Ref`.|
|[Cero](#zero)|Estática. En efecto, devuelve `Rep`(0).|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[duración::operador-](#operator-)|Devuelve una copia del objeto `duration` junto con un recuento de pasos negado.|
|[duración::operador--](#operator--)|Disminuye el recuento de pasos almacenado.|
|[duración::operador](#op_eq)|Reduce el módulo del recuento de pasos almacenado en un valor especificado.|
|[duration::operator*=](#op_star_eq)|Multiplica el recuento de pasos almacenado por un valor especificado.|
|[duración::operador/](#op_div_eq)|Divide el recuento de pasos almacenado por el recuento de pasos de un objeto `duration` especificado.|
|[duración::operador+](#op_add)|Devuelve `*this`.|
|[duración::operador++](#op_add_add)|Incrementa el recuento de pasos almacenado.|
|[duración::operador+o](#op_add_eq)|Suma el recuento de pasos de un objeto `duration` especificado al recuento de pasos almacenado.|
|[duración::operador--](#operator-_eq)|Resta el recuento de pasos de un objeto `duration` especificado del recuento de pasos almacenado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<crono>

**Espacio de nombres:** std::chrono

## <a name="durationcount"></a><a name="count"></a>duración::contar

Recupera el número de ciclos del reloj del intervalo de tiempo.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Valor devuelto

Número de ciclos del reloj del intervalo de tiempo.

## <a name="durationduration-constructor"></a><a name="duration"></a>duration::duration Constructor

Construye un objeto `duration`.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parámetros

*Rep2*\
Un tipo aritmético para representar el número de ciclos.

*Período2*\
Una especialización de plantilla `std::ratio` para representar el período de ciclo en unidades de segundos.

*R*\
El número de ciclos del período predeterminado.

*Dur*\
El número de ticks de período especificado por *el Período2*.

### <a name="remarks"></a>Observaciones

El constructor predeterminado crea un objeto que no se ha inicializado. La inicialización de un valor mediante llaves vacías inicializa un objeto que representa un intervalo de tiempo de cero ciclos de reloj.

El segundo constructor de un argumento de plantilla construye *R* un objeto que representa un `std::ratio<1>`intervalo de tiempo de ticks de reloj R utilizando un período predeterminado de . Para evitar el redondeo de los recuentos de ticks, es un error construir un objeto duration a `duration::rep` partir de un tipo de representación *Rep2* que se puede tratar como un tipo de punto flotante cuando no se puede tratar como un tipo de punto flotante.

El tercer constructor de argumentos de plantilla construye un objeto que representa un intervalo de tiempo cuya longitud es el intervalo de tiempo especificado por *Dur*. Para evitar el truncamiento de los ciclos de reloj, es un error construir un objeto de duración a partir de otro objeto de duración cuyo tipo es *inconmensurable* con el tipo de destino.

Un tipo de duración `D1` es *inconmensurable* con otro tipo de duración `D2` si `D2` no se puede tratar como un tipo de punto flotante y [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) no es 1.

A menos que *Rep2* sea `treat_as_floating_point<rep>`implícitamente `treat_as_floating_point<Rep2>`convertible `rep` y mantenga true o *constituya* *false* , el segundo constructor no participa en la resolución de sobrecargas. Para más información, vea [<type_traits>](../standard-library/type-traits.md).

A menos que no se induzca ningún desbordamiento en la conversión y `treat_as_floating_point<rep>`*sea True* o ambos `ratio_divide<Period2, period>::den` sean iguales a 1 y `treat_as_floating_point<Rep2>`*sea False*, el tercer constructor no participa en la resolución de sobrecarga. Para más información, vea [<type_traits>](../standard-library/type-traits.md).

## <a name="durationmax"></a><a name="max"></a>duración::max

Método estático que devuelve el límite superior para los valores de tipo de parámetro de plantilla `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `duration(duration_values<rep>::max())`.

## <a name="durationmin"></a><a name="min"></a>duración::min

Método estático que devuelve el límite inferior para los valores de tipo de parámetro de plantilla `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `duration(duration_values<rep>::min())`.

## <a name="durationoperator-"></a><a name="operator-"></a>duración::operador-

Devuelve una copia del objeto `duration` junto con un recuento de pasos negado.

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>duración::operador--

Disminuye el recuento de pasos almacenado.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Valor devuelto

El primer método devuelve `*this`.

El segundo método devuelve una copia de `*this` que se ha creado antes del decremento.

## <a name="durationoperator"></a><a name="op_eq"></a>duración::operador

Reduce el módulo del recuento de pasos almacenado en un valor especificado.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parámetros

*Div*\
Para el primer método, *Div* representa un recuento de ticks. Para el segundo *Div* método, `duration` Div es un objeto que contiene un recuento de ticks.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después de realizarse la operación de módulo.

## <a name="durationoperator"></a><a name="op_star_eq"></a>duración::operador*

Multiplica el recuento de pasos almacenado por un valor especificado.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parámetros

*Mult*\
Valor del tipo especificado por `duration::rep`.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la multiplicación.

## <a name="durationoperator"></a><a name="op_div_eq"></a>duración::operador/

Divide el recuento de pasos almacenado por un valor especificado.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parámetros

*Div*\
Valor del tipo especificado por `duration::rep`.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la división.

## <a name="durationoperator"></a><a name="op_add"></a>duración::operador+

Devuelve `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>duración::operador++

Incrementa el recuento de pasos almacenado.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Valor devuelto

El primer método devuelve `*this`.

El segundo método devuelve una copia de `*this` que se hizo antes del incremento.

## <a name="durationoperator"></a><a name="op_add_eq"></a>duración::operador+o

Suma el recuento de pasos de un objeto `duration` especificado al recuento de pasos almacenado.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parámetros

*Dur*\
Objeto `duration` .

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la suma.

## <a name="durationoperator-"></a><a name="operator-_eq"></a>duración::operador--

Resta el recuento de pasos de un objeto `duration` especificado del recuento de pasos almacenado.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parámetros

*Dur*\
Objeto `duration` .

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la resta.

## <a name="durationzero"></a><a name="zero"></a>duración::cero

Devuelve `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>duración::operador mod

Reduce el módulo del recuento de pasos almacenado en Div o Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parámetros

*Div*\
El divisor, que es un objeto de duración o un valor que representa los recuentos de pasos.

### <a name="remarks"></a>Observaciones

La primera función miembro reduce el módulo del recuento de pasos almacenado Div y devuelve *this. La segunda función miembro reduce el módulo del recuento de pasos almacenado Div.count() y devuelve \*this.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>crono](../standard-library/chrono.md)\
[duration_values (Estructura)](../standard-library/duration-values-structure.md)
