---
title: DontUseNewUseMake (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c1f3a57401a3ab2efd45cab2dace127010c24e6
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235287"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Comentarios

Impide el uso de operador `new` en `RuntimeClass`. Por lo tanto, debe usar el [función](../windows/make-function.md) en su lugar.

## <a name="members"></a>Miembros

### <a name="public-operators"></a>Operadores públicos

Name                                             | Descripción
------------------------------------------------ | ---------------------------------------------------------------------------
[Dontusenewusemake nuevo](#operator-new) | Las sobrecargas de operador `new` e impide que se usa en `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DontUseNewUseMake`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="operator-new"></a>Dontusenewusemake nuevo

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parámetros

*__unnamed0*<br/>
Un parámetro sin nombre que especifica el número de bytes de memoria para asignar.

*selección de ubicación*<br/>
El tipo de asignación.

### <a name="return-value"></a>Valor devuelto

Proporciona una forma de pasar argumentos adicionales si se sobrecarga el operador `new`.

### <a name="remarks"></a>Comentarios

Las sobrecargas de operador `new` e impide que se usa en `RuntimeClass`.
