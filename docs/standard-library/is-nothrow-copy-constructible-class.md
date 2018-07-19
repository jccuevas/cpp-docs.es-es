---
title: Clase is_nothrow_copy_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc4f839ed955048b96f6327c63cd2cc82fef8aca
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953778"
---
# <a name="isnothrowcopyconstructible-class"></a>is_nothrow_copy_constructible (clase)

Comprueba si el tipo tiene un constructor de copias **nothrow**.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* tiene un nothrow constructor de copias, en caso contrario, es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
