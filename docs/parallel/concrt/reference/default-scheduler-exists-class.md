---
title: default_scheduler_exists (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists
- CONCRT/concurrency::default_scheduler_exists::default_scheduler_exists
dev_langs:
- C++
helpviewer_keywords:
- default_scheduler_exists class
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a72365cf44c1d1ac92dfc4acde378567668ebdb8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394896"
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

##  <a name="ctor"></a> default_scheduler_exists)

Construye un objeto `default_scheduler_exists`.

```
explicit _CRTIMP default_scheduler_exists(_In_z_ const char* _Message) throw();

default_scheduler_exists() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
