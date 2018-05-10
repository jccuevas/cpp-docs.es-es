---
title: IUMSThreadProxy (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbba2955adc14ef73a0ba9932756ace57c4136e6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy (Estructura)
Una abstracción para un subproceso de ejecución. Si desea conceder subprocesos programables en modo usuario (UMS) al programador, establezca el valor para el elemento de directiva de programador `SchedulerKind` en `UmsThreadDefault` e implemente la interfaz `IUMSScheduler`. Los subprocesos UMS se admiten únicamente en sistemas operativos de 64 bits con Windows 7 o una versión posterior.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Se llama para especificar una región crítica. Cuando esté en una región crítica, el programador no observará operaciones asincrónicas de bloqueo que se producen durante la región. Esto significa que el programador no se volverá de errores de página, suspensiones de subproceso, llamadas a procedimiento asincrónico (APC) del kernel etc., para un subproceso UMS.|  
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Se llama para especificar una región hyper crítica. Cuando esté en una región hyper crítica, el programador no observará ninguna operación de bloqueo que se producen durante la región. Esto significa que el programador no se volverá de bloqueo de llamadas de función, intentos de adquisición de bloqueo que bloquean, errores de página, subproceso suspensiones, llamadas a procedimiento asincrónico del núcleo (APC) y así sucesivamente, para un UMS subprocesos.|  
|[IUMSThreadProxy:: ExitCriticalRegion](#exitcriticalregion)|Se llama para salir de una región crítica.|  
|[IUMSThreadProxy:: ExitHyperCriticalRegion](#exithypercriticalregion)|Se llama para salir de una región hyper crítica.|  
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Devuelve el tipo de región crítica el proxy del subproceso está dentro. Dado que las regiones hyper críticas son un superconjunto de las regiones críticas, si el código ha entrado en una región crítica y, a continuación, una región hyper crítica, `InsideHyperCriticalRegion` se devolverá.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="entercriticalregion"></a>  IUMSThreadProxy:: EnterCriticalRegion (método)  
 Se llama para especificar una región crítica. Cuando esté en una región crítica, el programador no observará operaciones asincrónicas de bloqueo que se producen durante la región. Esto significa que el programador no se volverá de errores de página, suspensiones de subproceso, llamadas a procedimiento asincrónico (APC) del kernel etc., para un subproceso UMS.  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región crítica. Las regiones críticas son reentrantes.  
  
##  <a name="enterhypercriticalregion"></a>  IUMSThreadProxy:: EnterHyperCriticalRegion (método)  
 Se llama para especificar una región hyper crítica. Cuando esté en una región hyper crítica, el programador no observará ninguna operación de bloqueo que se producen durante la región. Esto significa que el programador no se volverá de bloqueo de llamadas de función, intentos de adquisición de bloqueo que bloquean, errores de página, subproceso suspensiones, llamadas a procedimiento asincrónico del núcleo (APC) y así sucesivamente, para un UMS subprocesos.  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región hyper crítica. Las regiones Hyper críticas son reentrantes.  
  
### <a name="remarks"></a>Comentarios  
 El programador debe ser extraordinariamente cuidadoso sobre qué métodos llama y qué bloqueos adquiere en esas regiones. Si el código de esa región se bloquea en un bloqueo que se mantiene por algo que el programador es responsable de la programación, puede producirse un interbloqueo.  
  
##  <a name="exitcriticalregion"></a>  IUMSThreadProxy:: ExitCriticalRegion (método)  
 Se llama para salir de una región crítica.  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región crítica. Las regiones críticas son reentrantes.  
  
##  <a name="exithypercriticalregion"></a>  IUMSThreadProxy:: ExitHyperCriticalRegion (método)  
 Se llama para salir de una región hyper crítica.  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región hyper crítica. Las regiones Hyper críticas son reentrantes.  
  
##  <a name="getcriticalregiontype"></a>  IUMSThreadProxy:: GetCriticalRegionType (método)  
 Devuelve el tipo de región crítica el proxy del subproceso está dentro. Dado que las regiones hyper críticas son un superconjunto de las regiones críticas, si el código ha entrado en una región crítica y, a continuación, una región hyper crítica, `InsideHyperCriticalRegion` se devolverá.  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de región crítica el proxy del subproceso está dentro.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IUMSScheduler (estructura)](iumsscheduler-structure.md)
