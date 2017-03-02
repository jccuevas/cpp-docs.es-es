---
title: espacio de nombres de simultaneidad operadores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 7fc7b500d882bb4e023904a147a7736996b5c5de
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-operators"></a>espacio de nombres de simultaneidad operadores
||||  
|-|-|-|  
|[operador! = (operador)](#operator_neq)|[operador&amp; &amp; (operador)](#operator_amp_amp)|[operador&gt; (operador)](#operator_gt)|  
|[operador&gt;= (operador)](#operator_gt_eq)|[operador&lt; (operador)](#operator_lt)|[operador&lt;= (operador)](#operator_lt_eq)|  
|[Operator == (operador)](#operator_eq_eq)|[operator|| Operator](#operator_lor)|  
  
##  <a name="a-nameoperatorlora--operator124124-operator"></a><a name="operator_lor"></a>operador || (Operador)  
 Crea una tarea que se completará correctamente cuando una de las tareas proporcionadas como argumentos se complete correctamente.  
  
```  
template<
    typename _ReturnType  
>  
task<_ReturnType>   operator||(
    const task<_ReturnType>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>   operator||(
    const task<std::vector<_ReturnType>>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>   operator||(
    const task<_ReturnType>& _Lhs,  
    const task<std::vector<_ReturnType>>& _Rhs);

 
inline task<void>   operator||(
    const task<void>& _Lhs,  
    const task<void>& _Rhs);
```  
  
### <a name="parameters"></a>Parámetros  
 `_ReturnType`  
 Tipo de la tarea devuelta.  
  
 `_Lhs`  
 Primera tarea que debe combinarse en la tarea resultante.  
  
 `_Rhs`  
 Segunda tarea que se va a combinar en la tarea resultante.  
  
### <a name="return-value"></a>Valor devuelto  
 Una tarea que se completa correctamente cuando cualquiera de las tareas de entrada se ha completado correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.  
  
### <a name="remarks"></a>Comentarios  
 Si las tareas se cancelan o excepciones, se completará la tarea devuelta en el estado cancelado, y una de las excepciones, si se encuentra alguno, se producirá cuando se llama a `get()` o `wait()` en esa tarea.  
  
##  <a name="a-nameoperatorampampa--operatorampamp-operator"></a><a name="operator_amp_amp"></a>operador&amp; &amp; (operador)  
 Crea una tarea que se completará correctamente cuando las tareas proporcionadas como argumentos se completen correctamente.  
  
```  
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<_ReturnType>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<std::vector<_ReturnType>>& _Lhs,  
    const task<_ReturnType>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<_ReturnType>& _Lhs,  
    const task<std::vector<_ReturnType>>& _Rhs);

 
template<
    typename _ReturnType  
>  
task<std::vector<_ReturnType>>    operator&&(
    const task<std::vector<_ReturnType>>& _Lhs,  
    const task<std::vector<_ReturnType>>& _Rhs);

 
inline task<void>    operator&&(
    const task<void>& _Lhs,  
    const task<void>& _Rhs);
```  
  
### <a name="parameters"></a>Parámetros  
 `_ReturnType`  
 Tipo de la tarea devuelta.  
  
 `_Lhs`  
 Primera tarea que debe combinarse en la tarea resultante.  
  
 `_Rhs`  
 Segunda tarea que se va a combinar en la tarea resultante.  
  
### <a name="return-value"></a>Valor devuelto  
 Tarea que se completa correctamente cuando ambas tareas de entrada se completan correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.  
  
### <a name="remarks"></a>Comentarios  
 Si una de las tareas se cancela o inicia una excepción, la tarea devuelta finalizará prematuramente con el estado cancelado y se generará una excepción (si se encuentra una) al llamar a `get()` o `wait()` en dicha tarea.  
  
##  <a name="a-nameoperatoreqeqa--operator-operator"></a><a name="operator_eq_eq"></a>Operator == (operador)  
 Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es igual al objeto `concurrent_vector` del lado derecho.  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de los elementos almacenados en los vectores simultáneos.  
  
 `A1`  
 El tipo de asignador del primer `concurrent_vector` objeto.  
  
 `A2`  
 El tipo de asignador del segundo `concurrent_vector` objeto.  
  
 `_A`  
 Objeto de tipo `concurrent_vector`.  
  
 `_B`  
 Objeto de tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vector simultáneo en el lado izquierdo del operador es igual que el vector simultáneo en el lado derecho del operador; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
 Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.  
  
##  <a name="a-nameoperatorneqa--operator-operator"></a><a name="operator_neq"></a>operador! = (operador)  
 Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador no es igual al objeto `concurrent_vector` del lado derecho.  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de los elementos almacenados en los vectores simultáneos.  
  
 `A1`  
 El tipo de asignador del primer `concurrent_vector` objeto.  
  
 `A2`  
 El tipo de asignador del segundo `concurrent_vector` objeto.  
  
 `_A`  
 Objeto de tipo `concurrent_vector`.  
  
 `_B`  
 Objeto de tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si los vectores simultáneos no son iguales; `false` si los vectores simultáneos son iguales.  
  
### <a name="remarks"></a>Comentarios  
 Dos vectores simultáneos son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
 Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.  
  
##  <a name="a-nameoperatorlta--operatorlt-operator"></a><a name="operator_lt"></a>operador&lt; (operador)  
 Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor que el objeto `concurrent_vector` del lado derecho.  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de los elementos almacenados en los vectores simultáneos.  
  
 `A1`  
 El tipo de asignador del primer `concurrent_vector` objeto.  
  
 `A2`  
 El tipo de asignador del segundo `concurrent_vector` objeto.  
  
 `_A`  
 Objeto de tipo `concurrent_vector`.  
  
 `_B`  
 Objeto de tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vector simultáneo en el lado izquierdo del operador es menor que el vector simultáneo en el lado derecho del operador; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento de este operador es idéntico al operador equivalente para la `vector` de clase en el `std` espacio de nombres.  
  
 Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.  
  
##  <a name="a-nameoperatorlteqa--operatorlt-operator"></a><a name="operator_lt_eq"></a>operador&lt;= (operador)  
 Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor o igual que el objeto `concurrent_vector` del lado derecho.  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de los elementos almacenados en los vectores simultáneos.  
  
 `A1`  
 El tipo de asignador del primer `concurrent_vector` objeto.  
  
 `A2`  
 El tipo de asignador del segundo `concurrent_vector` objeto.  
  
 `_A`  
 Objeto de tipo `concurrent_vector`.  
  
 `_B`  
 Objeto de tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vector simultáneo en el lado izquierdo del operador es menor o igual que el vector simultáneo en el lado derecho del operador; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento de este operador es idéntico al operador equivalente para la `vector` de clase en el `std` espacio de nombres.  
  
 Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.  
  
##  <a name="a-nameoperatorgta--operatorgt-operator"></a><a name="operator_gt"></a>operador&gt; (operador)  
 Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor que el objeto `concurrent_vector` del lado derecho.  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de los elementos almacenados en los vectores simultáneos.  
  
 `A1`  
 El tipo de asignador del primer `concurrent_vector` objeto.  
  
 `A2`  
 El tipo de asignador del segundo `concurrent_vector` objeto.  
  
 `_A`  
 Objeto de tipo `concurrent_vector`.  
  
 `_B`  
 Objeto de tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vector simultáneo en el lado izquierdo del operador es mayor que el vector simultáneo en el lado derecho del operador; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento de este operador es idéntico al operador equivalente para la `vector` de clase en el `std` espacio de nombres.  
  
 Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.  
  
##  <a name="a-nameoperatorgteqa--operatorgt-operator"></a><a name="operator_gt_eq"></a>operador&gt;= (operador)  
 Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor o igual que el objeto `concurrent_vector` del lado derecho.  
  
```  
template<
    typename T,  
    class A1,  
    class A2  
>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de los elementos almacenados en los vectores simultáneos.  
  
 `A1`  
 El tipo de asignador del primer `concurrent_vector` objeto.  
  
 `A2`  
 El tipo de asignador del segundo `concurrent_vector` objeto.  
  
 `_A`  
 Objeto de tipo `concurrent_vector`.  
  
 `_B`  
 Objeto de tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vector simultáneo en el lado izquierdo del operador es mayor o igual que el vector simultáneo en el lado derecho del operador; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento de este operador es idéntico al operador equivalente para la `vector` de clase en el `std` espacio de nombres.  
  
 Este método no es seguro para simultaneidad con respecto a otros métodos que podrían modificar cualquiera de los vectores simultáneos `_A` o `_B`.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

