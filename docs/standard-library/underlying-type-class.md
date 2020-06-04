---
title: underlying_type (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: ea4768d78047112a7584ca49b0e4487fad55a970
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688839"
---
# <a name="underlying_type-class"></a>underlying_type (Clase)

Genera el tipo entero subyacente para un tipo de enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parámetros

*T* \
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

La definición de tipo de miembro de `type` de la plantilla de clase nombra el tipo entero subyacente de *t*, cuando *t* es un tipo de enumeración; de lo contrario, no hay ningún miembro typedef `type`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
