---
title: is_lvalue_reference (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: 5bcd5c8333f011475cb11a452759c8986ab22215
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456203"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference (Clase)

Comprueba si el tipo es una referencia a un valor L.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia de este predicado de tipo contiene true si el tipo *Ty* es una referencia a un objeto o una función; de lo contrario, contiene false. Tenga en cuenta que *Ty* no puede ser una referencia rvalue. Para obtener más información sobre rvalues, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)
