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
ms.openlocfilehash: d21fcc27b5b4f92b690d8fae7669a18a5fcc1c46
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964943"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference (Clase)

Comprueba si el tipo es una referencia a un valor L.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia de este predicado de tipo contiene true si el tipo *Ty* es una referencia a un objeto o una función, en caso contrario, es false. Tenga en cuenta que *Ty* no puede ser una referencia rvalue. Para obtener más información sobre rvalues, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
