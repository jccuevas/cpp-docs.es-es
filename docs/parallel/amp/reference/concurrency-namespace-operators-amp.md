---
title: Operadores de espacio de nombres de simultaneidad (AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1e313dbda3dfc75f291310818d593b9a4daf90b
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162183"
---
# <a name="concurrency-namespace-operators-amp"></a>Operadores de espacio de nombres de simultaneidad (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|
|[operator==](#operator_eq_eq)|

##  <a name="operator_eq_eq"></a>  operator==

Determina si los argumentos especificados son iguales.

```
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
El rango de los argumentos de tupla.

*_Lhs*<br/>
Una de las tuplas para comparar.

*_Rhs*<br/>
Una de las tuplas para comparar.

### <a name="return-value"></a>Valor devuelto

**True** si las tuplas son iguales; en caso contrario, **false**.

##  <a name="operator_neq"></a> operator!=

Determina si los argumentos especificados no son iguales.

```
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
El rango de los argumentos de tupla.

*_Lhs*<br/>
Una de las tuplas para comparar.

*_Rhs*<br/>
Una de las tuplas para comparar.

### <a name="return-value"></a>Valor devuelto

**True** si las tuplas no son iguales; en caso contrario, **false**.

##  <a name="operator_add"></a>  operator+

Calcula la suma de todos los componentes de los argumentos especificados.

```
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
El rango de los argumentos de tupla.

*_Lhs*<br/>
Uno de los argumentos que se van a agregar.

*_Rhs*<br/>
Uno de los argumentos que se van a agregar.

### <a name="return-value"></a>Valor devuelto

La suma de los argumentos especificados.

##  <a name="operator-"></a>  operator-

Calcula la diferencia de todos los componentes entre los argumentos especificados.

```
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
El rango de los argumentos de tupla.

*_Lhs*<br/>
El argumento que se restará.

*_Rhs*<br/>
El argumento a restar.

### <a name="return-value"></a>Valor devuelto

La diferencia entre los argumentos especificados de todos.

##  <a name="operator_star"></a>  operator*

Calcula el producto de todos los componentes de los argumentos especificados.

```
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
El rango de los argumentos de tupla.

*_Lhs*<br/>
Una de las tuplas que se va a multiplicar.

*_Rhs*<br/>
Una de las tuplas que se va a multiplicar.

### <a name="return-value"></a>Valor devuelto

El producto por componente de los argumentos especificados.

##  <a name="operator_div"></a>  operator/

Calcula el cociente de todos los componentes de los argumentos especificados.

```
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
El rango de los argumentos de tupla.

*_Lhs*<br/>
La tupla que se va a dividir.

*_Rhs*<br/>
Dividir por la tupla.

### <a name="return-value"></a>Valor devuelto

El cociente de todos de los argumentos especificados.

##  <a name="operator_mod"></a>  operator%

Calcula el módulo del primer argumento especificado dividido por el segundo argumento especificado.

```
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
El rango de los argumentos de tupla.

*_Lhs*<br/>
Tupla desde la que el módulo se calcula.

*_Rhs*<br/>
La tupla que módulo por.

### <a name="return-value"></a>Valor devuelto

El resultado del primer módulo de argumento especificado el segundo argumento especificado.

## <a name="see-also"></a>Vea también

[simultaneidad Namespace ](concurrency-namespace-cpp-amp.md)
