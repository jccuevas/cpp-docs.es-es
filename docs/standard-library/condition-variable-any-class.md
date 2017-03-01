---
title: condition_variable_any (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- condition_variable/std::condition_variable_any
dev_langs:
- C++
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
caps.latest.revision: 15
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: a04164eb30bdb0403f131d64a31b9c7d9cb5656f
ms.lasthandoff: 02/24/2017

---
# <a name="conditionvariableany-class"></a>condition_variable_any (Clase)
Utilice la clase `condition_variable_any` para esperar un evento que tenga cualquier tipo  `mutex`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class condition_variable_any;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[condition_variable_any::condition_variable_any (Constructor)](#condition_variable_any__condition_variable_any_constructor)|Construye un objeto `condition_variable_any`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[condition_variable_any::notify_all](#condition_variable_any__notify_all_method)|Desbloquea todos los subprocesos que están esperando el objeto `condition_variable_any`.|  
|[condition_variable_any::notify_one](#condition_variable_any__notify_one_method)|Desbloquea uno de los subprocesos que están esperando el objeto `condition_variable_any`.|  
|[condition_variable_any::wait](#condition_variable_any__wait_method)|Bloquea un subproceso.|  
|[condition_variable_any::wait_for](#condition_variable_any__wait_for_method)|Bloquea un subproceso y establece un intervalo de tiempo después del cual el subproceso se desbloquea.|  
|[condition_variable_any::wait_until](#condition_variable_any__wait_until_method)|Bloquea un subproceso y establece un punto máximo en el tiempo en el que el subproceso se desbloquea.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** condition_variable  
  
 **Espacio de nombres:** std  
  
##  <a name="a-nameconditionvariableanyconditionvariableanyconstructora--conditionvariableanyconditionvariableany-constructor"></a><a name="condition_variable_any__condition_variable_any_constructor"></a>  condition_variable_any::condition_variable_any (Constructor)  
 Construye un objeto `condition_variable_any`.  
  
```
condition_variable_any();
```  
  
### <a name="remarks"></a>Comentarios  
 Si no queda suficiente memoria disponible, el constructor produce un objeto [system_error](../standard-library/system-error-class.md) que tiene un código de error de `not_enough_memory`. Si el objeto no puede construirse porque algún otro recurso no está disponible, el constructor produce un objeto `system_error` que tiene un código de error de `resource_unavailable_try_again`.  
  
##  <a name="a-nameconditionvariableanynotifyallmethoda--conditionvariableanynotifyall"></a><a name="condition_variable_any__notify_all_method"></a>  condition_variable_any::notify_all  
 Desbloquea todos los subprocesos que están esperando el objeto `condition_variable_any`.  
  
```
void notify_all() noexcept;
```  
  
##  <a name="a-nameconditionvariableanynotifyonemethoda--conditionvariableanynotifyone"></a><a name="condition_variable_any__notify_one_method"></a>  condition_variable_any::notify_one  
 Desbloquea uno de los subprocesos que están esperando el objeto `condition_variable_any`.  
  
```
void notify_one() noexcept;
```  
  
##  <a name="a-nameconditionvariableanywaitmethoda--conditionvariableanywait"></a><a name="condition_variable_any__wait_method"></a>  condition_variable_any::wait  
 Bloquea un subproceso.  
  
```
template <class Lock>  
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```  
  
### <a name="parameters"></a>Parámetros  
 `Lck`  
 Objeto `mutex` de cualquier tipo.  
  
 `Pred`  
 Cualquier expresión que devuelve `true` o `false`.  
  
### <a name="remarks"></a>Comentarios  
 El primer método se bloquea hasta que el objeto `condition_variable_any` se señaliza mediante una llamada a [notify_one](../standard-library/condition-variable-class.md#condition_variable__notify_one_method) o a [notify_all](../standard-library/condition-variable-class.md#condition_variable__notify_all_method). También se puede reactivar en falso.  
  
 El segundo método en efecto ejecuta el código siguiente.  
  
```
while (!Pred())
    wait(Lck);
```    
  
##  <a name="a-nameconditionvariableanywaitformethoda--conditionvariableanywaitfor"></a><a name="condition_variable_any__wait_for_method"></a>  condition_variable_any::wait_for  
 Bloquea un subproceso y establece un intervalo de tiempo después del cual el subproceso se desbloquea.  
  
```
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```  
  
### <a name="parameters"></a>Parámetros  
 `Lck`  
 Objeto `mutex` de cualquier tipo.  
  
 `Rel_time`  
 Objeto `chrono::duration` que especifica la cantidad de tiempo que tiene que transcurrir hasta que el subproceso se reactive.  
  
 `Pred`  
 Cualquier expresión que devuelve `true` o `false`.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer método devuelve `cv_status::timeout` si la espera termina cuando ha transcurrido `Rel_time`. De lo contrario, el método devuelve `cv_status::no_timeout`.  
  
 El segundo método devuelve el valor de `Pred`.  
  
### <a name="remarks"></a>Comentarios  
 El primer método se bloquea hasta que se señaliza el objeto `condition_variable_any` mediante una llamada a [notify_one](../standard-library/condition-variable-class.md#condition_variable__notify_one_method) o [notify_all](../standard-library/condition-variable-class.md#condition_variable__notify_all_method), o hasta que ha transcurrido el intervalo de tiempo `Rel_time`. También se puede reactivar en falso.  
  
 El segundo método en efecto ejecuta el código siguiente.  
  
```cpp  
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
##  <a name="a-nameconditionvariableanywaituntilmethoda--conditionvariableanywaituntil"></a><a name="condition_variable_any__wait_until_method"></a>  condition_variable_any::wait_until  
 Bloquea un subproceso y establece un punto máximo en el tiempo en el que el subproceso se desbloquea.  
  
```
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```  
  
### <a name="parameters"></a>Parámetros  
 `Lck`  
 Objeto de exclusión mutua.  
  
 `Abs_time`  
 Un objeto [chrono::time_point](../standard-library/time-point-class.md).  
  
 `Pred`  
 Cualquier expresión que devuelve `true` o `false`.  
  
### <a name="return-value"></a>Valor devuelto  
 Los métodos que devuelven un tipo `cv_status` devuelven `cv_status::timeout` si la espera termina cuando transcurre `Abs_time`. De lo contrario, los métodos devuelven `cv_status::no_timeout`.  
  
 Los métodos que devuelven un tipo `bool` devuelven el valor de `Pred`.  
  
### <a name="remarks"></a>Comentarios  
 El primer método se bloquea hasta que el objeto `condition_variable` se señaliza mediante una llamada a [notify_one](../standard-library/condition-variable-class.md#condition_variable__notify_one_method) o a [notify_all](../standard-library/condition-variable-class.md#condition_variable__notify_all_method), o hasta que transcurre `Abs_time`. También se puede reactivar en falso.  
  
 El segundo método en efecto ejecuta el código siguiente.  
  
```
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```  
  
 Los métodos tercero y cuarto utilizan un puntero a un objeto de tipo `xtime` para reemplazar el objeto `chrono::time_point`. El objeto `xtime` especifica el tiempo máximo que hay que esperar una señal.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [<condition_variable>](../standard-library/condition-variable.md)




