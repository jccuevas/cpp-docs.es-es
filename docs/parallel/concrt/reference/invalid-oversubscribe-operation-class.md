---
title: invalid_oversubscribe_operation (Clase)
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 200743d41c1c45f2a957dba0716dd7aa07e3de76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405318"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation (Clase)

Esta clase describe una excepción cuando el `Context::Oversubscribe` se llama al método con el `_BeginOversubscription` parámetro establecido en **false** sin una llamada anterior a la `Context::Oversubscribe` método con el `_BeginOversubscription` parámetro establecido en **true**.

## <a name="syntax"></a>Sintaxis

```
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Sobrecargado. Construye un objeto `invalid_oversubscribe_operation`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> invalid_oversubscribe_operation

Construye un objeto `invalid_oversubscribe_operation`.

```
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
