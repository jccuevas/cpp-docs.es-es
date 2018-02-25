---
title: completion_future (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
dev_langs:
- C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24f7012f7fdd9aaeb2443665187aba4eef483e0f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="completionfuture-class"></a>completion_future (Clase)
Representa un futuro que corresponde a una operación asincrónica de C++ AMP.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[completion_future Constructor](#ctor)|Inicializa una nueva instancia de la clase `completion_future`.|  
|[~completion_future Destructor](#dtor)|Destruye el objeto `completion_future`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[get](#get)|Espera hasta que se complete la operación asincrónica asociada.|  
|[a continuación](#then)|Un objeto de función de devolución de llamada que se encadena el `completion_future` objeto que se ejecuta cuando finaliza la ejecución de la operación asincrónica asociada.|  
|[to_task](#to_task)|Devuelve un `task` objeto corresponde a la operación asincrónica asociada.|  
|[valid](#valid)|Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.|  
|[wait](#wait)|Se bloquea hasta que se complete la operación asincrónica asociada.|  
|[wait_for](#wait_for)|Se bloquea hasta que se complete la operación asincrónica asociada o el tiempo especificado por `_Rel_time` ha transcurrido.|  
|[wait_until](#wait_until)|Se bloquea hasta que se complete la operación asincrónica asociada o hasta que la hora actual supera el valor especificado por `_Abs_time`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator std::shared_future\<void>](#operator_shared_future)|Convierte implícitamente el `completion_future` el objeto a un `std::shared_future` objeto.|  
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `completion_future` objeto en éste.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `completion_future`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** simultaneidad  


## <a name="ctor"></a> completion_future 

Inicializa una nueva instancia de la clase `completion_future`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
completion_future();  
  
completion_future(  
    const completion_future& _Other );  
  
completion_future(  
    completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `completion_future` objeto para copiar o mover.  
  
### <a name="overloads-list"></a>Lista de sobrecargas  
  
|nombre|Descripción|  
|----------|-----------------|  
|`completion_future();`|Inicializa una nueva instancia de la `completion_future` (clase)|  
|`completion_future(const completion_future& _Other);`|Inicializa una nueva instancia de la `completion_future` clase copiando un constructor.|  
|`completion_future(completion_future&& _Other);`|Inicializa una nueva instancia de la `completion_future` clase moviendo un constructor.|  
  
## <a name="get"></a> Obtener 

Espera hasta que se complete la operación asincrónica asociada. Produce la excepción almacenada si se encontró uno durante la operación asincrónica.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void get() const;  
```  
  
## <a name="operator_shared_future"></a> operador std::shared_future<void> 

Convierte implícitamente el `completion_future` el objeto a un `std::shared_future` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto `std::shared_future`.  
  
## <a name="operator_eq"></a> operador = 

Copia el contenido del elemento especificado `completion_future` objeto en éste.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 El objeto que lo copien.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `completion_future` objeto.  
  
## <a name="overloads-list"></a>Lista de sobrecargas  
  
|nombre|Descripción|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|Copia el contenido del elemento especificado `completion_future` objeto en este caso, mediante una copia en profundidad.|  
|`completion_future& operator=(completion_future&& _Other);`|Copia el contenido del elemento especificado `completion_future` objeto en este caso, mediante una asignación de movimiento.|  
  
## <a name="then">a continuación</a> 

Un objeto de función de devolución de llamada que se encadena el `completion_future` objeto que se ejecuta cuando finaliza la ejecución de la operación asincrónica asociada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template <typename _Functor>  
void then(const _Functor & _Func ) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Functor`  
 El functor de devolución de llamada.  
  
 `_Func`  
 El objeto de función de devolución de llamada.  
  
## <a name="to_task"></a> to_task 

Devuelve un `task` objeto corresponde a la operación asincrónica asociada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `task` objeto corresponde a la operación asincrónica asociada.  
  
## <a name="valid"></a> válido 

Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el objeto está asociado a una operación asincrónica; en caso contrario, `false`.  
  
## <a name="wait"></a> espera 

Se bloquea hasta que se complete la operación asincrónica asociada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void wait() const;  
```  
  
## <a name="wait_for"></a> wait_for 

Se bloquea hasta que se complete la operación asincrónica asociada o la hora especificada por `_Rel_time` ha transcurrido.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template <  
    class _Rep,  
    class _Period  
>  
std::future_status::future_status wait_for(  
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rep`  
 Un tipo aritmético que representa el número de pasos.  
  
 `_Period`  
 Std::ratio que representa el número de segundos que deben transcurrir por TIC.  
  
 `_Rel_time`  
 La cantidad máxima de tiempo de espera para que se complete la operación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve:  
  
-   `std::future_status::deferred` Si no se está ejecutando la operación asincrónica asociada.  
  
-   `std::future_status::ready` Si finaliza la operación asincrónica asociada.  
  
-   `std::future_status::timeout` Si el especificado ha transcurrido el período de tiempo.  
  
## <a name="wait_until"></a> wait_until 

Se bloquea hasta que se complete la operación asincrónica asociada o hasta que la hora actual supera el valor especificado por `_Abs_time`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template <  
    class _Clock,  
    class _Duration  
>  
std::future_status::future_status wait_until(  
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Clock`  
 El reloj en el que se mide en este momento.  
  
 `_Duration`  
 El intervalo de tiempo desde el inicio del `_Clock`del tiempo, tras el cual la función agotará el tiempo.  
  
 `_Abs_time`  
 El punto en el tiempo después del cual la función agotará el tiempo de espera.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve:  
  
1.  `std::future_status::deferred` Si no se está ejecutando la operación asincrónica asociada.  
  
2.  `std::future_status::ready` Si finaliza la operación asincrónica asociada.  
  
3.  `std::future_status::timeout` Si el período de tiempo especificado haya transcurrido.  
  
## <a name="dtor"></a> ~completion_future 

Destruye el objeto `completion_future`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
