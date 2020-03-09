---
title: Operadores del espacio de nombres de simultaneidad (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 3b536f75e4ef6405b60d45e89290a7d97a01707d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883737"
---
# <a name="concurrency-namespace-operators-amp"></a>Operadores del espacio de nombres de simultaneidad (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|
|[operator==](#operator_eq_eq)|

## <a name="operator_eq_eq"></a>  operator==

Determina si los argumentos especificados son iguales.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de los argumentos de la tupla.

*_Lhs*<br/>
Una de las tuplas que se van a comparar.

*_Rhs*<br/>
Una de las tuplas que se van a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si las tuplas son iguales; en caso contrario, **false**.

## <a name="operator_neq"></a> operator!=

Determina si los argumentos especificados no son iguales.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de los argumentos de la tupla.

*_Lhs*<br/>
Una de las tuplas que se van a comparar.

*_Rhs*<br/>
Una de las tuplas que se van a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si las tuplas no son iguales; en caso contrario, **false**.

## <a name="operator_add"></a>  operator+

Calcula la suma de todos los componentes de los argumentos especificados.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de los argumentos de la tupla.

*_Lhs*<br/>
Uno de los argumentos que se van a agregar.

*_Rhs*<br/>
Uno de los argumentos que se van a agregar.

### <a name="return-value"></a>Valor devuelto

Suma de componentes de los argumentos especificados.

## <a name="operator-"></a>  operator-

Calcula la diferencia de todos los componentes entre los argumentos especificados.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de los argumentos de la tupla.

*_Lhs*<br/>
Argumento del que se va a restar.

*_Rhs*<br/>
Argumento que se va a restar.

### <a name="return-value"></a>Valor devuelto

Diferencia de componentes entre los argumentos especificados.

## <a name="operator_star"></a>  operator*

Calcula el producto de todos los componentes de los argumentos especificados.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de los argumentos de la tupla.

*_Lhs*<br/>
Una de las tuplas que se van a multiplicar.

*_Rhs*<br/>
Una de las tuplas que se van a multiplicar.

### <a name="return-value"></a>Valor devuelto

Producto de componentes de los argumentos especificados.

## <a name="operator_div"></a>  operator/

Calcula el cociente de todos los componentes de los argumentos especificados.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de los argumentos de la tupla.

*_Lhs*<br/>
Tupla que se va a dividir.

*_Rhs*<br/>
Tupla por la que se va a dividir.

### <a name="return-value"></a>Valor devuelto

Cociente de componentes de los argumentos especificados.

## <a name="operator_mod"></a>  operator%

Calcula el módulo del primer argumento especificado dividido por el segundo argumento especificado.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de los argumentos de la tupla.

*_Lhs*<br/>
Tupla de la que se calcula el módulo.

*_Rhs*<br/>
Tupla por la que se va a organizar.

### <a name="return-value"></a>Valor devuelto

El resultado del primer argumento especificado se reforman en el segundo argumento especificado.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad](concurrency-namespace-cpp-amp.md)
