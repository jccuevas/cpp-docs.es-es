---
title: "time_point (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::time_point"
dev_langs: 
  - "C++"
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# time_point (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`time_point` describe un tipo que representa un punto en el tiempo.  Contiene un objeto de tipo [duration](../standard-library/duration-class.md) que almacena el tiempo transcurrido desde el tiempo base representado por el argumento de plantilla `Clock`.  
  
## Sintaxis  
  
```  
template<  
   class Clock,  
   class Duration = typename Clock::duration  
>  
class time_point;  
```  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`time_point::clock`|Sinónimo del parámetro de plantilla `Clock`.|  
|`time_point::duration`|Sinónimo del parámetro de plantilla `Duration`.|  
|`time_point::period`|Sinónimo del nombre de tipo anidado `duration::period`.|  
|`time_point::rep`|Sinónimo del nombre de tipo anidado `duration::rep`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[time\_point::time\_point \(Constructor\)](../Topic/time_point::time_point%20Constructor.md)|Construye un objeto `time_point`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[time\_point::max \(Método\)](../Topic/time_point::max%20Method.md)|Especifica el límite superior de `time_point::ref`.|  
|[time\_point::min \(Método\)](../Topic/time_point::min%20Method.md)|Especifica el límite inferior de `time_point::ref`.|  
|[time\_point::time\_since\_epoch \(Método\)](../Topic/time_point::time_since_epoch%20Method.md)|Devuelve el valor de `duration` almacenado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[time\_point::operator\+\= \(Operador\)](../Topic/time_point::operator+=%20Operator.md)|Suma un valor especificado a la duración almacenada.|  
|[time\_point::operator\-\= \(Operador\)](../Topic/time_point::operator-=%20Operator.md)|Resta un valor especificado de la duración almacenada.|  
  
## Requisitos  
 **Encabezado:** chrono  
  
 **Espacio de nombres:** std::chrono  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)