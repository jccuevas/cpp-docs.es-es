---
title: "Eliminar todos los objetos de una colecci&#243;n CObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "colección de clase CObject"
  - "CObject (clase), eliminar de la colección"
  - "clases de colección, eliminar todos los objetos"
  - "clases de colección, objetos compartidos"
  - "objetos [C++], eliminar de las colecciones"
  - "objetos en colecciones CObject"
  - "objetos en colecciones CObject, eliminar"
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Eliminar todos los objetos de una colecci&#243;n CObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo eliminar todos los objetos en una colección \(sin eliminar el propio objeto de colección\).  
  
 Para eliminar todos los objetos de una colección de s de `CObject`\(o de objetos derivados de `CObject`\), se usa una de las técnicas de iteración descritas en el caso [Acceso a miembros desde una colección](../mfc/accessing-all-members-of-a-collection.md) para eliminar cada objeto a la vez.  
  
> [!CAUTION]
>  Los objetos de colecciones pueden ser compartidos.  Es decir, la colección mantiene un puntero al objeto, pero otras partes del programa también pueden tener punteros al mismo objeto.  Debe tener cuidado de no eliminar un objeto se comparte hasta que todas las partes hayan terminado de utilizar el objeto.  
  
 En este artículo se muestra cómo eliminar los objetos de:  
  
-   [Una lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)  
  
-   [Una matriz](#_core_to_delete_all_elements_in_an_array)  
  
-   [Un mapa](#_core_to_delete_all_elements_in_a_map)  
  
#### Para eliminar todos los objetos de una lista de punteros a CObject  
  
1.  Uso `GetHeadPosition` y `GetNext` de recorrer en iteración la lista.  
  
2.  Utilice el operador de **borrar** para eliminar cada objeto como se encuentra en la iteración.  
  
3.  Llame a la función de `RemoveAll` para quitar todos los elementos de la lista después de los objetos asociados a esos elementos se han eliminado.  
  
 El ejemplo siguiente se muestra cómo eliminar todos los objetos de una lista de objetos de `CPerson` .  Cada objeto de la lista es un puntero a un objeto de `CPerson` que fue asignado originalmente en la pila.  
  
 [!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_1.cpp)]  
  
 La llamada de función última, `RemoveAll`, es una función miembro de la lista que quita todos los elementos de la lista.  La función `RemoveAt` miembro quita un solo elemento.  
  
 Observe la diferencia entre eliminar el objeto de un elemento y quitar el propio elemento.  Quitar un elemento de la lista quita simplemente la referencia de lista al objeto.  El objeto aún existe en memoria.  Cuando se elimina un objeto, dejan de existir y la reclamación de la memoria.  Por tanto, es importante quitar un elemento inmediatamente después de que se ha eliminado el objeto de elemento de modo que la lista no intente tener acceso a los objetos que ya no existen.  
  
#### Para eliminar todos los elementos de una matriz  
  
1.  Utilice `GetSize` y los valores de índice enteros para recorrer la matriz.  
  
2.  Utilice el operador de **borrar** para eliminar cada elemento como se encuentra en la iteración.  
  
3.  Llame a la función de `RemoveAll` para quitar todos los elementos de la matriz después de que se han eliminado.  
  
     El código para eliminar todos los elementos de una matriz es la siguiente:  
  
     [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_2.cpp)]  
  
 Como en el ejemplo de la lista anterior, puede llamar a `RemoveAll` para quitar todos los elementos de una matriz o `RemoveAt` para quitar un elemento individual.  
  
#### Para eliminar todos los elementos de un mapa  
  
1.  Utilice `GetStartPosition` y `GetNextAssoc` para recorrer la matriz.  
  
2.  Utilice el operador de **borrar** para eliminar la clave y el valor para cada elemento asignado como se encuentra en la iteración.  
  
3.  Llame a la función de `RemoveAll` para quitar todos los elementos de mapa después de que se han eliminado.  
  
     El código para eliminar todos los elementos de una colección de `CMap` es la siguiente.  Cada elemento del mapa tiene una cadena como clave y objeto de `CPerson` \(derivados de `CObject`\) como valor.  
  
     [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_3.cpp)]  
  
 Puede llamar a `RemoveAll` para quitar todos los elementos de un mapa o `RemoveKey` para quitar un elemento individual con la clave especificada.  
  
## Vea también  
 [Acceso a todos los miembros de una colección](../mfc/accessing-all-members-of-a-collection.md)