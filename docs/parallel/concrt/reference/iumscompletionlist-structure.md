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
ms.openlocfilehash: ec3c38ee609dfa7aec8d688269f1183d307be5b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438212"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList (Estructura)

Representa una lista de finalización UMS. Cuando se bloquea un subproceso UMS, el contexto de programación designado del programador se envía de forma que se puede tomar una decisión sobre qué programar en la raíz del procesador virtual subyacente mientras se bloquea el subproceso original. Cuando el subproceso original se desbloquea, el sistema operativo lo pone en cola de la lista de finalización, que es accesible a través de esta interfaz. El programador puede consultar la lista de finalización en el contexto de programación designado o en cualquier otro lugar que busca trabajo.

## <a name="syntax"></a>Sintaxis

```
struct IUMSCompletionList;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IUMSCompletionList:: GetUnblockNotifications](#getunblocknotifications)|Recupera una cadena de `IUMSUnblockNotification` interfaces que representan los contextos de ejecución cuyo subproceso asociado han desbloqueado los servidores proxy desde la última vez este método se invocó.|

## <a name="remarks"></a>Comentarios

Un programador debe ser extraordinariamente cuidadoso sobre qué acciones se deben realizar después de usar esta interfaz para quitar elementos de la lista de finalización de la cola. Los elementos se deben colocar en la lista del programador de contextos ejecutables y ser accesibles a nivel general tan pronto como sea posible. Es perfectamente posible que uno de los elementos quitados de la cola se ha concedido la propiedad de un bloqueo arbitrario. El programador no puede realizar ninguna llamada de función arbitraria que se puedan bloquear entre la llamada a quitar elementos de la cola y la colocación de los elementos en una lista que se puede acceder con carácter general desde dentro del programador.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUMSCompletionList`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="getunblocknotifications"></a>  IUMSCompletionList:: GetUnblockNotifications (método)

Recupera una cadena de `IUMSUnblockNotification` interfaces que representan los contextos de ejecución cuyo subproceso asociado han desbloqueado los servidores proxy desde la última vez este método se invocó.

```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>Valor devuelto

Una cadena de `IUMSUnblockNotification` interfaces.

### <a name="remarks"></a>Comentarios

Las notificaciones devueltas no son válidas una vez que se vuelven a programar los contextos de ejecución.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification (estructura)](iumsunblocknotification-structure.md)
