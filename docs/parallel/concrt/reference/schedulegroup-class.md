---
title: ScheduleGroup (Clase)
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
ms.openlocfilehash: 6132ec6623a009c09a37b7d704ce683a58956a04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518721"
---
# <a name="schedulegroup-class"></a>ScheduleGroup (Clase)

Representa una abstracción para un grupo de programación. Los grupos de programación organizan un conjunto de trabajos relacionados que se benefician de programarse juntos ya sea temporalmente, mediante la ejecución de otra tarea en el mismo grupo antes de trasladarse a otro grupo, o espacialmente, mediante la ejecución de varios elementos del mismo grupo en el mismo nodo NUMA o socket físico.

## <a name="syntax"></a>Sintaxis

```
class ScheduleGroup;
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[~ ScheduleGroup (destructor)](#dtor)||

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Id.](#id)|Devuelve un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.|
|[Referencia](#reference)|Incrementa el contador de referencias del grupo de programación.|
|[Release](#release)|Disminuye el contador de referencias del grupo de programación.|
|[ScheduleTask](#scheduletask)|Programa una tarea ligera dentro del grupo de programación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ScheduleGroup`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="id"></a> Id.

Devuelve un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.

```
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.

##  <a name="operator_delete"></a> operador delete

Un `ScheduleGroup` objeto se destruye internamente por el tiempo de ejecución cuando se liberan todas las referencias externas a él. No se puede eliminar explícitamente.

```
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
Un puntero al objeto que se va a eliminar.

##  <a name="reference"></a> Referencia

Incrementa el contador de referencias del grupo de programación.

```
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencias incrementado recientemente.

### <a name="remarks"></a>Comentarios

Esto normalmente se usa para administrar la duración del grupo de programación para la composición. Cuando el recuento de referencias de un grupo de programación llega a cero, el grupo de programación se elimina el tiempo de ejecución. Un grupo de programación creado mediante el [CurrentScheduler:: CreateScheduleGroup](currentscheduler-class.md#createschedulegroup) método, o la [CreateScheduleGroup](scheduler-class.md#createschedulegroup) método comienza con un recuento de referencias de uno.

##  <a name="release"></a> Versión

Disminuye el contador de referencias del grupo de programación.

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento de referencias disminuido recientemente.

### <a name="remarks"></a>Comentarios

Esto normalmente se usa para administrar la duración del grupo de programación para la composición. Cuando el recuento de referencias de un grupo de programación llega a cero, el grupo de programación se elimina el tiempo de ejecución. Después de haber llamado el `Release` método hacen referencia el número específico de veces que se quite la creación del recuento y cualquier referencia adicional colocada con la `Reference` método, no puede utilizar el grupo de programación adicional. Si lo hace, dará como resultado un comportamiento indefinido.

Un grupo de programación está asociado a una instancia del programador determinado. Debe asegurarse de que todas las referencias al grupo de programación se liberan antes de que se liberan todas las referencias al programador, ya que podría producir en el programador está destruyendo. Hacer en caso contrario, da como resultado un comportamiento indefinido.

##  <a name="dtor"></a> ~ ScheduleGroup

```
virtual ~ScheduleGroup();
```

##  <a name="scheduletask"></a> ScheduleTask

Programa una tarea ligera dentro del grupo de programación.

```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>Parámetros

*_Proc*<br/>
Un puntero a la función que se ejecutan para realizar el cuerpo de la tarea ligera.

*_Datos*<br/>
Un puntero void para los datos que se pasa como parámetro al cuerpo de la tarea.

### <a name="remarks"></a>Comentarios

Una llamada a la `ScheduleTask` método implícitamente coloca un recuento de referencias en el grupo de programación que se quita el tiempo de ejecución en el momento adecuado cuando se ejecuta la tarea.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[CurrentScheduler (clase)](currentscheduler-class.md)<br/>
[Scheduler (clase)](scheduler-class.md)<br/>
[Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

