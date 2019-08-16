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
ms.openlocfilehash: 4c537b7dfdd23ba641438e0caf6306cf5549b2d7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454306"
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

## <a name="remarks"></a>Comentarios

El argumento de plantilla `Rep` describe el tipo que se utiliza para almacenar el número de ciclos de reloj del intervalo. El argumento de plantilla `Period` es una creación de instancias de [ratio](../standard-library/ratio.md) que describe el tamaño del intervalo que representa cada ciclo.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|duration::period (Typedef)|Representa un sinónimo para el parámetro de plantilla `Period`.|
|duration::rep (Typedef)|Representa un sinónimo para el parámetro de plantilla `Rep`.|

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[Duration](#duration)|Construye un objeto `duration`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[count](#count)|Devuelve el número de pasos del reloj del intervalo de tiempo.|
|[max](#max)|Estático. Devuelve el valor máximo permitido del parámetro de plantilla `Ref`.|
|[min](#min)|Estático. Devuelve el valor mínimo permitido del parámetro de plantilla `Ref`.|
|[zero](#zero)|Estático. En efecto, devuelve `Rep`(0).|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[duration::operator-](#operator-)|Devuelve una copia del objeto `duration` junto con un recuento de pasos negado.|
|[duration::operator--](#operator--)|Disminuye el recuento de pasos almacenado.|
|[duration::operator=](#op_eq)|Reduce el módulo del recuento de pasos almacenado en un valor especificado.|
|[duration::operator*=](#op_star_eq)|Multiplica el recuento de pasos almacenado por un valor especificado.|
|[duration::operator/=](#op_div_eq)|Divide el recuento de pasos almacenado por el recuento de pasos de un objeto `duration` especificado.|
|[duration::operator+](#op_add)|Devuelve `*this`.|
|[duration::operator++](#op_add_add)|Incrementa el recuento de pasos almacenado.|
|[duration::operator+=](#op_add_eq)|Suma el recuento de pasos de un objeto `duration` especificado al recuento de pasos almacenado.|
|[duration::operator-=](#operator-_eq)|Resta el recuento de pasos de un objeto `duration` especificado del recuento de pasos almacenado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> crónico

**Espacio de nombres:** std::chrono

## <a name="count"></a>  duration::count

Recupera el número de ciclos del reloj del intervalo de tiempo.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Valor devuelto

Número de ciclos del reloj del intervalo de tiempo.

## <a name="duration"></a>  duration::duration (Constructor)

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

*Period2*\
Una especialización de plantilla `std::ratio` para representar el período de ciclo en unidades de segundos.

*R*\
El número de ciclos del período predeterminado.

*Respectivamente*\
Número de TICs del período especificado por *Period2*.

### <a name="remarks"></a>Comentarios

El constructor predeterminado crea un objeto que no se ha inicializado. La inicialización de un valor mediante llaves vacías inicializa un objeto que representa un intervalo de tiempo de cero ciclos de reloj.

En el segundo, un constructor de argumento de plantilla crea un objeto que representa un intervalo de tiempo de ciclos de reloj de *R* mediante `std::ratio<1>`un período predeterminado de. Para evitar el redondeo de los recuentos de pasos, es un error construir un objeto de duración a partir de un *Rep2* de tipo de representación que se puede tratar como `duration::rep` un tipo de punto flotante cuando no se puede tratar como un tipo de punto flotante.

El tercer constructor de argumento de plantilla crea un objeto que representa un intervalo de tiempo cuya longitud es el intervalo de tiempo especificado por *Dur*. Para evitar el truncamiento de los ciclos de reloj, es un error construir un objeto de duración a partir de otro objeto de duración cuyo tipo es *inconmensurable* con el tipo de destino.

Un tipo de duración `D1` es *inconmensurable* con otro tipo de duración `D2` si `D2` no se puede tratar como un tipo de punto flotante y [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) no es 1.

A menos que *Rep2* se pueda convertir `rep` implícitamente `treat_as_floating_point<rep>`en y sea `treat_as_floating_point<Rep2>` *true* o *contenga false*, el segundo constructor no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

A menos que no se induzca ningún desbordamiento en la conversión y `treat_as_floating_point<rep>`*sea True* o ambos `ratio_divide<Period2, period>::den` sean iguales a 1 y `treat_as_floating_point<Rep2>`*sea False*, el tercer constructor no participa en la resolución de sobrecarga. Para obtener más información, vea [<type_traits>](../standard-library/type-traits.md).

## <a name="max"></a>  duration::max

Método estático que devuelve el límite superior para los valores de tipo de parámetro de plantilla `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `duration(duration_values<rep>::max())`.

## <a name="min"></a>  duration::min

Método estático que devuelve el límite inferior para los valores de tipo de parámetro de plantilla `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `duration(duration_values<rep>::min())`.

## <a name="operator-"></a>  duration::operator-

Devuelve una copia del objeto `duration` junto con un recuento de pasos negado.

```cpp
constexpr duration operator-() const;
```

## <a name="operator--"></a>  duration::operator--

Disminuye el recuento de pasos almacenado.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Valor devuelto

El primer método devuelve `*this`.

El segundo método devuelve una copia de `*this` que se ha creado antes del decremento.

## <a name="op_eq"></a>  duration::operator=

Reduce el módulo del recuento de pasos almacenado en un valor especificado.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parámetros

*Div*\
Para el primer método, *div* representa un recuento de pasos. En el segundo método, *div* es un `duration` objeto que contiene un recuento de pasos.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después de realizarse la operación de módulo.

## <a name="op_star_eq"></a>  duration::operator*=

Multiplica el recuento de pasos almacenado por un valor especificado.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parámetros

*Mult*\
Valor del tipo especificado por `duration::rep`.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la multiplicación.

## <a name="op_div_eq"></a>  duration::operator/=

Divide el recuento de pasos almacenado por un valor especificado.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parámetros

*Div*\
Valor del tipo especificado por `duration::rep`.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la división.

## <a name="op_add"></a>  duration::operator+

Devuelve `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  duration::operator++

Incrementa el recuento de pasos almacenado.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Valor devuelto

El primer método devuelve `*this`.

El segundo método devuelve una copia de `*this` que se hizo antes del incremento.

## <a name="op_add_eq"></a>  duration::operator+=

Suma el recuento de pasos de un objeto `duration` especificado al recuento de pasos almacenado.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parámetros

*Respectivamente*\
Objeto `duration`.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la suma.

## <a name="operator-_eq"></a>  duration::operator-=

Resta el recuento de pasos de un objeto `duration` especificado del recuento de pasos almacenado.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parámetros

*Respectivamente*\
Objeto `duration`.

### <a name="return-value"></a>Valor devuelto

Objeto `duration` después del cual se realiza la resta.

## <a name="zero"></a>  duration::zero

Devuelve `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  duration::operator mod=

Reduce el módulo del recuento de pasos almacenado en Div o Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parámetros

*Div*\
El divisor, que es un objeto de duración o un valor que representa los recuentos de pasos.

### <a name="remarks"></a>Comentarios

La primera función miembro reduce el módulo del recuento de pasos almacenado Div y devuelve *this. La segunda función miembro reduce el módulo del recuento de pasos almacenado Div.count() y devuelve \*this.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values (Estructura)](../standard-library/duration-values-structure.md)
