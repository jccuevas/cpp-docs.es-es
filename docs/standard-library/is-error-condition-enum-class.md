---
title: is_error_condition_enum (Clase)
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 213970d6260eaf55ac1bd678e6317cf2346ed9bc
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245177"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum (Clase)

Representa un predicado de tipo que comprueba la enumeración [error_condition](../standard-library/error-condition-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>Comentarios

Una instancia de este [predicado de tipo](../standard-library/type-traits.md) es true si el tipo `_Enum` es un valor de enumeración adecuado para el almacenamiento en un objeto de tipo `error_condition`.

Está permitido agregar especializaciones a este tipo para tipos definidos por el usuario.

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
