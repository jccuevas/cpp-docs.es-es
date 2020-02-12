---
title: IUMSScheduler (estructura)
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 45df744a9850510006e4bf887c8ed61b000a8e5c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139994"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler (estructura)

Una interfaz a una abstracción de un programador de trabajo que desea que el Administrador de recursos del runtime de simultaneidad controle los subprocesos programables de modo de usuario (UMS). El Administrador de recursos usa esta interfaz para comunicarse con los programadores de subprocesos UMS. La interfaz `IUMSScheduler` hereda de la interfaz `IScheduler` .

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IUMSScheduler (:: SetCompletionList (](#setcompletionlist)|Asigna una interfaz `IUMSCompletionList` a un programador de subprocesos UMS.|

## <a name="remarks"></a>Observaciones

Si está implementando un programador personalizado que se comunica con el Administrador de recursos y desea que los subprocesos UMS se entreguen al programador en lugar de a los subprocesos Win32 normales, debe proporcionar una implementación de la interfaz `IUMSScheduler`. Además, debe establecer el valor de directiva de la clave de directiva de Scheduler `SchedulerKind` que se va a `UmsThreadDefault`. Si la Directiva especifica el subproceso UMS, la interfaz `IScheduler` que se pasa como parámetro al método [IResourceManager:: RegisterScheduler (](iresourcemanager-structure.md#registerscheduler) debe ser una interfaz `IUMSScheduler`.

El Administrador de recursos puede controlar los subprocesos UMS solo en los sistemas operativos que tienen la característica UMS. los sistemas operativos de 64 bits con Windows 7 y versiones posteriores admiten subprocesos UMS. Si crea una directiva de programador con la clave `SchedulerKind` establecida en el valor `UmsThreadDefault` y la plataforma subyacente no es compatible con UMS, el valor de la clave `SchedulerKind` en esa Directiva se cambiará al valor `ThreadScheduler`. Siempre debe leer este valor de Directiva antes de esperar para recibir los subprocesos UMS.

La interfaz de `IUMSScheduler` es un extremo de un canal bidireccional de comunicación entre un programador y el Administrador de recursos. El otro extremo se representa mediante las interfaces `IResourceManager` y `ISchedulerProxy`, que se implementan mediante el Administrador de recursos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="setcompletionlist"></a>IUMSScheduler (:: SetCompletionList ((método)

Asigna una interfaz `IUMSCompletionList` a un programador de subprocesos UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parámetros

*pCompletionList*<br/>
La interfaz de la lista de finalización del programador. Hay una sola lista por programador.

### <a name="remarks"></a>Observaciones

El Administrador de recursos invocará este método en un programador que lo especifique como subprocesos UMS, una vez que el programador haya solicitado una asignación inicial de recursos. Scheduler puede utilizar la interfaz `IUMSCompletionList` para determinar cuándo se han desbloqueado los proxies de subproceso UMS. Solo es válido para tener acceso a esta interfaz desde un proxy del subproceso que se ejecuta en una raíz del procesador virtual asignada al programador UMS.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Policyelementkey (](concurrency-namespace-enums.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IUMSCompletionList (estructura)](iumscompletionlist-structure.md)<br/>
[IResourceManager (estructura)](iresourcemanager-structure.md)
