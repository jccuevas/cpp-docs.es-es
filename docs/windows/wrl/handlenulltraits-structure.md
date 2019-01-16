---
title: HANDLENullTraits (estructura)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: d70425f414b998eb67e3937c2c126dd3eda0c00d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337665"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits (estructura)

Define las características comunes de un identificador sin inicializar.

## <a name="syntax"></a>Sintaxis

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name   | Descripción
------ | ---------------------
`Type` | Un sinónimo de identificador.

### <a name="public-methods"></a>Métodos públicos

Name                                                  | Descripción
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Close](#close)                     | Cierra el identificador especificado.
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | Representa un identificador no válido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLENullTraits::Close

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

## <a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

Representa un identificador no válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve `nullptr`.
