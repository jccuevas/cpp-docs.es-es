---
title: Clase make_signed | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::make_signed
dev_langs:
- C++
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b58c31c7f4180f9c65b04bbb852bf15c7315c35d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="makesigned-class"></a>make_signed (Clase)

Hace que el tipo o el tipo con signo más pequeño sea igual o superior en tamaño al tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>Parámetros

`T` Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia del modificador de tipo contiene un tipo modificado que es `T` si `is_signed<T>` es true. En caso contrario, es el tipo sin signo menor `UT` para el que `sizeof (T) <= sizeof (UT)`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
