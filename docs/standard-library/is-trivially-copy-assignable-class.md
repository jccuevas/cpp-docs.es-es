---
title: Clase is_trivially_copy_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7c4c748d7328f534aebfb2133c72635bbdc36f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953971"
---
# <a name="istriviallycopyassignable-class"></a>Clase is_trivially_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parámetros

*T* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es una clase que tiene un copia trivial operador de asignación, en caso contrario, es false.

Un constructor de asignación para una clase *T* es trivial si se proporciona implícitamente, la clase *T* no tiene ninguna función virtual, la clase *T* tiene ninguna base virtual, las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación triviales.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
