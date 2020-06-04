---
title: alignment_of (Clase)
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: d241848edf57fe4876c35e22f1762abf5d6888fa
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302320"
---
# <a name="alignment_of-class"></a>alignment_of (Clase)

Obtiene una alineación del tipo especificado. Este struct se implementa en términos de [alignof](../cpp/alignment-cpp-declarations.md). Use **aligna** directamente cuando solo necesite consultar un valor de alineación. Use alignment_of cuando necesite una constante integral, por ejemplo, al realizar un envío de etiquetas.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parámetros

\ *Ty*
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

La consulta de tipo contiene el valor de la alineación del tipo *Ty*.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits >

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[aligned_storage (Clase)](../standard-library/aligned-storage-class.md)
