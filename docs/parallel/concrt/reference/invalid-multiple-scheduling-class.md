---
title: invalid_multiple_scheduling (clase)
ms.date: 11/04/2016
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
ms.openlocfilehash: a8b2a045ce94562dcba0019bc03aaa90c4d384a9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140905"
---
# <a name="invalid_multiple_scheduling-class"></a>invalid_multiple_scheduling (clase)

Esta clase describe una excepción que se produce cuando un objeto `task_handle` se programa varias veces mediante el método `run` de un objeto `task_group` o `structured_task_group` sin una llamada que se interponga a los métodos `wait` o `run_and_wait`.

## <a name="syntax"></a>Sintaxis

```cpp
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|Sobrecargado. Construye un objeto `invalid_multiple_scheduling`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>invalid_multiple_scheduling

Construye un objeto `invalid_multiple_scheduling`.

```cpp
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[task_handle (clase)](task-handle-class.md)<br/>
[task_group (clase)](task-group-class.md)<br/>
[run](task-group-class.md)<br/>
[currir](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group (clase)](structured-task-group-class.md)
