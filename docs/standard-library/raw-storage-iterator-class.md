---
title: "raw_storage_iterator (Clase) | Microsoft Docs"
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
  - "std::raw_storage_iterator"
  - "raw_storage_iterator"
  - "std.raw_storage_iterator"
  - "memory/std::raw_storage_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_storage_iterator (clase)"
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
caps.latest.revision: 17
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_storage_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de adaptador que se proporciona para permitir que los algoritmos almacenen sus resultados en memoria sin inicializar.  
  
## Sintaxis  
  
```  
  
        template <class   
        OutputIterator,  
         class   
        Type>  
class raw_storage_iterator  
```  
  
#### Parámetros  
 `OutputIterator`  
 Especifica el iterador de salida para el objeto que se almacena.  
  
 *Tipo*  
 Tipo de objeto al que se va a asignar almacenamiento.  
  
## Comentarios  
 La clase describe un iterador de salida que construye objetos del tipo **Type** en la secuencia que genera.  Un objeto de la clase `raw_storage_iterator`\<**ForwardIterator**, **Type**\> accede al almacenamiento a través de un objeto de iterador hacia delante, de la clase **ForwardIterator**, que se especifica al construir el objeto.  Para un objeto first de la clase **ForwardIterator**, la expresión **&\*first** debe designar el almacenamiento no construido para el siguiente objeto \(de tipo **Type**\) en la secuencia generada.  
  
 Esta clase de adaptador se usa cuando es necesario separar la asignación de memoria y la construcción de objetos.  `raw_storage_iterator` puede usarse para copiar objetos en el almacenamiento no inicializado, como la memoria asignada mediante la función `malloc`.  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[raw\_storage\_iterator](../Topic/raw_storage_iterator::raw_storage_iterator.md)|Crea un iterador de almacenamiento sin formato con un iterador de salida subyacente especificado.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[element\_type](../Topic/raw_storage_iterator::element_type.md)|Proporciona un tipo que describe un elemento para almacenar un iterador de almacenamiento sin formato.|  
|[iter\_type](../Topic/raw_storage_iterator::iter_type.md)|Proporciona un tipo que describe un iterador que subyace a un iterador de almacenamiento sin formato.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*](../Topic/raw_storage_iterator::operator*.md)|Operador de desreferencia usado para implementar la expresión del iterador de salida \*`ii` \= `x`.|  
|[operador \=](../Topic/raw_storage_iterator::operator=.md)|Operador de asignación usado para implementar la expresión del iterador de almacenamiento sin formato \*`i` \= `x` para almacenar en memoria.|  
|[operator\+\+](../Topic/raw_storage_iterator::operator++.md)|Operadores de preincremento y prostincremento para los iteradores de almacenamiento sin formato.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)