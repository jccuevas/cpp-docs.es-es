---
title: DerefHelper (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 96b7e83a854765fb872b87d062928311731cfd26
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032016"
---
# <a name="derefhelper-structure"></a>DerefHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Un parámetro de plantilla.

## <a name="remarks"></a>Comentarios

Representa un puntero sin referencia a la `T*` parámetro de plantilla.

**DerefHelper** se utiliza en una expresión como: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`DerefType`|Identificador del parámetro de plantilla desreferenciado `T*`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DerefHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (Espacio de nombres)](microsoft-wrl-details-namespace.md)