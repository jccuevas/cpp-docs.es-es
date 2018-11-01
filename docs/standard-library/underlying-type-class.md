---
title: underlying_type (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 23e5e9bc5406265f49fca2ed220c597cb32e2a9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609708"
---
# <a name="underlyingtype-class"></a>underlying_type (Clase)

Genera el tipo entero subyacente para un tipo de enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

El `type` typedef de miembro de la clase de plantilla nombra el tipo entero subyacente de *T*, cuando *T* es un tipo de enumeración, en caso contrario, no hay ninguna definición de tipo de miembro `type`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
