---
title: DontUseNewUseMake (clase)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: 02420f2657c7d7d6a7a0294f0321717a3bb2b5d7
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337550"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Comentarios

Impide el uso de operador `new` en `RuntimeClass`. Por lo tanto, debe usar el [función](make-function.md) en su lugar.

## <a name="members"></a>Miembros

### <a name="public-operators"></a>Operadores públicos

Name                                             | Descripción
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator new](#operator-new) | Las sobrecargas de operador `new` e impide que se usa en `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DontUseNewUseMake`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="operator-new"></a>DontUseNewUseMake::operator new

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

*placement*<br/>
El tipo de asignación.

### <a name="return-value"></a>Valor devuelto

Proporciona una forma de pasar argumentos adicionales si se sobrecarga el operador `new`.

### <a name="remarks"></a>Comentarios

Las sobrecargas de operador `new` e impide que se usa en `RuntimeClass`.
