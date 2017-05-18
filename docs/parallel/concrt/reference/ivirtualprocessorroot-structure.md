---
title: IVirtualProcessorRoot (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
dev_langs:
- C++
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
caps.latest.revision: 18
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
ms.openlocfilehash: 2635f1c18dd61127360b8398ad1b0da03f1666d7
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot (Estructura)
Una abstracción para un subproceso de hardware en el que un proxy del subproceso puede ejecutarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IVirtualProcessorRoot : public IExecutionResource;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IVirtualProcessorRoot:: Activate](#activate)|Hace que el proxy del subproceso asociado a la interfaz de contexto de ejecución `pContext` empiece a ejecutar en esta raíz del procesador virtual.|  
|[IVirtualProcessorRoot:: Deactivate](#deactivate)|Hace que el proxy del subproceso está ejecutando actualmente en esta raíz del procesador virtual deje de enviar el contexto de ejecución. El proxy del subproceso reanudará la ejecución en una llamada a la `Activate` (método).|  
|[IVirtualProcessorRoot:: EnsureAllTasksVisible](#ensurealltasksvisible)|Hace que los datos almacenados en la jerarquía de la memoria de procesadores individuales se vuelvan visible a todos los procesadores del sistema. Se asegura de que se ha ejecutado una barrera de memoria completa en todos los procesadores antes de que el método devuelve.|  
|[IVirtualProcessorRoot:: GetId](#getid)|Devuelve un identificador único para la raíz del procesador virtual.|  
  
## <a name="remarks"></a>Comentarios  
 Cada raíz del procesador virtual tiene un recurso de ejecución asociados. El `IVirtualProcessorRoot` interfaz se hereda de la [IExecutionResource](iexecutionresource-structure.md) interfaz. Varias raíces de procesador virtual pueden corresponder al mismo subproceso de hardware subyacente.  
  
 El Administrador de recursos concede las raíces de procesador virtual a programadores en respuesta a las solicitudes de recursos. Un programador puede usar una raíz del procesador virtual para realizar el trabajo activándolo con un contexto de ejecución.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [IExecutionResource](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="activate"></a>IVirtualProcessorRoot:: Activate (método)  
 Hace que el proxy del subproceso asociado a la interfaz de contexto de ejecución `pContext` empiece a ejecutar en esta raíz del procesador virtual.  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 Una interfaz al contexto de ejecución que se enviará en esta raíz del procesador virtual.  
  
### <a name="remarks"></a>Comentarios  
 El Administrador de recursos proporcionará a un proxy del subproceso si uno no está asociado a la interfaz de contexto de ejecución`pContext`  
  
 El `Activate` método puede utilizarse para empezar a ejecutar el trabajo en una nueva raíz del procesador virtual devuelta por el Administrador de recursos o reanudar el proxy del subproceso en una raíz del procesador virtual que se ha desactivado o que está a punto de desactivar. Consulte [IVirtualProcessorRoot:: Deactivate](#deactivate) para obtener más información sobre la desactivación. Cuando está reanudando una raíz del procesador virtual desactivada, el parámetro `pContext` debe ser el mismo que el parámetro se utiliza para desactivar la raíz del procesador virtual.  
  
 Una vez que se ha activado una raíz del procesador virtual por primera vez, los pares subsiguientes de llamadas a `Deactivate` y `Activate` pueden competir entre sí. Esto significa que es aceptable para el Administrador de recursos para recibir una llamada a `Activate` antes de recibir el `Deactivate` llamada que fue creado.  
  
 Al activar una raíz del procesador virtual, indicar al administrador de recursos que esta raíz del procesador virtual está actualmente ocupada con trabajo. Si el programador no puede encontrar ningún trabajo para ejecutar en esta raíz, se espera para invocar el `Deactivate` método informar al administrador de recursos que la raíz del procesador virtual está inactiva. El Administrador de recursos usa estos datos para el sistema de equilibrio de carga.  
  
 `invalid_argument`se produce si el argumento `pContext` tiene el valor `NULL`.  
  
 `invalid_operation`se produce si el argumento `pContext` no representa el contexto de ejecución que fue enviado recientemente por esta raíz del procesador virtual.  
  
 La acción de activar una raíz del procesador virtual aumenta el nivel de suscripción del subproceso de hardware subyacente por uno. Para obtener más información sobre niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="deactivate"></a>IVirtualProcessorRoot:: Deactivate (método)  
 Hace que el proxy del subproceso está ejecutando actualmente en esta raíz del procesador virtual deje de enviar el contexto de ejecución. El proxy del subproceso reanudará la ejecución en una llamada a la `Activate` (método).  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 El contexto que actualmente está siendo enviado por esta raíz.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor booleano. Un valor de `true` indica que el proxy del subproceso se devuelve desde el `Deactivate` método en respuesta a una llamada a la `Activate` (método). Un valor de `false` indica que el proxy del subproceso devuelto desde el método en respuesta a un evento de notificación en el Administrador de recursos. En un programador de subproceso (UMS) de programables de modo de usuario, esto indica que hayan aparecido los elementos en la lista de finalización del programador y el programador se requiere para controlarlos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para detener temporalmente la ejecución de una raíz del procesador virtual cuando no puede encontrar ningún trabajo en el programador. Una llamada a la `Deactivate` método debe originarse desde el `Dispatch` método del contexto de ejecución que la raíz del procesador virtual se activó en último lugar. En otras palabras, el proxy del subproceso invoca el `Deactivate` método debe ser el único que se está ejecutando actualmente en la raíz del procesador virtual. Llamar al método en una raíz del procesador virtual, no se está ejecutando en podría provocar un comportamiento indefinido.  
  
 Una raíz del procesador virtual desactivada puede reactivarse con una llamada a la `Activate` método con el mismo argumento que se pasó a la `Deactivate` (método). El programador es responsable de garantizar que las llamadas a la `Activate` y `Deactivate` están emparejados de métodos, pero no son necesarios para recibirse en un orden específico. El Administrador de recursos puede controlar la recepción de una llamada a la `Activate` método antes de recibir una llamada a la `Deactivate` método que fue creado.  
  
 Si una raíz del procesador virtual despierta y el valor devuelto de la `Deactivate` método es el valor `false`, el programador debe consultar la lista de finalización UMS a través de la `IUMSCompletionList::GetUnblockNotifications` método, actuar sobre esa información y, a continuación, vuelve a llamar a la `Deactivate` nuevo al método. Esto debe repetirse hasta que el `Deactivate` método devuelve el valor `true`.  
  
 `invalid_argument`se produce si el argumento `pContext` tiene el valor `NULL`.  
  
 `invalid_operation`se produce si nunca se ha activado la raíz del procesador virtual, o el argumento `pContext` no representa el contexto de ejecución que fue enviado recientemente por esta raíz del procesador virtual.  
  
 La acción de desactivar una raíz del procesador virtual disminuye el nivel de suscripción del subproceso de hardware subyacente por uno. Para obtener más información sobre niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot:: EnsureAllTasksVisible (método)  
 Hace que los datos almacenados en la jerarquía de la memoria de procesadores individuales se vuelvan visible a todos los procesadores del sistema. Se asegura de que se ha ejecutado una barrera de memoria completa en todos los procesadores antes de que el método devuelve.  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 El contexto que actualmente está siendo enviado por esta raíz del procesador virtual.  
  
### <a name="remarks"></a>Comentarios  
 Puede encontrar útil este método cuando desee sincronizar la desactivación de una raíz del procesador virtual con la adición del nuevo trabajo en el programador. Por motivos de rendimiento, puede decidir agregar elementos de trabajo a su programador sin ejecutar una barrera de memoria, lo que significa que los elementos de trabajo agregados por un subproceso que se ejecuta en un procesador no son inmediatamente visibles para todos los demás procesadores. Mediante este método junto con el `Deactivate` raíces de método, puede asegurarse de que el programador no desactiva todos su procesador virtual mientras los elementos de trabajo existen en las colecciones de su programador.  
  
 Una llamada a la `EnsureAllTasksVisibleThe` método debe originarse desde el `Dispatch` método del contexto de ejecución que la raíz del procesador virtual se activó en último lugar. En otras palabras, el proxy del subproceso invoca el `EnsureAllTasksVisible` método debe ser el único que se está ejecutando actualmente en la raíz del procesador virtual. Llamar al método en una raíz del procesador virtual, no se está ejecutando en podría provocar un comportamiento indefinido.  
  
 `invalid_argument`se produce si el argumento `pContext` tiene el valor `NULL`.  
  
 `invalid_operation`se produce si nunca se ha activado la raíz del procesador virtual, o el argumento `pContext` no representa el contexto de ejecución que fue enviado recientemente por esta raíz del procesador virtual.  
  
##  <a name="getid"></a>IVirtualProcessorRoot:: GetId (método)  
 Devuelve un identificador único para la raíz del procesador virtual.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador entero.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

