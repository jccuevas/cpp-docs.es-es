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
ms.openlocfilehash: ae67373b4f2f2d4a199b939b06e6f526f1365446
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371550"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Observaciones

Impide el `new` `RuntimeClass`uso del operador en . Por lo tanto, debe utilizar la [función Make](make-function.md) en su lugar.

## <a name="members"></a>Miembros

### <a name="public-operators"></a>Operadores públicos

Nombre                                             | Descripción
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator new](#operator-new) | Sobrecarga el `new` operador y evita `RuntimeClass`que se utilice en .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DontUseNewUseMake`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a>DontUseNewUseMake::operator new

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parámetros

*__unnamed0*<br/>
Un parámetro sin nombre que especifica el número de bytes de memoria que se van a asignar.

*Colocación*<br/>
El tipo que se va a asignar.

### <a name="return-value"></a>Valor devuelto

Proporciona una manera de pasar argumentos `new`adicionales si sobrecarga el operador .

### <a name="remarks"></a>Observaciones

Sobrecarga el `new` operador y evita `RuntimeClass`que se utilice en .
