---
title: "time_put (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::time_put"
  - "time_put"
  - "xloctime/std::time_put"
  - "std.time_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_put (clase)"
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# time_put (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de valores de hora en secuencias de tipo `CharType`.  
  
## Sintaxis  
  
```  
template <  
   class CharType,  
   class OutputIterator = ostreambuf_iterator<CharType>  
> class time_put : public locale::facet;  
```  
  
#### Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar caracteres.  
  
 `OutputIterator`  
 El tipo de iterador en el que las funciones time put escriben sus resultados.  
  
## Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero.  El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### Constructores  
  
|||  
|-|-|  
|[time\_put](../Topic/time_put::time_put.md)|Constructor para los objetos de tipo `time_put`.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/time_put::char_type.md)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter\_type](../Topic/time_put::iter_type.md)|Tipo que describe un iterador de salida.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[do\_put](../Topic/time_put::do_put.md)|Una función virtual que genera información de hora y fecha como una secuencia de `CharType`s.|  
|[put](../Topic/time_put::put.md)|Genera información de hora y fecha como una secuencia de `CharType`s.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<locale\>](../standard-library/locale.md)   
 [time\_base \(Clase\)](../standard-library/time-base-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)