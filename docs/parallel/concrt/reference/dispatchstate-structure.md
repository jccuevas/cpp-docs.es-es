---
title: DispatchState (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs:
- C++
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cb60a183497942d7a8bea6a333d2dea62d8e2b4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448082"
---
# <a name="dispatchstate-structure"></a>DispatchState (Estructura)

La estructura `DispatchState` se usa para transferir el estado al método `IExecutionContext::Dispatch`. Describe las circunstancias bajo las que el método `Dispatch` se invoca en una interfaz `IExecutionContext`.

## <a name="syntax"></a>Sintaxis

```
struct DispatchState;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[DispatchState:: DispatchState](#ctor)|Construye un nuevo objeto `DispatchState`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Tamaño de esta estructura, que se usa para el control de versiones.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Indica si este contexto ha entrado la `Dispatch` método porque el contexto anterior se bloqueó de forma asincrónica. Esto sólo se utiliza en el contexto de programación UMS y se establece en el valor `0` para todos los otros contextos de ejecución.|
|[DispatchState::m_reserved](#m_reserved)|Bits reservados para pasar información del futuro.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DispatchState`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a>  DispatchState:: DispatchState Constructor

Construye un nuevo objeto `DispatchState`.

```
DispatchState();
```

##  <a name="m_dispatchstatesize"></a>  Miembro de datos M_dispatchstatesize

Tamaño de esta estructura, que se usa para el control de versiones.

```
unsigned long m_dispatchStateSize;
```

##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  DispatchState:: M_fispreviouscontextasynchronouslyblocked miembro de datos

Indica si este contexto ha entrado la `Dispatch` método porque el contexto anterior se bloqueó de forma asincrónica. Esto sólo se utiliza en el contexto de programación UMS y se establece en el valor `0` para todos los otros contextos de ejecución.

```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

##  <a name="m_reserved"></a>  DispatchState:: M_reserved miembro de datos

Bits reservados para pasar información del futuro.

```
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
