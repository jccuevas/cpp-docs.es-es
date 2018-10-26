---
title: Clase de eventos (WRL) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7fce42093eb5d5c9eede67699b58124218d924d4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075468"
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
[Event:: Event](#event) | Inicializa una nueva instancia de la clase `Event`.

### <a name="public-operators"></a>Operadores públicos

Name                                 | Descripción
------------------------------------ | ------------------------------------------------------------------------
[Event:: operator =](#operator-assign) | Asigna especificado `Event` referencia a la actual `Event` instancia.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HandleT`

`Event`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="event"></a>Event:: Event

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

## <a name="operator-assign"></a>Event:: operator =

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
