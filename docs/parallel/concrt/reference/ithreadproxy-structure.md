---
title: IThreadProxy (estructura)
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424258"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy (estructura)

Una abstracción para un subproceso de ejecución. Dependiendo de la clave de directiva `SchedulerType` del programador que se crea, el Administrador de recursos concederá al usuario un proxy del subproceso que está respaldado por un subproceso de Win32 normal o por un subproceso programable de modo de usuario (UMS). Los subprocesos UMS se admiten en sistemas operativos de 64 bits con Windows 7 o una versión posterior.

## <a name="syntax"></a>Sintaxis

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IThreadProxy:: GetId](#getid)|Devuelve un identificador único para el proxy del subproceso.|
|[IThreadProxy:: SwitchOut](#switchout)|Desasocia el contexto de la raíz del procesador virtual subyacente.|
|[IThreadProxy:: SwitchTo](#switchto)|Realiza un cambio de contexto cooperativo desde el contexto que se ejecuta actualmente a otro diferente.|
|[IThreadProxy:: YieldToSystem (](#yieldtosystem)|Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el subproceso siguiente que se va a ejecutar.|

## <a name="remarks"></a>Observaciones

Los proxies de subprocesos se acoplan a los contextos de ejecución representados por la interfaz `IExecutionContext` como un medio para enviar el trabajo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IThreadProxy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="getid"></a>IThreadProxy:: GetId (método)

Devuelve un identificador único para el proxy del subproceso.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero único.

## <a name="switchout"></a>IThreadProxy:: SwitchOut (método)

Desasocia el contexto de la raíz del procesador virtual subyacente.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parámetros

*switchState*<br/>
Indica el estado del proxy del subproceso que está ejecutando el modificador. El parámetro es del tipo `SwitchingProxyState`.

### <a name="remarks"></a>Observaciones

Use `SwitchOut` si necesita desasociar un contexto de la raíz de procesador virtual en la que se ejecuta, por cualquier razón. En función del valor pasado en el parámetro `switchState`, y de si se está ejecutando o no en una raíz de procesador virtual, la llamada volverá inmediatamente o bloqueará el proxy del subproceso asociado al contexto. Es un error llamar a `SwitchOut` con el parámetro establecido en `Idle`. Si lo hace, se producirá una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) .

`SwitchOut` resulta útil cuando desea reducir el número de raíces de procesador virtual que tiene su programador, ya sea porque el administrador de recursos ha dado instrucciones de que lo haga, o porque solicitó temporalmente una suscripción excesiva de raíz del procesador virtual y ya ha terminado con ella. En este caso, debe invocar el método [IVirtualProcessorRoot:: Remove](iexecutionresource-structure.md#remove) en la raíz del procesador virtual, antes de realizar una llamada a `SwitchOut` con el parámetro `switchState` establecido en `Blocking`. Esto bloqueará el proxy del subproceso y reanudará la ejecución cuando está disponible una raíz del procesador virtual diferente en el programador para ejecutarlo. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, vea [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).

También se puede usar `SwitchOut` si desea reinicializar el procesador virtual de forma que se pueda activar en el futuro mientras se bloquea el proxy del subproceso o se desasocia temporalmente este de la raíz del procesador virtual en el que se ejecuta, y del programador para el que está enviando trabajo. Use `SwitchOut` con el parámetro `switchState` establecido en `Blocking` si desea bloquear el proxy del subproceso. Podrá reanudarlo posteriormente mediante `SwitchTo` o `IVirtualProcessorRoot::Activate` como se indicó anteriormente. Use `SwitchOut` con el parámetro establecido en `Nesting` si desea desasociar temporalmente este proxy del subproceso de la raíz del procesador virtual en el que se ejecuta, y del programador con el que está asociado el procesador virtual. La llamada a `SwitchOut` con el parámetro `switchState` establecido en `Nesting` mientras se está ejecutando en una raíz del procesador virtual hará que la raíz se reinicialice y que el proxy del subproceso actual continúe ejecutándose sin necesidad. Se considera que el proxy del subproceso ha dejado el programador hasta que llama al método [IThreadProxy:: SwitchOut](#switchout) con `Blocking` en un momento posterior. La segunda llamada a `SwitchOut` con el parámetro establecido en `Blocking` tiene por objeto devolver el contexto a un estado bloqueado para que lo pueda reanudar `SwitchTo` o `IVirtualProcessorRoot::Activate` en el programador del que se desasoció. Dado que no estaba ejecutando en una raíz del procesador virtual, no se realiza ningún reinicio.

Una raíz del procesador virtual reinicializada no es distinta de una nueva raíz del procesador virtual que el Administrador de recursos concede al programador. Puede usarlo para la ejecución activándola con un contexto de ejecución mediante `IVirtualProcessorRoot::Activate`.

Se debe llamar a `SwitchOut` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.

En las bibliotecas y los encabezados incluidos con Visual Studio 2010, este método no tomaba un parámetro y no reinicializaba la raíz del procesador virtual. Para conservar el comportamiento anterior, se proporciona el valor de parámetro predeterminado de `Blocking`.

## <a name="switchto"></a>IThreadProxy:: SwitchTo (método)

Realiza un cambio de contexto cooperativo desde el contexto que se ejecuta actualmente a otro diferente.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Contexto de ejecución al que se cambia de forma cooperativa.

*switchState*<br/>
Indica el estado del proxy del subproceso que está ejecutando el modificador. El parámetro es del tipo `SwitchingProxyState`.

### <a name="remarks"></a>Observaciones

Use este método para cambiar de un contexto de ejecución a otro, desde el método [IExecutionContext::D ispatch](iexecutioncontext-structure.md#dispatch) del primer contexto de ejecución. El método asocia el contexto de ejecución `pContext` con un proxy del subproceso si aún no está asociado a uno. La propiedad del proxy del subproceso actual viene determinada por el valor especificado para el argumento `switchState`.

Utilice el valor `Idle` cuando desee devolver el proxy del subproceso que se está ejecutando actualmente al Administrador de recursos. La llamada a `SwitchTo` con el parámetro `switchState` establecido en `Idle` hará que el contexto de ejecución `pContext` empiece a ejecutarse en el recurso de ejecución subyacente. La propiedad de este proxy del subproceso se transfiere al Administrador de recursos y se espera que vuelva del método de `Dispatch` del contexto de ejecución poco después de que se devuelva `SwitchTo`, para completar la transferencia. El contexto de ejecución que el proxy del subproceso estaba enviando se desasocia del proxy del subproceso, y el programador es gratuito para reutilizarlo o destruirlo tal como se ve apto.

Use el valor `Blocking` cuando desee que este proxy del subproceso entre en un estado bloqueado. La llamada a `SwitchTo` con el parámetro `switchState` establecido en `Blocking` hará que el contexto de ejecución `pContext` empiece a ejecutarse y bloqueará el proxy del subproceso actual hasta que se reanude. Scheduler conserva la propiedad del proxy del subproceso cuando el proxy del subproceso está en el estado `Blocking`. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, vea [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).

Use el valor `Nesting` cuando quiera desasociar temporalmente este proxy de subproceso de la raíz del procesador virtual en el que se está ejecutando y el programador para el que está enviando el trabajo. La llamada a `SwitchTo` con el parámetro `switchState` establecido en `Nesting` hará que el contexto de ejecución `pContext` empiece a ejecutarse y el proxy del subproceso actual también se siga ejecutando sin necesidad de una raíz del procesador virtual. Se considera que el proxy del subproceso ha dejado el programador hasta que llama al método [IThreadProxy:: SwitchOut](#switchout) en un momento posterior. El método `IThreadProxy::SwitchOut` podría bloquear el proxy del subproceso hasta que esté disponible una raíz del procesador virtual para volver a programarlo.

Se debe llamar a `SwitchTo` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen. La función produce `invalid_argument` si el `pContext` del parámetro se establece en `NULL`.

## <a name="yieldtosystem"></a>IThreadProxy:: YieldToSystem ((método)

Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el subproceso siguiente que se va a ejecutar.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Observaciones

Cuando lo llama un proxy de subproceso respaldado por un subproceso de Windows normal, `YieldToSystem` se comporta exactamente igual que la función de Windows `SwitchToThread`. Sin embargo, cuando se llama desde subprocesos programables en modo usuario (UMS), la función `SwitchToThread` delega la tarea de seleccionar el siguiente subproceso que se ejecutará en el programador de modo de usuario, no en el sistema operativo. Para lograr el efecto deseado de cambiar a un subproceso preparado diferente en el sistema, use `YieldToSystem`.

Se debe llamar a `YieldToSystem` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IExecutionContext (estructura)](iexecutioncontext-structure.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)
