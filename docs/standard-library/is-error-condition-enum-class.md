---
title: is_error_condition_enum (Clase)
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: c40f8f6eb93a33098cfbcf8133f08c56285abb43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452603"
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

[<type_traits>](../standard-library/type-traits.md)
