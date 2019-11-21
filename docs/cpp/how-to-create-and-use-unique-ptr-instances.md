---
title: 'How to: Create and use unique_ptr instances'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 4b3362f71d1ccab0efb03d7e8705c6b3f25f9780
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246522"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>How to: Create and use unique_ptr instances

A [unique_ptr](../standard-library/unique-ptr-class.md) does not share its pointer. It cannot be copied to another `unique_ptr`, passed by value to a function, or used in any C++ Standard Library algorithm that requires copies to be made. Un `unique_ptr` solo se puede mover. Esto significa que la propiedad del recurso de memoria se transfiere a otro `unique_ptr` y el `unique_ptr` original deja de poseerlo. Se recomienda limitar un objeto a un propietario, porque la propiedad múltiple agrega complejidad a la lógica del programa. Therefore, when you need a smart pointer for a plain C++ object, use `unique_ptr`, and when you construct a `unique_ptr`, use the [make_unique](../standard-library/memory-functions.md#make_unique) helper function.

El diagrama siguiente muestra la transferencia de propiedad entre dos instancias de `unique_ptr`.

![Moving the ownership of a unique&#95;ptr](media/unique_ptr.png "Moving the ownership of a unique&#95;ptr")

`unique_ptr` is defined in the `<memory>` header in the C++ Standard Library. It is exactly as efficient as a raw pointer and can be used in C++ Standard Library containers. The addition of `unique_ptr` instances to C++ Standard Library containers is efficient because the move constructor of the `unique_ptr` eliminates the need for a copy operation.

## <a name="example-1"></a>Ejemplo 1

En el ejemplo siguiente se muestra cómo crear instancias de `unique_ptr` y pasarlas entre funciones.

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

Estos ejemplos muestran esta característica básica de `unique_ptr`: se puede mover, pero no copiar. "Mover" transfiere la propiedad a un nuevo `unique_ptr` y restablece el antiguo `unique_ptr`.

## <a name="example-2"></a>Ejemplo 2

En el ejemplo siguiente se muestra cómo crear instancias del objeto `unique_ptr` y usarlas en un vector.

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

En el intervalo del bucle, observe que `unique_ptr` se pasa por referencia. Si intenta pasar el parámetro por valor aquí, el compilador producirá un error porque se elimina el constructor de copias `unique_ptr`.

## <a name="example-3"></a>Ejemplo 3

En el siguiente ejemplo se muestra cómo se inicializa un `unique_ptr` que es miembro de una clase.

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>Ejemplo 4

You can use [make_unique](../standard-library/memory-functions.md#make_unique) to create a `unique_ptr` to an array, but you cannot use `make_unique` to initialize the array elements.

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

For more examples, see [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Vea también

[Punteros inteligentes (C++ moderno)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
