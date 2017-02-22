---
title: "duration (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::duration"
dev_langs: 
  - "C++"
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# duration (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un tipo que contiene un *intervalo de tiempo*, que es el tiempo transcurrido entre dos puntos en el tiempo.  
  
## Sintaxis  
  
```  
template<  
   class Rep,  
   class Period = ratio<1>  
>  
class duration;  
template<  
   class Rep,  
   class Period  
>  
class duration;  
template<  
   class Rep,  
   class Period1,  
   class Period2  
>  
class duration  
   <duration<Rep, Period1>, Period2>;  
```  
  
## Comentarios  
 El argumento de plantilla `Rep` describe el tipo que se utiliza para almacenar el número de ciclos de reloj del intervalo.  El argumento de plantilla `Period` es una creación de instancias de [ratio](../standard-library/ratio.md) que describe el tamaño del intervalo que representa cada ciclo.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[duration::period Typedef](http://msdn.microsoft.com/es-es/ebf2a1b9-769f-475f-8c66-cf9ed12015f2)|Representa un sinónimo para el parámetro de plantilla `Period`.|  
|[duration::rep Typedef](http://msdn.microsoft.com/es-es/f47b8abb-ae2c-4dc8-858a-f44695156950)|Representa un sinónimo para el parámetro de plantilla `Rep`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[duration::duration \(Constructor\)](../Topic/duration::duration%20Constructor.md)|Construye un objeto `duration`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[duration::count \(Método\)](../Topic/duration::count%20Method.md)|Devuelve el número de pasos del reloj del intervalo de tiempo.|  
|[duration::max \(Método\)](../Topic/duration::max%20Method.md)|Estático.  Devuelve el valor máximo permitido del parámetro de plantilla `Ref`.|  
|[duration::min \(Método\)](../Topic/duration::min%20Method.md)|Estático.  Devuelve el valor mínimo permitido del parámetro de plantilla `Ref`.|  
|[duration::zero \(Método\)](../Topic/duration::zero%20Method.md)|Estático.  En efecto, devuelve `Rep`\(0\).|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[duration::operator\- \(Operador\)](../Topic/duration::operator-%20Operator.md)|Devuelve una copia del objeto `duration` junto con un recuento de pasos negado.|  
|[duration::operator\-\- \(Operador\)](../Topic/duration::operator--%20Operator.md)|Disminuye el recuento de pasos almacenado.|  
|[duration::operator\= \(Operador\)](../Topic/duration::operator=%20Operator.md)|Reduce el módulo del recuento de pasos almacenado en un valor especificado.|  
|[duration::operator\*\= \(Operador\)](../Topic/duration::operator*=%20Operator.md)|Multiplica el recuento de pasos almacenado por un valor especificado.|  
|[duration::operator\/\= \(Operador\)](../Topic/duration::operator-=%20Operator1.md)|Divide el recuento de pasos almacenado por el recuento de pasos de un objeto `duration` especificado.|  
|[duration::operator\+ \(Operador\)](../Topic/duration::operator+%20Operator.md)|Devuelve `*this`.|  
|[duration::operator\+\+ \(Operador\)](../Topic/duration::operator++%20Operator.md)|Incrementa el recuento de pasos almacenado.|  
|[duration::operator\+\= Operator](../Topic/duration::operator+=%20Operator.md)|Suma el recuento de pasos de un objeto `duration` especificado al recuento de pasos almacenado.|  
|[duration::operator\-\= \(Operador\)](../Topic/duration::operator-=%20Operator2.md)|Resta el recuento de pasos de un objeto `duration` especificado del recuento de pasos almacenado.|  
  
## Requisitos  
 **Encabezado:** chrono  
  
 **Espacio de nombres:** std::chrono  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [duration\_values \(Estructura\)](../standard-library/duration-values-structure.md)