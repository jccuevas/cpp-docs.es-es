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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423661"
---
# <a name="boolstruct-structure"></a>BoolStruct (estructura)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Observaciones

La estructura `BoolStruct` define si un `ComPtr` está administrando la duración del objeto de una interfaz. el operador [booltype (()](comptr-class.md#operator-microsoft-wrl-details-booltype) utiliza internamente `BoolStruct`.

## <a name="members"></a>Members

### <a name="public-data-members"></a>Miembros de datos públicos

Nombre                          | Descripción
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct (:: Member](#member) | Especifica que un [ComPtr](comptr-class.md) es, o no, la administración de la duración del objeto de una interfaz.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BoolStruct`

## <a name="requirements"></a>Requisitos

**Encabezado:** Internal. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="member"></a>Boolstruct (:: Member

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

```cpp
int Member;
```

### <a name="remarks"></a>Observaciones

Especifica que un [ComPtr](comptr-class.md) es, o no, la administración de la duración del objeto de una interfaz.
