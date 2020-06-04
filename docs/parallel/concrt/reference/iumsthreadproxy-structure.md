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
ms.openlocfilehash: 2e748b1da02394e1f70afd8b92947e1291957c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368077"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy (Estructura)

Una abstracción para un subproceso de ejecución. Si desea conceder subprocesos programables en modo usuario (UMS) al programador, establezca el valor para el elemento de directiva de programador `SchedulerKind` en `UmsThreadDefault` e implemente la interfaz `IUMSScheduler`. Los subprocesos UMS se admiten únicamente en sistemas operativos de 64 bits con Windows 7 o una versión posterior.

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Llamado para ingresar una región crítica. Cuando se encuentra dentro de una región crítica, el programador no observará las operaciones de bloqueo asincrónicas que se producen durante la región. Esto significa que el programador no se volverá a introducir para errores de página, suspensiones de subprocesos, llamadas a procedimientos asincrónicos del kernel (ACC), etc., para un subproceso UMS.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Llamado para ingresar una región hipercrítica. Cuando se encuentra dentro de una región hipercrítica, el programador no observará ninguna operación de bloqueo que se produzca durante la región. Esto significa que el programador no se volverá a introducir para bloquear llamadas de función, bloquear intentos de adquisición que bloquean, errores de página, suspensiones de subprocesos, llamadas a procedimientos asincrónicos del kernel (ACC), etc., para un subproceso UMS.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Llamado para salir de una región crítica.|
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Llamado para salir de una región hipercrítica.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Devuelve el tipo de región crítica en la que se encuentra el proxy de subproceso. Dado que las regiones hipercríticas son un superconjunto de regiones críticas, `InsideHyperCriticalRegion` si el código ha entrado en una región crítica y, a continuación, se devuelve una región hipercrítica.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>Método IUMSThreadProxy::EnterCriticalRegion

Llamado para ingresar una región crítica. Cuando se encuentra dentro de una región crítica, el programador no observará las operaciones de bloqueo asincrónicas que se producen durante la región. Esto significa que el programador no se volverá a introducir para errores de página, suspensiones de subprocesos, llamadas a procedimientos asincrónicos del kernel (ACC), etc., para un subproceso UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de la región crítica. Las regiones críticas son reentrantes.

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>Método IUMSThreadProxy::EnterHyperCriticalRegion

Llamado para ingresar una región hipercrítica. Cuando se encuentra dentro de una región hipercrítica, el programador no observará ninguna operación de bloqueo que se produzca durante la región. Esto significa que el programador no se volverá a introducir para bloquear llamadas de función, bloquear intentos de adquisición que bloquean, errores de página, suspensiones de subprocesos, llamadas a procedimientos asincrónicos del kernel (ACC), etc., para un subproceso UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de la región hipercrítica. Las regiones hipercríticas son reentrantes.

### <a name="remarks"></a>Observaciones

El programador debe ser extraordinariamente cuidadoso con respecto a los métodos a los que llama y qué bloqueos adquiere en dichas regiones. Si el código de una región de este tipo se bloquea en un bloqueo que está en manos de algo que el programador es responsable de programar, puede haber un interbloqueo.

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>Método IUMSThreadProxy::ExitCriticalRegion

Llamado para salir de una región crítica.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de la región crítica. Las regiones críticas son reentrantes.

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>Método IUMSThreadProxy::ExitHyperCriticalRegion

Llamado para salir de una región hipercrítica.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Valor devuelto

La nueva profundidad de la región hipercrítica. Las regiones hipercríticas son reentrantes.

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>Método IUMSThreadProxy::GetCriticalRegionType

Devuelve el tipo de región crítica en la que se encuentra el proxy de subproceso. Dado que las regiones hipercríticas son un superconjunto de regiones críticas, `InsideHyperCriticalRegion` si el código ha entrado en una región crítica y, a continuación, se devuelve una región hipercrítica.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El tipo de región crítica en la que se encuentra el proxy de subproceso.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)
