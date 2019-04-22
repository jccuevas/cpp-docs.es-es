---
title: Clase de eventos (WRL)
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
ms.openlocfilehash: 2d36b4fa3d1824f43e0cfafe55c439a6bdeccb6f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786011"
---
# <a name="event-class-wrl"></a>Clase de eventos (WRL)

Representa un evento.

## <a name="syntax"></a>Sintaxis

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                   | Descripción
---------------------- | ------------------------------------------------
[Event::Event](#event) | Inicializa una nueva instancia de la clase `Event`.

### <a name="public-operators"></a>Operadores públicos

Name                                 | Descripción
------------------------------------ | ------------------------------------------------------------------------
[Event::operator=](#operator-assign) | Asigna especificado `Event` referencia a la actual `Event` instancia.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HandleT`

`Event`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="event"></a>Event::Event

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

*h*<br/>
Identificador para un evento. De forma predeterminada, *h* se inicializa en `nullptr`.

## <a name="operator-assign"></a>Event::operator=

Asigna especificado `Event` referencia a la actual `Event` instancia.

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Una referencia rvalue para un `Event` instancia.

### <a name="return-value"></a>Valor devuelto

Un puntero a la actual `Event` instancia.
