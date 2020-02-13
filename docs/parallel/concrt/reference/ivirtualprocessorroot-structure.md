---
title: IVirtualProcessorRoot (estructura)
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: 60757b0edea6b60d080c2175d4df4830ffec0cc3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139892"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot (estructura)

Una abstracción para un subproceso de hardware en el que un proxy del subproceso puede ejecutarse.

## <a name="syntax"></a>Sintaxis

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IVirtualProcessorRoot:: Activate](#activate)|Hace que el proxy del subproceso asociado a la interfaz de contexto de ejecución `pContext` empiece a ejecutarse en esta raíz del procesador virtual.|
|[IVirtualProcessorRoot::D eactivate](#deactivate)|Hace que el proxy del subproceso que se está ejecutando actualmente en esta raíz del procesador virtual deje de enviar el contexto de ejecución. El proxy del subproceso se reanudará la ejecución en una llamada al método `Activate`.|
|[IVirtualProcessorRoot:: EnsureAllTasksVisible (](#ensurealltasksvisible)|Hace que los datos almacenados en la jerarquía de memoria de procesadores individuales estén visibles para todos los procesadores del sistema. Garantiza que se ha ejecutado una barrera de memoria completa en todos los procesadores antes de que se devuelva el método.|
|[IVirtualProcessorRoot:: GetId](#getid)|Devuelve un identificador único para la raíz del procesador virtual.|

## <a name="remarks"></a>Observaciones

Cada raíz del procesador virtual tiene un recurso de ejecución asociado. La interfaz `IVirtualProcessorRoot` hereda de la interfaz [IExecutionResource](iexecutionresource-structure.md) . Varias raíces de procesador virtual pueden corresponder al mismo subproceso de hardware subyacente.

El Administrador de recursos concede las raíces del procesador virtual a los programadores en respuesta a las solicitudes de recursos. Un programador puede utilizar una raíz del procesador virtual para realizar el trabajo mediante su activación con un contexto de ejecución.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="activate"></a>IVirtualProcessorRoot:: Activate (método)

Hace que el proxy del subproceso asociado a la interfaz de contexto de ejecución `pContext` empiece a ejecutarse en esta raíz del procesador virtual.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Una interfaz al contexto de ejecución que se enviará en esta raíz del procesador virtual.

### <a name="remarks"></a>Observaciones

El Administrador de recursos proporcionará un proxy de subproceso si uno no está asociado a la interfaz de contexto de ejecución `pContext`

El método `Activate` se puede usar para iniciar la ejecución del trabajo en una nueva raíz del procesador virtual devuelta por el Administrador de recursos, o para reanudar el proxy del subproceso en una raíz del procesador virtual que ha desactivado o está a punto de desactivarse. Vea [IVirtualProcessorRoot::D eactivate](#deactivate) para obtener más información sobre la desactivación. Al reanudar una raíz del procesador virtual desactivada, el parámetro `pContext` debe ser el mismo que el parámetro usado para desactivar la raíz del procesador virtual.

Una vez que se ha activado por primera vez una raíz del procesador virtual, los pares subsiguientes de llamadas a `Deactivate` y `Activate` pueden anticiparse entre sí. Esto significa que es aceptable que el Administrador de recursos reciba una llamada a `Activate` antes de recibir la llamada de `Deactivate` para la que se diseñó.

Al activar una raíz del procesador virtual, señala al Administrador de recursos que esta raíz del procesador virtual está actualmente ocupada con el trabajo. Si el programador no encuentra ningún trabajo para ejecutar en esta raíz, se espera que invoque al método `Deactivate` que informe de la Administrador de recursos que la raíz del procesador virtual está inactiva. El Administrador de recursos usa estos datos para equilibrar la carga del sistema.

`invalid_argument` se produce si el argumento `pContext` tiene el valor `NULL`.

`invalid_operation` se produce si el argumento `pContext` no representa el contexto de ejecución que ha enviado más recientemente esta raíz del procesador virtual.

El hecho de activar una raíz del procesador virtual aumenta el nivel de suscripción del subproceso de hardware subyacente en uno. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource:: currentsubscriptionlevel (](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="deactivate"></a>IVirtualProcessorRoot::D método eactivate

Hace que el proxy del subproceso que se está ejecutando actualmente en esta raíz del procesador virtual deje de enviar el contexto de ejecución. El proxy del subproceso se reanudará la ejecución en una llamada al método `Activate`.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Contexto que esta raíz está enviando actualmente.

### <a name="return-value"></a>Valor devuelto

Un valor booleano. Un valor de **true** indica que el proxy del subproceso devuelto desde el método `Deactivate` como respuesta a una llamada al método `Activate`. Un valor de `false` indica que el proxy del subproceso devolvió el método en respuesta a un evento de notificación en el Administrador de recursos. En un programador de subprocesos programables en modo usuario (UMS), esto indica que los elementos han aparecido en la lista de finalización del programador y que el programador debe administrarlos.

### <a name="remarks"></a>Observaciones

Use este método para detener temporalmente la ejecución de una raíz del procesador virtual cuando no encuentre ningún trabajo en el programador. Una llamada al método `Deactivate` debe originarse en el `Dispatch` método del contexto de ejecución en el que se activó por última vez la raíz del procesador virtual. En otras palabras, el proxy del subproceso que invoca el método `Deactivate` debe ser el que se está ejecutando actualmente en la raíz del procesador virtual. Si se llama al método en una raíz del procesador virtual que no se está ejecutando, se podría producir un comportamiento indefinido.

Una raíz del procesador virtual desactivada puede reactivarán con una llamada al método `Activate`, con el mismo argumento que se pasó al método `Deactivate`. El programador es responsable de garantizar que las llamadas a los métodos `Activate` y `Deactivate` están emparejadas, pero no es necesario que se reciban en un orden específico. El Administrador de recursos puede controlar la recepción de una llamada al método de `Activate` antes de recibir una llamada al método `Deactivate` para el que se diseñó.

Si se activa una raíz del procesador virtual y el valor devuelto por el método `Deactivate` es el valor **false**, Scheduler debe consultar la lista de finalización de UMS a través del método `IUMSCompletionList::GetUnblockNotifications`, actuar sobre esa información y, a continuación, llamar de nuevo al método `Deactivate`. Debe repetirse hasta ese momento, ya que el método `Deactivate` devuelve el valor `true`.

`invalid_argument` se produce si el argumento `pContext` tiene el valor NULL.

se produce `invalid_operation` si la raíz del procesador virtual no se ha activado nunca, o si el argumento `pContext` no representa el contexto de ejecución que la raíz del procesador virtual envió más recientemente.

La acción de desactivar una raíz del procesador virtual reduce el nivel de suscripción del subproceso de hardware subyacente en uno. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource:: currentsubscriptionlevel (](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot:: EnsureAllTasksVisible ((método)

Hace que los datos almacenados en la jerarquía de memoria de procesadores individuales estén visibles para todos los procesadores del sistema. Garantiza que se ha ejecutado una barrera de memoria completa en todos los procesadores antes de que se devuelva el método.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Contexto que la raíz del procesador virtual está enviando en este momento.

### <a name="remarks"></a>Observaciones

Este método puede resultar útil si desea sincronizar la desactivación de una raíz del procesador virtual con la adición de nuevo trabajo en el programador. Por motivos de rendimiento, puede decidir agregar elementos de trabajo al programador sin ejecutar una barrera de memoria, lo que significa que los elementos de trabajo agregados por un subproceso que se ejecuta en un procesador no son visibles inmediatamente para todos los demás procesadores. Al usar este método junto con el método `Deactivate` puede asegurarse de que el programador no desactive todas las raíces del procesador virtual mientras existan elementos de trabajo en las colecciones del programador.

Una llamada al método `EnsureAllTasksVisibleThe` debe originarse en el `Dispatch` método del contexto de ejecución en el que se activó por última vez la raíz del procesador virtual. En otras palabras, el proxy del subproceso que invoca el método `EnsureAllTasksVisible` debe ser el que se está ejecutando actualmente en la raíz del procesador virtual. Si se llama al método en una raíz del procesador virtual que no se está ejecutando, se podría producir un comportamiento indefinido.

`invalid_argument` se produce si el argumento `pContext` tiene el valor `NULL`.

se produce `invalid_operation` si la raíz del procesador virtual no se ha activado nunca, o si el argumento `pContext` no representa el contexto de ejecución que la raíz del procesador virtual envió más recientemente.

## <a name="getid"></a>IVirtualProcessorRoot:: GetId (método)

Devuelve un identificador único para la raíz del procesador virtual.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
