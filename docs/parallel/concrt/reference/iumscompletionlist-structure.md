---
title: IUMSCompletionList (estructura)
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: 02382ef4606a6e73804fcbd5ce7735ecf2f0dcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140050"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList (estructura)

Representa una lista de finalización UMS. Cuando se bloquea un subproceso UMS, el contexto de programación designado del programador se envía de forma que se puede tomar una decisión sobre qué programar en la raíz del procesador virtual subyacente mientras se bloquea el subproceso original. Cuando el subproceso original se desbloquea, el sistema operativo lo pone en cola de la lista de finalización, que es accesible a través de esta interfaz. El programador puede consultar la lista de finalización en el contexto de programación designado o en cualquier otro lugar que busca trabajo.

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Iumscompletionlist (:: Getunblocknotifications (](#getunblocknotifications)|Recupera una cadena de interfaces `IUMSUnblockNotification` que representan contextos de ejecución cuyos proxies de subproceso asociados se han desbloqueado desde la última vez que se invocó este método.|

## <a name="remarks"></a>Observaciones

Un programador debe ser extraordinariamente cuidadoso con respecto a las acciones que se realizan después de usar esta interfaz para quitar elementos de la cola de la lista de finalización. Los elementos deben colocarse en la lista de contextos ejecutables del programador y ser generalmente accesibles lo antes posible. Es totalmente posible que uno de los elementos quitados de la cola tenga la propiedad de un bloqueo arbitrario. Scheduler no puede realizar llamadas a funciones arbitrarias que se puedan bloquear entre la llamada a los elementos de eliminación de la cola y la ubicación de esos elementos en una lista a la que se puede tener acceso normalmente desde dentro del programador.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUMSCompletionList`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="getunblocknotifications"></a>Iumscompletionlist (:: Getunblocknotifications ((método)

Recupera una cadena de interfaces `IUMSUnblockNotification` que representan contextos de ejecución cuyos proxies de subproceso asociados se han desbloqueado desde la última vez que se invocó este método.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Valor devuelto

Cadena de interfaces de `IUMSUnblockNotification`.

### <a name="remarks"></a>Observaciones

Las notificaciones devueltas no son válidas una vez que se vuelven a programar los contextos de ejecución.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification (estructura)](iumsunblocknotification-structure.md)
