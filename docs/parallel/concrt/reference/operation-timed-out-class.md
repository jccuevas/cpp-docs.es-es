---
title: operation_timed_out (clase)
ms.date: 11/04/2016
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
ms.openlocfilehash: 7a2513d30aa68798707f3bb16318db9b594b9e16
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138874"
---
# <a name="operation_timed_out-class"></a>operation_timed_out (clase)

Esta clase describe una excepción que se produce cuando una operación ha agotado su tiempo de espera.

## <a name="syntax"></a>Sintaxis

```cpp
class operation_timed_out : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operation_timed_out](#ctor)|Sobrecargado. Construye un objeto `operation_timed_out`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`operation_timed_out`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>operation_timed_out

Construye un objeto `operation_timed_out`.

```cpp
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
