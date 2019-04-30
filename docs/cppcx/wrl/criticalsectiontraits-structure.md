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
ms.openlocfilehash: ce904ecbd9a5855c63fd43f07f88c215cef544ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398607"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (estructura)

Se especializa un `CriticalSection` objeto sea compatible con una sección crítica no válida o una función para liberar una sección crítica.

## <a name="syntax"></a>Sintaxis

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name   | Descripción
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | Un `typedef` que define un puntero a una sección crítica. `Type` se define como `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>Métodos públicos

Name                                                       | Descripción
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Se especializa un `CriticalSection` plantilla para que la plantilla no siempre es válida.
[CriticalSectionTraits::Unlock](#unlock)                   | Se especializa un `CriticalSection` plantilla, por lo que admite liberar la propiedad del objeto especificado de sección crítica.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CriticalSectionTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Se especializa un `CriticalSection` plantilla para que la plantilla no siempre es válida.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve un puntero a una sección crítica no válida.

### <a name="remarks"></a>Comentarios

El `Type` modificador se define como `typedef CRITICAL_SECTION* Type;`.

## <a name="unlock"></a>CriticalSectionTraits::Unlock

Se especializa un `CriticalSection` plantilla, por lo que admite liberar la propiedad del objeto especificado de sección crítica.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parámetros

*cs*<br/>
Un puntero a un objeto de sección crítica.

### <a name="remarks"></a>Comentarios

El `Type` modificador se define como `typedef CRITICAL_SECTION* Type;`.

Para obtener más información, consulte **LeaveCriticalSection función** en el **funciones de sincronización** sección de la documentación de API de Windows.
