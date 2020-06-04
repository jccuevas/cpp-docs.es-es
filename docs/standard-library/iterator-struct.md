---
title: iterator (Struct)
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 64c9be76cb92d818e40714dd141ded3a8cc17c8a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455618"
---
# <a name="iterator-struct"></a>iterator (Struct)

Struct base vacío que se usa para garantizar que una clase de iterador definida por el `iterator_trait`usuario funciona correctamente con s.

## <a name="syntax"></a>Sintaxis

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>Comentarios

El struct de plantilla se usa como tipo base para todos los iteradores. Define los tipos de miembro:

- `iterator_category` (sinónimo para el parámetro de plantilla `Category`).

- `value_type` (sinónimo para el parámetro de plantilla `Type`).

- `difference_type` (sinónimo para el parámetro de plantilla `Distance`).

- `distance_type` (sinónimo para el parámetro de plantilla `Distance`).

- `pointer` (sinónimo para el parámetro de plantilla `Pointer`).

- `reference` (sinónimo para el parámetro de plantilla `Reference`).

Tenga en `value_type` cuenta que no debe ser un tipo de `pointer` constante aunque los puntos en un objeto de **const** `Type` y Reference designen un objeto de **const** `Type`.

## <a name="example"></a>Ejemplo

Vea [iterator_traits](../standard-library/iterator-traits-struct.md) para obtener un ejemplo de cómo declarar y usar los tipos de la clase base del iterador.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<iterator>](../standard-library/iterator.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
