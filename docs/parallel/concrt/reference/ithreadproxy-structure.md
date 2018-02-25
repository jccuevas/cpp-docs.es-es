---
title: IThreadProxy (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs:
- C++
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e96f02677e3a79d1a6e15b9b22b777ca794b516d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ithreadproxy-structure"></a>IThreadProxy (Estructura)
Una abstracción para un subproceso de ejecución. Dependiendo de la clave de directiva `SchedulerType` del programador que se crea, el Administrador de recursos concederá al usuario un proxy del subproceso que está respaldado por un subproceso de Win32 normal o por un subproceso programable de modo de usuario (UMS). Los subprocesos UMS se admiten en sistemas operativos de 64 bits con Windows 7 o una versión posterior.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IThreadProxy::GetId](#getid)|Devuelve un identificador único para el proxy del subproceso.|  
|[IThreadProxy::SwitchOut](#switchout)|Desasocia el contexto de la raíz del procesador virtual subyacente.|  
|[IThreadProxy::SwitchTo](#switchto)|Realiza un cambio de contexto cooperativo desde el contexto está ejecutando actualmente por otra distinta.|  
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el siguiente subproceso que se ejecuta.|  
  
## <a name="remarks"></a>Comentarios  
 Proxy del subproceso se acopla a los contextos de ejecución representados por la interfaz `IExecutionContext` como un medio de envío de trabajo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IThreadProxy`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getid"></a>  IThreadProxy:: GetId (método)  
 Devuelve un identificador único para el proxy del subproceso.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador entero único.  
  
##  <a name="switchout"></a>  IThreadProxy:: SwitchOut (método)  
 Desasocia el contexto de la raíz del procesador virtual subyacente.  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `switchState`  
 Indica el estado del proxy del subproceso que está ejecutando el modificador. El parámetro es del tipo `SwitchingProxyState`.  
  
### <a name="remarks"></a>Comentarios  
 Use `SwitchOut` si necesita desasociar un contexto de la raíz de procesador virtual en la que se ejecuta, por cualquier razón. En función del valor pasado en el parámetro `switchState`, y de si se está ejecutando o no en una raíz de procesador virtual, la llamada volverá inmediatamente o bloqueará el proxy del subproceso asociado al contexto. Es un error llamar a `SwitchOut` con el parámetro establecido en `Idle`. Si lo hace, se producirá en un [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción.  
  
 `SwitchOut` resulta útil cuando desea reducir el número de raíces de procesador virtual que tiene su programador, ya sea porque el administrador de recursos ha dado instrucciones de que lo haga, o porque solicitó temporalmente una suscripción excesiva de raíz del procesador virtual y ya ha terminado con ella. En este caso debe invocar el método [IVirtualProcessorRoot::Remove](http://msdn.microsoft.com/en-us/ad699b4a-1972-4390-97ee-9c083ba7d9e4) en la raíz del procesador virtual, antes de realizar una llamada a `SwitchOut` con el parámetro `switchState` establecido en `Blocking`. Esto bloqueará el proxy del subproceso y reanudará la ejecución cuando está disponible una raíz del procesador virtual diferente en el programador para ejecutarlo. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, consulte [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).  
  
 También se puede usar `SwitchOut` si desea reinicializar el procesador virtual de forma que se pueda activar en el futuro mientras se bloquea el proxy del subproceso o se desasocia temporalmente este de la raíz del procesador virtual en el que se ejecuta, y del programador para el que está enviando trabajo. Use `SwitchOut` con el parámetro `switchState` establecido en `Blocking` si desea bloquear el proxy del subproceso. Podrá reanudarlo posteriormente mediante `SwitchTo` o `IVirtualProcessorRoot::Activate` como se indicó anteriormente. Use `SwitchOut` con el parámetro establecido en `Nesting` si desea desasociar temporalmente este proxy del subproceso de la raíz del procesador virtual en el que se ejecuta, y del programador con el que está asociado el procesador virtual. La llamada a `SwitchOut` con el parámetro `switchState` establecido en `Nesting` mientras se está ejecutando en una raíz del procesador virtual hará que la raíz se reinicialice y que el proxy del subproceso actual continúe ejecutándose sin necesidad. El proxy del subproceso se considera que ha dejado el programador hasta que llama el [IThreadProxy:: SwitchOut](#switchout) método con `Blocking` en un momento posterior. La segunda llamada a `SwitchOut` con el parámetro establecido en `Blocking` tiene por objeto devolver el contexto a un estado bloqueado para que lo pueda reanudar `SwitchTo` o `IVirtualProcessorRoot::Activate` en el programador del que se desasoció. Dado que no estaba ejecutando en una raíz del procesador virtual, no se realiza ningún reinicio.  
  
 Una raíz del procesador virtual reinicializada no es distinta de una nueva raíz del procesador virtual que el Administrador de recursos concede al programador. Puede usarlo para la ejecución activándola con un contexto de ejecución mediante `IVirtualProcessorRoot::Activate`.  
  
 Se debe llamar a `SwitchOut` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.  
  
 En las bibliotecas y los encabezados incluidos con Visual Studio 2010, este método no tomaba un parámetro y no reinicializaba la raíz del procesador virtual. Para conservar el comportamiento anterior, se proporciona el valor de parámetro predeterminado de `Blocking`.  
  
##  <a name="switchto"></a>  IThreadProxy::SwitchTo Method  
 Realiza un cambio de contexto cooperativo desde el contexto está ejecutando actualmente por otra distinta.  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 El contexto de ejecución para cambiar de forma cooperativa a.  
  
 `switchState`  
 Indica el estado del proxy del subproceso que está ejecutando el modificador. El parámetro es del tipo `SwitchingProxyState`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para cambiar de un contexto de ejecución a otro, desde el [IExecutionContext:: Dispatch](iexecutioncontext-structure.md#dispatch) método del primer contexto de ejecución. El método asocia el contexto de ejecución `pContext` con un proxy del subproceso si aún no está asociado a uno. La propiedad del proxy del subproceso actual está determinada por el valor especificado para el `switchState` argumento.  
  
 Utilice el valor `Idle` cuando desee devolver el proxy del subproceso actualmente en ejecución en el Administrador de recursos. Al llamar a `SwitchTo` con el parámetro `switchState` establecido en `Idle` hará que el contexto de ejecución `pContext` para empezar a ejecutar en el recurso de ejecución subyacente. La propiedad de este proxy del subproceso se transfiere al administrador de recursos, y se espera que se devuelven desde el contexto de ejecución `Dispatch` método poco después `SwitchTo` devuelve, para completar la transferencia. El contexto de ejecución que el proxy del subproceso estaba enviando se desasocia del proxy del subproceso y el programador es libre de reutilizarlo o destruirlo como que considere apropiada.  
  
 Utilice el valor `Blocking` cuando desee que este proxy del subproceso entre en un estado bloqueado. Al llamar a `SwitchTo` con el parámetro `switchState` establecido en `Blocking` hará que el contexto de ejecución `pContext` para empezar a ejecutarse y bloquear el proxy del subproceso actual hasta que se reanude. El programador conserva la propiedad del proxy del subproceso cuando el proxy del subproceso está en el `Blocking` estado. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, consulte [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).  
  
 Utilice el valor `Nesting` cuando desea desasociar temporalmente este proxy del subproceso de la raíz del procesador virtual que se ejecuta y el programador está enviando trabajo. Al llamar a `SwitchTo` con el parámetro `switchState` establecido en `Nesting` hará que el contexto de ejecución `pContext` para iniciar la ejecución y la actual proxy del subproceso también sigue ejecutándose sin necesidad de una raíz del procesador virtual. El proxy del subproceso se considera que ha dejado el programador hasta que llama el [IThreadProxy:: SwitchOut](#switchout) método en un momento posterior. El `IThreadProxy::SwitchOut` método podría bloquear el proxy del subproceso hasta que esté disponible para volver a programar una raíz del procesador virtual.  
  
 Se debe llamar a `SwitchTo` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen. La función produce `invalid_argument` si el parámetro `pContext` está establecido en `NULL`.  
  
##  <a name="yieldtosystem"></a>  IThreadProxy::YieldToSystem Method  
 Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el siguiente subproceso que se ejecuta.  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a un proxy del subproceso respaldado por un subproceso de Windows normal, `YieldToSystem` se comporta exactamente igual que la función de Windows `SwitchToThread`. Sin embargo, cuando se llama desde subprocesos programables (UMS) de modo de usuario, la `SwitchToThread` función delega la tarea de elegir el subproceso siguiente para ejecutar el programador de modo de usuario, no en el sistema operativo. Para lograr el efecto deseado de cambiar a otro subproceso preparado en el sistema, utilice `YieldToSystem`.  
  
 Se debe llamar a `YieldToSystem` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IExecutionContext (estructura)](iexecutioncontext-structure.md)   
 [IScheduler (estructura)](ischeduler-structure.md)   
 [IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)
