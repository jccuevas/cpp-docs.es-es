---
title: espacio de nombres de simultaneidad operadores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
dev_langs:
- C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8065be6cc53cad04d5d52bea91da05bb3125dd63
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162573"
---
# <a name="concurrency-namespace-operators"></a>los operadores del espacio de nombres de simultaneidad

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator||](#operator_lor)|

##  <a name="operator_lor"></a>  operador&#124; &#124; operador

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

### <a name="parameters"></a>Parámetros

*ReturnType*<br/>
Tipo de la tarea devuelta.

*LHS*<br/>
Primera tarea que debe combinarse en la tarea resultante.

*RHS*<br/>
Segunda tarea que se va a combinar en la tarea resultante.

### <a name="return-value"></a>Valor devuelto

Una tarea que se completa correctamente cuando cualquiera de las tareas de entrada se ha completado correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.

### <a name="remarks"></a>Comentarios

Si las dos tareas se cancelan o producen excepciones, la tarea devuelta se completará en el estado cancelado, y una de las excepciones, si se encuentra alguno, se producirá cuando se llama a `get()` o `wait()` en esa tarea.

##  <a name="operator_amp_amp"></a>  operador&amp; &amp; operador

Crea una tarea que se completará correctamente cuando las tareas proporcionadas como argumentos se completen correctamente.

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

### <a name="parameters"></a>Parámetros

*ReturnType*<br/>
Tipo de la tarea devuelta.

*LHS*<br/>
Primera tarea que debe combinarse en la tarea resultante.

*RHS*<br/>
Segunda tarea que se va a combinar en la tarea resultante.

### <a name="return-value"></a>Valor devuelto

Tarea que se completa correctamente cuando ambas tareas de entrada se completan correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.

### <a name="remarks"></a>Comentarios

Si una de las tareas se cancela o inicia una excepción, la tarea devuelta finalizará prematuramente con el estado cancelado y se generará una excepción (si se encuentra una) al llamar a `get()` o `wait()` en dicha tarea.

##  <a name="operator_eq_eq"></a>  operador == (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es igual al objeto `concurrent_vector` del lado derecho.

```
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

**True** si el vector simultáneo en el lado izquierdo del operador es igual que el vector simultáneo en el lado derecho del operador; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_neq"></a>  operador! = (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador no es igual al objeto `concurrent_vector` del lado derecho.

```
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

**True** si los vectores simultáneos no son iguales; **false** si los vectores simultáneos son iguales.

### <a name="remarks"></a>Comentarios

Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_lt"></a>  operador&lt; operador

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor que el objeto `concurrent_vector` del lado derecho.

```
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

**True** si el vector simultáneo en el lado izquierdo del operador es menor que el vector simultáneo en el lado derecho del operador; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

El comportamiento de este operador es idéntico al operador equivalente para la `vector` clase en el `std` espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_lt_eq"></a>  operador&lt;= (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor o igual que el objeto `concurrent_vector` del lado derecho.

```
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

**True** si el vector simultáneo en el lado izquierdo del operador es menor o igual que el vector simultáneo en el lado derecho del operador; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

El comportamiento de este operador es idéntico al operador equivalente para la `vector` clase en el `std` espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_gt"></a>  operador&gt; operador

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor que el objeto `concurrent_vector` del lado derecho.

```
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

**True** si el vector simultáneo en el lado izquierdo del operador es mayor que el vector simultáneo en el lado derecho del operador; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

El comportamiento de este operador es idéntico al operador equivalente para la `vector` clase en el `std` espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

##  <a name="operator_gt_eq"></a>  operador&gt;= (operador)

Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor o igual que el objeto `concurrent_vector` del lado derecho.

```
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

**True** si el vector simultáneo en el lado izquierdo del operador es mayor o igual que el vector simultáneo en el lado derecho del operador; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

El comportamiento de este operador es idéntico al operador equivalente para la `vector` clase en el `std` espacio de nombres.

Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
