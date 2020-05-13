---
title: Event (clase) (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 85b4c2d1f1a27e90a65e47aa749e079f4aa08739
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371521"
---
# <a name="event-class-wrl"></a>Event (clase) (WRL)

Representa un evento.

## <a name="syntax"></a>Sintaxis

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                   | Descripción
---------------------- | ------------------------------------------------
[Evento::Evento](#event) | Inicializa una nueva instancia de la clase `Event`.

### <a name="public-operators"></a>Operadores públicos

Nombre                                 | Descripción
------------------------------------ | ------------------------------------------------------------------------
[Evento::operador ?](#operator-assign) | Asigna la referencia `Event` especificada a `Event` la instancia actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HandleT`

`Event`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="eventevent"></a><a name="event"></a>Evento::Evento

Inicializa una nueva instancia de la clase `Event`.

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Identificador para un evento. De forma *h* predeterminada, h `nullptr`se inicializa en .

## <a name="eventoperator"></a><a name="operator-assign"></a>Evento::operador ?

Asigna la referencia `Event` especificada a `Event` la instancia actual.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Una referencia rvalue `Event` a una instancia.

### <a name="return-value"></a>Valor devuelto

Un puntero a `Event` la instancia actual.
