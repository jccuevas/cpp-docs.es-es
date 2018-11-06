---
title: iterator (Struct)
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: 1dd62a6141e690d3bd4dcad69aa107c126a0f386
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631405"
---
# <a name="iterator-struct"></a>iterator (Struct)

Un struct base vacío que se utiliza para garantizar que una clase de iterador definida por el usuario funciona correctamente con `iterator_trait`s.

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

Tenga en cuenta que `value_type` no debe estar a tipo de constante, incluso si `pointer` apunta a un objeto de **const** `Type` y la referencia designa un objeto de **const** `Type`.

## <a name="example"></a>Ejemplo

Vea [iterator_traits](../standard-library/iterator-traits-struct.md) para obtener un ejemplo de cómo declarar y usar los tipos de la clase base del iterador.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<iterator>](../standard-library/iterator.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
