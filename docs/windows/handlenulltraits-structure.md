---
title: HANDLENullTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1060d28e35a52e2a8c5c550664d36d8272628526
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161741"
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
[Handlenulltraits](#close)                     | Cierra el identificador especificado.
[Handlenulltraits](#getinvalidvalue) | Representa un identificador no válido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="close"></a>Handlenulltraits

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

## <a name="getinvalidvalue"></a>Handlenulltraits

Representa un identificador no válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve `nullptr`.
