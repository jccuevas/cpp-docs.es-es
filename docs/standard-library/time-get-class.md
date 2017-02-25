---
title: "time_get (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.time_get"
  - "xloctime/std::time_get"
  - "time_get"
  - "std::time_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_get (clase)"
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# time_get (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de las secuencias de tipo `CharType` en valores de hora.  
  
## Sintaxis  
  
```  
template <  
   class CharType,  
   class InputIterator = istreambuf_iterator<CharType>  
> class time_get : public time_base;  
```  
  
#### Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar caracteres.  
  
 `InputIterator`  
 Iterador del que se leen los valores de hora.  
  
## Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero.  El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### Constructores  
  
|||  
|-|-|  
|[time\_get](../Topic/time_get::time_get.md)|Constructor para los objetos de tipo `time_get`.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/time_get::char_type.md)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter\_type](../Topic/time_get::iter_type.md)|Tipo que describe un iterador de entrada.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[date\_order](../Topic/time_get::date_order.md)|Devuelve el orden de fecha utilizado por una faceta.|  
|[do\_date\_order](../Topic/time_get::do_date_order.md)|Una función miembro virtual protegida a la que se llama para devolver el orden de fecha utilizado por una faceta.|  
|[do\_get](../Topic/time_get::do_get.md)|Lee y convierten datos de caracteres en un valor de hora.|  
|[do\_get\_date](../Topic/time_get::do_get_date.md)|Una función miembro virtual protegida a la que se llama para analizar una cadena como la fecha generada por el especificador `x` para `strftime`.|  
|[do\_get\_monthname](../Topic/time_get::do_get_monthname.md)|Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del mes.|  
|[do\_get\_time](../Topic/time_get::do_get_time.md)|Una función miembro virtual protegida a la que se llama para analizar una cadena como la fecha generada por el especificador `X` para `strftime`.|  
|[do\_get\_weekday](../Topic/time_get::do_get_weekday.md)|Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del día de la semana.|  
|[do\_get\_year](../Topic/time_get::do_get_year.md)|Una función miembro virtual protegida a la que se llama para analizar una cadena como el nombre del año.|  
|[get](../Topic/time_get::get.md)|Lee de un origen de datos de caracteres y convierte estos datos en una hora que se almacena en un struct de hora.|  
|[get\_date](../Topic/time_get::get_date.md)|Analiza una cadena como la fecha generada por el especificador `x` para `strftime`.|  
|[get\_monthname](../Topic/time_get::get_monthname.md)|Analiza una cadena como el nombre del mes.|  
|[get\_time](../Topic/time_get::get_time.md)|Analiza una cadena como la fecha generada por el especificador `X` para `strftime`.|  
|[get\_weekday](../Topic/time_get::get_weekday.md)|Analiza una cadena como el nombre del día de la semana.|  
|[get\_year](../Topic/time_get::get_year.md)|Analiza una cadena como el nombre del año.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<locale\>](../standard-library/locale.md)   
 [time\_base \(Clase\)](../standard-library/time-base-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)