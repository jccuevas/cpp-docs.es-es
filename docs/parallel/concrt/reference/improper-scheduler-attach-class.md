---
title: improper_scheduler_attach (clase)
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach::improper_scheduler_attach
helpviewer_keywords:
- improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
ms.openlocfilehash: 85adf3f919d94a82f5a68a5cd9e5f44cdca10006
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141225"
---
# <a name="improper_scheduler_attach-class"></a>improper_scheduler_attach (clase)

Esta clase describe una excepción que se produce cuando se llama al método `Attach` en un objeto `Scheduler` que ya se ha adjuntado al contexto actual.

## <a name="syntax"></a>Sintaxis

```cpp
class improper_scheduler_attach : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[improper_scheduler_attach](#ctor)|Sobrecargado. Construye un objeto `improper_scheduler_attach`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`improper_scheduler_attach`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>improper_scheduler_attach

Construye un objeto `improper_scheduler_attach`.

```cpp
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)
