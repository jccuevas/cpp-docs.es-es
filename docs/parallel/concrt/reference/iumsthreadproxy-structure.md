---
title: IUMSThreadProxy (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IUMSThreadProxy
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 55ed05f137775e819c81ce231cf8c8ad3a9974f3
ms.lasthandoff: 02/24/2017

---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy (Estructura)
Una abstracción para un subproceso de ejecución. Si desea conceder subprocesos programables en modo usuario (UMS) al programador, establezca el valor para el elemento de directiva de programador `SchedulerKind` en `UmsThreadDefault` e implemente la interfaz `IUMSScheduler`. Los subprocesos UMS se admiten únicamente en sistemas operativos de 64 bits con Windows 7 o una versión posterior.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IUMSThreadProxy:: EnterCriticalRegion (método)](#entercriticalregion)|Se llama para especificar una región crítica. Dentro de una región crítica, el programador no observará operaciones asincrónicas de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para errores de página, suspensiones de subproceso, llamadas a procedimiento asincrónico (APC) del kernel etc., en un subproceso UMS.|  
|[IUMSThreadProxy:: EnterHyperCriticalRegion (método)](#enterhypercriticalregion)|Se llama para especificar una región hyper crítica. Dentro de una región hipercrítica, el programador no observará ninguna operación de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para bloquear llamadas de función, intentos de adquisición de bloqueo que bloquean, errores de página, suspensiones, llamadas a procedimiento asincrónico (APC) del kernel de subprocesos y así sucesivamente, para un UMS subprocesos.|  
|[IUMSThreadProxy:: ExitCriticalRegion (método)](#exitcriticalregion)|Se llama para salir de una región crítica.|  
|[IUMSThreadProxy:: ExitHyperCriticalRegion (método)](#exithypercriticalregion)|Se llama para salir de una región hipercrítica.|  
|[IUMSThreadProxy:: GetCriticalRegionType (método)](#getcriticalregiontype)|Devuelve el tipo de región crítica, el proxy del subproceso está dentro. Dado que las regiones hyper críticas son un supraconjunto de regiones críticas, si el código ha entrado en una región crítica y, a continuación, una región hyper crítica, `InsideHyperCriticalRegion` se devolverá.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameentercriticalregiona--iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>IUMSThreadProxy:: EnterCriticalRegion (método)  
 Se llama para especificar una región crítica. Dentro de una región crítica, el programador no observará operaciones asincrónicas de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para errores de página, suspensiones de subproceso, llamadas a procedimiento asincrónico (APC) del kernel etc., en un subproceso UMS.  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región crítica. Las regiones críticas son reentrantes.  
  
##  <a name="a-nameenterhypercriticalregiona--iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>IUMSThreadProxy:: EnterHyperCriticalRegion (método)  
 Se llama para especificar una región hyper crítica. Dentro de una región hipercrítica, el programador no observará ninguna operación de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para bloquear llamadas de función, intentos de adquisición de bloqueo que bloquean, errores de página, suspensiones, llamadas a procedimiento asincrónico (APC) del kernel de subprocesos y así sucesivamente, para un UMS subprocesos.  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región hipercrítica. Regiones Hyper críticas son reentrantes.  
  
### <a name="remarks"></a>Comentarios  
 El programador debe ser extraordinariamente cuidadoso sobre qué métodos llama y qué bloqueos adquiere en esas regiones. Si el código de esa región se bloquea en un bloqueo mantenido por algo que el programador es responsable de la programación, puede producirse un interbloqueo.  
  
##  <a name="a-nameexitcriticalregiona--iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>IUMSThreadProxy:: ExitCriticalRegion (método)  
 Se llama para salir de una región crítica.  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región crítica. Las regiones críticas son reentrantes.  
  
##  <a name="a-nameexithypercriticalregiona--iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>IUMSThreadProxy:: ExitHyperCriticalRegion (método)  
 Se llama para salir de una región hipercrítica.  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La nueva profundidad de región hipercrítica. Regiones Hyper críticas son reentrantes.  
  
##  <a name="a-namegetcriticalregiontypea--iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>IUMSThreadProxy:: GetCriticalRegionType (método)  
 Devuelve el tipo de región crítica, el proxy del subproceso está dentro. Dado que las regiones hyper críticas son un supraconjunto de regiones críticas, si el código ha entrado en una región crítica y, a continuación, una región hyper crítica, `InsideHyperCriticalRegion` se devolverá.  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de región crítica, que el proxy del subproceso está dentro.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IUMSScheduler (estructura)](iumsscheduler-structure.md)

