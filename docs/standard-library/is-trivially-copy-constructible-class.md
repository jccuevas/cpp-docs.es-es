---
title: Clase is_trivially_copy_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01c95007f1db1bcaf549398fa8865a9e51fe23d1
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "33954107"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible (Clase)

Comprueba si el tipo tiene un constructor de copia trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `T` es una clase que tiene un constructor de copias trivial; en caso contrario, es false.

Un constructor de copia para una clase `T` es trivial si se declara implícitamente, la clase `T` no tiene funciones virtuales o bases virtuales, todas las bases directas de la clase `T` tienen constructores de copia triviales, las clases de todos los miembros de datos no estáticos de tipo de clase tienen constructores de copia triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de copia triviales.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
