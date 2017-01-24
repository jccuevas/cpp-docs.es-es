---
title: "gslice (Clase) | Microsoft Docs"
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
  - "std::gslice"
  - "std.gslice"
  - "gslice"
  - "valarray/std::gslice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gslice (clase)"
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
caps.latest.revision: 21
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gslice (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de utilidad para valarray que se usa para definir subconjuntos multidimensionales de una valarray.  Si una valarray se considera como una matriz multidimensional con todos los elementos de una matriz, el segmento extrae un vector de la matriz multidimensional.  
  
## Comentarios  
 La clase almacena los parámetros que caracterizan a un objeto de tipo [gslice\_array](../standard-library/gslice-array-class.md).  El subconjunto de una valarray se crea indirectamente cuando un objeto de clase gslice aparece como argumento para un objeto de clase [valarray](../Topic/valarray::operator.md)**\<Type\>**.  Los valores almacenados que especifican el subconjunto seleccionado de la valarray primaria incluyen:  
  
-   Un índice de inicio.  
  
-   Un vector de longitud de la clase **valarray\<size\_t\>**.  
  
-   Un vector de intervalo de la clase **valarray\<size\_t\>**.  
  
 Los dos vectores deben tener la misma longitud.  
  
 Si el conjunto definido por un gslice es el subconjunto de una valarray de constantes, el gslice es una nueva valarray.  Si el conjunto definido por un gslice es el subconjunto de una valarray de no constantes, el gslice tiene semántica de referencia a la valarray original.  El mecanismo de evaluación para valarrays de no constantes ahorra tiempo y memoria.  
  
 Las operaciones en valarrays solo se garantizan si los subconjuntos de origen y de destino definidos por los gslices son distintos y todos los índices son válidos.  
  
### Constructores  
  
|||  
|-|-|  
|[gslice](../Topic/gslice::gslice.md)|Define un subconjunto de un `valarray` que consta de varios segmentos de la `valarray` que todas comienzan a partir de un elemento especificado.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[size](../Topic/gslice::size.md)|Busca los valores de la matriz especificando el número de elementos en un segmento general de un `valarray`.|  
|[inicio](../Topic/gslice::start.md)|Busca el índice inicial de un segmento general de un `valarray`.|  
|[stride](../Topic/gslice::stride.md)|Busca la distancia entre los elementos de un segmento general de un `valarray`.|  
  
## Requisitos  
 **Encabezado:** \<valarray\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)