---
title: IUMSCompletionList (Estructura)
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: c388cc98aedbd35b2d0e00a4653a85a47abcb838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368121"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList (Estructura)

Representa una lista de finalización UMS. Cuando se bloquea un subproceso UMS, el contexto de programación designado del programador se envía de forma que se puede tomar una decisión sobre qué programar en la raíz del procesador virtual subyacente mientras se bloquea el subproceso original. Cuando el subproceso original se desbloquea, el sistema operativo lo pone en cola de la lista de finalización, que es accesible a través de esta interfaz. El programador puede consultar la lista de finalización en el contexto de programación designado o en cualquier otro lugar que busca trabajo.

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|Recupera una cadena `IUMSUnblockNotification` de interfaces que representan contextos de ejecución cuyos proxies de subproceso sasociados se han desbloqueado desde la última vez que se invocó este método.|

## <a name="remarks"></a>Observaciones

Un programador debe tener un cuidado adicional sobre qué acciones se realizan después de utilizar esta interfaz para quitar los elementos de la lista de finalización. Los elementos deben colocarse en la lista de contextos que se pueden ejecutar del programador y ser generalmente accesibles tan pronto como sea posible. Es totalmente posible que uno de los elementos en cola haya recibido la propiedad de un bloqueo arbitrario. El programador no puede realizar ninguna llamada de función arbitraria que pueda bloquear entre la llamada a los elementos de la cola y la colocación de esos elementos en una lista a la que se puede tener acceso generalmente desde el programador.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUMSCompletionList`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>Método IUMSCompletionList::GetUnblockNotifications

Recupera una cadena `IUMSUnblockNotification` de interfaces que representan contextos de ejecución cuyos proxies de subproceso sasociados se han desbloqueado desde la última vez que se invocó este método.

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Valor devuelto

Una cadena `IUMSUnblockNotification` de interfaces.

### <a name="remarks"></a>Observaciones

Las notificaciones devueltas no son válidas una vez que se reprograman los contextos de ejecución.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification (estructura)](iumsunblocknotification-structure.md)
