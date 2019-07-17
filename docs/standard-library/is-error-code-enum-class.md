---
title: is_error_code_enum (Clase)
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_code_enum
helpviewer_keywords:
- is_error_code_enum class
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
ms.openlocfilehash: bc4ed7cd2e058414448c9366011b9efab97ee3d5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245187"
---
# <a name="iserrorcodeenum-class"></a>is_error_code_enum (Clase)

Representa un predicado de tipo que comprueba la enumeración [error_code](../standard-library/error-code-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <_Enum>
    class is_error_code_enum;
```

## <a name="remarks"></a>Comentarios

Una instancia de este [predicado de tipo](../standard-library/type-traits.md) es true si el tipo `_Enum` es un valor de enumeración adecuado para el almacenamiento en un objeto de tipo `error_code`.

Está permitido agregar especializaciones a este tipo para tipos definidos por el usuario.

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
