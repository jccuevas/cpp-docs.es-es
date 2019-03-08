---
title: IUMSThreadProxy (Estructura)
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 258f249aa178b73da2080cca888409dc07f63dbb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263044"
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
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Se llama para especificar una región crítica. Dentro de una región crítica, el programador no observará operaciones asincrónicas de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para errores de página, suspensiones de subproceso, las llamadas de procedimientos asincrónicos (APC) del kernel y así sucesivamente, para un subproceso UMS.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Se llama para especificar una región hyper crítica. Dentro de una región hyper crítica, el programador no observarán ninguna operación de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para bloquear llamadas de función, intentos de adquisición de bloqueo que bloquean, errores de página, subproceso suspensiones, las llamadas del kernel procedimientos asincrónicos (APC) y así sucesivamente, para un UMS subprocesos.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Se llama para salir de una región crítica.|
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Se llama para salir de una región hyper crítica.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Devuelve el tipo de región crítica, el proxy del subproceso está dentro. Dado que las regiones hyper críticas son un superconjunto de las regiones críticas, si el código ha entrado en una región crítica y, a continuación, en una región hyper crítica, `InsideHyperCriticalRegion` se devolverá.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="entercriticalregion"></a>  IUMSThreadProxy:: EnterCriticalRegion (método)

Se llama para especificar una región crítica. Dentro de una región crítica, el programador no observará operaciones asincrónicas de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para errores de página, suspensiones de subproceso, las llamadas de procedimientos asincrónicos (APC) del kernel y así sucesivamente, para un subproceso UMS.

```
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de región crítica. Las regiones críticas son reentrantes.

##  <a name="enterhypercriticalregion"></a>  IUMSThreadProxy:: EnterHyperCriticalRegion (método)

Se llama para especificar una región hyper crítica. Dentro de una región hyper crítica, el programador no observarán ninguna operación de bloqueo que se producen durante la región. Esto significa que el programador no se volverá para bloquear llamadas de función, intentos de adquisición de bloqueo que bloquean, errores de página, subproceso suspensiones, las llamadas del kernel procedimientos asincrónicos (APC) y así sucesivamente, para un UMS subprocesos.

```
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de región hyper crítica. Regiones Hyper críticas son reentrantes.

### <a name="remarks"></a>Comentarios

El programador debe ser extraordinariamente cuidadoso sobre qué métodos llama y qué bloqueos adquiere en esas regiones. Si el código de esa región se bloquea en un bloqueo mantenido por algo que el programador es responsable de programar, puede producirse un interbloqueo.

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

La nueva profundidad de región hyper crítica. Regiones Hyper críticas son reentrantes.

##  <a name="getcriticalregiontype"></a>  IUMSThreadProxy:: GetCriticalRegionType (método)

Devuelve el tipo de región crítica, el proxy del subproceso está dentro. Dado que las regiones hyper críticas son un superconjunto de las regiones críticas, si el código ha entrado en una región crítica y, a continuación, en una región hyper crítica, `InsideHyperCriticalRegion` se devolverá.

```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El tipo de región crítica, que el proxy del subproceso está dentro.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)
