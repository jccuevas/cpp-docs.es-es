---
title: invalid_oversubscribe_operation (clase)
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 7a879fc2da2f963cd4b5ea5fcd7e9506f86ce051
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140833"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation (clase)

Esta clase describe una excepción que se produce cuando se llama al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en **false** sin una llamada anterior al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en **true**.

## <a name="syntax"></a>Sintaxis

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Sobrecargado. Construye un objeto `invalid_oversubscribe_operation`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>invalid_oversubscribe_operation

Construye un objeto `invalid_oversubscribe_operation`.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
