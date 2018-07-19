---
title: Clase is_nothrow_default_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38e076d5a8e552efa353be711d84485c96f6ffd3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962993"
---
# <a name="isnothrowdefaultconstructible-class"></a>Clase is_nothrow_default_constructible

Comprueba si el tipo tiene un constructor predeterminado que no produce excepciones.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* tiene un nothrow constructor predeterminado, en caso contrario, es false. Una instancia del predicado de tipo es equivalente a `is_nothrow_constructible<Ty>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
