---
title: Clase is_trivially_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 789839482e623e94172bbd55342d257c2b031614
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109374"
---
# <a name="istriviallyconstructible-class"></a>Clase is_trivially_constructible

Comprueba si un tipo se puede construir de forma trivial cuando se usan los tipos de argumento especificados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

*Args*<br/>
Para obtener coincidencias en un constructor de los tipos de argumento *T*.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es construir de forma trivial mediante los tipos de argumento en *Args*, en caso contrario, es false. Tipo *T* es construir de forma trivial si la definición de variable `T t(std::declval<Args>()...);` tiene el formato correcto y se sabe que llamar a ninguna operación no trivial. Ambos *T* y todos los tipos de *Args* deben ser tipos completos, **void**, o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
