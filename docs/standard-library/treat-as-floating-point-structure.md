---
title: treat_as_floating_point (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: add69179b23a953a937458cbfa55254b21c5ea37
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685112"
---
# <a name="treat_as_floating_point-structure"></a>treat_as_floating_point (Estructura)

Especifica si `Rep` se puede tratar como un tipo de punto flotante.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Comentarios

`Rep` se puede tratar como un tipo de punto flotante solo cuando la especialización `treat_as_floating_point<Rep>` se deriva de [true_type](../standard-library/type-traits-typedefs.md#true_type). La plantilla de clase se puede especializar para un tipo definido por el usuario.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<chrono >

**Espacio de nombres:** std::chrono

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
