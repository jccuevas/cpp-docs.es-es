---
title: CriticalSection (clase)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: 5deb89e795d1886ca316886ae1ea260ce1f36fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372586"
---
# <a name="criticalsection-class"></a>CriticalSection (clase)

Representa un objeto de sección crítico.

## <a name="syntax"></a>Sintaxis

```cpp
class CriticalSection;
```

## <a name="members"></a>Miembros

### <a name="constructor"></a>Constructor

Nombre                                                        | Descripción
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::CriticalSection](#criticalsection)        | Inicializa un objeto de sincronización que es similar a un objeto mutex, pero solo los subprocesos de un único proceso pueden usarlo.
[CriticalSection::-CriticalSection](#tilde-criticalsection) | Desinicializa y destruye `CriticalSection` el objeto actual.

### <a name="public-methods"></a>Métodos públicos

Nombre                                 | Descripción
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Indica si la sección crítica actual es válida.
[CriticalSection::Bloqueo](#lock)       | Espera la propiedad del objeto de sección crítica especificado. La función devuelve cuando se concede la propiedad al subproceso que realiza la llamada.
[CriticalSection::TryLock](#trylock) | Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso que realiza la llamada toma la propiedad de la sección crítica.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                        | Descripción
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Declara un miembro de datos de sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection::-CriticalSection

Desinicializa y destruye `CriticalSection` el objeto actual.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection::CriticalSection

Inicializa un objeto de sincronización que es similar a un objeto mutex, pero solo los subprocesos de un único proceso pueden usarlo.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parámetros

*spincount*<br/>
El recuento de giros para el objeto de sección crítica. El valor predeterminado es 0.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de las `InitializeCriticalSectionAndSpinCount` secciones `Synchronization` críticas y los espincounts, consulte la función en la sección de la documenation de la API de Windows.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection::cs_

Declara un miembro de datos de sección crítica.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Observaciones

Este miembro de datos está protegido.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection::IsValid

Indica si la sección crítica actual es válida.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

De forma predeterminada, siempre devuelve **true**.

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection::Bloqueo

Espera la propiedad del objeto de sección crítica especificado. La función devuelve cuando se concede la propiedad al subproceso que realiza la llamada.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
Objeto de sección crítica especificado por el usuario.

### <a name="return-value"></a>Valor devuelto

Objeto de bloqueo que se puede utilizar para desbloquear la sección crítica actual.

### <a name="remarks"></a>Observaciones

La `Lock` primera función afecta al objeto de sección crítica actual. La `Lock` segunda función afecta a una sección crítica especificada por el usuario.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection::TryLock

Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso que realiza la llamada toma la propiedad de la sección crítica.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
Objeto de sección crítica especificado por el usuario.

### <a name="return-value"></a>Valor devuelto

Un valor distinto de cero si la sección crítica se ha introducido correctamente o el subproceso actual ya posee la sección crítica. Cero si otro subproceso ya posee la sección crítica.

### <a name="remarks"></a>Observaciones

La `TryLock` primera función afecta al objeto de sección crítica actual. La `TryLock` segunda función afecta a una sección crítica especificada por el usuario.
