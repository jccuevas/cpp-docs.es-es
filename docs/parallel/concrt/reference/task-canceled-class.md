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
ms.openlocfilehash: b17050deacd1dee0c1b08ffbc4056e957884cd3a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617456"
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

*_Cuerpo*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
