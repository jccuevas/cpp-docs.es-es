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
ms.openlocfilehash: f377d6079017266630434ce71602a7e70e58ae21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301869"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler (Estructura)

Una interfaz a una abstracción de un programador de trabajo que desea que el Administrador de recursos del runtime de simultaneidad controle los subprocesos programables de modo de usuario (UMS). El Administrador de recursos usa esta interfaz para comunicarse con los programadores de subprocesos UMS. La interfaz `IUMSScheduler` hereda de la interfaz `IScheduler` .

## <a name="syntax"></a>Sintaxis

```
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Asigna un `IUMSCompletionList` interfaz para un programador de subprocesos UMS.|

## <a name="remarks"></a>Comentarios

Si está implementando un programador personalizado que se comunica con el Administrador de recursos, y desea que los subprocesos UMS que se va a pasar a su programador, en lugar de subprocesos Win32 normales, debe proporcionar una implementación de la `IUMSScheduler` interfaz. Además, debe establecer el valor de directiva de la clave de directiva de programador `SchedulerKind` sea `UmsThreadDefault`. Si la directiva especifica subproceso UMS, el `IScheduler` interfaz que se pasa como parámetro a la [IResourceManager:: RegisterScheduler](iresourcemanager-structure.md#registerscheduler) método debe ser un `IUMSScheduler` interfaz.

El Administrador de recursos es capaz de entregar los subprocesos UMS únicamente en sistemas operativos que tienen la característica UMS. los sistemas operativos de 64 bits con la versión de Windows 7 y versiones posteriores admiten los subprocesos UMS. Si crea una directiva de programador con el `SchedulerKind` clave se establece en el valor `UmsThreadDefault` y la plataforma subyacente no admite UMS, el valor de la `SchedulerKind` clave en esa directiva se cambiará al valor `ThreadScheduler`. Siempre debe leer volver este valor de directiva antes de esperar recibir los subprocesos UMS.

El `IUMSScheduler` interfaz es un extremo de un canal bidireccional de comunicación entre un programador y el Administrador de recursos. El otro extremo es representado por la `IResourceManager` y `ISchedulerProxy` interfaces, que se implementan mediante el Administrador de recursos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="setcompletionlist"></a>  IUMSScheduler:: SetCompletionList (método)

Asigna un `IUMSCompletionList` interfaz para un programador de subprocesos UMS.

```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parámetros

*pCompletionList*<br/>
La interfaz de la lista de finalización para el programador. Hay una sola lista por programador.

### <a name="remarks"></a>Comentarios

El Administrador de recursos invocará este método en un programador que especifica que quiere que los subprocesos UMS, después de que el programador ha solicitado una asignación inicial de los recursos. El programador puede utilizar el `IUMSCompletionList` interfaz para determinar cuándo se han desbloqueado proxy del subproceso UMS. Solo es válido para tener acceso a esta interfaz desde un proxy del subproceso que se ejecuta en una raíz del procesador virtual asignada al programador UMS.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IUMSCompletionList (estructura)](iumscompletionlist-structure.md)<br/>
[IResourceManager (estructura)](iresourcemanager-structure.md)
