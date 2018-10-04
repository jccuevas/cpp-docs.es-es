---
title: CriticalSection (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 67ca6e8eab90e1e97a3ab8aacd46616dbcbf2d0e
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234728"
---
# <a name="criticalsection-class"></a>CriticalSection (clase)

Representa un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```cpp
class CriticalSection;
```

## <a name="members"></a>Miembros

### <a name="constructor"></a>Constructor

nombre                                                        | Descripción
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection](#criticalsection)        | Inicializa un objeto de sincronización que es similar a un objeto de exclusión mutua, pero se puede usar solo los subprocesos de un único proceso.
[CriticalSection:: ~ CriticalSection](#tilde-criticalsection) | Desinicializa y destruye actual `CriticalSection` objeto.

### <a name="public-methods"></a>Métodos públicos

Name                                 | Descripción
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection](#isvalid) | Indica si la sección crítica actual es válida.
[CriticalSection](#lock)       | Espera a que la propiedad del objeto especificado de sección crítica. La función devuelve cuando el subproceso de llamada se concede la propiedad.
[TryLock](#trylock) | Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.

### <a name="protected-data-members"></a>Miembros de datos protegidos

nombre                        | Descripción
--------------------------- | ----------------------------------------
[Cs_](#cs) | Declara a un miembro de datos de la sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="tilde-criticalsection"></a>CriticalSection:: ~ CriticalSection

Desinicializa y destruye actual `CriticalSection` objeto.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsection"></a>CriticalSection

Inicializa un objeto de sincronización que es similar a un objeto de exclusión mutua, pero se puede usar solo los subprocesos de un único proceso.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parámetros

*SpinCount*<br/>
El recuento circular para el objeto de sección crítica. El valor predeterminado es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de las secciones críticas y spincounts, consulte el `InitializeCriticalSectionAndSpinCount` funcionando en la `Synchronization` sección de la documentación de API de Windows.

## <a name="cs"></a>Cs_

Declara a un miembro de datos de la sección crítica.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Comentarios

Este miembro de datos está protegida.

## <a name="isvalid"></a>CriticalSection

Indica si la sección crítica actual es válida.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

De forma predeterminada, siempre devuelve `true`.

## <a name="lock"></a>CriticalSection

Espera a que la propiedad del objeto especificado de sección crítica. La función devuelve cuando el subproceso de llamada se concede la propiedad.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*CS*<br/>
Un objeto de sección crítica especificado por el usuario.

### <a name="return-value"></a>Valor devuelto

Un objeto de bloqueo que puede usarse para desbloquear la sección crítica actual.

### <a name="remarks"></a>Comentarios

La primera `Lock` el objeto de sección crítica actual afecta a la función. El segundo `Lock` función afecta a una sección crítica especificado por el usuario.

## <a name="trylock"></a>TryLock

Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*CS*<br/>
Un objeto de sección crítica especificado por el usuario.

### <a name="return-value"></a>Valor devuelto

Un valor distinto de cero si la sección crítica está escrita correctamente o el subproceso actual ya posee la sección crítica. Cero si otro subproceso ya posee la sección crítica.

### <a name="remarks"></a>Comentarios

La primera `TryLock` el objeto de sección crítica actual afecta a la función. El segundo `TryLock` función afecta a una sección crítica especificado por el usuario.
