---
title: task_canceled (Clase)
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: caef1c62ff09ffb76f74d4a1453e9d59dcb7d45b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385250"
---
# <a name="taskcanceled-class"></a>task_canceled (Clase)

Esta clase describe una excepción producida por la capa de tareas de PPL para obligar a que se cancele la tarea actual. También se produce por la `get()` método [tarea](/visualstudio/extensibility/debugger/task-class-internal-members), para una tarea cancelada.

## <a name="syntax"></a>Sintaxis

```
class task_canceled : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[task_canceled](#ctor)|Sobrecargado. Construye un objeto `task_canceled`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`task_canceled`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> task_canceled)

Construye un objeto `task_canceled`.

```
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
