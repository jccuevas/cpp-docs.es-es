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
ms.openlocfilehash: 303b8a566a730c5abd06d51fb7977174e19a6435
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370537"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Eliminar todos los objetos de una colección CObject

En este artículo se explica cómo eliminar todos los objetos de una colección (sin eliminar el propio objeto de colección).

Para eliminar todos los objetos de una colección de `CObject`s (o de objetos derivados de `CObject`), utilice una de las técnicas de iteración descritas en el artículo Acceso a todos los [miembros de una colección](../mfc/accessing-all-members-of-a-collection.md) para eliminar cada objeto a su vez.

> [!CAUTION]
> Los objetos de las colecciones se pueden compartir. Es decir, la colección mantiene un puntero al objeto, pero otras partes del programa también pueden tener punteros al mismo objeto. Debe tener cuidado de no eliminar un objeto que se comparte hasta que todas las partes hayan terminado de utilizar el objeto.

En este artículo se muestra cómo eliminar los objetos en:

- [Una lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Una matriz](#_core_to_delete_all_elements_in_an_array)

- [Un mapa](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>Para eliminar todos los objetos de una lista de punteros a CObject

1. Usar `GetHeadPosition` `GetNext` y recorrer en iteración la lista.

1. Utilice el operador **delete** para eliminar cada objeto tal como se encuentra en la iteración.

1. Llame `RemoveAll` a la función para quitar todos los elementos de la lista después de que se hayan eliminado los objetos asociados a esos elementos.

En el ejemplo siguiente se muestra cómo `CPerson` eliminar todos los objetos de una lista de objetos. Cada objeto de la lista `CPerson` es un puntero a un objeto que se asignó originalmente en el montón.

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

La última llamada `RemoveAll`de función, , es una función miembro de lista que quita todos los elementos de la lista. La función `RemoveAt` miembro quita un solo elemento.

Observe la diferencia entre eliminar el objeto de un elemento y quitar el propio elemento. La eliminación de un elemento de la lista simplemente elimina la referencia de la lista al objeto. El objeto todavía existe en la memoria. Cuando se elimina un objeto, deja de existir y se recupera su memoria. Por lo tanto, es importante quitar un elemento inmediatamente después de que se ha eliminado el objeto del elemento para que la lista no intente tener acceso a los objetos que ya no existen.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>Para eliminar todos los elementos de una matriz

1. Utilice `GetSize` valores de índice enteros y de uso para recorrer en iteración la matriz.

1. Utilice el operador **delete** para eliminar cada elemento tal como se encuentra en la iteración.

1. Llame `RemoveAll` a la función para quitar todos los elementos de la matriz después de que se han eliminado.

   El código para eliminar todos los elementos de una matriz es el siguiente:

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Al igual que con el `RemoveAll` ejemplo de lista anterior, `RemoveAt` puede llamar para quitar todos los elementos de una matriz o para quitar un elemento individual.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>Para eliminar todos los elementos de un mapa

1. Utilice `GetStartPosition` `GetNextAssoc` y para recorrer en iteración la matriz.

1. Utilice el operador **delete** para eliminar la clave y/o el valor de cada elemento de mapa tal como se encuentra en la iteración.

1. Llame `RemoveAll` a la función para eliminar todos los elementos del mapa después de que se hayan eliminado.

   El código para eliminar todos `CMap` los elementos de una colección es el siguiente. Cada elemento del mapa tiene una cadena `CPerson` como clave `CObject`y un objeto (derivado de ) como valor.

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Puede llamar `RemoveAll` para quitar todos los `RemoveKey` elementos de un mapa o para quitar un elemento individual con la clave especificada.

## <a name="see-also"></a>Consulte también

[Acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md)
