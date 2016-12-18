---
title: "Clase combinable | Microsoft Docs"
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
  - "ppl/concurrency::combinable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combinable (clase)"
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase combinable
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El objeto `combinable<T>` está diseñado para proporcionar copias de subprocesos privados de datos, para realizar subcálculos de subprocesos locales sin bloqueos durante algoritmos paralelos.  Al final de la operación paralela, los subcálculos de subprocesos privados pueden combinarse en un resultado final.  Esta clase se puede utilizar en lugar de una variable compartida y puede dar lugar a una mejora en el rendimiento que, de lo contrario, daría lugar a mucha contención en esa variable compartida.  
  
## Sintaxis  
  
```  
template<  
   typename _Ty  
>  
class combinable;  
```  
  
#### Parámetros  
 `_Ty`  
 El tipo de datos del resultado combinado final.  El tipo debe tener un constructor de copias y un constructor predeterminado.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[combinable::combinable \(Constructor\)](../Topic/combinable::combinable%20Constructor.md)|Sobrecargado.  Crea un nuevo objeto `combinable`.|  
|[combinable::~combinable \(Destructor\)](../Topic/combinable::~combinable%20Destructor.md)|Destruye un objeto `combinable`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[combinable::clear \(Método\)](../Topic/combinable::clear%20Method.md)|Borra cualquier resultado computacional intermedio de un uso anterior.|  
|[combinable::combine \(Método\)](../Topic/combinable::combine%20Method.md)|Calcula un valor final de subcómputos del conjunto de subprocesos locales llamando al functor de combinación.|  
|[combinable::combine\_each \(Método\)](../Topic/combinable::combine_each%20Method.md)|Calcula un valor final de subcómputos del conjunto de subprocesos locales llamando al functor de combinación proporcionado una vez por subcómputo del subproceso local.  El objeto de función acumula el resultado final.|  
|[combinable::local \(Método\)](../Topic/combinable::local%20Method.md)|Sobrecargado.  Devuelve una referencia al subcálculo del subproceso privado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[combinable::operator\= \(Operador\)](../Topic/combinable::operator=%20Operator.md)|Asigna a un objeto `combinable` de otro objeto `combinable`.|  
  
## Comentarios  
 Para obtener más información, vea [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Jerarquía de herencia  
 `combinable`  
  
## Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)