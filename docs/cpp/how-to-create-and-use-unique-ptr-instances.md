---
title: Procedimiento Crear y usar instancias de unique_ptr
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 48e459b69592bf4c231407c2a378a7b7e01ff4ae
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220587"
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>Procedimiento Crear y usar instancias de unique_ptr

Un [unique_ptr](../standard-library/unique-ptr-class.md) no comparte el puntero. No se puede copiar a otro `unique_ptr`, pasan por valor a una función o utilizar en ningún algoritmo de la biblioteca estándar de C++ que requiere la realización de copias. Un `unique_ptr` solo se puede mover. Esto significa que la propiedad del recurso de memoria se transfiere a otro `unique_ptr` y el `unique_ptr` original deja de poseerlo. Se recomienda limitar un objeto a un propietario, porque la propiedad múltiple agrega complejidad a la lógica del programa. Por lo tanto, cuando necesite un puntero inteligente para un objeto de C++ sin formato, use `unique_ptr`, y cuando construya un `unique_ptr`, utilice el [make_unique](../standard-library/memory-functions.md#make_unique) función auxiliar.

El diagrama siguiente muestra la transferencia de propiedad entre dos instancias de `unique_ptr`.

![Transferencia de la propiedad de un único&#95;ptr](../cpp/media/unique_ptr.png "transferencia de la propiedad de un único&#95;ptr")

`unique_ptr` se define en el `<memory>` encabezado en la biblioteca estándar de C++. Es exactamente tan eficaz como un puntero sin formato y se pueden usar en contenedores de la biblioteca estándar de C++. La adición de `unique_ptr` instancias para contenedores de la biblioteca estándar de C++ es eficaz porque el constructor de movimiento de la `unique_ptr` elimina la necesidad de una operación de copia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear instancias de `unique_ptr` y pasarlas entre funciones.

[!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

Estos ejemplos muestran esta característica básica de `unique_ptr`: se puede mover, pero no copiar. "Mover" transfiere la propiedad a un nuevo `unique_ptr` y restablece el antiguo `unique_ptr`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear instancias del objeto `unique_ptr` y usarlas en un vector.

[!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

En el intervalo del bucle, observe que `unique_ptr` se pasa por referencia. Si intenta pasar el parámetro por valor aquí, el compilador producirá un error porque se elimina el constructor de copias `unique_ptr`.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo se inicializa un `unique_ptr` que es miembro de una clase.

[!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example"></a>Ejemplo

Puede usar [make_unique](../standard-library/memory-functions.md#make_unique) para crear un `unique_ptr` en una matriz, pero no se puede usar `make_unique` para inicializar los elementos de matriz.

[!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

Para obtener más ejemplos, vea [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Vea también

[Punteros inteligentes (C++ moderno)](../cpp/smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
