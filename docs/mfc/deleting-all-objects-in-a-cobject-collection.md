---
title: "Eliminar todos los objetos de una colección CObject | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04f1edc7f181bdb23e050d2fa608c9b3a2056749
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Eliminar todos los objetos de una colección CObject
En este artículo se explica cómo eliminar todos los objetos de una colección (sin eliminar el propio objeto de colección).  
  
 Para eliminar todos los objetos de una colección de `CObject`s (o de objetos derivados de `CObject`), utilice una de las técnicas de iteración descritas en el artículo [obtiene acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md) para eliminar todos los objetos de Activar.  
  
> [!CAUTION]
>  Se pueden compartir objetos en colecciones. Es decir, la colección mantiene un puntero al objeto, pero otras partes del programa también pueden tener punteros al mismo objeto. Que debe tener cuidado de no eliminar un objeto que esté compartido hasta que todas las partes han terminado de utilizar el objeto.  
  
 En este artículo se muestra cómo eliminar los objetos en:  
  
-   [Una lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)  
  
-   [Una matriz](#_core_to_delete_all_elements_in_an_array)  
  
-   [Un mapa](#_core_to_delete_all_elements_in_a_map)  
  
#### <a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>Para eliminar todos los objetos en una lista de punteros a CObject  
  
1.  Use `GetHeadPosition` y `GetNext` para recorrer en iteración la lista.  
  
2.  Use la **eliminar** operador que se va a eliminar cada objeto que se encuentre en la iteración.  
  
3.  Llame a la `RemoveAll` function para quitar todos los elementos de la lista después de que se haya eliminado los objetos asociados a dichos elementos.  
  
 En el ejemplo siguiente se muestra cómo eliminar todos los objetos de una lista de `CPerson` objetos. Cada objeto de la lista es un puntero a un `CPerson` objeto que se asignó originalmente en el montón.  
  
 [!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]  
  
 La última llamada de función, `RemoveAll`, es una función de miembro de lista que quita todos los elementos de la lista. La función miembro `RemoveAt` quita un solo elemento.  
  
 Tenga en cuenta la diferencia entre eliminar un objeto de un elemento y quitar el propio elemento. Quitar un elemento de la lista simplemente quita la referencia de la lista para el objeto. El objeto sigue existiendo en la memoria. Cuando se elimina un objeto, deja de existir y su memoria se recupera. Por lo tanto, es importante quitar un elemento inmediatamente después de que se ha eliminado el objeto del elemento para que la lista no intente tener acceso a objetos que ya no existen.  
  
#### <a name="_core_to_delete_all_elements_in_an_array"></a>Para eliminar todos los elementos de una matriz  
  
1.  Use `GetSize` y valores de índice de entero para recorrer en iteración la matriz.  
  
2.  Use la **eliminar** operador que se va a eliminar cada elemento que se encuentre en la iteración.  
  
3.  Llame a la `RemoveAll` function para quitar todos los elementos de la matriz después de que se han eliminado.  
  
     El código para eliminar todos los elementos de una matriz es como sigue:  
  
     [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]  
  
 Como con el ejemplo de lista anterior, puede llamar a `RemoveAll` para quitar todos los elementos de una matriz o `RemoveAt` para quitar un elemento individual.  
  
#### <a name="_core_to_delete_all_elements_in_a_map"></a>Para eliminar todos los elementos de un mapa  
  
1.  Use `GetStartPosition` y `GetNextAssoc` para recorrer en iteración la matriz.  
  
2.  Use la **eliminar** operador que se va a eliminar la clave o valor de cada elemento de mapa que se encuentre en la iteración.  
  
3.  Llame a la `RemoveAll` function para quitar todos los elementos del mapa después de que se han eliminado.  
  
     El código para eliminar todos los elementos de un `CMap` colección es como sigue. Cada elemento del mapa tiene una cadena como clave y un `CPerson` objeto (derivado de `CObject`) como el valor.  
  
     [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]  
  
 Puede llamar a `RemoveAll` para quitar todos los elementos de un mapa o `RemoveKey` para quitar un elemento individual con la clave especificada.  
  
## <a name="see-also"></a>Vea también  
 [Acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md)

