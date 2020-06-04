---
title: DispatchState (Estructura)
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
ms.openlocfilehash: 2c4103f89f7fc74c5368bafac3c82685ff9b6e03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372694"
---
# <a name="dispatchstate-structure"></a>DispatchState (Estructura)

La estructura `DispatchState` se usa para transferir el estado al método `IExecutionContext::Dispatch`. Describe las circunstancias bajo las que el método `Dispatch` se invoca en una interfaz `IExecutionContext`.

## <a name="syntax"></a>Sintaxis

```cpp
struct DispatchState;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[DispatchState::DispatchState](#ctor)|Construye un nuevo objeto `DispatchState`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Tamaño de esta estructura, que se utiliza para el control de versiones.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Indica si este contexto `Dispatch` ha entrado en el método porque el contexto anterior se bloqueó de forma asincrónica. Esto solo se utiliza en el contexto de programación de UMS y se establece en el valor `0` para todos los demás contextos de ejecución.|
|[DispatchState::m_reserved](#m_reserved)|Bits reservados para la transmisión de información futura.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DispatchState`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>DispatchState::DispatchState Constructor

Construye un nuevo objeto `DispatchState`.

```cpp
DispatchState();
```

## <a name="dispatchstatem_dispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>Miembro de datos DispatchState::m_dispatchStateSize

Tamaño de esta estructura, que se utiliza para el control de versiones.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="dispatchstatem_fispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>DispatchState::m_fIsPreviousContextAsynchronouslyBlocked Miembro de datos

Indica si este contexto `Dispatch` ha entrado en el método porque el contexto anterior se bloqueó de forma asincrónica. Esto solo se utiliza en el contexto de programación de UMS y se establece en el valor `0` para todos los demás contextos de ejecución.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="dispatchstatem_reserved-data-member"></a><a name="m_reserved"></a>Miembro de datos DispatchState::m_reserved

Bits reservados para la transmisión de información futura.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
