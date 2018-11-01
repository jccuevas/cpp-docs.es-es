---
title: improper_scheduler_detach (Clase)
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
ms.openlocfilehash: b2fc90656051be62528d0aac600fad67485c81f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643292"
---
# <a name="improperschedulerdetach-class"></a>improper_scheduler_detach (Clase)

Esta clase describe una excepción que se produce cuando se llama al método `CurrentScheduler::Detach` en un contexto que no se ha adjuntado a ningún programador mediante el método `Attach` de un objeto `Scheduler`.

## <a name="syntax"></a>Sintaxis

```
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|Sobrecargado. Construye un objeto `improper_scheduler_detach`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> improper_scheduler_detach)

Construye un objeto `improper_scheduler_detach`.

```
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>Parámetros

*_Cuerpo*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)
