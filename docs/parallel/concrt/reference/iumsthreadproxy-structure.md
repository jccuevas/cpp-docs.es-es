---
title: IUMSThreadProxy (estructura)
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
ms.openlocfilehash: f4fb43a4223cad8cc63049d2a0f8345e48b90f17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139971"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy (estructura)

Una abstracción para un subproceso de ejecución. Si desea conceder subprocesos programables en modo usuario (UMS) al programador, establezca el valor para el elemento de directiva de programador `SchedulerKind` en `UmsThreadDefault` e implemente la interfaz `IUMSScheduler`. Los subprocesos UMS se admiten únicamente en sistemas operativos de 64 bits con Windows 7 o una versión posterior.

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IUMSThreadProxy:: Entercriticalregion (](#entercriticalregion)|Se llama para especificar una región crítica. Cuando se encuentra dentro de una región crítica, el programador no observará las operaciones de bloqueo asincrónica que se producen durante la región. Esto significa que el programador no se volverá a escribir para errores de página, suspensiones de subprocesos, llamadas a procedimientos asincrónicos del kernel (APC), etc., para un subproceso UMS.|
|[IUMSThreadProxy:: Enterhypercriticalregion (](#enterhypercriticalregion)|Se llama para especificar una región de Hyper-crítico. Cuando se encuentra dentro de una región de Hyper-crítico, el programador no observará las operaciones de bloqueo que se produzcan durante la región. Esto significa que Scheduler no se volverá a introducir para bloquear llamadas a funciones, los intentos de adquisición de bloqueos, el bloque, los errores de página, las suspensiones de subprocesos, las llamadas a procedimiento asincrónico del kernel (APC), etc., para un subproceso UMS.|
|[IUMSThreadProxy:: Exitcriticalregion (](#exitcriticalregion)|Se llama para salir de una región crítica.|
|[IUMSThreadProxy:: ExitHyperCriticalRegion (](#exithypercriticalregion)|Se llama para salir de una región de Hyper-crítico.|
|[IUMSThreadProxy:: Getcriticalregiontype (](#getcriticalregiontype)|Devuelve el tipo de región crítica en la que se encuentra el proxy del subproceso. Dado que las regiones de nivel crítico de Hyper son un superconjunto de regiones críticas, si el código ha entrado en una región crítica y, a continuación, en una región de Hyper-crítico, se devolverá `InsideHyperCriticalRegion`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="entercriticalregion"></a>IUMSThreadProxy:: Entercriticalregion ((método)

Se llama para especificar una región crítica. Cuando se encuentra dentro de una región crítica, el programador no observará las operaciones de bloqueo asincrónica que se producen durante la región. Esto significa que el programador no se volverá a escribir para errores de página, suspensiones de subprocesos, llamadas a procedimientos asincrónicos del kernel (APC), etc., para un subproceso UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

Nueva profundidad de la región crítica. Las regiones críticas son reentrantes.

## <a name="enterhypercriticalregion"></a>IUMSThreadProxy:: Enterhypercriticalregion ((método)

Se llama para especificar una región de Hyper-crítico. Cuando se encuentra dentro de una región de Hyper-crítico, el programador no observará las operaciones de bloqueo que se produzcan durante la región. Esto significa que Scheduler no se volverá a introducir para bloquear llamadas a funciones, los intentos de adquisición de bloqueos, el bloque, los errores de página, las suspensiones de subprocesos, las llamadas a procedimiento asincrónico del kernel (APC), etc., para un subproceso UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de la región de Hyper-crítico. Las regiones de Hyper-crítico son reentrantes.

### <a name="remarks"></a>Observaciones

El programador debe ser extraordinariamente cuidadoso sobre los métodos a los que llama y los bloqueos que adquiere en esas regiones. Si el código de este tipo de región se bloquea en un bloqueo que se retiene en algo que el programador es responsable de la programación, puede producirse un interbloqueo.

## <a name="exitcriticalregion"></a>IUMSThreadProxy:: Exitcriticalregion ((método)

Se llama para salir de una región crítica.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

Nueva profundidad de la región crítica. Las regiones críticas son reentrantes.

## <a name="exithypercriticalregion"></a>IUMSThreadProxy:: ExitHyperCriticalRegion ((método)

Se llama para salir de una región de Hyper-crítico.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de la región de Hyper-crítico. Las regiones de Hyper-crítico son reentrantes.

## <a name="getcriticalregiontype"></a>IUMSThreadProxy:: Getcriticalregiontype ((método)

Devuelve el tipo de región crítica en la que se encuentra el proxy del subproceso. Dado que las regiones de nivel crítico de Hyper son un superconjunto de regiones críticas, si el código ha entrado en una región crítica y, a continuación, en una región de Hyper-crítico, se devolverá `InsideHyperCriticalRegion`.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El tipo de región crítica en el que se encuentra el proxy del subproceso.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)
