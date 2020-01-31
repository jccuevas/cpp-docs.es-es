---
title: concurrency (Operadores del espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 00accee4f28167b94b9193aec6d90f32ed242dbe
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821133"
---
# <a name="concurrency-namespace-operators"></a>concurrency (Operadores del espacio de nombres)

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator&#124;&#124;](#operator_lor)| |

##  <a name="operator_lor"></a>&#124; &#124; operador Operator

Crea una tarea que se completará correctamente cuando una de las tareas proporcionadas como argumentos se complete correctamente.

```
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

### <a name="parameters"></a>Parameters

*ReturnType*<br/>
Tipo de la tarea devuelta.

*lhs*<br/>
Primera tarea que debe combinarse en la tarea resultante.

*rhs*<br/>
Segunda tarea que se va a combinar en la tarea resultante.

### <a name="return-value"></a>Valor devuelto

Tarea que se completa correctamente cuando una de las tareas de entrada se ha completado correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.

### <a name="remarks"></a>Notas

Si las dos tareas se cancelan o inician excepciones, la tarea devuelta se completará en el estado cancelado y se producirá una de las excepciones, si se encuentra alguna, cuando llame a `get()` o `wait()` en esa tarea.

##  <a name="operator_amp_amp"></a>Operator&amp;operador de &amp;

Crea una tarea que se completará correctamente cuando las dos tareas proporcionadas como argumentos se completen correctamente.

```
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

### <a name="parameters"></a>Parameters

*ReturnType*<br/>
Tipo de la tarea devuelta.

*lhs*<br/>
Primera tarea que debe combinarse en la tarea resultante.

*rhs*<br/>
Segunda tarea que se va a combinar en la tarea resultante.

### <a name="return-value"></a>Valor devuelto

Tarea que se completa correctamente cuando ambas tareas de entrada se completan correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.

### <a name="remarks"></a>Notas

Si una de las tareas se cancela o inicia una excepción, la tarea devuelta finalizará prematuramente con el estado cancelado y se generará una excepción (si se encuentra una) al llamar a `get()` o `wait()` en dicha tarea.

##  <a name="operator_eq_eq"></a>Operator = = (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es igual al objeto `concurrent_vector` del lado derecho.

```
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameters

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
Tipo de asignador del primer objeto `concurrent_vector`.

*A2*<br/>
Tipo de asignador del segundo objeto de `concurrent_vector`.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es igual que el vector simultáneo del lado derecho del operador. en caso contrario, **false**.

### <a name="remarks"></a>Notas

Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_neq"></a>Operator! = (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador no es igual al objeto `concurrent_vector` del lado derecho.

```
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameters

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
Tipo de asignador del primer objeto `concurrent_vector`.

*A2*<br/>
Tipo de asignador del segundo objeto de `concurrent_vector`.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si los vectores simultáneos no son iguales; **false** si los vectores simultáneos son iguales.

### <a name="remarks"></a>Notas

Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_lt"></a>operador Operator&lt;

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor que el objeto `concurrent_vector` del lado derecho.

```
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameters

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
Tipo de asignador del primer objeto `concurrent_vector`.

*A2*<br/>
Tipo de asignador del segundo objeto de `concurrent_vector`.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es menor que el vector simultáneo del lado derecho del operador. en caso contrario, **false**.

### <a name="remarks"></a>Notas

El comportamiento de este operador es idéntico al operador equivalente para la clase `vector` en el espacio de nombres `std`.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_lt_eq"></a>Operator&lt;= (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor o igual que el objeto `concurrent_vector` del lado derecho.

```
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameters

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
Tipo de asignador del primer objeto `concurrent_vector`.

*A2*<br/>
Tipo de asignador del segundo objeto de `concurrent_vector`.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es menor o igual que el vector simultáneo del lado derecho del operador. en caso contrario, **false**.

### <a name="remarks"></a>Notas

El comportamiento de este operador es idéntico al operador equivalente para la clase `vector` en el espacio de nombres `std`.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_gt"></a>operador Operator&gt;

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor que el objeto `concurrent_vector` del lado derecho.

```
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameters

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
Tipo de asignador del primer objeto `concurrent_vector`.

*A2*<br/>
Tipo de asignador del segundo objeto de `concurrent_vector`.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es mayor que el vector simultáneo del lado derecho del operador. en caso contrario, **false**.

### <a name="remarks"></a>Notas

El comportamiento de este operador es idéntico al operador equivalente para la clase `vector` en el espacio de nombres `std`.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_gt_eq"></a>Operator&gt;= (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor o igual que el objeto `concurrent_vector` del lado derecho.

```
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parameters

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*A1*<br/>
Tipo de asignador del primer objeto `concurrent_vector`.

*A2*<br/>
Tipo de asignador del segundo objeto de `concurrent_vector`.

*_A*<br/>
Objeto de tipo `concurrent_vector`.

*_B*<br/>
Objeto de tipo `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

**true** si el vector simultáneo en el lado izquierdo del operador es mayor o igual que el vector simultáneo del lado derecho del operador. en caso contrario, **false**.

### <a name="remarks"></a>Notas

El comportamiento de este operador es idéntico al operador equivalente para la clase `vector` en el espacio de nombres `std`.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
