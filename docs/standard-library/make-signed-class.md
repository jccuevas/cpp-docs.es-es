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
ms.openlocfilehash: f339b0e26475607ed95f60e33173aa624b892871
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108946"
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

*T*<br/>
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia del modificador de tipo contiene un tipo modificado que es *T* si `is_signed<T>` es verdadero. En caso contrario, es el tipo sin signo menor `UT` para el que `sizeof (T) <= sizeof (UT)`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
