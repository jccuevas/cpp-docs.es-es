---
title: CompareStringOrdinal (Método)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: a1ac0576bdd374daa5cbd445af480e7652b61e45
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027708"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
La primera HSTRING para comparar.

*RHS*<br/>
El segundo HSTRING para comparar.

## <a name="return-value"></a>Valor devuelto

|Valor|Condición|
|-----------|---------------|
|-1|*LHS* es menor que *rhs*.|
|0|*LHS* es igual a *rhs*.|
|1|*LHS* es mayor que *rhs*.|

## <a name="remarks"></a>Comentarios

Compara dos objetos HSTRING especificados y devuelve un entero que indica su posición relativa en un criterio de ordenación.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::Details (Espacio de nombres)](microsoft-wrl-wrappers-details-namespace.md)