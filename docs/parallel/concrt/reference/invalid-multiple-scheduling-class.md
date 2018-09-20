---
title: invalid_multiple_scheduling (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
dev_langs:
- C++
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71898449447595db5df66ce619c423d62f2410be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384926"
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling (Clase)

Esta clase describe una excepción que se produce cuando un objeto `task_handle` se programa varias veces mediante el método `run` de un objeto `task_group` o `structured_task_group` sin una llamada que se interponga a los métodos `wait` o `run_and_wait`.

## <a name="syntax"></a>Sintaxis

```
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|Sobrecargado. Construye un objeto `invalid_multiple_scheduling`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> invalid_multiple_scheduling)

Construye un objeto `invalid_multiple_scheduling`.

```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[task_handle (clase)](task-handle-class.md)<br/>
[task_group (clase)](task-group-class.md)<br/>
[run](task-group-class.md)<br/>
[Espere](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group (clase)](structured-task-group-class.md)
