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
ms.openlocfilehash: 410566c623595cc941ab6e6ad21dd95bd70fe516
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963672"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible (Clase)

Comprueba si el tipo tiene un constructor de copia trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parámetros

*T* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es una clase que tiene un constructor de copias triviales, en caso contrario, es false.

Un constructor de copias para una clase *T* es trivial si se está declarado implícitamente, la clase *T* no tiene funciones virtuales o bases virtuales, todas las bases directas de la clase *T* tiene constructores de copias triviales, las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de copias triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de copias triviales.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
