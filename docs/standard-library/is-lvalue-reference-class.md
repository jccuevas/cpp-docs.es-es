---
title: Clase is_lvalue_reference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_lvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 692c5243a7fe2984d43a1e70fc39616de5cbcc9c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845367"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference (Clase)

Comprueba si el tipo es una referencia a un valor L.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia de este predicado de tipo contiene true si el tipo `Ty` es una referencia a un objeto o una función; de lo contrario, contiene false. Tenga en cuenta que es posible que `Ty` no sea una referencia a un valor R. Para obtener más información sobre rvalues, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
