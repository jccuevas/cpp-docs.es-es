---
title: treat_as_floating_point (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: 4cf3ac5be972d8636f1d3dbda3b195f4012517be
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459882"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point (Estructura)

Especifica si `Rep` se puede tratar como un tipo de punto flotante.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Comentarios

`Rep` se puede tratar como un tipo de punto flotante solo cuando la especialización `treat_as_floating_point<Rep>` se deriva de [true_type](../standard-library/type-traits-typedefs.md#true_type). La clase de plantilla se puede especializar para un tipo definido por el usuario.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> crónico

**Espacio de nombres:** std::chrono

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
