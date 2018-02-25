---
title: time_point (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
dev_langs:
- C++
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::chrono [C++], time_point
ms.workload:
- cplusplus
ms.openlocfilehash: 4d81f49fd94dcedacfe33de75e307a441f74a94e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="timepoint-class"></a>time_point (Clase)
`time_point` describe un tipo que representa un punto en el tiempo. Contiene un objeto de tipo [duration](../standard-library/duration-class.md) que almacena el tiempo transcurrido desde la época representada por el argumento de plantilla `Clock`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Clock,  
    class Duration = typename Clock::duration>  
class time_point;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`time_point::clock`|Sinónimo del parámetro de plantilla `Clock`.|  
|`time_point::duration`|Sinónimo del parámetro de plantilla `Duration`.|  
|`time_point::period`|Sinónimo del nombre de tipo anidado `duration::period`.|  
|`time_point::rep`|Sinónimo del nombre de tipo anidado `duration::rep`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[time_point](#time_point)|Construye un objeto `time_point`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[max](#max)|Especifica el límite superior de `time_point::ref`.|  
|[min](#min)|Especifica el límite inferior de `time_point::ref`.|  
|[time_since_epoch](#time_since_epoch)|Devuelve el valor de `duration` almacenado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[time_point::operator+=](#op_add_eq)|Suma un valor especificado a la duración almacenada.|  
|[time_point::operator-=](#operator-_eq)|Resta un valor especificado de la duración almacenada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<chrono >  
  
 **Espacio de nombres:** std::chrono  
  
##  <a name="max"></a>  time_point::max
 Método estático que devuelve el límite superior para los valores de tipo `time_point::ref`.  
  
```  
static constexpr time_point max();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En efecto, devuelve `time_point(duration::max())`.  
  
##  <a name="min"></a>  time_point::min
 Método estático que devuelve el límite inferior para valores de tipo `time_point::ref`.  
  
```  
static constexpr time_point min();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En efecto, devuelve `time_point(duration::min())`.  
  
##  <a name="op_add_eq"></a>  time_point::operator+=  
 Suma un valor especificado al valor [duration](../standard-library/duration-class.md) almacenado.  
  
```  
time_point& operator+=(const duration& Dur);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Un objeto `duration`.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `time_point` después del cual se realiza la suma.  
  
##  <a name="time_point__operator-_eq"></a>  time_point::operator-=  
 Resta un valor especificado del valor [duration](../standard-library/duration-class.md) almacenado.  
  
```  
time_point& operator-=(const duration& Dur);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Un objeto `duration`.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `time_point` después del cual se realiza la resta.  
  
##  <a name="time_point"></a>  time_point::time_point (Constructor)  
 Construye un objeto `time_point`.  
  
```  
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>  
constexpr time_point(const time_point<clock, Duration2>& Tp);
```  
  
### <a name="parameters"></a>Parámetros  
 `Dur`  
 Un objeto [duration](../standard-library/duration-class.md).  
  
 `Tp`  
 Un objeto `time_point`.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor crea un objeto cuyo valor `duration` almacenado es igual a [duration::zero](../standard-library/duration-class.md#zero).  
  
 El segundo constructor crea un objeto cuyo valor de duración almacenado es igual a `Dur`. A menos que `is_convertible<Duration2, duration>`*sea true*, el segundo constructor no participa en la resolución de sobrecarga. Para más información, vea [<type_traits>](../standard-library/type-traits.md).  
  
 El tercer constructor inicializa su valor `duration` mediante `Tp.time_since_epoch()`.  
  
##  <a name="time_since_epoch"></a>  time_point::time_since_epoch
 Recupera el valor [duration](../standard-library/duration-class.md) almacenado.  
  
```  
constexpr duration time_since_epoch() const;
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)

