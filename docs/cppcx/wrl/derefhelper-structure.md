---
title: DerefHelper (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 43453d3162de697fa1cfcf0581953c91bbe3934f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214050"
---
# <a name="derefhelper-structure"></a>DerefHelper (estructura)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Parámetro de plantilla.

## <a name="remarks"></a>Observaciones

Representa un puntero desreferenciado al parámetro de plantilla `T*`.

**Derefhelper (** se utiliza en una expresión como: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`DerefType`|Identificador del parámetro de plantilla desreferenciado `T*`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`DerefHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** Async. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
