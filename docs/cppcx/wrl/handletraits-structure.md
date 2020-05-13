---
title: HANDLETraits (estructura)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: 604098cd3289722767117910d6e44e272dcb8b77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371446"
---
# <a name="handletraits-structure"></a>HANDLETraits (estructura)

Define las características comunes de un identificador.

## <a name="syntax"></a>Sintaxis

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre   | Descripción
------ | ---------------------
`Type` | Sinónimo de HANDLE.

### <a name="public-methods"></a>Métodos públicos

Nombre                                              | Descripción
------------------------------------------------- | -----------------------------
[HANDLETraits::Cerrar](#close)                     | Cierra el identificador especificado.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Representa un identificador no válido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLETraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits::Cerrar

Cierra el identificador especificado.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
El mango para cerrar.

### <a name="return-value"></a>Valor devuelto

**true** si el manejador *h* cerró correctamente; de lo contrario, **false**.

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Representa un identificador no válido.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE está definido por Windows.)
