---
title: task_canceled (clase)
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: b1436f921343843ee2b50888f00b6d470e513329
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142603"
---
# <a name="task_canceled-class"></a>task_canceled (clase)

Esta clase describe una excepción producida por la capa de tareas de PPL para obligar a que se cancele la tarea actual. También lo inicia el método `get()` en la [tarea](/visualstudio/extensibility/debugger/task-class-internal-members), para una tarea cancelada.

## <a name="syntax"></a>Sintaxis

```cpp
class task_canceled : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[task_canceled](#ctor)|Sobrecargado. Construye un objeto `task_canceled`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`task_canceled`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>task_canceled

Construye un objeto `task_canceled`.

```cpp
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
