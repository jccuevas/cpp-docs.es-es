---
title: IThreadProxy (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 0a002dc4440b4784dee7f808a9e3be8dd4f89124
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="ithreadproxy-structure"></a>IThreadProxy (Estructura)
Una abstracción para un subproceso de ejecución. Dependiendo de la clave de directiva `SchedulerType` del programador que se crea, el Administrador de recursos concederá al usuario un proxy del subproceso que está respaldado por un subproceso de Win32 normal o por un subproceso programable de modo de usuario (UMS). Los subprocesos UMS se admiten en sistemas operativos de 64 bits con Windows 7 o una versión posterior.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IThreadProxy:: GetId](#getid)|Devuelve un identificador único para el proxy del subproceso.|  
|[IThreadProxy:: SwitchOut](#switchout)|Desasocia el contexto de la raíz del procesador virtual subyacente.|  
|[IThreadProxy:: SwitchTo](#switchto)|Realiza un cambio de contexto cooperativo del contexto actualmente en ejecución a otro.|  
|[IThreadProxy:: YieldToSystem](#yieldtosystem)|Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el siguiente subproceso que se ejecuta.|  
  
## <a name="remarks"></a>Comentarios  
 Proxy del subproceso se acopla a los contextos de ejecución representados por la interfaz `IExecutionContext` como un medio de envío de trabajo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IThreadProxy`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getid"></a>IThreadProxy:: GetId (método)  
 Devuelve un identificador único para el proxy del subproceso.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador entero único.  
  
##  <a name="switchout"></a>IThreadProxy:: SwitchOut (método)  
 Desasocia el contexto de la raíz del procesador virtual subyacente.  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `switchState`  
 Indica el estado del proxy del subproceso que está ejecutando el modificador. El parámetro es del tipo `SwitchingProxyState`.  
  
### <a name="remarks"></a>Comentarios  
 Use `SwitchOut` si necesita desasociar un contexto de la raíz de procesador virtual en la que se ejecuta, por cualquier razón. En función del valor pasado en el parámetro `switchState`, y de si se está ejecutando o no en una raíz de procesador virtual, la llamada volverá inmediatamente o bloqueará el proxy del subproceso asociado al contexto. Es un error llamar a `SwitchOut` con el parámetro establecido en `Idle`. Si lo hace en un [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción.  
  
 `SwitchOut` resulta útil cuando desea reducir el número de raíces de procesador virtual que tiene su programador, ya sea porque el administrador de recursos ha dado instrucciones de que lo haga, o porque solicitó temporalmente una suscripción excesiva de raíz del procesador virtual y ya ha terminado con ella. En este caso debe invocar el método [IVirtualProcessorRoot::Remove](http://msdn.microsoft.com/en-us/ad699b4a-1972-4390-97ee-9c083ba7d9e4) en la raíz del procesador virtual, antes de realizar una llamada a `SwitchOut` con el parámetro `switchState` establecido en `Blocking`. Esto bloqueará el proxy del subproceso y reanudará la ejecución cuando está disponible una raíz del procesador virtual diferente en el programador para ejecutarlo. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, consulte [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).  
  
 También se puede usar `SwitchOut` si desea reinicializar el procesador virtual de forma que se pueda activar en el futuro mientras se bloquea el proxy del subproceso o se desasocia temporalmente este de la raíz del procesador virtual en el que se ejecuta, y del programador para el que está enviando trabajo. Use `SwitchOut` con el parámetro `switchState` establecido en `Blocking` si desea bloquear el proxy del subproceso. Podrá reanudarlo posteriormente mediante `SwitchTo` o `IVirtualProcessorRoot::Activate` como se indicó anteriormente. Use `SwitchOut` con el parámetro establecido en `Nesting` si desea desasociar temporalmente este proxy del subproceso de la raíz del procesador virtual en el que se ejecuta, y del programador con el que está asociado el procesador virtual. La llamada a `SwitchOut` con el parámetro `switchState` establecido en `Nesting` mientras se está ejecutando en una raíz del procesador virtual hará que la raíz se reinicialice y que el proxy del subproceso actual continúe ejecutándose sin necesidad. Se considera que el proxy del subproceso ha dejado el programador hasta que llama el [IThreadProxy:: SwitchOut](#switchout) método con `Blocking` en un momento posterior. La segunda llamada a `SwitchOut` con el parámetro establecido en `Blocking` tiene por objeto devolver el contexto a un estado bloqueado para que lo pueda reanudar `SwitchTo` o `IVirtualProcessorRoot::Activate` en el programador del que se desasoció. Dado que no estaba ejecutando en una raíz del procesador virtual, no se realiza ningún reinicio.  
  
 Una raíz del procesador virtual reinicializada no es distinta de una nueva raíz del procesador virtual que el Administrador de recursos concede al programador. Puede usarlo para la ejecución activándola con un contexto de ejecución mediante `IVirtualProcessorRoot::Activate`.  
  
 Se debe llamar a `SwitchOut` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.  
  
 En las bibliotecas y los encabezados incluidos con Visual Studio 2010, este método no tomaba un parámetro y no reinicializaba la raíz del procesador virtual. Para conservar el comportamiento anterior, se proporciona el valor de parámetro predeterminado de `Blocking`.  
  
##  <a name="switchto"></a>IThreadProxy:: SwitchTo (método)  
 Realiza un cambio de contexto cooperativo del contexto actualmente en ejecución a otro.  
  
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
 Utilice este método para cambiar de un contexto de ejecución a otro, desde el [IExecutionContext:: Dispatch](iexecutioncontext-structure.md#dispatch) método del primer contexto de ejecución. El método asocia el contexto de ejecución `pContext` con un proxy del subproceso si aún no está asociado a uno. La propiedad de proxy del subproceso actual está determinada por el valor especificado para el `switchState` argumento.  
  
 Utilice el valor `Idle` cuando desee devolver el proxy del subproceso actualmente en ejecución en el Administrador de recursos. Llamar a `SwitchTo` con el parámetro `switchState` establecido en `Idle` hará que el contexto de ejecución `pContext` para empezar a ejecutar en el recurso de ejecución subyacente. Propiedad de este proxy del subproceso se transfiere al administrador de recursos y se espera que devuelvan desde el contexto de ejecución `Dispatch` método poco después `SwitchTo` devuelve, para completar la transferencia. El contexto de ejecución que el proxy del subproceso estaba enviando se desasocia del proxy del subproceso y el programador es libre de reutilizarlo o destruirlo como considere apropiado.  
  
 Utilice el valor `Blocking` cuando desee que este proxy del subproceso entre en estado bloqueado. Llamar a `SwitchTo` con el parámetro `switchState` establecido en `Blocking` hará que el contexto de ejecución `pContext` para empezar a ejecutar y bloquear el proxy del subproceso actual hasta que se reanude. El programador conserva la propiedad del proxy del subproceso cuando el proxy del subproceso se encuentra en la `Blocking` estado. El proxy del subproceso de bloqueo se puede reanudar llamando a la función `SwitchTo` para cambiar al contexto de ejecución del proxy de este subproceso. También puede reanudar el proxy del subproceso, utilizando su contexto asociado para activar una raíz del procesador virtual. Para obtener más información sobre cómo hacerlo, consulte [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate).  
  
 Utilice el valor `Nesting` cuando desea desasociar temporalmente este proxy del subproceso de la raíz del procesador virtual que se ejecuta y el programador está enviando trabajo. Llamar a `SwitchTo` con el parámetro `switchState` establecido en `Nesting` hará que el contexto de ejecución `pContext` para iniciar la ejecución y la actual proxy del subproceso también sigue ejecutándose sin necesidad de una raíz del procesador virtual. Se considera que el proxy del subproceso ha dejado el programador hasta que llama el [IThreadProxy:: SwitchOut](#switchout) método en un momento posterior. El `IThreadProxy::SwitchOut` método podría bloquear el proxy del subproceso hasta que una raíz del procesador virtual esté disponible para programarla.  
  
 Se debe llamar a `SwitchTo` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen. La función produce `invalid_argument` si el parámetro `pContext` está establecido en `NULL`.  
  
##  <a name="yieldtosystem"></a>IThreadProxy:: YieldToSystem (método)  
 Hace que el subproceso que realiza la llamada ceda la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual. El sistema operativo selecciona el siguiente subproceso que se ejecuta.  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando lo llama un proxy del subproceso respaldado por un subproceso de Windows normal, `YieldToSystem` se comporta exactamente como la función de Windows `SwitchToThread`. Sin embargo, cuando se llama desde subprocesos programables (UMS) en modo de usuario, la `SwitchToThread` función delega la tarea de elegir el subproceso siguiente para ejecutar el programador de modo de usuario, no el sistema operativo. Para lograr el efecto deseado de cambiar a un subproceso listo diferente en el sistema, utilice `YieldToSystem`.  
  
 Se debe llamar a `YieldToSystem` en la interfaz `IThreadProxy` que representa el subproceso actualmente en ejecución o los resultados no se definen.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IExecutionContext (estructura)](iexecutioncontext-structure.md)   
 [IScheduler (estructura)](ischeduler-structure.md)   
 [IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)

