---
title: invalid_scheduler_policy_value (clase)
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: 6a66b2b303a4b3b0cb8c2c7a3c515ac8cd1b33a0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142989"
---
# <a name="invalid_scheduler_policy_value-class"></a>invalid_scheduler_policy_value (clase)

Esta clase describe una excepción que se produce cuando una clave de directiva de un objeto `SchedulerPolicy` se establece en un valor no válido para esa clave.

## <a name="syntax"></a>Sintaxis

```cpp
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|Sobrecargado. Construye un objeto `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>invalid_scheduler_policy_value

Construye un objeto `invalid_scheduler_policy_value`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[SchedulerPolicy (clase)](schedulerpolicy-class.md)
