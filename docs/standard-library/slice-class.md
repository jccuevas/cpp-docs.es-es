---
title: "slice (Clase) | Microsoft Docs"
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
  - "valarray/std::slice"
  - "std.slice"
  - "slice"
  - "std::slice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "slice (clase)"
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
caps.latest.revision: 23
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# slice (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de utilidad para valarray que se usa para definir subconjuntos unidimensionales de una valarray principal.  Si una valarray se considera como una matriz bidimensional con todos los elementos de una matriz, el segmento extrae un vector en una dimensión de la matriz bidimensional.  
  
## Comentarios  
 La clase almacena los parámetros que caracterizan a un objeto de tipo [slice\_array](../standard-library/slice-array-class.md). El subconjunto de una valarray se crea indirectamente cuando un objeto de clase slice aparece como argumento para un objeto de clase [valarray](../Topic/valarray::operator.md)**\<Type\>**.  Los valores almacenados que especifican el subconjunto seleccionado de la valarray primaria incluyen:  
  
-   Índice inicial de la valarray.  
  
-   Longitud total o número de elementos en el segmento.  
  
-   Un intervalo, o la distancia entre índices subsiguientes de los elementos de la valarray.  
  
 Si el conjunto definido por un segmento es el subconjunto de una valarray de constantes, el segmento es una nueva valarray.  Si el conjunto definido por un segmento es el subconjunto de una valarray de no constantes, el segmento tiene semántica de referencia a la valarray original.  El mecanismo de evaluación para valarrays de no constantes ahorra tiempo y memoria.  
  
 Las operaciones en valarrays solo se garantizan si los subconjuntos de origen y de destino definidos por los segmentos son distintos y todos los índices son válidos.  
  
### Constructores  
  
|||  
|-|-|  
|[slice](../Topic/slice::slice.md)|Define un subconjunto de un `valarray` que consta de un número de elementos equidistantes y que comienzan en un elemento especificado.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[size](../Topic/slice::size.md)|Busca el número de elementos de un segmento de una `valarray`.|  
|[inicio](../Topic/slice::start.md)|Busca el índice inicial de un segmento de una `valarray`.|  
|[stride](../Topic/slice::stride.md)|Busca la distancia entre los elementos de un segmento de una `valarray`.|  
  
## Requisitos  
 **Encabezado:** \<valarray\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)