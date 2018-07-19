---
title: underlying_type (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f45af807b37294b87920b6fabac18647f170025
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853227"
---
# <a name="underlyingtype-class"></a>underlying_type (Clase)

Genera el tipo entero subyacente para un tipo de enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parámetros

`T` Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

La definición de tipo miembro `type` de la clase de plantilla nombra el tipo entero subyacente de `T`, cuando `T` es un tipo de enumeración, de lo contrario, no hay ninguna definición de tipo miembro `type`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
