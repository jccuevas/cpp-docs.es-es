---
title: IVirtualProcessorRoot (Estructura)
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
ms.openlocfilehash: f642a29d0a80568f7a5f2a5e89f6951d4819243e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364262"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot (Estructura)

Una abstracción para un subproceso de hardware en el que un proxy del subproceso puede ejecutarse.

## <a name="syntax"></a>Sintaxis

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IVirtualProcessorRoot::Activate](#activate)|Hace que el proxy de `pContext` subproceso asociado a la interfaz de contexto de ejecución comience a ejecutarse en esta raíz del procesador virtual.|
|[IVirtualProcessorRoot::Deactivate](#deactivate)|Hace que el proxy de subproceso que se está ejecutando actualmente en esta raíz del procesador virtual deje de distribuir el contexto de ejecución. El proxy de subproceso reanudará la `Activate` ejecución en una llamada al método.|
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|Hace que los datos almacenados en la jerarquía de memoria de procesadores individuales sean visibles para todos los procesadores del sistema. Se asegura de que se ha ejecutado una valla de memoria completa en todos los procesadores antes de que se devuelva el método.|
|[IVirtualProcessorRoot::GetId](#getid)|Devuelve un identificador único para la raíz del procesador virtual.|

## <a name="remarks"></a>Observaciones

Cada raíz del procesador virtual tiene un recurso de ejecución asociado. La `IVirtualProcessorRoot` interfaz hereda de la interfaz [IExecutionResource.](iexecutionresource-structure.md) Varias raíces de procesador virtual pueden corresponder al mismo subproceso de hardware subyacente.

Resource Manager concede raíces de procesador virtual a los programadores en respuesta a las solicitudes de recursos. Un programador puede usar una raíz de procesador virtual para realizar el trabajo activándolo con un contexto de ejecución.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>Método IVirtualProcessorRoot::Activate

Hace que el proxy de `pContext` subproceso asociado a la interfaz de contexto de ejecución comience a ejecutarse en esta raíz del procesador virtual.

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Una interfaz para el contexto de ejecución que se distribuirá en esta raíz del procesador virtual.

### <a name="remarks"></a>Observaciones

Resource Manager proporcionará un proxy de subproceso si uno no está asociado con la interfaz de contexto de ejecución`pContext`

El `Activate` método se puede usar para iniciar la ejecución de trabajo en una nueva raíz de procesador virtual devuelta por Resource Manager o para reanudar el proxy de subproceso en una raíz de procesador virtual que se ha desactivado o está a punto de desactivarse. Consulte [IVirtualProcessorRoot::Deactivate](#deactivate) para obtener más información sobre la desactivación. Cuando se reanuda una raíz de procesador `pContext` virtual desactivada, el parámetro debe ser el mismo que el parámetro utilizado para desactivar la raíz del procesador virtual.

Una vez que una raíz del procesador virtual se `Deactivate` ha `Activate` activado por primera vez, los pares de llamadas posteriores y pueden competir entre sí. Esto significa que es aceptable que Resource Manager `Activate` reciba una `Deactivate` llamada antes de recibir la llamada para la que estaba destinada.

Al activar una raíz de procesador virtual, se indica al Administrador de recursos que esta raíz del procesador virtual está actualmente ocupada con el trabajo. Si el programador no puede encontrar ningún trabajo que ejecutar `Deactivate` en esta raíz, se espera que invoque el método que informa al Administrador de recursos de que la raíz del procesador virtual está inactiva. Resource Manager utiliza estos datos para equilibrar la carga del sistema.

`invalid_argument`se produce si `pContext` el argumento `NULL`tiene el valor .

`invalid_operation`se produce si `pContext` el argumento no representa el contexto de ejecución que se distribuyó más recientemente por esta raíz del procesador virtual.

El acto de activar una raíz de procesador virtual aumenta el nivel de suscripción del subproceso de hardware subyacente en uno. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot::Deactivate Método

Hace que el proxy de subproceso que se está ejecutando actualmente en esta raíz del procesador virtual deje de distribuir el contexto de ejecución. El proxy de subproceso reanudará la `Activate` ejecución en una llamada al método.

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
El contexto que actualmente está siendo distribuido por esta raíz.

### <a name="return-value"></a>Valor devuelto

Un valor booleano. Un valor de **true** indica que el `Deactivate` proxy de subproceso devuelto `Activate` desde el método en respuesta a una llamada al método. Un valor `false` de indica que el proxy de subproceso devuelto desde el método en respuesta a un evento de notificación en el Administrador de recursos. En un programador de subprocesos programable en modo de usuario (UMS), esto indica que los elementos han aparecido en la lista de finalización del programador y el programador es necesario para controlarlos.

### <a name="remarks"></a>Observaciones

Utilice este método para detener temporalmente la ejecución de una raíz de procesador virtual cuando no pueda encontrar ningún trabajo en el programador. Una llamada `Deactivate` al método debe `Dispatch` originarse dentro del método del contexto de ejecución con el que se activó por última vez la raíz del procesador virtual. En otras palabras, el `Deactivate` proxy de subproceso que invoca el método debe ser el que se está ejecutando actualmente en la raíz del procesador virtual. Llamar al método en una raíz de procesador virtual en la que no se está ejecutando podría dar lugar a un comportamiento indefinido.

Una raíz de procesador virtual desactivada se puede `Activate` activar con una llamada al método, `Deactivate` con el mismo argumento que se pasó al método. El programador es responsable de asegurarse de que las llamadas a los `Activate` métodos y `Deactivate` están emparejados, pero no es necesario que se reciban en un orden específico. Resource Manager puede controlar la `Activate` recepción de una llamada al `Deactivate` método antes de recibir una llamada al método para el que estaba destinado.

Si una raíz de procesador virtual se `Deactivate` despierta y el valor devuelto del método es `IUMSCompletionList::GetUnblockNotifications` el valor **false**, el programador debe consultar la lista de finalización de UMS a través del método, actuar sobre esa información y, a continuación, volver a llamar al `Deactivate` método. Esto debe repetirse hasta `Deactivate` que el `true`método devuelva el valor .

`invalid_argument`se produce si `pContext` el argumento tiene el valor NULL.

`invalid_operation`se produce si la raíz del procesador virtual `pContext` nunca se ha activado o el argumento no representa el contexto de ejecución que esta raíz del procesador virtual distribuyó más recientemente.

El acto de desactivar una raíz de procesador virtual reduce el nivel de suscripción del subproceso de hardware subyacente en uno. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot::EnsureAllTasksVisible Método

Hace que los datos almacenados en la jerarquía de memoria de procesadores individuales sean visibles para todos los procesadores del sistema. Se asegura de que se ha ejecutado una valla de memoria completa en todos los procesadores antes de que se devuelva el método.

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
El contexto que está siendo distribuido actualmente por esta raíz del procesador virtual.

### <a name="remarks"></a>Observaciones

Puede encontrar este método útil cuando desee sincronizar la desactivación de una raíz de procesador virtual con la adición de nuevo trabajo en el programador. Por motivos de rendimiento, puede decidir agregar elementos de trabajo al programador sin ejecutar una barrera de memoria, lo que significa que los elementos de trabajo agregados por un subproceso que se ejecuta en un procesador no son visibles inmediatamente para todos los demás procesadores. Mediante el uso de `Deactivate` este método junto con el método puede asegurarse de que el programador no desactiva todas sus raíces de procesador virtual mientras existen elementos de trabajo en las colecciones del programador.

Una llamada `EnsureAllTasksVisibleThe` al método debe `Dispatch` originarse dentro del método del contexto de ejecución con el que se activó por última vez la raíz del procesador virtual. En otras palabras, el `EnsureAllTasksVisible` proxy de subproceso que invoca el método debe ser el que se está ejecutando actualmente en la raíz del procesador virtual. Llamar al método en una raíz de procesador virtual en la que no se está ejecutando podría dar lugar a un comportamiento indefinido.

`invalid_argument`se produce si `pContext` el argumento `NULL`tiene el valor .

`invalid_operation`se produce si la raíz del procesador virtual `pContext` nunca se ha activado o el argumento no representa el contexto de ejecución que esta raíz del procesador virtual distribuyó más recientemente.

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>Método IVirtualProcessorRoot::GetId

Devuelve un identificador único para la raíz del procesador virtual.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
