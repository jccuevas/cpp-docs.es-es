---
title: SchedulerPolicy (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
dev_langs:
- C++
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: a00f7d9cafbd84fc3bbf6b10f322fad6166110cd
ms.lasthandoff: 03/17/2017

---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy (Clase)
La clase `SchedulerPolicy` contiene un conjunto de pares clave-valor, uno para cada elemento de directiva, que controla el comportamiento de una instancia del programador.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class SchedulerPolicy;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[SchedulerPolicy](#ctor)|Sobrecargado. Construye una nueva directiva de programador y lo rellena con valores de [claves de directiva](concurrency-namespace-enums.md) admitidas por programadores del Runtime de simultaneidad y el Administrador de recursos.|  
|[~ SchedulerPolicy (destructor)](#dtor)|Destruye una directiva de programador.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[GetPolicyValue](#getpolicyvalue)|Recupera el valor de la clave de directiva proporcionado como el parámetro `key`.|  
|[SetConcurrencyLimits](#setconcurrencylimits)|Simultáneamente establece las directivas `MinConcurrency` y `MaxConcurrency` en el objeto `SchedulerPolicy`.|  
|[SetPolicyValue](#setpolicyvalue)|Establece el valor de la clave de directiva proporcionado como el parámetro `key` y devuelve el valor anterior.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operator=](#operator_eq)|Asigna la directiva de programador a partir de otra directiva de programador.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las directivas que se pueden controlar mediante la `SchedulerPolicy` de clases, consulte [PolicyElementKey](concurrency-namespace-enums.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SchedulerPolicy`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h, concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getpolicyvalue"></a>GetPolicyValue 

 Recupera el valor de la clave de directiva proporcionado como el parámetro `key`.  
  
```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Para recuperar un valor para la clave de directiva.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la clave especificada por el `key` se admite el parámetro, el valor de directiva de la clave se convierte en un `unsigned int`.  
  
### <a name="remarks"></a>Comentarios  
 El método producirá [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) para una clave de directiva no válido.  
  
##  <a name="operator_eq"></a>operador = 

 Asigna la directiva de programador a partir de otra directiva de programador.  
  
```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```  
  
### <a name="parameters"></a>Parámetros  
 `_RhsPolicy`  
 La directiva para asignar a esta directiva.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la directiva del programador.  
  
### <a name="remarks"></a>Comentarios  
 A menudo, la manera más conveniente de definir una nueva directiva del programador es copiar una directiva existente y modificarla mediante los métodos `SetPolicyValue` o `SetConcurrencyLimits`.  
  
##  <a name="ctor"></a>SchedulerPolicy 

 Construye una nueva directiva de programador y lo rellena con valores de [claves de directiva](concurrency-namespace-enums.md) admitidas por programadores del Runtime de simultaneidad y el Administrador de recursos.  
  
```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
 ...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PolicyKeyCount`  
 El número de pares clave-valor que sigue al parámetro `_PolicyKeyCount`.  
  
 `_SrcPolicy`  
 La directiva de origen que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor crea una nueva directiva de programador donde todas las directivas se inicializarán en sus valores predeterminado.  
  
 El segundo constructor crea una nueva directiva del programador que usa un estilo de inicialización de parámetro con nombre. Los valores que aparecen después del parámetro `_PolicyKeyCount` se proporcionan como pares clave-valor. Cualquier clave de directiva que no se especifique en este constructor tendrá su valor predeterminado. Este constructor podría producir las excepciones [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) o [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).  
  
 El tercer constructor es un constructor de copias. A menudo, la manera más conveniente de definir una nueva directiva del programador es copiar una directiva existente y modificarla mediante los métodos `SetPolicyValue` o `SetConcurrencyLimits`.  
  
##  <a name="dtor"></a>~ SchedulerPolicy 

 Destruye una directiva de programador.  
  
```
~SchedulerPolicy();
```  
  
##  <a name="setconcurrencylimits"></a>SetConcurrencyLimits 

 Simultáneamente establece las directivas `MinConcurrency` y `MaxConcurrency` en el objeto `SchedulerPolicy`.  
  
```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MinConcurrency`  
 El valor de la `MinConcurrency` clave de directiva.  
  
 `_MaxConcurrency`  
 El valor de la `MaxConcurrency` clave de directiva.  
  
### <a name="remarks"></a>Comentarios  
 El método producirá [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) si el valor especificado para la `MinConcurrency` directiva es mayor que el especificado para el `MaxConcurrency` directiva.  
  
 El método también puede producir [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) para otros valores no válidos.  
  
##  <a name="setpolicyvalue"></a>SetPolicyValue 

 Establece el valor de la clave de directiva proporcionado como el parámetro `key` y devuelve el valor anterior.  
  
```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Para establecer un valor para la clave de directiva.  
  
 `value`  
 El valor para establecer la clave de directiva.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la clave especificada por el `key` se admite el parámetro, el valor de directiva anterior de la clave se convierte en un `unsigned int`.  
  
### <a name="remarks"></a>Comentarios  
 El método producirá [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) para una clave de directiva no válida o cualquier clave de directiva cuyo valor no se puede establecer mediante el `SetPolicyValue` método.  
  
 El método producirá [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) para un valor que no es compatible con la clave especificada por el `key` parámetro.  
  
 Tenga en cuenta que este método no se permite establecer el `MinConcurrency` o `MaxConcurrency` las directivas. Para establecer estos valores, utilice la [SetConcurrencyLimits](#setconcurrencylimits) método.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [CurrentScheduler (clase)](currentscheduler-class.md)   
 [Scheduler (clase)](scheduler-class.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




