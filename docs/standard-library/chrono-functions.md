---
title: Funciones de &lt;chrono&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
caps.latest.revision: 10
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 68c68070265c8cc7ff4d6c5c070b4e7849d50a91
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="ltchronogt-functions"></a>Funciones de &lt;chrono&gt;
||||  
|-|-|-|  
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|  
  

##  <a name="duration_cast"></a>duration_cast
 Convierte un objeto `duration` a un tipo especificado.  
  
```  
template <class To, class Rep, class Period>  
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `duration` de tipo `To` que representa el intervalo de tiempo `Dur`, que se trunca si tiene que ajustarse al tipo de destino.  
  
### <a name="remarks"></a>Comentarios  
 Si `To` es una creación de instancia de `duration`, esta función no participa en la resolución de sobrecarga.  
  
##  <a name="time_point_cast"></a>time_point_cast
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


