---
title: concurrency (Operadores del espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: aac43a15b09bd792118fbfe7ea51493b73b8ac9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374379"
---
# <a name="concurrency-namespace-operators"></a>concurrency (Operadores del espacio de nombres)

||||
|-|-|-|
|[¡Operador!](#operator_neq)|[Operador&amp;&amp;](#operator_amp_amp)|[Operador&gt;](#operator_gt)|
|[Operador&gt;=](#operator_gt_eq)|[Operador&lt;](#operator_lt)|[Operador&lt;=](#operator_lt_eq)|
|[operadora](#operator_eq_eq)|[operator&#124;&#124;](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>operador&#124;&#124; Operador

Crea una tarea que se completará correctamente cuando una de las tareas proporcionadas como argumentos se complete correctamente.

```cpp
template<typename ReturnType>
task<ReturnType> operator||(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void> operator||(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Parámetros

*ReturnType*<br/>
Tipo de la tarea devuelta.

*Lhs*<br/>
Primera tarea que debe combinarse en la tarea resultante.

*rhs*<br/>
Segunda tarea que se va a combinar en la tarea resultante.

### <a name="return-value"></a>Valor devuelto

Tarea que se completa correctamente cuando cualquiera de las tareas de entrada se ha completado correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.

### <a name="remarks"></a>Observaciones

Si ambas tareas se cancelan o se producen excepciones, la tarea devuelta se completará en el estado cancelado y `get()` una `wait()` de las excepciones, si se encuentra alguna, se producirá cuando se llame o en esa tarea.

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>operador&amp; &amp; Operador

Crea una tarea que se completará correctamente cuando ambas tareas proporcionadas como argumentos se completen correctamente.

```cpp
template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void>  operator&&(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Parámetros

*ReturnType*<br/>
Tipo de la tarea devuelta.

*Lhs*<br/>
Primera tarea que debe combinarse en la tarea resultante.

*rhs*<br/>
Segunda tarea que se va a combinar en la tarea resultante.

### <a name="return-value"></a>Valor devuelto

Tarea que se completa correctamente cuando ambas tareas de entrada se completan correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.

### <a name="remarks"></a>Observaciones

Si una de las tareas se cancela o produce una excepción, la tarea devuelta se completará antes, en el `get()` `wait()` estado cancelado, y la excepción, si se produce una, se producirá si se llama o en esa tarea.

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>Operador: Operador

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es igual al objeto `concurrent_vector` del lado derecho.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
El tipo de asignador del primer `concurrent_vector` objeto.

*A2*<br/>
El tipo de asignador del segundo `concurrent_vector` objeto.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es igual al vector simultáneo en el lado derecho del operador; de lo contrario **falso**.

### <a name="remarks"></a>Observaciones

Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus respectivos elementos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Este método no es seguro para simultaneidad con respecto a otros `_A` métodos que podrían modificar cualquiera de los vectores simultáneos o `_B`.

## <a name="operator-operator"></a><a name="operator_neq"></a>operador!

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador no es igual al objeto `concurrent_vector` del lado derecho.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
El tipo de asignador del primer `concurrent_vector` objeto.

*A2*<br/>
El tipo de asignador del segundo `concurrent_vector` objeto.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si los vectores simultáneos no son iguales; **false** si los vectores simultáneos son iguales.

### <a name="remarks"></a>Observaciones

Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus respectivos elementos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Este método no es seguro para simultaneidad con respecto a otros `_A` métodos que podrían modificar cualquiera de los vectores simultáneos o `_B`.

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>operador&lt; Operador

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor que el objeto `concurrent_vector` del lado derecho.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
El tipo de asignador del primer `concurrent_vector` objeto.

*A2*<br/>
El tipo de asignador del segundo `concurrent_vector` objeto.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es menor que el vector simultáneo en el lado derecho del operador; de lo contrario **falso**.

### <a name="remarks"></a>Observaciones

El comportamiento de este operador es idéntico `vector` al `std` operador equivalente para la clase en el espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros `_A` métodos que podrían modificar cualquiera de los vectores simultáneos o `_B`.

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>Operador&lt;- Operador

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor o igual que el objeto `concurrent_vector` del lado derecho.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
El tipo de asignador del primer `concurrent_vector` objeto.

*A2*<br/>
El tipo de asignador del segundo `concurrent_vector` objeto.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es menor o igual que el vector simultáneo en el lado derecho del operador; de lo contrario **falso**.

### <a name="remarks"></a>Observaciones

El comportamiento de este operador es idéntico `vector` al `std` operador equivalente para la clase en el espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros `_A` métodos que podrían modificar cualquiera de los vectores simultáneos o `_B`.

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>operador&gt; Operador

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor que el objeto `concurrent_vector` del lado derecho.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
El tipo de asignador del primer `concurrent_vector` objeto.

*A2*<br/>
El tipo de asignador del segundo `concurrent_vector` objeto.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es mayor que el vector simultáneo en el lado derecho del operador; de lo contrario **falso**.

### <a name="remarks"></a>Observaciones

El comportamiento de este operador es idéntico `vector` al `std` operador equivalente para la clase en el espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros `_A` métodos que podrían modificar cualquiera de los vectores simultáneos o `_B`.

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>Operador&gt;- Operador

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor o igual que el objeto `concurrent_vector` del lado derecho.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
El tipo de asignador del primer `concurrent_vector` objeto.

*A2*<br/>
El tipo de asignador del segundo `concurrent_vector` objeto.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es mayor o igual que el vector simultáneo en el lado derecho del operador; de lo contrario **falso**.

### <a name="remarks"></a>Observaciones

El comportamiento de este operador es idéntico `vector` al `std` operador equivalente para la clase en el espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros `_A` métodos que podrían modificar cualquiera de los vectores simultáneos o `_B`.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
