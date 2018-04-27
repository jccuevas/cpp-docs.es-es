---
title: Clase is_trivially_copy_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73928574f2c96da952b7f18908c6b7a175549981
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
