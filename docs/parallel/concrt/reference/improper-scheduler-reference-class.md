---
title: improper_scheduler_reference (clase)
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 18536043b0d46a6f27f1e5c60778a22af82ad2d3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141108"
---
# <a name="improper_scheduler_reference-class"></a>improper_scheduler_reference (clase)

Esta clase describe una excepción que se produce cuando se llama al método `Reference` en un objeto `Scheduler` que se está cerrando, desde un contexto que no forma parte de ese programador.

## <a name="syntax"></a>Sintaxis

```cpp
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|Sobrecargado. Construye un objeto `improper_scheduler_reference`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>improper_scheduler_reference

Construye un objeto `improper_scheduler_reference`.

```cpp
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)
