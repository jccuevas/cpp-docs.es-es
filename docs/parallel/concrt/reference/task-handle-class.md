---
title: task_handle (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
dev_langs: C++
helpviewer_keywords: task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 358d217a131ec3e282775604619f1ff265baf490
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="taskhandle-class"></a>task_handle (Clase)
La clase `task_handle` representa un elemento de trabajo individual paralelo. Encapsula las instrucciones y los datos necesarios para ejecutar una parte del trabajo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<
    typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Function`  
 El tipo de objeto de función que se invocará para ejecutar el trabajo representado por la `task_handle` objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[task_handle)](#ctor)|Construye un nuevo objeto `task_handle`. El trabajo de la tarea se realiza invocando la función especificada como un parámetro al constructor.|  
|[~ task_handle (destructor)](#dtor)|Destruye el objeto `task_handle`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Operator()](#task_handle__operator_call)|El operador de llamada de función que invoca el tiempo de ejecución para realizar el trabajo del identificador de tarea.|  
  
## <a name="remarks"></a>Comentarios  
 `task_handle`objetos que pueden utilizarse junto con un `structured_task_group` o un más general `task_group` objeto, para descomponer el trabajo en tareas paralelas. Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Tenga en cuenta que el creador de un `task_handle` objeto es responsable de mantener la duración de creado `task_handle` objeto hasta que ya no es necesaria por el Runtime de simultaneidad. Normalmente, esto significa que la `task_handle` objeto no se debe destruir hasta que el `wait` o `run_and_wait` método de la `task_group` o `structured_task_group` se ha llamado a la que está en la cola.  
  
 `task_handle`objetos se utilizan normalmente junto con las expresiones lambda de C++. Dado que no se conoce el tipo verdadero de la expresión lambda, el [make_task](concurrency-namespace-functions.md#make_task) función normalmente se utiliza para crear un `task_handle` objeto.  
  
 El tiempo de ejecución crea una copia de la función de trabajo que se pasa a un `task_handle` objeto. Por lo tanto, cualquier cambio de estado que se produce en una función de objeto que se pasa a un `task_handle` objeto no aparecerán en la copia de ese objeto de función.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `task_handle`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="task_handle__operator_call"></a>Operator() 

 El operador de llamada de función que invoca el tiempo de ejecución para realizar el trabajo del identificador de tarea.  
  
```  
void operator()() const;

 
```  
  
##  <a name="task_handle__ctor"></a>task_handle) 

 Construye un nuevo objeto `task_handle`. El trabajo de la tarea se realiza invocando la función especificada como un parámetro al constructor.  
  
```  
task_handle(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Func`  
 La función que se invocará para ejecutar el trabajo representado por la `task_handle` objeto. Esto puede ser un functor lambda, un puntero a una función, o cualquier otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.  
  
### <a name="remarks"></a>Comentarios  
 El tiempo de ejecución crea una copia de la función de trabajo que se pasa al constructor. Por lo tanto, cualquier cambio de estado que se produce en una función de objeto que se pasa a un `task_handle` objeto no aparecerán en la copia de ese objeto de función.  
  
##  <a name="dtor"></a>~ task_handle 

 Destruye el objeto `task_handle`.  
  
```  
~task_handle();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [task_group (clase)](task-group-class.md)   
 [structured_task_group (clase)](structured-task-group-class.md)
