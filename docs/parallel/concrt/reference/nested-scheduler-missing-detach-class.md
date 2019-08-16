---
title: nested_scheduler_missing_detach (Clase)
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: db51f7b083cc0cbd9337fbbe5c672d190208f328
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394395"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach (Clase)

Esta clase describe una excepción que se produce cuando el runtime de simultaneidad detecta que se dejó de llamar al método `CurrentScheduler::Detach` en un contexto adjunto a un segundo programador mediante el método `Attach` del objeto `Scheduler`.

## <a name="syntax"></a>Sintaxis

```
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Sobrecargado. Construye un objeto `nested_scheduler_missing_detach`.|

## <a name="remarks"></a>Comentarios

Esta excepción se produce únicamente cuando se anida un programador dentro de otra mediante una llamada a la `Attach` método de un `Scheduler` objeto en un contexto que ya es propiedad o se adjunta a otro programador. El Runtime de simultaneidad produce esta excepción según la ocasión cuando puede detectar el escenario como una ayuda para localizar el problema. No todas las instancias de olvidarse de llamar a la `CurrentScheduler::Detach` se garantiza que el método va a producir esta excepción.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> nested_scheduler_missing_detach

Construye un objeto `nested_scheduler_missing_detach`.

```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)
