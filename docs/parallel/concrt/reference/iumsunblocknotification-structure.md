---
title: IUMSUnblockNotification (Estructura)
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: 0b88ddd4184e982a5e07c536efc301eaa16f4a41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368071"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification (Estructura)

Representa una notificación del Administrador de recursos indicando que un proxy del subproceso que había bloqueado y desencadenado un valor devuelto al contexto de programación designado del programador, se ha desbloqueado y está listo para su programación. Esta interfaz no es válida una vez que el contexto de ejecución asociado del proxy del subproceso, devuelto desde el método `GetContext`, se vuelve a programar.

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|Devuelve `IExecutionContext` la interfaz para el contexto de ejecución asociado con el proxy de subproceso que se ha desbloqueado. Una vez que este método devuelve y el contexto de `IThreadProxy::SwitchTo` ejecución subyacente se ha reprogramado a través de una llamada al método, esta interfaz ya no es válida.|
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|Devuelve la `IUMSUnblockNotification` siguiente interfaz de `IUMSCompletionList::GetUnblockNotifications`la cadena devuelta por el método .|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUMSUnblockNotification`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>Método IUMSUnblockNotification::GetContext

Devuelve `IExecutionContext` la interfaz para el contexto de ejecución asociado con el proxy de subproceso que se ha desbloqueado. Una vez que este método devuelve y el contexto de `IThreadProxy::SwitchTo` ejecución subyacente se ha reprogramado a través de una llamada al método, esta interfaz ya no es válida.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Valor devuelto

Una `IExecutionContext` interfaz para el contexto de ejecución a un proxy de subproceso que se ha desbloqueado.

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>Método IUMSUnblockNotification::GetNextUnblockNotification

Devuelve la `IUMSUnblockNotification` siguiente interfaz de `IUMSCompletionList::GetUnblockNotifications`la cadena devuelta por el método .

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Valor devuelto

La `IUMSUnblockNotification` siguiente interfaz de la `IUMSCompletionList::GetUnblockNotifications`cadena devuelta desde el método .

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)<br/>
[IUMSCompletionList (Estructura)](iumscompletionlist-structure.md)
