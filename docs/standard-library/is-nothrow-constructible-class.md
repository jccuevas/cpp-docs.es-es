---
title: Clase is_nothrow_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0726839baadf5265d604f231615f1add069ccfcb
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106536"
---
# <a name="isnothrowconstructible-class"></a>Clase is_nothrow_constructible

Comprueba si un tipo se puede construir y se sabe que no se inicia cuando se usan los tipos de argumento especificados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

*Args*<br/>
Para obtener coincidencias en un constructor de los tipos de argumento *T*.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es que se puede construir mediante los tipos de argumento en *Args*y el constructor es conocido por el compilador no se inicia; en caso contrario, es false. Tipo *T* es que se puede construir si la definición de variable `T t(std::declval<Args>()...);` tiene el formato correcto. Ambos *T* y todos los tipos de *Args* deben ser tipos completos, **void**, o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
