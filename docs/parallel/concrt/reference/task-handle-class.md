---
title: task_handle (clase)
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: a61e72f14448d5033d5be9069ffeec7d3bb08061
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142552"
---
# <a name="task_handle-class"></a>task_handle (clase)

La clase `task_handle` representa un elemento de trabajo individual paralelo. Encapsula las instrucciones y los datos necesarios para ejecutar una parte del trabajo.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se invocará para ejecutar el trabajo representado por el objeto `task_handle`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[task_handle](#task_handle)|Construye un nuevo objeto `task_handle`. El trabajo de la tarea se realiza invocando la función especificada como parámetro al constructor.|
|[~ task_handle destructor](#dtor)|Destruye el objeto `task_handle`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator()](#task_handle__operator_call)|Operador de llamada de función que invoca el Runtime para realizar el trabajo del identificador de la tarea.|

## <a name="remarks"></a>Observaciones

`task_handle` objetos se pueden usar junto con un `structured_task_group` o un objeto de `task_group` más general, para descomponer el trabajo en tareas paralelas. Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Tenga en cuenta que el creador de un objeto `task_handle` es responsable del mantenimiento de la duración del objeto `task_handle` creado hasta que el Runtime de simultaneidad no lo necesite. Normalmente, esto significa que el objeto de `task_handle` no debe destruirse hasta que se haya llamado al método `wait` o `run_and_wait` del `task_group` o `structured_task_group` al que está en cola.

los objetos `task_handle` se usan normalmente junto con C++ las expresiones lambda. Dado que no conoce el tipo true de la expresión lambda, la función [make_task](concurrency-namespace-functions.md#make_task) se utiliza normalmente para crear un objeto `task_handle`.

El tiempo de ejecución crea una copia de la función de trabajo que se pasa a un objeto `task_handle`. Por lo tanto, los cambios de estado que se producen en un objeto de función que se pasa a un objeto `task_handle` no aparecerán en la copia de ese objeto de función.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task_handle`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="task_handle__operator_call"></a>operador ()

Operador de llamada de función que invoca el Runtime para realizar el trabajo del identificador de la tarea.

```cpp
void operator()() const;
```

## <a name="task_handle"></a>task_handle

Construye un nuevo objeto `task_handle`. El trabajo de la tarea se realiza invocando la función especificada como parámetro al constructor.

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>Parámetros

*_Func*<br/>
Función que se invocará para ejecutar el trabajo representado por el objeto `task_handle`. Puede ser un functor lambda, un puntero a una función o cualquier objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.

### <a name="remarks"></a>Observaciones

El tiempo de ejecución crea una copia de la función de trabajo que se pasa al constructor. Por lo tanto, los cambios de estado que se producen en un objeto de función que se pasa a un objeto `task_handle` no aparecerán en la copia de ese objeto de función.

## <a name="dtor"></a>~ task_handle

Destruye el objeto `task_handle`.

```cpp
~task_handle();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[task_group (clase)](task-group-class.md)<br/>
[structured_task_group (clase)](structured-task-group-class.md)
