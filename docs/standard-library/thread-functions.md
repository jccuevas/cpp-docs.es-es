---
title: Funciones de &lt;thread&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
caps.latest.revision: 12
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: de302b9a2d971b2a39d4ce775799f27dd7244a5c
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt-functions"></a>Funciones de &lt;thread&gt;
||||  
|-|-|-|  
|[get_id](#get_id_function)|[sleep_for](#sleep_for_function)|[sleep_until](#sleep_until_function)|  
|[swap](#swap_function)|[yield](#yield_function)|  
  
##  <a name="a-namegetidfunctiona--getid"></a><a name="get_id_function"></a>  get_id  
 Identifica de forma única el subproceso de ejecución actual.  
  
```  
thread::id this_thread::get_id() noexcept;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de tipo [thread::id](../standard-library/thread-class.md) que identifica de forma única el subproceso de ejecución actual.  
  
##  <a name="a-namesleepforfunctiona--sleepfor"></a><a name="sleep_for_function"></a>  sleep_for  
 Bloquea el subproceso de llamada.  
  
```  
template <class Rep,  
class Period>  
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>Parámetros  
 `Rel_time`  
 Un objeto [duration](../standard-library/duration-class.md) que especifica un intervalo de tiempo.  
  
### <a name="remarks"></a>Comentarios  
 La función bloquea el subproceso de llamada al menos durante el tiempo especificado por `Rel_time`. Esta función no produce ninguna excepción.  
  
##  <a name="a-namesleepuntilfunctiona--sleepuntil"></a><a name="sleep_until_function"></a>  sleep_until  
 Bloquea el subproceso de llamada al menos hasta la hora especificada.  
  
```  
template <class Clock, class Duration>  
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```  
  
### <a name="parameters"></a>Parámetros  
 `Abs_time`  
 Representa un punto en el tiempo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no produce ninguna excepción.  
  
##  <a name="a-nameswapfunctiona--swap"></a><a name="swap_function"></a>  swap  
 Intercambia los estados de dos objetos `thread`.  
  
```  
void swap(thread& Left, thread& Right) noexcept;  
```  
  
### <a name="parameters"></a>Parámetros  
 `Left`  
 Objeto `thread` izquierdo.  
  
 `Right`  
 Objeto `thread` derecho.  
  
### <a name="remarks"></a>Comentarios  
 La función llama a `Left.swap(Right)`.  
  
##  <a name="a-nameyieldfunctiona--yield"></a><a name="yield_function"></a>  yield  
 Indica al sistema operativo que ejecute otros subprocesos, incluso si el subproceso actual seguiría ejecutándose en condiciones normales.  
  
```  
inline void yield() noexcept;  
```  
  
## <a name="see-also"></a>Vea también  
 [\<thread>](../standard-library/thread.md)


