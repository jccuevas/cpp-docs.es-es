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
ms.openlocfilehash: 4dd2cde62d36c46926e703e6fb649e2ae4ef7811
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398373"
---
# <a name="handletraits-structure"></a>HANDLETraits (estructura)

Define las características comunes de un controlador.

## <a name="syntax"></a>Sintaxis

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name   | Descripción
------ | ---------------------
`Type` | Un sinónimo de identificador.

### <a name="public-methods"></a>Métodos públicos

Name                                              | Descripción
------------------------------------------------- | -----------------------------
[HANDLETraits::Close](#close)                     | Cierra el identificador especificado.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Representa un identificador no válido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLETraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLETraits::Close

Cierra el identificador especificado.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Para cerrar el identificador.

### <a name="return-value"></a>Valor devuelto

**True** si controlar *h* cerrado correctamente; en caso contrario, **false**.

## <a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Representa un identificador no válido.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Always returns INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE se define por Windows).
