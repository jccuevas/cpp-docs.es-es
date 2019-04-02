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
ms.openlocfilehash: dd34206741ba8fee8b283e22b6e8eefb3b3efb0e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786083"
---
# <a name="criticalsection-class"></a>CriticalSection (clase)

Representa un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```cpp
class CriticalSection;
```

## <a name="members"></a>Miembros

### <a name="constructor"></a>Constructor

Name                                                        | Descripción
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::CriticalSection](#criticalsection)        | Inicializa un objeto de sincronización que es similar a un objeto de exclusión mutua, pero se puede usar solo los subprocesos de un único proceso.
[CriticalSection::~CriticalSection](#tilde-criticalsection) | Desinicializa y destruye actual `CriticalSection` objeto.

### <a name="public-methods"></a>Métodos públicos

Name                                 | Descripción
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Indica si la sección crítica actual es válida.
[CriticalSection::Lock](#lock)       | Espera a que la propiedad del objeto especificado de sección crítica. La función devuelve cuando el subproceso de llamada se concede la propiedad.
[CriticalSection::TryLock](#trylock) | Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Name                        | Descripción
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Declara a un miembro de datos de la sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="tilde-criticalsection"></a>CriticalSection::~CriticalSection

Desinicializa y destruye actual `CriticalSection` objeto.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsection"></a>CriticalSection::CriticalSection

Inicializa un objeto de sincronización que es similar a un objeto de exclusión mutua, pero se puede usar solo los subprocesos de un único proceso.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parámetros

*spincount*<br/>
El recuento circular para el objeto de sección crítica. El valor predeterminado es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de las secciones críticas y spincounts, consulte el `InitializeCriticalSectionAndSpinCount` funcionando en la `Synchronization` sección de la documentación de API de Windows.

## <a name="cs"></a>CriticalSection::cs_

Declara a un miembro de datos de la sección crítica.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Comentarios

Este miembro de datos está protegida.

## <a name="isvalid"></a>CriticalSection::IsValid

Indica si la sección crítica actual es válida.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

De forma predeterminada, siempre devuelve **true**.

## <a name="lock"></a>CriticalSection::Lock

Espera a que la propiedad del objeto especificado de sección crítica. La función devuelve cuando el subproceso de llamada se concede la propiedad.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
Un objeto de sección crítica especificado por el usuario.

### <a name="return-value"></a>Valor devuelto

Un objeto de bloqueo que puede usarse para desbloquear la sección crítica actual.

### <a name="remarks"></a>Comentarios

La primera `Lock` el objeto de sección crítica actual afecta a la función. El segundo `Lock` función afecta a una sección crítica especificado por el usuario.

## <a name="trylock"></a>CriticalSection::TryLock

Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
Un objeto de sección crítica especificado por el usuario.

### <a name="return-value"></a>Valor devuelto

Un valor distinto de cero si la sección crítica está escrita correctamente o el subproceso actual ya posee la sección crítica. Cero si otro subproceso ya posee la sección crítica.

### <a name="remarks"></a>Comentarios

La primera `TryLock` el objeto de sección crítica actual afecta a la función. El segundo `TryLock` función afecta a una sección crítica especificado por el usuario.
