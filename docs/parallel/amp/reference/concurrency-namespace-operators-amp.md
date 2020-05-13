---
title: Operadores del espacio de nombres de simultaneidad (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: c4086029b71d71091a12b9b6023cc6098faf2f85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376299"
---
# <a name="concurrency-namespace-operators-amp"></a>Operadores del espacio de nombres de simultaneidad (AMP)

||||
|-|-|-|
|[¡Operador!](#operator_neq)|[operador%](#operator_mod)|[operador*](#operator_star)|
|[operador+](#operator_add)|[operador-](#operator-)|[operador/](#operator_div)|
|[operadora](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>operadora

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
El rango de los argumentos de la tupla.

*_Lhs*<br/>
Una de las tuplas para comparar.

*_Rhs*<br/>
Una de las tuplas para comparar.

### <a name="return-value"></a>Valor devuelto

**true** si las tuplas son iguales; de lo contrario, **false**.

## <a name="operator"></a><a name="operator_neq"></a>¡Operador!

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
El rango de los argumentos de la tupla.

*_Lhs*<br/>
Una de las tuplas para comparar.

*_Rhs*<br/>
Una de las tuplas para comparar.

### <a name="return-value"></a>Valor devuelto

**true** si las tuplas no son iguales; de lo contrario, **false**.

## <a name="operator"></a><a name="operator_add"></a>operador+

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
El rango de los argumentos de la tupla.

*_Lhs*<br/>
Uno de los argumentos a agregar.

*_Rhs*<br/>
Uno de los argumentos a agregar.

### <a name="return-value"></a>Valor devuelto

La suma de componentes de los argumentos especificados.

## <a name="operator-"></a><a name="operator-"></a>operador-

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
El rango de los argumentos de la tupla.

*_Lhs*<br/>
El argumento que se va a restar de.

*_Rhs*<br/>
El argumento para restar.

### <a name="return-value"></a>Valor devuelto

La diferencia de componente entre los argumentos especificados.

## <a name="operator"></a><a name="operator_star"></a>operador*

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
El rango de los argumentos de la tupla.

*_Lhs*<br/>
Una de las tuplas para multiplicarse.

*_Rhs*<br/>
Una de las tuplas para multiplicarse.

### <a name="return-value"></a>Valor devuelto

El producto de componentes de los argumentos especificados.

## <a name="operator"></a><a name="operator_div"></a>operador/

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
El rango de los argumentos de la tupla.

*_Lhs*<br/>
La tupla a dividir.

*_Rhs*<br/>
La tupla por la que dividir.

### <a name="return-value"></a>Valor devuelto

El cociente de componentes de los argumentos especificados.

## <a name="operator"></a><a name="operator_mod"></a>operador%

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
El rango de los argumentos de la tupla.

*_Lhs*<br/>
La tupla a partir de la cual se calcula el módulo.

*_Rhs*<br/>
La tupla para modulo por.

### <a name="return-value"></a>Valor devuelto

El resultado del primer argumento especificado modifica el segundo argumento especificado.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad](concurrency-namespace-cpp-amp.md)
