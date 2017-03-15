---
title: completion_future (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amprt/Concurrency::completion_future
dev_langs:
- C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: 8
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: a9a77c3cf3c183021b70789b0e17a6b8ad8d786c
ms.lasthandoff: 02/24/2017

---
# <a name="completionfuture-class"></a>completion_future (Clase)
Representa un futuro que corresponde a una operación asincrónica de C++ AMP.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[completion_future (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `completion_future`.|  
|[~ completion_future (destructor)](#dtor)|Destruye el objeto `completion_future`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Get (método)](#get)|Espera a que finalice la operación asincrónica asociada.|  
|[Then (método)](#then)|Un objeto de función de devolución de llamada que se encadena el `completion_future` objeto que se ejecuta cuando finaliza la ejecución de la operación asincrónica asociada.|  
|[to_task (método)](#to_task)|Devuelve un `task` objeto correspondiente a la operación asincrónica asociada.|  
|[Método válido](#valid)|Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.|  
|[Wait (método)](#wait)|Se bloquea hasta que se complete la operación asincrónica asociada.|  
|[wait_for (método)](#wait_for)|Se bloquea hasta que finaliza la operación asincrónica asociada o el tiempo especificado por `_Rel_time` ha transcurrido.|  
|[wait_until (método)](#wait_until)|Se bloquea hasta que se complete la operación asincrónica asociada o hasta que el tiempo actual supera el valor especificado por `_Abs_time`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador std::shared_future\<void > (operador)](#operator_shared_future)|Convierte implícitamente el `completion_future` objeto un `std::shared_future` objeto.|  
|[operador = (operador)](#operator_eq)|Copia el contenido del elemento `completion_future` objeto en éste.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `completion_future`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** simultaneidad  


## <a name="a-namectora-completionfuture"></a><a name="ctor"></a>completion_future 

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|`completion_future();`|Inicializa una nueva instancia de la `completion_future` (clase)|  
|`completion_future(const completion_future& _Other);`|Inicializa una nueva instancia de la `completion_future` clase copiando un constructor.|  
|`completion_future(completion_future&& _Other);`|Inicializa una nueva instancia de la `completion_future` clase moviendo un constructor.|  
  
## <a name="a-namegeta-get"></a><a name="get"></a>Obtener 

Espera a que finalice la operación asincrónica asociada. Produce la excepción almacenada si uno se encontró durante la operación asincrónica.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void get() const;  
```  
  
## <a name="a-nameoperatorsharedfuturea-operator-stdsharedfuturevoid"></a><a name="operator_shared_future"></a>std::shared_future (operador)<void> 

Convierte implícitamente el `completion_future` objeto un `std::shared_future` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto `std::shared_future`.  
  
## <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

Copia el contenido del elemento `completion_future` objeto en éste.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 Objeto que se va a copiar desde.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `completion_future` objeto.  
  
## <a name="overloads-list"></a>Lista de sobrecargas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|Copia el contenido del elemento `completion_future` objeto en este caso, mediante una copia en profundidad.|  
|`completion_future& operator=(completion_future&& _Other);`|Copia el contenido del elemento `completion_future` objeto en este caso, utilizando una asignación de movimiento.|  
  
## <a name="a-namethena-then"></a><a name="then"></a>a continuación 

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
  
## <a name="a-nametotaska-totask"></a><a name="to_task"></a>to_task 

Devuelve un `task` objeto correspondiente a la operación asincrónica asociada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `task` objeto correspondiente a la operación asincrónica asociada.  
  
## <a name="a-namevalida-valid"></a><a name="valid"></a>válido 

Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el objeto está asociado a una operación asincrónica; de lo contrario, `false`.  
  
## <a name="a-namewaita-wait"></a><a name="wait"></a>esperar 

Se bloquea hasta que se complete la operación asincrónica asociada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void wait() const;  
```  
  
## <a name="a-namewaitfora-waitfor"></a><a name="wait_for"></a>wait_for 

Se bloquea hasta que finaliza la operación asincrónica asociada o el tiempo especificado por `_Rel_time` ha transcurrido.  
  
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
 Un std::ratio que representa el número de segundos que transcurren por tic-tac.  
  
 `_Rel_time`  
 La cantidad máxima de tiempo de espera para que se complete la operación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve:  
  
-   `std::future_status::deferred`Si no se está ejecutando la operación asincrónica asociada.  
  
-   `std::future_status::ready`Si ha finalizado la operación asincrónica asociada.  
  
-   `std::future_status::timeout`Si la especificado ha transcurrido el período de tiempo.  
  
## <a name="a-namewaituntila-waituntil"></a><a name="wait_until"></a>wait_until 

Se bloquea hasta que se complete la operación asincrónica asociada o hasta que el tiempo actual supera el valor especificado por `_Abs_time`.  
  
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
 El intervalo de tiempo desde el inicio de `_Clock`del tiempo, después del cual la función agotará el tiempo.  
  
 `_Abs_time`  
 El punto en el tiempo después del cual la función el tiempo de espera.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve:  
  
1.  `std::future_status::deferred`Si no se está ejecutando la operación asincrónica asociada.  
  
2.  `std::future_status::ready`Si ha finalizado la operación asincrónica asociada.  
  
3.  `std::future_status::timeout`Si el período de tiempo especificado haya transcurrido.  
  
## <a name="a-namedtora-completionfuture"></a><a name="dtor"></a>~ completion_future 

Destruye el objeto `completion_future`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

