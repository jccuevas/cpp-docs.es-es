---
title: IUMSUnblockNotification (estructura)
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: d4fd95b1f11ed6edac26cb03e41e8b650acfafa3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139983"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification (estructura)

Representa una notificación del Administrador de recursos indicando que un proxy del subproceso que había bloqueado y desencadenado un valor devuelto al contexto de programación designado del programador, se ha desbloqueado y está listo para su programación. Esta interfaz no es válida una vez que el contexto de ejecución asociado del proxy del subproceso, devuelto desde el método `GetContext`, se vuelve a programar.

## <a name="syntax"></a>Sintaxis

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IUMSUnblockNotification (:: GetContext](#getcontext)|Devuelve la interfaz de `IExecutionContext` para el contexto de ejecución asociado al proxy del subproceso que se ha desbloqueado. Una vez que este método devuelve y se ha vuelto a programar el contexto de ejecución subyacente a través de una llamada al método `IThreadProxy::SwitchTo`, esta interfaz ya no es válida.|
|[IUMSUnblockNotification (:: Getnextunblocknotification (](#getnextunblocknotification)|Devuelve la siguiente interfaz de `IUMSUnblockNotification` de la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUMSUnblockNotification`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="getcontext"></a>IUMSUnblockNotification (:: GetContext (método)

Devuelve la interfaz de `IExecutionContext` para el contexto de ejecución asociado al proxy del subproceso que se ha desbloqueado. Una vez que este método devuelve y se ha vuelto a programar el contexto de ejecución subyacente a través de una llamada al método `IThreadProxy::SwitchTo`, esta interfaz ya no es válida.

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IExecutionContext` para el contexto de ejecución a un proxy de subproceso que se ha desbloqueado.

## <a name="getnextunblocknotification"></a>IUMSUnblockNotification (:: Getnextunblocknotification ((método)

Devuelve la siguiente interfaz de `IUMSUnblockNotification` de la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Valor devuelto

La siguiente interfaz de `IUMSUnblockNotification` de la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)<br/>
[IUMSCompletionList (estructura)](iumscompletionlist-structure.md)
