---
title: CriticalSectionTraits (estructura)
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: 05c93bf6a2765bd11489075067c627ab3c3ab691
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372577"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (estructura)

Especializa un `CriticalSection` objeto para admitir una sección crítica no válida o una función para liberar una sección crítica.

## <a name="syntax"></a>Sintaxis

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre   | Descripción
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A `typedef` que define un puntero a una sección crítica. `Type` se define como `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                                       | Descripción
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Especializa una `CriticalSection` plantilla para que la plantilla siempre no sea válida.
[CriticalSectionTraits::Unlock](#unlock)                   | Especializa una `CriticalSection` plantilla para que admita liberar la propiedad del objeto de sección crítica especificado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CriticalSectionTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Especializa una `CriticalSection` plantilla para que la plantilla siempre no sea válida.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve un puntero a una sección crítica no válida.

### <a name="remarks"></a>Observaciones

El `Type` modificador se `typedef CRITICAL_SECTION* Type;`define como .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits::Unlock

Especializa una `CriticalSection` plantilla para que admita liberar la propiedad del objeto de sección crítica especificado.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
Puntero a un objeto de sección crítica.

### <a name="remarks"></a>Observaciones

El `Type` modificador se `typedef CRITICAL_SECTION* Type;`define como .

Para obtener más información, consulte **La función LeaveCriticalSection** en la sección Funciones de **sincronización** de la documentación de la API de Windows.
