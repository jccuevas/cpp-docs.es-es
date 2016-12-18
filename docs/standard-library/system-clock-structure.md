---
title: "system_clock (Estructura) | Microsoft Docs"
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
  - "chrono/std::chrono::system_clock"
dev_langs: 
  - "C++"
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
caps.latest.revision: 14
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# system_clock (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un *tipo de reloj* basado en el reloj en tiempo real del sistema.  
  
## Sintaxis  
  
```  
struct system_clock;  
```  
  
## Comentarios  
 Se utiliza un *tipo de reloj* para obtener la hora actual en formato UTC.  El tipo personifica una creación de instancias de [duration](../standard-library/duration-class.md) y la plantilla de clase [time\_point](../standard-library/time-point-class.md), y define una función miembro estática `now()` que devuelve la hora.  
  
 Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.  
  
 Un reloj es *constante* si es *monotónico* y si el tiempo entre los ciclos de reloj es constante.  
  
 En esta implementación, `system_clock` es sinónimo de `high_resolution_clock`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`system_clock::duration`|Sinónimo de `duration<rep, period>`.|  
|`system_clock::period`|Sinónimo del tipo que se utiliza para representar el período de ciclo en la creación de instancias contenida de `duration`.|  
|`system_clock::rep`|Sinónimo del tipo que se utiliza para representar el número de ciclos del reloj en la creación de instancias contenida de `duration`.|  
|`system_clock::time_point`|Sinónimo de `time_point<Clock, duration>`, donde `Clock` es un sinónimo del tipo de reloj propiamente dicho o de otro tipo de reloj basado en la mismo tiempo base y tiene el mismo tipo `duration` anidado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[system\_clock::from\_time\_t \(Método\)](../Topic/system_clock::from_time_t%20Method.md)|Estático.  Devuelve el `time_point` que más se aproxima a una hora especificada.|  
|[system\_clock::now \(Método\)](../Topic/system_clock::now%20Method.md)|Estático.  Devuelve la hora actual.|  
|[system\_clock::to\_time\_t \(Método\)](../Topic/system_clock::to_time_t%20Method.md)|Estático.  Devuelve el objeto `time_t` que más se aproxima a un `time_point` especificado.|  
  
### Constantes públicas  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[system\_clock::is\_monotonic \(Constante\)](../Topic/system_clock::is_monotonic%20Constant.md)|Especifica si el tipo de reloj es monotónico.|  
|[system\_clock::is\_steady \(Constante\)](../Topic/system_clock::is_steady%20Constant.md)|Especifica si el tipo de reloj es constante.|  
  
## Requisitos  
 **Encabezado:** chrono  
  
 **Espacio de nombres:** std::chrono  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [Struct steady\_clock](../standard-library/steady-clock-struct.md)