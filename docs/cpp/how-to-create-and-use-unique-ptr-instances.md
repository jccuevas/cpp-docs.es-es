---
title: 'Cómo: crear y usar instancias de unique_ptr'
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
# <a name="how-to-create-and-use-unique_ptr-instances"></a>Cómo: crear y usar instancias de unique_ptr

Un [unique_ptr](../standard-library/unique-ptr-class.md) no comparte su puntero. No se puede copiar en otro `unique_ptr`, pasar por valor a una función o usarse en cualquier C++ algoritmo de la biblioteca estándar que requiere que se realicen copias. Un `unique_ptr` solo se puede mover. Esto significa que la propiedad del recurso de memoria se transfiere a otro `unique_ptr` y el `unique_ptr` original deja de poseerlo. Se recomienda limitar un objeto a un propietario, porque la propiedad múltiple agrega complejidad a la lógica del programa. Por lo tanto, si necesita un puntero inteligente para un C++ objeto sin formato, utilice `unique_ptr`y, cuando construya un `unique_ptr`, utilice la función auxiliar [make_unique](../standard-library/memory-functions.md#make_unique) .

El diagrama siguiente muestra la transferencia de propiedad entre dos instancias de `unique_ptr`.

![Mover la propiedad de un PTR&#95;único](media/unique_ptr.png "Mover la propiedad de un PTR&#95;único")

`unique_ptr` se define en el encabezado `<memory>` de la C++ biblioteca estándar. Es exactamente tan eficaz como un puntero sin formato y se puede usar en C++ contenedores de la biblioteca estándar. La adición de instancias de `unique_ptr` C++ a contenedores de la biblioteca estándar es eficaz porque el constructor de movimiento del `unique_ptr` elimina la necesidad de una operación de copia.

## <a name="example-1"></a>Ejemplo 1

En el ejemplo siguiente se muestra cómo crear instancias de `unique_ptr` y pasarlas entre funciones.

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

Estos ejemplos muestran esta característica básica de `unique_ptr`: se puede mover, pero no copiar. "Mover" transfiere la propiedad a un nuevo `unique_ptr` y restablece el antiguo `unique_ptr`.

## <a name="example-2"></a>Ejemplo 2

En el ejemplo siguiente se muestra cómo crear instancias del objeto `unique_ptr` y usarlas en un vector.

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

En el intervalo del bucle, observe que `unique_ptr` se pasa por referencia. Si intenta pasar el parámetro por valor aquí, el compilador producirá un error porque se elimina el constructor de copias `unique_ptr`.

## <a name="example-3"></a>Ejemplo 3

En el siguiente ejemplo se muestra cómo se inicializa un `unique_ptr` que es miembro de una clase.

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>Ejemplo 4

Puede usar [make_unique](../standard-library/memory-functions.md#make_unique) para crear una `unique_ptr` en una matriz, pero no puede usar `make_unique` para inicializar los elementos de la matriz.

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

Para obtener más ejemplos, vea [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Vea también

[Punteros inteligentes (C++ moderno)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
