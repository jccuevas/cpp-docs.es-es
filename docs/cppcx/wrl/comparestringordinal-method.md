---
title: CompareStringOrdinal (Método)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: 1291084395b02602b7a3de9013df6720d2e237fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214102"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal (Método)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer HSTRING que se va a comparar.

*rhs*<br/>
Segundo HSTRING que se va a comparar.

## <a name="return-value"></a>Valor devuelto

|Value|Condición|
|-----------|---------------|
|-1|*LHS* es menor que *RHS*.|
|0|*LHS* es igual a *RHS*.|
|1|*LHS* es mayor que *RHS*.|

## <a name="remarks"></a>Observaciones

Compara dos objetos HSTRING especificados y devuelve un entero que indica su posición relativa en un criterio de ordenación.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers. h

**Espacio de nombres:** Microsoft:: WRL:: wrappers::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Wrappers::Details (espacio de nombres)](microsoft-wrl-wrappers-details-namespace.md)
