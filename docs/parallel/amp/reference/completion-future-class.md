---
title: completion_future (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 1c6d8e880fbdb784b22b1e9c879473efa7bc9802
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

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
|[get](#get)|Espera a que finalice la operación asincrónica asociada.|  
|[a continuación](#then)|Un objeto de función de devolución de llamada que se encadena el `completion_future` objeto que se ejecuta cuando finaliza la ejecución de la operación asincrónica asociada.|  
|[to_task](#to_task)|Devuelve un `task` objeto correspondiente a la operación asincrónica asociada.|  
|[válido](#valid)|Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.|  
|[esperar](#wait)|Se bloquea hasta que se complete la operación asincrónica asociada.|  
|[wait_for](#wait_for)|Se bloquea hasta que finaliza la operación asincrónica asociada o el tiempo especificado por `_Rel_time` ha transcurrido.|  
|[wait_until](#wait_until)|Se bloquea hasta que se complete la operación asincrónica asociada o hasta que el tiempo actual supera el valor especificado por `_Abs_time`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador std::shared_future\<void >](#operator_shared_future)|Convierte implícitamente el `completion_future` objeto un `std::shared_future` objeto.|  
|[operator=](#operator_eq)|Copia el contenido del elemento `completion_future` objeto en éste.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `completion_future`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** simultaneidad  


## <a name="ctor"></a>completion_future 

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
  
## <a name="get"></a>Obtener 

Espera a que finalice la operación asincrónica asociada. Produce la excepción almacenada si uno se encontró durante la operación asincrónica.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void get() const;  
```  
  
## <a name="operator_shared_future"></a>std::shared_future (operador)<void> 

Convierte implícitamente el `completion_future` objeto un `std::shared_future` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto `std::shared_future`.  
  
## <a name="operator_eq"></a>operador = 

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
  
## <a name="then"></a>a continuación 

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
  
## <a name="to_task"></a>to_task 

Devuelve un `task` objeto correspondiente a la operación asincrónica asociada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `task` objeto correspondiente a la operación asincrónica asociada.  
  
## <a name="valid"></a>válido 

Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el objeto está asociado a una operación asincrónica; de lo contrario, `false`.  
  
## <a name="wait"></a>esperar 

Se bloquea hasta que se complete la operación asincrónica asociada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void wait() const;  
```  
  
## <a name="wait_for"></a>wait_for 

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
  
## <a name="wait_until"></a>wait_until 

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
  
## <a name="dtor"></a>~ completion_future 

Destruye el objeto `completion_future`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

