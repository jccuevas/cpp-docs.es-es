---
title: is_rvalue_reference (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: ea3be02db2a4a840ed8f8b8a253d7409c26cf759
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604144"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference (Clase)

Comprueba si el tipo es una referencia a un valor R.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia de este predicado de tipo contiene true si el tipo *Ty* es un [referencia rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
