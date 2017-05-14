---
title: Funciones de &lt;thread&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
caps.latest.revision: 12
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 3c603ac75955c057cfba009494a9a430fd987a69
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="ltthreadgt-functions"></a>Funciones de &lt;thread&gt;
||||  
|-|-|-|  
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|  
|[swap](#swap)|[yield](#yield)|  
  
##  <a name="get_id"></a>  get_id  
 Identifica de forma única el subproceso de ejecución actual.  
  
```  
thread::id this_thread::get_id() noexcept;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de tipo [thread::id](../standard-library/thread-class.md) que identifica de forma única el subproceso de ejecución actual.  
  
##  <a name="sleep_for"></a>  sleep_for  
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
  
##  <a name="sleep_until"></a>  sleep_until  
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
  
##  <a name="swap"></a>  swap  
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
  
##  <a name="yield"></a>  yield  
 Indica al sistema operativo que ejecute otros subprocesos, incluso si el subproceso actual seguiría ejecutándose en condiciones normales.  
  
```  
inline void yield() noexcept;  
```  
  
## <a name="see-also"></a>Vea también  
 [\<thread>](../standard-library/thread.md)


