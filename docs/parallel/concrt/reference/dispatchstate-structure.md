---
title: DispatchState (estructura)
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 69e00893373ccca6e2ed676fbb7f5a109c49efdf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143044"
---
# <a name="dispatchstate-structure"></a>DispatchState (estructura)

La estructura `DispatchState` se usa para transferir el estado al método `IExecutionContext::Dispatch`. Describe las circunstancias bajo las que el método `Dispatch` se invoca en una interfaz `IExecutionContext`.

## <a name="syntax"></a>Sintaxis

```cpp
struct DispatchState;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Dispatchstate (::D ispatchState](#ctor)|Construye un nuevo objeto `DispatchState`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Dispatchstate (:: m_dispatchStateSize](#m_dispatchstatesize)|Tamaño de esta estructura, que se usa para el control de versiones.|
|[Dispatchstate (:: m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Indica si este contexto ha entrado en el método `Dispatch` porque el contexto anterior se bloqueó de forma asincrónica. Solo se utiliza en el contexto de programación UMS y se establece en el valor `0` para el resto de contextos de ejecución.|
|[Dispatchstate (:: m_reserved](#m_reserved)|Bits reservados para el paso futuro de la información.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DispatchState`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>Dispatchstate (::D constructor de ispatchState

Construye un nuevo objeto `DispatchState`.

```cpp
DispatchState();
```

## <a name="m_dispatchstatesize"></a>Miembro de datos Dispatchstate (:: m_dispatchStateSize

Tamaño de esta estructura, que se usa para el control de versiones.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="m_fispreviouscontextasynchronouslyblocked"></a>Miembro de datos Dispatchstate (:: m_fIsPreviousContextAsynchronouslyBlocked

Indica si este contexto ha entrado en el método `Dispatch` porque el contexto anterior se bloqueó de forma asincrónica. Solo se utiliza en el contexto de programación UMS y se establece en el valor `0` para el resto de contextos de ejecución.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="m_reserved"></a>Miembro de datos Dispatchstate (:: m_reserved

Bits reservados para el paso futuro de la información.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
