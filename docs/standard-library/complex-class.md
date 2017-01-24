---
title: "complex (Clase) | Microsoft Docs"
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
  - "complex"
  - "std::complex"
  - "std.complex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex (clase)"
  - "números complejos"
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
caps.latest.revision: 18
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que almacena dos objetos de **Tipo**escrito, uno que representa la parte real de un número complejo y uno que representa la parte imaginaria.  
  
## Sintaxis  
  
```  
  
   template<class   
   Type  
   >  
class complex  
```  
  
## Comentarios  
 Un objeto de clase **Tipo**:  
  
-   Tiene un constructor predeterminado público, destructor, el constructor de copias, y el operador de asignación con comportamiento convencional.  
  
-   Puede asignar el entero o de punto flotante, o de tipo dichos valores con comportamiento convencional.  
  
-   Define los operadores aritméticos y funciones matemáticas, según convenga, que se definen para los tipos de punto flotante con comportamiento convencional.  
  
 En particular, las diferencias sutiles pueden existir entre la construcción de copia y la construcción predeterminado seguidas de asignación.  Ninguna de las operaciones en objetos de clase **Tipo** pueden producir excepciones.  
  
 Especializaciones explícitas complejo de la clase de plantilla existen para los tres tipos de punto flotante.  En esta implementación, un valor de cualquier otro tipo **Tipo** es convertir a **double** para los cálculos reales, con el resultado de **double** asignado al objeto almacenado de **Tipo**tipo`.`  
  
### Constructores  
  
|||  
|-|-|  
|[profundidad](../Topic/complex::complex.md)|Construye un número complejo con elementos real e imaginarias especificadas o como copia de algún otro número complejo.|  
  
### Typedefs  
  
|||  
|-|-|  
|[value\_type](../Topic/complex::value_type.md)|Un tipo que representa el tipo de datos utilizado para representar las partes real e imaginarias de un número complejo.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[imag](../Topic/complex::imag.md)|Extrae el componente imaginario de un número complejo.|  
|[real](../Topic/complex::real.md)|Extrae el componente real de un número complejo.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*\=](../Topic/complex::operator*=.md)|Multiplica un número complejo de destino por un factor, que puede ser complejo o es el mismo tipo que son elementos real e imaginarias de números complejos.|  
|[operator\+\=](../Topic/complex::operator+=.md)|Agrega un número a un número complejo de destino, donde el número agregado puede ser complejo o del mismo tipo que son elementos real e imaginarias de números complejos al que se agrega.|  
|[operator\-\=](../Topic/complex::operator-=1.md)|Resta un número a un número complejo de destino, donde el número restado puede ser complejo o del mismo tipo que son elementos real e imaginarias de números complejos al que se agrega.|  
|[operator\/\=](../Topic/complex::operator-=2.md)|Divide un número complejo de destino por un divisor, que puede ser complejo o es el mismo tipo que son elementos real e imaginarias de números complejos.|  
|[operator\=](../Topic/complex::operator=.md)|Asigna un número a un número complejo de destino, donde el número asignado puede ser complejo o del mismo tipo que son elementos real e imaginarias de números complejos al que se está asignando.|  
  
## Requisitos  
 **Encabezado**: \<complejo\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [miembros complejos](http://msdn.microsoft.com/es-es/d5c4466c-43a0-4817-aca1-9a5d492dae28)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)