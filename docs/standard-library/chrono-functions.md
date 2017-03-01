---
title: Funciones de &lt;chrono&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 9824bdc37d1ae2d1d3a8e42c727986fd2a194514
ms.lasthandoff: 02/24/2017

---
# <a name="ltchronogt-functions"></a>Funciones de &lt;chrono&gt;
||||  
|-|-|-|  
|[duration_cast (Función)](#duration_cast_function)|[time_point_cast (Función)](#time_point_cast_function)|  
  

##  <a name="a-namedurationcastfunctiona--durationcast-function"></a><a name="duration_cast_function"></a>  duration_cast (Función)  
 Convierte un objeto `duration` a un tipo especificado.  
  
```  
template <class To, class Rep, class Period>  
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `duration` de tipo `To` que representa el intervalo de tiempo `Dur`, que se trunca si tiene que ajustarse al tipo de destino.  
  
### <a name="remarks"></a>Comentarios  
 Si `To` es una creación de instancia de `duration`, esta función no participa en la resolución de sobrecarga.  
  
##  <a name="a-nametimepointcastfunctiona--timepointcast-function"></a><a name="time_point_cast_function"></a>  time_point_cast (Función)  
 Convierte un objeto [time_point](../standard-library/time-point-class.md) en un tipo especificado.  
  
```  
template <class To, class Clock, class Duration>  
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `time_point` que tiene una duración de tipo `To`.  
  
### <a name="remarks"></a>Comentarios  
 A menos que `To` sea una creación de instancia de [duration](../standard-library/duration-class.md), esta función no participa en la resolución de sobrecarga.  
  
## <a name="see-also"></a>Vea también  
 [\<chrono>](../standard-library/chrono.md)


