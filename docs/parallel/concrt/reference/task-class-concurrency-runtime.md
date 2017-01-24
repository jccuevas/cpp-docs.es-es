---
title: "task (Clase) (Motor en tiempo de ejecuci&#243;n de simultaneidad) | Microsoft Docs"
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
  - "ppltasks/concurrency::task"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task (clase)"
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task (Clase) (Motor en tiempo de ejecuci&#243;n de simultaneidad)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `task` de la biblioteca de patrones de procesamiento paralelo \(PPL\).  Un objeto `task` representa el trabajo que se puede ejecutar de forma asincrónica y de forma simultánea con otras tareas y trabajos paralelos generados por los algoritmos paralelos en el runtime de simultaneidad.  Genera un resultado de tipo `_ResultType` al finalizar correctamente.  Las tareas de tipo `task<void>` no producen ningún resultado.  Es posible esperar y cancelar una tarea de forma independiente al resto de tareas.  También se puede componer con otras tareas mediante continuaciones \(`then`\), así como con patrones de unión \(`when_all`\) y elección \(`when_any`\).  
  
## Sintaxis  
  
```  
template <  
   typename _Type  
>  
class task;  
  
template <>  
class task<void>;  
  
template<  
   typename _ReturnType  
>  
class task;  
```  
  
#### Parámetros  
 `_Type`  
 `T`  
 `_ReturnType`  
 Tipo de resultado de esta tarea.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`result_type`|El tipo del resultado que un objeto de esta clase produce.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task::task \(Constructor\)](../Topic/task::task%20Constructor.md)|Sobrecargado.  Construye un objeto `task`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task::get \(Método\)](../Topic/task::get%20Method.md)|Sobrecargado.  Devuelve el resultado generado por esta tarea.  Si la tarea no está en un estado terminal, una llamada a `get` esperará a que finalice la tarea.  Este método no devuelve un valor cuando se llama en una tarea con un `result_type` de `void`.|  
|[task::is\_apartment\_aware \(Método\)](../Topic/task::is_apartment_aware%20Method.md)|Determina si la tarea desencapsula una interfaz `IAsyncInfo` de Windows en tiempo de ejecución o si desciende de esta tarea.|  
|[task::is\_done \(Método\) \(Runtime de simultaneidad\)](../Topic/task::is_done%20Method%20\(Concurrency%20Runtime\).md)|Determina si se completa la tarea.|  
|[task::scheduler \(Método\) \(Runtime de simultaneidad\)](../Topic/task::scheduler%20Method%20\(Concurrency%20Runtime\).md)|Devuelve el programador para esta tarea|  
|[task::then \(Método\)](../Topic/task::then%20Method.md)|Sobrecargado.  Agrega una tarea de continuación a esta tarea.|  
|[task::wait \(Método\)](../Topic/task::wait%20Method.md)|Espera a que esta tarea alcance un estado terminal.  `wait` puede ejecutar la tarea alineada si se cumplen todas las dependencias de tareas y el trabajador en segundo plano aún no lo ha seleccionado para su ejecución.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task::operator\!\= \(Operador\)](../Topic/task::operator!=%20Operator.md)|Sobrecargado.  Determina si dos objetos `task` representan diferentes tareas internas.|  
|[task::operator\= \(Operador\)](../Topic/task::operator=%20Operator.md)|Sobrecargado.  Reemplaza el contenido de un objeto `task` con otro.|  
|[task::operator\=\= \(Operador\)](../Topic/task::operator==%20Operator.md)|Sobrecargado.  Determina si dos objetos `task` representan la misma tarea interna.|  
  
## Comentarios  
 Para obtener más información, vea [Paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## Jerarquía de herencia  
 `task`  
  
## Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)