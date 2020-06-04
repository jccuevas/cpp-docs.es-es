---
title: improper_lock (clase)
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: 886444f3e856234be010715a8ee0c707cf919bb4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142397"
---
# <a name="improper_lock-class"></a>improper_lock (clase)

Esta clase describe una excepción que se produce cuando se realiza un bloqueo de forma incorrecta.

## <a name="syntax"></a>Sintaxis

```cpp
class improper_lock : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[improper_lock](#ctor)|Sobrecargado. Construye un objeto `improper_lock exception`.|

## <a name="remarks"></a>Observaciones

Normalmente, esta excepción se produce cuando se realiza un intento de adquirir un bloqueo no reentrante de forma recursiva en el mismo contexto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`exception`

`improper_lock`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>improper_lock

Construye un objeto `improper_lock exception`.

```cpp
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>Parámetros

*_Message*<br/>
Mensaje descriptivo del error.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[critical_section (clase)](critical-section-class.md)<br/>
[reader_writer_lock (clase)](reader-writer-lock-class.md)
