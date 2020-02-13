---
title: nested_scheduler_missing_detach (clase)
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: 8c9553b036890c4ce28f1060bfe2f58ee1904935
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138866"
---
# <a name="nested_scheduler_missing_detach-class"></a>nested_scheduler_missing_detach (clase)

Esta clase describe una excepción que se produce cuando el runtime de simultaneidad detecta que se dejó de llamar al método `CurrentScheduler::Detach` en un contexto adjunto a un segundo programador mediante el método `Attach` del objeto `Scheduler`.

## <a name="syntax"></a>Sintaxis

```cpp
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Sobrecargado. Construye un objeto `nested_scheduler_missing_detach`.|

## <a name="remarks"></a>Observaciones

Esta excepción solo se produce cuando se anida un programador dentro de otro llamando al método `Attach` de un objeto `Scheduler` en un contexto que ya es propiedad o se adjunta a otro programador. El Runtime de simultaneidad produce esta excepción de forma oportunista cuando puede detectar el escenario como ayuda para localizar el problema. No todas las instancias de sin tener que llamar al método `CurrentScheduler::Detach` se garantiza que produzca esta excepción.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>nested_scheduler_missing_detach

Construye un objeto `nested_scheduler_missing_detach`.

```cpp
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)
