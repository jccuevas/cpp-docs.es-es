---
title: alignment_of (Clase)
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: c2af00ac32b3013820a3109783c4bf7eb42ec445
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623732"
---
# <a name="alignment_of-class"></a>alignment_of (Clase)

Obtiene una alineación del tipo especificado. Este struct se implementa en términos de [alignof](../cpp/alignment-cpp-declarations.md). Use **aligna** directamente cuando solo necesite consultar un valor de alineación. Use alignment_of cuando necesite una constante integral, por ejemplo, al realizar un envío de etiquetas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Observaciones

La consulta de tipo contiene el valor de la alineación del tipo *Ty*.

## <a name="requirements"></a>Requisitos

**Encabezado:**\<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[<type_traits>](type-traits.md)\
[aligned_storage (clase)](aligned-storage-class.md)
