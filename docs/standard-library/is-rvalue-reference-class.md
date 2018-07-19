---
title: Clase is_rvalue_reference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acba0f78df8cc537aecd5d2fc33380e4674e5721
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956926"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference (Clase)

Comprueba si el tipo es una referencia a un valor R.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia de este predicado de tipo contiene true si el tipo *Ty* es un [referencia rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
