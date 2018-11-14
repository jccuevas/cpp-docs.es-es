---
title: task_handle (Clase)
ms.date: 11/04/2016
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: 060be8614fc3a0a93d446c747b65de82b863ab3c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518886"
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

*_Function*<br/>
El tipo de objeto de función que se invocará para ejecutar el trabajo representado por la `task_handle` objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[task_handle](#ctor)|Construye un nuevo objeto `task_handle`. El trabajo de la tarea se realiza invocando la función especificada como un parámetro al constructor.|
|[~ task_handle (destructor)](#dtor)|Destruye el objeto `task_handle`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|El operador de llamada de función que invoca el tiempo de ejecución para realizar el trabajo del identificador de tarea.|

## <a name="remarks"></a>Comentarios

`task_handle` los objetos se pueden usar junto con un `structured_task_group` o un más general `task_group` objeto para descomponer el trabajo en tareas paralelas. Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Tenga en cuenta que el creador de un `task_handle` objeto es responsable de mantener la duración de creado `task_handle` objeto hasta que ya no es necesario por el Runtime de simultaneidad. Normalmente, esto significa que el `task_handle` no se debe destruir objeto hasta que el `wait` o `run_and_wait` método de la `task_group` o `structured_task_group` se ha llamado a la que está en la cola.

`task_handle` los objetos se utilizan normalmente junto con las expresiones lambda de C++. Dado que no se conoce el tipo verdadero de la expresión lambda, el [make_task](concurrency-namespace-functions.md#make_task) función normalmente se usa para crear un `task_handle` objeto.

El tiempo de ejecución crea una copia de la función de trabajo que se pasa a un `task_handle` objeto. Por lo tanto, cualquier cambio de estado que se produce en función de una objeto que se pasa a un `task_handle` objeto no aparecerá en la copia de ese objeto de función.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task_handle`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppl.h

**Espacio de nombres:** simultaneidad

##  <a name="task_handle__operator_call"></a> Operator()

El operador de llamada de función que invoca el tiempo de ejecución para realizar el trabajo del identificador de tarea.

```
void operator()() const;
```

##  <a name="task_handle__ctor"></a> task_handle

Construye un nuevo objeto `task_handle`. El trabajo de la tarea se realiza invocando la función especificada como un parámetro al constructor.

```
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>Parámetros

*_Func*<br/>
La función que se invocará para ejecutar el trabajo representado por la `task_handle` objeto. Esto puede ser un functor lambda, un puntero a una función, o cualquier otro objeto que admite una versión del operador de llamada de función con la firma `void operator()()`.

### <a name="remarks"></a>Comentarios

El tiempo de ejecución crea una copia de la función de trabajo que se pasa al constructor. Por lo tanto, cualquier cambio de estado que se produce en función de una objeto que se pasa a un `task_handle` objeto no aparecerá en la copia de ese objeto de función.

##  <a name="dtor"></a> ~ task_handle

Destruye el objeto `task_handle`.

```
~task_handle();
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[task_group (clase)](task-group-class.md)<br/>
[structured_task_group (clase)](structured-task-group-class.md)
