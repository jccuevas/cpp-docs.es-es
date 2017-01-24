---
title: "&lt;chrono&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::nanoseconds"
  - "chrono/std::chrono::minutes"
  - "chrono/std::chrono::seconds"
  - "<chrono>"
  - "chrono/std::chrono::hours"
  - "chrono/std::chrono::milliseconds"
  - "chrono/std::chrono::microseconds"
dev_langs: 
  - "C++"
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
caps.latest.revision: 17
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;chrono&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el encabezado estándar \<chrono\> para definir las clases y funciones que representan y manipulan las duraciones de tiempo e instantes de tiempo.  
  
 **\(Visual Studio 2015:\)** la implementación de `steady_clock` ha cambiado para cumplir los requisitos del estándar de C\+\+ en cuanto a estabilidad y monotonía \(steadiness y monotonicity\).  `steady_clock` ahora se basa en QueryPerformanceCounter\(\) y `high_resolution_clock` ahora es un typedef para `steady_clock`.  Como resultado, en Visual C\+\+ `steady_clock::time_point` es ahora un typedef para `chrono::time_point<steady_clock>`; sin embargo, esto no es necesariamente así en otras implementaciones.  
  
## Sintaxis  
  
```cpp  
#include <chrono>  
```  
  
### Literales  
 Los literales del encabezado \< chrono \> son miembros del espacio de nombres insertado  literals::chrono\_literals.  Para obtener más información, consulte [literales chrono](../standard-library/chrono-literals.md).  
  
|||  
|-|-|  
|operador de "" h\(unsigned long long Val\) operador de "" h\(long double Val\)|Especifica que el valor representa las horas.|  
|operador de "" min\(unsigned long long Val\)  operador de "" min\(long double Val\)|Especifica que el valor representa los minutos.|  
|operador de "" s\(unsigned long long Val\)operator "" s\(long double Val\)|Especifica que el valor representa los segundos.|  
|operador de "" ms\(unsigned long long Val\)operator "" ms\(long double Val\)|Especifica que el valor representa los milisegundos.|  
|operador de "" us\(unsigned long long Val\)operator "" us\(long double Val\)|Especifica que el valor representa los microsegundos.|  
|operador de "" ns\(unsigned long long Val\)operador de "" ns\(long double Val\)|Especifica que el valor representa los nanosegundos.|  
  
### Clases  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[duration \(Clase\)](../standard-library/duration-class.md)|Describe un tipo que contenga un intervalo de tiempo.|  
|[time\_point \(Clase\)](../standard-library/time-point-class.md)|Describe un tipo que representa un punto en el tiempo.|  
  
### Structs  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[common\_type \(Estructura\)](../standard-library/common-type-structure.md)|Describe especializaciones de la clase de plantilla [common\_type](../standard-library/common-type-class.md) para las creaciones de instancias de `duration` y `time_point`.|  
|[duration\_values \(Estructura\)](../standard-library/duration-values-structure.md)|Proporciona valores concretos para el parámetro `Rep` de plantilla `duration`.|  
|[Struct steady\_clock](../standard-library/steady-clock-struct.md)|Representa un reloj `steady`.|  
|[system\_clock \(Estructura\)](../standard-library/system-clock-structure.md)|Representa un *tipo de reloj* basado en el reloj en tiempo real del sistema.|  
|[treat\_as\_floating\_point \(Estructura\)](../standard-library/treat-as-floating-point-structure.md)|Especifica si un tipo puede tratarse como un tipo de punto flotante.|  
  
### Funciones  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[duration\_cast \(Función\)](../Topic/duration_cast%20Function.md)|Convierte un objeto `duration` a un tipo especificado.|  
|[time\_point\_cast \(Función\)](../Topic/time_point_cast%20Function.md)|Convierte un objeto `time_point` a un tipo especificado.|  
  
### Operadores  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[operator\- \(Operador, STL\)](../Topic/operator-%20Operator%20\(STL\)1.md)|Operador para la resta o la negación de objetos `duration` y `time_point`.|  
|[operator\!\= \(Operador, STL\)](../Topic/operator!=%20Operator%20\(STL\).md)|Operador de desigualdad que se utiliza con objetos `duration` o `time_point`.|  
|[módulo del operador \(STL\)](../Topic/operator%20modulo%20\(STL\).md)|Operador para operaciones de módulo en objetos `duration`.|  
|[operator\* \(Operador, STL\)](../Topic/operator*%20Operator%20\(STL\).md)|Operador de multiplicación para objetos `duration`.|  
|[operator\/ \(Operador, STL\)](../Topic/operator-%20Operator%20\(STL\)2.md)|Operador de división para objetos `duration`.|  
|[operator\+ \(Operador, STL\)](../Topic/operator+%20Operator%20\(STL\).md)|Agrega objetos `duration` y `time_point`.|  
|[operator\< \(Operador, STL\)](../Topic/operator%3C%20Operator%20\(STL\).md)|Determina si un objeto `duration` o `time_point` es menor que otro objeto `duration` o `time_point`.|  
|[operator\<\= \(Operador, STL\)](../Topic/operator%3C=%20Operator%20\(STL\).md)|Determina si un objeto `duration` o `time_point` es menor o igual que otro objeto `duration` o `time_point`.|  
|[operator\=\= \(Operador, STL\)](../Topic/operator==%20Operator%20\(STL\).md)|Determina si dos objetos `duration` representan intervalos de tiempo de la misma longitud o si dos objetos `time_point` representan el mismo punto en el tiempo.|  
|[operator\> \(Operador, STL\)](../Topic/operator%3E%20Operator%20\(STL\).md)|Determina si un objeto `duration` o `time_point` es mayor que otro objeto `duration` o `time_point`.|  
|[operator\>\= \(Operador, STL\)](../Topic/operator%3E=%20Operator%20\(STL\).md)|Determina si un objeto `duration` o `time_point` es mayor o igual que otro objeto `duration` o `time_point`.|  
  
### Tipos predefinidos de duración  
 Para obtener más información acerca de los tipos de relación que se utilizan en los siguientes typedef, vea [\<ratio\>](../standard-library/ratio.md).  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|`typedef duration<long long, nano> nanoseconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un nanosegundo.|  
|`typedef duration<long long, micro> microseconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un microsegundo.|  
|`typedef duration<long long, milli> milliseconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un milisegundo.|  
|`typedef duration<long long> seconds;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un segundo.|  
|`typedef duration<int, ratio<60> > minutes;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de un minuto.|  
|`typedef duration<int, ratio<3600> > hours;`|Sinónimo de un tipo `duration` que tiene un período de ciclo de una hora.|  
  
### Literales  
 **\(C\+\+11\)**El encabezado \<chrono\> define los siguientes [literales definidos por el usuario](../cpp/user-defined-literals-cpp.md) que puede usar para mayor comodidad, seguridad de tipos y mantenimiento del código.  Estos literales se definen en el espacio de nombres alineado `literals::chrono_literals` y están en ámbito cuando std:: chrono está en ámbito.  
  
|Literal|Descripción|  
|-------------|-----------------|  
|operador chrono::hours "" h \(unsigned long long Val\)|Especifica horas como un valor entero.|  
|operador chrono::duration\<double, ratio\< 3600 \> \> "" h\(long double Val\)|Especifica horas como un valor de coma flotante.|  
|chrono::minutes \(operador "" min\)\(unsigned long long Val\)|Especifica minutos como un valor entero.|  
|chrono::duration\<double, ratio\<60\> \> \(operator "" min\)\(long double Val\)|Especifica minutos como un valor de coma flotante.|  
|operador chrono::seconds "" s\(unsigned long long Val\)|Especifica minutos como un valor entero.|  
|operador chrono::duration\<double\> "" s\(long double Val\)|Especifica segundos como un valor de coma flotante.|  
|operador chrono::milliseconds "" ms\(unsigned long long Val\)|Especifica milisegundos como un valor entero.|  
|operador chrono::duration\<double, mili\> "" ms\(long double Val\)|Especifica milisegundos como un valor de coma flotante.|  
|operador chrono::microseconds "" us\(unsigned long long Val\)|Especifica microsegundos como un valor entero.|  
|operador chrono::duration\<double, micro\> "" us\(long double Val\)|Especifica microsegundos como un valor de coma flotante.|  
|operador chrono::nanoseconds "" ns\(unsigned long long Val\)|Especifica nanosegundos como un valor entero.|  
|operador chrono::duration\<double, nano\> "" ns\(long double Val\)|Especifica nanosegundos como un valor de coma flotante.|  
|||  
  
## Comentarios  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)