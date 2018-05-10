---
title: Clase is_error_condition_enum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::is_error_condition_enum
dev_langs:
- C++
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01650db9c1aec141852f66a2f4e2f09f5d5e78ac
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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

## <a name="requirements"></a>Requisitos

**Encabezado:** \<system_error>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
