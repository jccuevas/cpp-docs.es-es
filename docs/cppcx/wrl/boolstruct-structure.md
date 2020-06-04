---
title: BoolStruct (estructura)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: 4f2a5acf6edb824cff2121c1b6444181b5cfcf98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371851"
---
# <a name="boolstruct-structure"></a>BoolStruct (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Observaciones

La `BoolStruct` estructura define `ComPtr` si a está administrando la duración del objeto de una interfaz. `BoolStruct`es utilizado internamente por el operador [BoolType().](comptr-class.md#operator-microsoft-wrl-details-booltype)

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

Nombre                          | Descripción
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Miembro](#member) | Especifica que un [ComPtr](comptr-class.md) está, o no, administrar la duración del objeto de una interfaz.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BoolStruct`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="boolstructmember"></a><a name="member"></a>BoolStruct::Miembro

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
int Member;
```

### <a name="remarks"></a>Observaciones

Especifica que un [ComPtr](comptr-class.md) está, o no, administrar la duración del objeto de una interfaz.
