---
title: Clase is_final | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_final
dev_langs:
- C++
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 016ad1c5017635000f17b8852f7ebdb8e2f62e4a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108699"
---
# <a name="isfinal-class"></a>Clase is_final

Comprueba si el tipo es un tipo de clase marcado como `final`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* se marca un tipo de clase `final`, en caso contrario, es false. Si *T* es un tipo de clase, debe ser un tipo completo.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[Especificador final](../cpp/final-specifier.md)<br/>
