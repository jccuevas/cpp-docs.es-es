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
ms.openlocfilehash: 7fe6eb3ffa83316071de2ba26cf80e6e6cbd5245
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957352"
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

*T* el tipo de modificación.

## <a name="remarks"></a>Comentarios

Una instancia del modificador de tipo contiene un tipo modificado que es *T* si `is_signed<T>` es verdadero. En caso contrario, es el tipo sin signo menor `UT` para el que `sizeof (T) <= sizeof (UT)`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
