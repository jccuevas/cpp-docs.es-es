---
title: "task_handle (Clase) | Microsoft Docs"
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
  - "ppl/concurrency::task_handle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_handle (clase)"
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: 23
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_handle (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `task_handle` representa un elemento de trabajo individual paralelo.  Encapsula las instrucciones y los datos necesarios para ejecutar una parte del trabajo.  
  
## Sintaxis  
  
```  
template<  
   typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### Parámetros  
 `_Function`  
 El tipo del objeto de función que se invocará para ejecutar el trabajo que representa el objeto `task_handle`.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_handle::task\_handle \(Constructor\)](../Topic/task_handle::task_handle%20Constructor.md)|Crea un nuevo objeto `task_handle`.  El trabajo de la tarea se realiza invocando la función especificada como un parámetro al constructor.|  
|[task\_handle::~task\_handle \(Destructor\)](../Topic/task_handle::~task_handle%20Destructor.md)|Destruye el objeto `task_handle`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_handle::operator\(\) \(Operador\)](../Topic/task_handle::operator\(\)%20Operator.md)|El operador de llamada de función que invoca el runtime para realizar el trabajo del identificador de tareas.|  
  
## Comentarios  
 Los objetos `task_handle` se pueden usar junto con un objeto `task_group` o un objeto más general `structured_task_group`, para descomponer el trabajo en tareas paralelas.  Para obtener más información, vea [Paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Observe que el creador de un objeto `task_handle` es responsable de mantener la duración del objeto `task_handle` creado hasta que ya no lo requiera el runtime de simultaneidad.  Normalmente, esto significa que el objeto `task_handle` no se debe destruir hasta que se llama al método `run_and_wait` o `wait`, de `task_group` o `structured_task_group`, al que se pone en cola.  
  
 Los objetos `task_handle` se utilizan normalmente junto con expresiones lambda C\+\+.  Dado que no conoce el verdadero tipo de lambda, la función [make\_task](../Topic/make_task%20Function.md) se usa normalmente para crear un objeto `task_handle`.  
  
 El motor en tiempo de ejecución crea una copia de la función de trabajo que se pasa a un objeto `task_handle`.  Por consiguiente, los cambios de estado que se produzcan en el objeto de función pasado a un objeto `task_handle` no aparecerán en su copia de dicho objeto de función.  
  
## Jerarquía de herencia  
 `task_handle`  
  
## Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group \(Clase\)](../Topic/task_group%20Class.md)   
 [structured\_task\_group \(Clase\)](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [make\_task \(Función\)](../Topic/make_task%20Function.md)   
 [task\_group::run \(Método\)](../Topic/task_group::run%20Method.md)   
 [task\_group::wait \(Método\)](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait \(Método\)](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group::run \(Método\)](../Topic/structured_task_group::run%20Method.md)   
 [structured\_task\_group::wait \(Método\)](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait \(Método\)](../Topic/structured_task_group::run_and_wait%20Method.md)