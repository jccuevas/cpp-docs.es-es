---
title: Clase is_null_pointer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_null_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_null_pointer
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6de5d24c0763e731b3123778e74b22c20798b729
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966542"
---
# <a name="isnullpointer-class"></a>Clase is_null_pointer

Comprueba si el tipo es std::nullptr_t.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_null_pointer;
```

### <a name="parameters"></a>Parámetros

*T* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es `std::nullptr_t`, en caso contrario, es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
