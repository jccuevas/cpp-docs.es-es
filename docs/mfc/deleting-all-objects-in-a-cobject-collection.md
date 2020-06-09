---
title: Eliminar todos los objetos de una colección CObject
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 2921fe4e4f10c96a096d30d8f842eecdfd644ca6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615907"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Eliminar todos los objetos de una colección CObject

En este artículo se explica cómo eliminar todos los objetos de una colección (sin eliminar el propio objeto de colección).

Para eliminar todos los objetos de una colección de `CObject` s (o de objetos derivados de `CObject` ), se usa una de las técnicas de iteración descritas en el artículo [acceso a todos los miembros de una colección](accessing-all-members-of-a-collection.md) para eliminar cada objeto a su vez.

> [!CAUTION]
> Los objetos de las colecciones se pueden compartir. Es decir, la colección mantiene un puntero al objeto, pero otras partes del programa también pueden tener punteros al mismo objeto. Debe tener cuidado de no eliminar un objeto compartido hasta que todas las partes hayan terminado de usar el objeto.

En este artículo se muestra cómo eliminar los objetos de:

- [Una lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Una matriz](#_core_to_delete_all_elements_in_an_array)

- [Un mapa](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>Para eliminar todos los objetos de una lista de punteros a CObject

1. Use `GetHeadPosition` y `GetNext` para recorrer en iteración la lista.

1. Use el operador **Delete** para eliminar cada objeto a medida que se encuentre en la iteración.

1. Llame `RemoveAll` a la función para quitar todos los elementos de la lista una vez eliminados los objetos asociados a esos elementos.

En el ejemplo siguiente se muestra cómo eliminar todos los objetos de una lista de `CPerson` objetos. Cada objeto de la lista es un puntero a un `CPerson` objeto que se asignó originalmente en el montón.

[!code-cpp[NVC_MFCCollections#17](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

La última llamada de función, `RemoveAll` , es una función miembro de lista que quita todos los elementos de la lista. La función miembro `RemoveAt` quita un solo elemento.

Observe la diferencia entre eliminar el objeto de un elemento y quitar el propio elemento. Al quitar un elemento de la lista, simplemente se quita la referencia de la lista al objeto. El objeto todavía existe en la memoria. Cuando se elimina un objeto, deja de existir y se recupera su memoria. Por lo tanto, es importante quitar un elemento inmediatamente después de que se haya eliminado el objeto del elemento, de modo que la lista no intente obtener acceso a los objetos que ya no existen.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>Para eliminar todos los elementos de una matriz

1. Use `GetSize` y valores de índice de entero para recorrer en iteración la matriz.

1. Use el operador **Delete** para eliminar todos los elementos que se encuentren en la iteración.

1. Llame `RemoveAll` a la función para quitar todos los elementos de la matriz una vez eliminados.

   El código para eliminar todos los elementos de una matriz es el siguiente:

   [!code-cpp[NVC_MFCCollections#18](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Como con el ejemplo anterior de lista, puede llamar `RemoveAll` a para quitar todos los elementos de una matriz o `RemoveAt` quitar un elemento individual.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>Para eliminar todos los elementos de un mapa

1. Use `GetStartPosition` y `GetNextAssoc` para recorrer en iteración la matriz.

1. Use el operador **Delete** para eliminar la clave o el valor de cada elemento de mapa tal y como se encuentra en la iteración.

1. Llame `RemoveAll` a la función para quitar todos los elementos de la asignación una vez eliminados.

   El código para eliminar todos los elementos de una `CMap` colección es el siguiente. Cada elemento del mapa tiene una cadena como clave y un `CPerson` objeto (derivado de `CObject` ) como valor.

   [!code-cpp[NVC_MFCCollections#19](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Puede llamar `RemoveAll` a para quitar todos los elementos de una asignación o `RemoveKey` quitar un elemento individual con la clave especificada.

## <a name="see-also"></a>Consulte también

[Obtener acceso a todos los miembros de una colección](accessing-all-members-of-a-collection.md)
