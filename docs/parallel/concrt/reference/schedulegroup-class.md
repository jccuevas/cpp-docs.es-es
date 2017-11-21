---
title: ScheduleGroup (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
dev_langs: C++
helpviewer_keywords: ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ac169e7cc01682b8ecd0dc4fb5dd387f3be38504
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
  
|Nombre|Descripción|  
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
  
##  <a name="id"></a>Id. 

 Devuelve un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.  
  
##  <a name="operator_delete"></a>operador delete 

 Un `ScheduleGroup` objeto sea destruido internamente por el tiempo de ejecución cuando se liberan todas las referencias externas a él. No se puede eliminar explícitamente.  
  
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
 `_PObject`  
 Un puntero al objeto que se va a eliminar.  
  
##  <a name="reference"></a>Referencia 

 Incrementa el contador de referencias del grupo de programación.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencias incrementado recientemente.  
  
### <a name="remarks"></a>Comentarios  
 Esto se utiliza normalmente para administrar la duración del grupo de programación para la creación. Cuando el recuento de referencias de un grupo de programación cae a cero, se elimina el grupo de programación en tiempo de ejecución. Un grupo de programación creado mediante el [CurrentScheduler:: CreateScheduleGroup](currentscheduler-class.md#createschedulegroup) método, o la [Scheduler:: CreateScheduleGroup](scheduler-class.md#createschedulegroup) método empieza con un recuento de referencias de uno.  
  
##  <a name="release"></a>Versión 

 Disminuye el contador de referencias del grupo de programación.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencias disminuido recientemente.  
  
### <a name="remarks"></a>Comentarios  
 Esto se utiliza normalmente para administrar la duración del grupo de programación para la creación. Cuando el recuento de referencias de un grupo de programación cae a cero, se elimina el grupo de programación en tiempo de ejecución. Después de haber llamado el `Release` método hacen referencia el número especificado de veces que se quite la creación del recuento y cualquier referencia adicional colocada mediante el `Reference` método, no puede utilizar el grupo de programación adicional. Si lo hace, se producirá un comportamiento indefinido.  
  
 Un grupo de programación está asociado a una instancia del programador determinada. Debe asegurarse de que todas las referencias al grupo de programación se liberan antes de que se liberan todas las referencias al programador, porque pueden provocar en el que se destruya el programador. Hace lo contrario da como resultado un comportamiento indefinido.  
  
##  <a name="dtor"></a>~ ScheduleGroup 

```
virtual ~ScheduleGroup();
```  
  
##  <a name="scheduletask"></a>ScheduleTask 

 Programa una tarea ligera dentro del grupo de programación.  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Proc`  
 Un puntero a función que se ejecuta para llevar a cabo el cuerpo de la tarea ligera.  
  
 `_Data`  
 Un puntero void para los datos que se pasarán como un parámetro en el cuerpo de la tarea.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a la `ScheduleTask` método coloca implícitamente un recuento de referencias en el grupo de programación que se quita el tiempo de ejecución en el momento adecuado cuando se ejecuta la tarea.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [CurrentScheduler (clase)](currentscheduler-class.md)   
 [Scheduler (clase)](scheduler-class.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



