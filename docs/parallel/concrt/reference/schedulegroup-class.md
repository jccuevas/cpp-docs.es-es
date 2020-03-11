---
title: ScheduleGroup (clase)
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: 8686b5ef0906e3188a1e683d1190bbe6124cd19e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867146"
---
# <a name="schedulegroup-class"></a>ScheduleGroup (clase)

Representa una abstracción para un grupo de programación. Los grupos de programación organizan un conjunto de trabajos relacionados que se benefician de programarse juntos ya sea temporalmente, mediante la ejecución de otra tarea en el mismo grupo antes de trasladarse a otro grupo, o espacialmente, mediante la ejecución de varios elementos del mismo grupo en el mismo nodo NUMA o socket físico.

## <a name="syntax"></a>Sintaxis

```cpp
class ScheduleGroup;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[~ ScheduleGroup (destructor)](#dtor)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Id](#id)|Devuelve un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.|
|[Referencia](#reference)|Incrementa el contador de referencias del grupo de programación.|
|[Versión](#release)|Disminuye el contador de referencias del grupo de programación.|
|[ScheduleTask (](#scheduletask)|Programa una tarea ligera dentro del grupo de programación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ScheduleGroup`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="id"></a>Sesión

Devuelve un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador del grupo de programación que es único dentro del programador al que pertenece el grupo.

## <a name="operator_delete"></a>operador Delete

El tiempo de ejecución destruye internamente un objeto `ScheduleGroup` cuando se liberan todas las referencias externas a él. No se puede eliminar explícitamente.

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>Parámetros

*_PObject*<br/>
Puntero al objeto que se va a eliminar.

## <a name="reference"></a>Referencia

Incrementa el contador de referencias del grupo de programación.

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Valor devuelto

Recuento de referencias incrementado recientemente.

### <a name="remarks"></a>Observaciones

Normalmente se utiliza para administrar la duración del grupo de programación para la composición. Cuando el recuento de referencias de un grupo de programación cae en cero, el tiempo de ejecución elimina el grupo de programación. Un grupo de programación creado mediante el método [CurrentScheduler:: createschedulegroup (](currentscheduler-class.md#createschedulegroup) o el método [Scheduler:: createschedulegroup (](scheduler-class.md#createschedulegroup) comienza con un recuento de referencias de uno.

## <a name="release"></a>Emisión

Disminuye el contador de referencias del grupo de programación.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valor devuelto

Recuento de referencias disminuido recientemente.

### <a name="remarks"></a>Observaciones

Normalmente se utiliza para administrar la duración del grupo de programación para la composición. Cuando el recuento de referencias de un grupo de programación cae en cero, el tiempo de ejecución elimina el grupo de programación. Después de llamar al método `Release` el número específico de veces que se va a quitar el recuento de referencias de creación y las referencias adicionales colocadas con el método `Reference`, no se puede utilizar el grupo de programación más allá. Si lo hace, se producirá un comportamiento indefinido.

Un grupo de programación está asociado a una instancia de Scheduler determinada. Debe asegurarse de que todas las referencias al grupo de programación se liberan antes de que se liberen todas las referencias al programador, ya que este último podría provocar la destrucción del programador. De lo contrario, se produce un comportamiento indefinido.

## <a name="dtor"></a>~ ScheduleGroup

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a>ScheduleTask (

Programa una tarea ligera dentro del grupo de programación.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Parámetros

*_Proc*<br/>
Puntero a la función que se va a ejecutar para realizar el cuerpo de la tarea ligera.

*_Data*<br/>
Un puntero void a los datos que se pasarán como parámetro al cuerpo de la tarea.

### <a name="remarks"></a>Observaciones

La llamada al método `ScheduleTask` coloca implícitamente un recuento de referencias en el grupo de programación que el Runtime quita en el momento adecuado después de que se ejecute la tarea.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[CurrentScheduler (clase)](currentscheduler-class.md)<br/>
[Scheduler (clase)](scheduler-class.md)<br/>
[Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
