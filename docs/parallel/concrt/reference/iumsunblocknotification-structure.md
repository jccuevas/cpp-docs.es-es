---
title: IUMSUnblockNotification (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63dcd78af0804a6921d34a35611591f044c2633f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438033"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification (Estructura)

Representa una notificación del Administrador de recursos indicando que un proxy del subproceso que había bloqueado y desencadenado un valor devuelto al contexto de programación designado del programador, se ha desbloqueado y está listo para su programación. Esta interfaz no es válida una vez que el contexto de ejecución asociado del proxy del subproceso, devuelto desde el método `GetContext`, se vuelve a programar.

## <a name="syntax"></a>Sintaxis

```
struct IUMSUnblockNotification;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IUMSUnblockNotification](#getcontext)|Devuelve el `IExecutionContext` interfaz para el contexto de ejecución asociado con el proxy del subproceso que se ha desbloqueado. Una vez que devuelve este método y el contexto de ejecución subyacente se ha reprogramado mediante una llamada a la `IThreadProxy::SwitchTo` método, esta interfaz ya no es válida.|
|[IUMSUnblockNotification:: GetNextUnblockNotification](#getnextunblocknotification)|Devuelve el siguiente `IUMSUnblockNotification` interfaz en la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUMSUnblockNotification`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="getcontext"></a>  IUMSUnblockNotification:: GetContext (método)

Devuelve el `IExecutionContext` interfaz para el contexto de ejecución asociado con el proxy del subproceso que se ha desbloqueado. Una vez que devuelve este método y el contexto de ejecución subyacente se ha reprogramado mediante una llamada a la `IThreadProxy::SwitchTo` método, esta interfaz ya no es válida.

```
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>Valor devuelto

Un `IExecutionContext` interfaz para el contexto de ejecución a un proxy del subproceso que se ha desbloqueado.

##  <a name="getnextunblocknotification"></a>  IUMSUnblockNotification:: GetNextUnblockNotification (método)

Devuelve el siguiente `IUMSUnblockNotification` interfaz en la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.

```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>Valor devuelto

La siguiente `IUMSUnblockNotification` interfaz en la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IUMSScheduler (estructura)](iumsscheduler-structure.md)<br/>
[IUMSCompletionList (estructura)](iumscompletionlist-structure.md)
