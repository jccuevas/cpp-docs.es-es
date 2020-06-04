---
title: IUMSScheduler (Estructura)
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 70954906122c048e5199a801632626d35a8e3f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368095"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler (Estructura)

Una interfaz a una abstracción de un programador de trabajo que desea que el Administrador de recursos del runtime de simultaneidad controle los subprocesos programables de modo de usuario (UMS). El Administrador de recursos usa esta interfaz para comunicarse con los programadores de subprocesos UMS. La interfaz `IUMSScheduler` hereda de la interfaz `IScheduler` .

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Asigna una `IUMSCompletionList` interfaz a un programador de subprocesos UMS.|

## <a name="remarks"></a>Observaciones

Si va a implementar un programador personalizado que se comunica con Resource Manager y desea que los subprocesos UMS se `IUMSScheduler` entreguen al programador en lugar de subprocesos Win32 normales, debe proporcionar una implementación de la interfaz. Además, debe establecer el valor de `SchedulerKind` directiva `UmsThreadDefault`para que la clave de directiva del programador sea . Si la política especifica el `IScheduler` subproceso UMS, la interfaz que se pasa como parámetro `IUMSScheduler` al método [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) debe ser una interfaz.

Resource Manager puede entregar subprocesos UMS solo en sistemas operativos que tienen la característica UMS. Los sistemas operativos de 64 bits con versión Windows 7 y superior admiten subprocesos UMS. Si crea una directiva `SchedulerKind` de programador con `UmsThreadDefault` la clave establecida en el valor y `SchedulerKind` la plataforma subyacente no admite `ThreadScheduler`UMS, el valor de la clave de esa directiva se cambiará al valor . Siempre debe leer este valor de directiva antes de esperar recibir subprocesos UMS.

La `IUMSScheduler` interfaz es un extremo de un canal bidireccional de comunicación entre un programador y resource Manager. El otro extremo se `IResourceManager` representa `ISchedulerProxy` mediante las interfaces y, que el Administrador de recursos implementa.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>Método IUMSScheduler::SetCompletionList

Asigna una `IUMSCompletionList` interfaz a un programador de subprocesos UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parámetros

*pCompletionList*<br/>
La interfaz de lista de finalización para el programador. Hay una sola lista por programador.

### <a name="remarks"></a>Observaciones

Resource Manager invocará este método en un programador que especifique que desea subprocesos UMS, después de que el programador haya solicitado una asignación inicial de recursos. El programador puede `IUMSCompletionList` usar la interfaz para determinar cuándo se han desbloqueado los servidores proxy de subprocesos de UMS. Solo es válido tener acceso a esta interfaz desde un proxy de subproceso que se ejecuta en una raíz de procesador virtual asignada al programador de UMS.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IUMSCompletionList (Estructura)](iumscompletionlist-structure.md)<br/>
[IResourceManager (Estructura)](iresourcemanager-structure.md)
