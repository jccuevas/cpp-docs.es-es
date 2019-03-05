---
title: default_scheduler_exists (Clase)
ms.date: 11/04/2016
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
ms.openlocfilehash: 326a2dfc6837665adb4d46a6aaa8780052ad2b22
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275300"
---
# <a name="defaultschedulerexists-class"></a>default_scheduler_exists (Clase)

Esta clase describe una excepción que se produce cuando se llama al método `Scheduler::SetDefaultSchedulerPolicy` cuando un programador predeterminado ya existe dentro del proceso.

## <a name="syntax"></a>Sintaxis

```
class default_scheduler_exists : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[default_scheduler_exists](#ctor)|Sobrecargado. Construye un objeto `default_scheduler_exists`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`default_scheduler_exists`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> default_scheduler_exists

Construye un objeto `default_scheduler_exists`.

```
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
