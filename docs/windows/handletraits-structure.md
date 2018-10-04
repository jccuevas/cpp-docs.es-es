---
title: HANDLETraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33181b2cf477c3f753eacf63110a426b36e62b31
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235274"
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
[Handletraits](#close)                     | Cierra el identificador especificado.
[Handletraits](#getinvalidvalue) | Representa un identificador no válido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLETraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="close"></a>Handletraits

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

`true` Si administrar *h* cerrado correctamente; en caso contrario, `false`.

## <a name="getinvalidvalue"></a>Handletraits

Representa un identificador no válido.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE se define por Windows).
