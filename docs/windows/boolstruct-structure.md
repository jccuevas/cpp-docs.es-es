---
title: BoolStruct (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74a292f2253d29730e8ee9104ea81308081c0496
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234273"
---
# <a name="boolstruct-structure"></a>BoolStruct (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Comentarios

El `BoolStruct` estructura define si un `ComPtr` administra la duración del objeto de una interfaz. `BoolStruct` se usa internamente el [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operador.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

Name                          | Descripción
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct](#member) | Especifica que un [ComPtr](../windows/comptr-class.md) es o no, es administrar la vigencia del objeto de una interfaz.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BoolStruct`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="member"></a>Boolstruct

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
int Member;
```

### <a name="remarks"></a>Comentarios

Especifica que un [ComPtr](../windows/comptr-class.md) es o no, es administrar la vigencia del objeto de una interfaz.
