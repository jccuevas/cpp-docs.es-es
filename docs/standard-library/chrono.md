---
title: '&lt;chrono&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
dev_langs:
- C++
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: c91a494644e2d8d12259c3ee6cd23333eb9bae9e
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="ltchronogt"></a>&lt;chrono&gt;
Incluya el encabezado estándar \<chrono> para definir las clases y funciones que representan y manipulan las duraciones de tiempo e instantes de tiempo.  
  
 A partir de Visual Studio 2015, la implementación de `steady_clock` ha cambiado para cumplir los requisitos estándar de C++ para steadiness y monotonicity. `steady_clock` ahora se basa en QueryPerformanceCounter() y `high_resolution_clock` ahora es un typedef para `steady_clock`. Como resultado, en Visual C++ `steady_clock::time_point` es ahora un typedef para `chrono::time_point<steady_clock>`; sin embargo, esto no es necesariamente así en otras implementaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#include <chrono>  
```  

### <a name="classes"></a>Clases  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[duration (Clase)](../standard-library/duration-class.md)|Describe un tipo que contenga un intervalo de tiempo.|  
|[time_point (Clase)](../standard-library/time-point-class.md)|Describe un tipo que representa un punto en el tiempo.|  
  
### <a name="structs"></a>Structs  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[common_type (Estructura)](../standard-library/common-type-structure.md)|Describe especializaciones de la clase de plantilla [common_type](../standard-library/common-type-class.md) para las creaciones de instancias de `duration` y `time_point`.|  
|[duration_values (Estructura)](../standard-library/duration-values-structure.md)|Proporciona valores concretos para el parámetro `Rep` de plantilla `duration`.|  
|[steady_clock (Struct)](../standard-library/steady-clock-struct.md)|Representa un reloj `steady`.|  
|[system_clock (Estructura)](../standard-library/system-clock-structure.md)|Representa un *tipo de reloj* basado en el reloj en tiempo real del sistema.|  
|[treat_as_floating_point (Estructura)](../standard-library/treat-as-floating-point-structure.md)|Especifica si un tipo puede tratarse como un tipo de punto flotante.|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Convierte un objeto `duration` a un tipo especificado.|  
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Convierte un objeto `time_point` a un tipo especificado.|  
  
### <a name="operators"></a>Operadores  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator-](../standard-library/chrono-operators.md#operator-)|Operador para la resta o la negación de objetos `duration` y `time_point`.|  
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operador de desigualdad que se utiliza con objetos `duration` o `time_point`.|  
|[operator modulo](../standard-library/chrono-operators.md#op_modulo)|Operador para operaciones de módulo en objetos `duration`.|  
|[operator*](../standard-library/chrono-operators.md#op_star)|Operador de multiplicación para objetos `duration`.|  
|[operator/](../standard-library/chrono-operators.md#op_div)|Operador de división para objetos `duration`.|  
|[operator+](../standard-library/chrono-operators.md#op_add)|Agrega objetos `duration` y `time_point`.|  
|[operator&lt;](../standard-library/chrono-operators.md#op_lt)|Determina si un objeto `duration` o `time_point` es menor que otro objeto `duration` o `time_point`.|  
|[operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Determina si un objeto `duration` o `time_point` es menor o igual que otro objeto `duration` o `time_point`.|  
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Determina si dos objetos `duration` representan intervalos de tiempo de la misma longitud o si dos objetos `time_point` representan el mismo punto en el tiempo.|  
|[operator&gt;](../standard-library/chrono-operators.md#op_gt)|Determina si un objeto `duration` o `time_point` es mayor que otro objeto `duration` o `time_point`.|  
|[operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Determina si un objeto `duration` o `time_point` es mayor o igual que otro objeto `duration` o `time_point`.|  
  
### <a name="predefined-duration-types"></a>Tipos predefinidos de duración  
 Para obtener más información sobre los tipos de relación que se usan en los siguientes typedefs, vea [\<ratio>](../standard-library/ratio.md).  
  
|Definición de tipo|Descripción|  
|-------------|-----------------|  
|`typedef duration<long long, nano> nanoseconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un nanosegundo.|  
|`typedef duration<long long, micro> microseconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un microsegundo.|  
|`typedef duration<long long, milli> milliseconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un milisegundo.|  
|`typedef duration<long long> seconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un segundo.|  
|`typedef duration<int, ratio<60> > minutes;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un minuto.|  
|`typedef duration<int, ratio<3600> > hours;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de una hora.|  
  
### <a name="literals"></a>Literales  
 **(C++11)**El encabezado \<chrono> define los siguientes [literales definidos por el usuario](../cpp/user-defined-literals-cpp.md) que puede usar para mayor comodidad, seguridad de tipos y mantenimiento del código. Estos literales se definen en el espacio de nombres alineado `literals::chrono_literals` y están en ámbito cuando std:: chrono está en ámbito.  
  
|Literal|Descripción|  
|-------------|-----------------|  
|operador chrono::hours "" h (unsigned long long Val)|Especifica horas como un valor entero.|  
|chrono:: Duration\<proporción double,\<3600 >> operador "" h (long double Val)|Especifica horas como un valor de coma flotante.|  
|chrono::minutes (operador "" min)(unsigned long long Val)|Especifica minutos como un valor entero.|  
|chrono:: Duration\<proporción double,\<60 >> (operador "" min) (long double Val)|Especifica minutos como un valor de coma flotante.|  
|operador chrono::seconds "" s(unsigned long long Val)|Especifica minutos como un valor entero.|  
|operador chrono::duration\<double> "" s(long double Val)|Especifica segundos como un valor de coma flotante.|  
|operador chrono::milliseconds "" ms(unsigned long long Val)|Especifica milisegundos como un valor entero.|  
|operador chrono::duration\<double, milli> "" ms(long double Val)|Especifica milisegundos como un valor de coma flotante.|  
|operador chrono::microseconds "" us(unsigned long long Val)|Especifica microsegundos como un valor entero.|  
|operador chrono::duration\<double, micro> "" us(long double Val)|Especifica microsegundos como un valor de coma flotante.|  
|operador chrono::nanoseconds "" ns(unsigned long long Val)|Especifica nanosegundos como un valor entero.|  
|operador chrono::duration\<double, nano> "" ns(long double Val)|Especifica nanosegundos como un valor de coma flotante.|  
|||  
  
En los siguientes ejemplos, se muestra cómo usar los literales chrono.  
  
```  
constexpr auto day = 24h;  
constexpr auto week = 24h* 7;  
constexpr auto my_duration_unit = 108ms;  
```  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)




