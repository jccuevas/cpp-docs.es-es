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
ms.openlocfilehash: cdec425e317585abbd9730447e2c4fbb19b8250a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398776"
---
# <a name="boolstruct-structure"></a>BoolStruct (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Comentarios

El `BoolStruct` estructura define si un `ComPtr` administra la duración del objeto de una interfaz. `BoolStruct` se usa internamente el [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) operador.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

Name                          | Descripción
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Member](#member) | Especifica que un [ComPtr](comptr-class.md) es o no, es administrar la vigencia del objeto de una interfaz.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BoolStruct`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="member"></a>BoolStruct::Member

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
int Member;
```

### <a name="remarks"></a>Comentarios

Especifica que un [ComPtr](comptr-class.md) es o no, es administrar la vigencia del objeto de una interfaz.
