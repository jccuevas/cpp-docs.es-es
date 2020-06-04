---
title: IThreadProxy (Estructura)
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
ms.openlocfilehash: fc2fb2df06225a5c963fe39178c1b4a10f77953d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368128"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy (Estructura)

Una abstracción para un subproceso de ejecución. Dependiendo de la clave de directiva `SchedulerType` del programador que se crea, el Administrador de recursos concederá al usuario un proxy del subproceso que está respaldado por un subproceso de Win32 normal o por un subproceso programable de modo de usuario (UMS). Los subprocesos UMS se admiten en sistemas operativos de 64 bits con Windows 7 o una versión posterior.

## <a name="syntax"></a>Sintaxis

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IThreadProxy::GetId](#getid)|Devuelve un identificador único para el proxy de subproceso.|
|[IThreadProxy::SwitchOut](#switchout)|Desasocia el contexto de la raíz del procesador virtual subyacente.|
|[IThreadProxy::SwitchTo](#switchto)|Realiza un cambio de contexto cooperativo del contexto que se está ejecutando actualmente a otro diferente.|
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el siguiente subproceso que se va a ejecutar.|

## <a name="remarks"></a>Observaciones

Los proxies de subproceso se acoplan `IExecutionContext` a los contextos de ejecución representados por la interfaz como medio de distribución del trabajo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IThreadProxy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="ithreadproxygetid-method"></a><a name="getid"></a>IThreadProxy::GetId Método

Devuelve un identificador único para el proxy de subproceso.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero único.

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a>Método IThreadProxy::SwitchOut

Desasocia el contexto de la raíz del procesador virtual subyacente.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Parámetros

*switchState*<br/>
Indica el estado del proxy del subproceso que está ejecutando el modificador. El parámetro es del tipo `SwitchingProxyState`.

### <a name="remarks"></a>Observaciones

Use `SwitchOut` si necesita desasociar un contexto de la raíz de procesador virtual en la que se ejecuta, por cualquier razón. En función del valor pasado en el parámetro `switchState`, y de si se está ejecutando o no en una raíz de procesador virtual, la llamada volverá inmediatamente o bloqueará el proxy del subproceso asociado al contexto. Es un error llamar a `SwitchOut` con el parámetro establecido en `Idle`. Si lo hace, se producirá una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción.

`SwitchOut` resulta útil cuando desea reducir el número de raíces de procesador virtual que tiene su programador, ya sea porque el administrador de recursos ha dado instrucciones de que lo haga, o porque solicitó temporalmente una suscripción excesiva de raíz del procesador virtual y ya ha terminado con ella. En este caso, debe invocar el método [IVirtualProcessorRoot::Remove](iexecutionresource-structure.md#remove) en la `SwitchOut` raíz `switchState` del `Blocking`procesador virtual, antes de realizar una llamada con el parámetro establecido en . Esto bloqueará el proxy del subproceso y reanudará la ejecución cuando está disponible una raíz del procesador virtual diferente en el programador para ejecutarlo. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, vea [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

También se puede usar `SwitchOut` si desea reinicializar el procesador virtual de forma que se pueda activar en el futuro mientras se bloquea el proxy del subproceso o se desasocia temporalmente este de la raíz del procesador virtual en el que se ejecuta, y del programador para el que está enviando trabajo. Use `SwitchOut` con el parámetro `switchState` establecido en `Blocking` si desea bloquear el proxy del subproceso. Podrá reanudarlo posteriormente mediante `SwitchTo` o `IVirtualProcessorRoot::Activate` como se indicó anteriormente. Use `SwitchOut` con el parámetro establecido en `Nesting` si desea desasociar temporalmente este proxy del subproceso de la raíz del procesador virtual en el que se ejecuta, y del programador con el que está asociado el procesador virtual. La llamada a `SwitchOut` con el parámetro `switchState` establecido en `Nesting` mientras se está ejecutando en una raíz del procesador virtual hará que la raíz se reinicialice y que el proxy del subproceso actual continúe ejecutándose sin necesidad. El proxy de subproceso se considera que ha dejado el programador hasta `Blocking` que llama a la [IThreadProxy::SwitchOut](#switchout) método con en un momento posterior en el tiempo. La segunda llamada a `SwitchOut` con el parámetro establecido en `Blocking` tiene por objeto devolver el contexto a un estado bloqueado para que lo pueda reanudar `SwitchTo` o `IVirtualProcessorRoot::Activate` en el programador del que se desasoció. Dado que no estaba ejecutando en una raíz del procesador virtual, no se realiza ningún reinicio.

Una raíz del procesador virtual reinicializada no es distinta de una nueva raíz del procesador virtual que el Administrador de recursos concede al programador. Puede usarlo para la ejecución activándola con un contexto de ejecución mediante `IVirtualProcessorRoot::Activate`.

Se debe llamar a `SwitchOut` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.

En las bibliotecas y los encabezados incluidos con Visual Studio 2010, este método no tomaba un parámetro y no reinicializaba la raíz del procesador virtual. Para conservar el comportamiento anterior, se proporciona el valor de parámetro predeterminado de `Blocking`.

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a>IThreadProxy::SwitchTo Método

Realiza un cambio de contexto cooperativo del contexto que se está ejecutando actualmente a otro diferente.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
El contexto de ejecución al que se cambia de forma cooperativa.

*switchState*<br/>
Indica el estado del proxy del subproceso que está ejecutando el modificador. El parámetro es del tipo `SwitchingProxyState`.

### <a name="remarks"></a>Observaciones

Utilice este método para cambiar de un contexto de ejecución a otro, desde el método [IExecutionContext::Dispatch](iexecutioncontext-structure.md#dispatch) del primer contexto de ejecución. El método asocia `pContext` el contexto de ejecución con un proxy de subproceso si aún no está asociado a uno. La propiedad del proxy de subproceso actual viene `switchState` determinada por el valor especificado para el argumento.

Utilice el `Idle` valor cuando desee devolver el proxy de subproceso que se está ejecutando actualmente al Administrador de recursos. Llamar `SwitchTo` con `switchState` el `Idle` parámetro establecido en `pContext` hará que el contexto de ejecución comience a ejecutarse en el recurso de ejecución subyacente. La propiedad de este proxy de subproceso se transfiere al Administrador de `Dispatch` recursos y `SwitchTo` se espera que vuelva del método del contexto de ejecución poco después de las devoluciones, con el fin de completar la transferencia. El contexto de ejecución que el proxy de subproceso estaba distribuyendo se desasocia del proxy de subproceso y el programador es libre de reutilizarlo o destruirlo como considere oportuno.

Utilice el `Blocking` valor cuando desee que este proxy de subproceso entre en un estado bloqueado. Llamar `SwitchTo` con `switchState` el `Blocking` parámetro establecido hará `pContext` que el contexto de ejecución comience a ejecutarse y bloqueará el proxy de subproceso actual hasta que se reanude. El programador conserva la propiedad del proxy de `Blocking` subproceso cuando el proxy de subproceso está en el estado. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, vea [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

Utilice el `Nesting` valor cuando desee separar temporalmente este proxy de subproceso de la raíz del procesador virtual en la que se está ejecutando y el programador para el que distribuye el trabajo. Llamar `SwitchTo` con `switchState` el `Nesting` parámetro establecido hará `pContext` que el contexto de ejecución comience a ejecutarse y el proxy de subproceso actual también continúa ejecutándose sin necesidad de una raíz de procesador virtual. Se considera que el proxy de subproceso ha dejado el programador hasta que llama al método [IThreadProxy::SwitchOut](#switchout) en un momento posterior. El `IThreadProxy::SwitchOut` método podría bloquear el proxy de subproceso hasta que una raíz de procesador virtual esté disponible para reprogramarlo.

Se debe llamar a `SwitchTo` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen. La función `invalid_argument` se `pContext` produce si `NULL`el parámetro está establecido en .

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a>Método IThreadProxy::YieldToSystem

Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el siguiente subproceso que se va a ejecutar.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Observaciones

Cuando se llama por un proxy de `YieldToSystem` subproceso respaldado por un `SwitchToThread`subproceso de Windows normal, se comporta exactamente igual que la función de Windows. Sin embargo, cuando se llama desde subprocesos programables `SwitchToThread` en modo de usuario (UMS), la función delega la tarea de elegir el siguiente subproceso para que se ejecute en el programador de modo de usuario, no en el sistema operativo. Para lograr el efecto deseado de cambiar a un `YieldToSystem`subproceso listo diferente en el sistema, utilice .

Se debe llamar a `YieldToSystem` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[IExecutionContext (estructura)](iexecutioncontext-structure.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)
