---
title: Clases basadas en plantillas
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: 29f5f815b62835aedbca1f79b797f826ea53d83b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370454"
---
# <a name="template-based-classes"></a>Clases basadas en plantillas

En este artículo se explican las clases de colección basadas en plantillas con seguridad de tipos en MFC versión 3.0 y versiones posteriores. El uso de estas plantillas para crear colecciones con seguridad de tipos es más conveniente y ayuda a proporcionar seguridad de tipos de forma más eficaz que el uso de las clases de colección no basadas en plantillas.

MFC predefine dos categorías de colecciones basadas en plantillas:

- [Clases simples de matriz, lista y mapa](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Matrices, listas y mapas de punteros con tipo](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Las clases de colección `CObject`simples se derivan de la clase, por `CObject`lo que heredan la serialización, la creación dinámica y otras propiedades de . Las clases de colección de punteros con tipo requieren que especifique la clase de la `CPtrList` que `CPtrArray`deriva, que debe ser una de las colecciones de punteros que no son de plantilla predefinidas por MFC, como o . La nueva clase de colección hereda de la clase base especificada y las funciones miembro de la nueva clase usan llamadas encapsuladas a los miembros de la clase base para aplicar la seguridad de tipos.

Para obtener más información acerca de las plantillas C++, consulte [Plantillas](../cpp/templates-cpp.md) en la Referencia de *idioma C++.*

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Uso de plantillas simples de matriz, lista y mapa

Para usar las plantillas de colección simples, debe saber qué tipo de datos puede almacenar en estas colecciones y qué parámetros usar en las declaraciones de colección.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>Uso simple de matrices y listas

Las clases de matriz y lista simples, [CArray](../mfc/reference/carray-class.md) `ARG_TYPE`y [CList](../mfc/reference/clist-class.md), toman dos parámetros: *TYPE* y . Estas clases pueden almacenar cualquier tipo de datos, que especifique en el parámetro *TYPE:*

- Tipos de datos C++ fundamentales, como **int**, **char**y **float**

- Estructuras y clases C++

- Otros tipos que defina

Para mayor comodidad y eficiencia, puede utilizar el parámetro *ARG_TYPE* para especificar el tipo de argumentos de función. Normalmente, se especifica *ARG_TYPE* como referencia al tipo que nombró en el parámetro *TYPE.* Por ejemplo:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

El primer ejemplo declara una `myArray`colección de matrices, , que contiene **int**s. El segundo ejemplo declara una `myList`colección `CPerson` de listas, , que almacena objetos. Ciertas funciones miembro de las clases de colección toman argumentos cuyo tipo se especifica mediante el *ARG_TYPE* parámetro de plantilla. Por ejemplo, `Add` la función miembro de class `CArray` toma un argumento *ARG_TYPE:*

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>Uso simple del mapa

La clase de mapa simple, [CMap](../mfc/reference/cmap-class.md), toma cuatro parámetros: *KEY*, *ARG_KEY*, *VALUE*y *ARG_VALUE*. Al igual que las clases de matriz y lista, las clases de mapa pueden almacenar cualquier tipo de datos. A diferencia de las matrices y listas, que indexan y ordenan los datos que almacenan, los mapas asocian claves y valores: se accede a un valor almacenado en un mapa especificando la clave asociada del valor. El parámetro *KEY* especifica el tipo de datos de las claves utilizadas para acceder a los datos almacenados en el mapa. Si el tipo de *KEY* es una estructura o clase, el parámetro *ARG_KEY* suele ser una referencia al tipo especificado en *KEY*. El parámetro *VALUE* especifica el tipo de los elementos almacenados en el mapa. Si el tipo de *ARG_VALUE* es una estructura o clase, el parámetro *ARG_VALUE* suele ser una referencia al tipo especificado en *VALUE*. Por ejemplo:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

El primer `MY_STRUCT` ejemplo almacena valores, los tiene acceso `MY_STRUCT` mediante claves **int** y devuelve los elementos a los que se tiene acceso por referencia. El segundo `CPerson` ejemplo almacena valores, `CString` los tiene acceso mediante claves y devuelve referencias a los elementos a los que se tiene acceso. Este ejemplo puede representar una libreta de direcciones simple, en la que se buscan personas por apellido.

Dado *KEY* que el parámetro `CString` KEY es de `LPCSTR`tipo y el parámetro *KEY_TYPE* es `CString` de tipo , las `SetAt` claves se `LPCSTR`almacenan en el mapa como elementos de tipo, pero se hace referencia a ellas en funciones como a través de punteros de tipo . Por ejemplo:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>Uso de plantillas de colección de puntero sin tipo

Para usar las plantillas de colección de punteros con tipo, debe saber qué tipos de datos puede almacenar en estas colecciones y qué parámetros usar en las declaraciones de colección.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>Uso de la lista y la matriz de punteros con tipo

Las clases de lista y matriz de puntero con tipo, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) y [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), toman dos parámetros: *BASE_CLASS* y *TYPE*. Estas clases pueden almacenar cualquier tipo de datos, que especifique en el parámetro *TYPE.* Se derivan de una de las clases de colección que no son de plantilla que almacena punteros; especifique esta clase base en *BASE_CLASS*. Para matrices, `CObArray` utilice `CPtrArray`o . Para las listas, utilice `CObList` `CPtrList`o .

En efecto, cuando se declara una `CObList`colección basada en, por ejemplo , la nueva clase no solo hereda los miembros de su clase base, sino que también declara una serie de operadores y funciones miembro con seguridad de tipos adicionales que ayudan a proporcionar seguridad de tipos encapsulando llamadas a los miembros de la clase base. Estas encapsulaciones administran toda la conversión de tipos necesaria. Por ejemplo:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

En el primer ejemplo se declara `myArray`una matriz `CObArray`de puntero con tipo, , derivada de . La matriz almacena y `CPerson` devuelve punteros a objetos (donde `CPerson` se deriva una clase de `CObject`). Puede llamar `CObArray` a cualquier función miembro, o `GetAt` puede `ElementAt` llamar a la nueva clase segura y funciones o utilizar el operador de tipo seguro **[ ].**

El segundo ejemplo declara una lista `myList`de punteros `CPtrList`con tipo, , derivada de . La lista almacena y `MY_STRUCT` devuelve punteros a objetos. Una clase `CPtrList` basada en se utiliza para almacenar punteros a objetos no derivados de `CObject`. `CTypedPtrList`tiene una serie de funciones `GetHead` `GetTail`miembro `RemoveHead` `RemoveTail`con `GetNext` `GetPrev`seguridad `GetAt`de tipos: , , , , , , , y .

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>Uso del mapa de puntero con tipo

La clase de mapa de puntero con tipo, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), toma tres parámetros: *BASE_CLASS*, *KEY*y *VALUE*. El parámetro *BASE_CLASS* especifica la clase de la `CMapPtrToWord` `CMapPtrToPtr`que `CMapStringToPtr` `CMapWordToPtr`se `CMapStringToOb`deriva la nueva clase: , , , , , , , , etc. *KEY* es análogo *KEY* a `CMap`KEY en : Especifica el tipo de clave utilizada para las búsquedas. *VALUE* es análogo *VALUE* a `CMap`VALUE en : Especifica el tipo de objeto almacenado en el mapa. Por ejemplo:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

El primer ejemplo es `CMapPtrToPtr` un mapa `CString` basado en — `MY_STRUCT`utiliza claves asignadas a punteros a . Puede buscar un puntero almacenado mediante una `Lookup` llamada a una función miembro con seguridad de tipos. Puede utilizar el operador **[ ]** para buscar un puntero almacenado y agregarlo si no se encuentra. Y puede iterar el mapa utilizando la función de tipo seguro. `GetNextAssoc` También puede llamar a otras `CMapPtrToPtr`funciones miembro de la clase .

El segundo ejemplo es `CMapStringToOb` un mapa basado en: utiliza `CMyObject` claves de cadena asignadas a punteros almacenados a objetos. Puede usar los mismos miembros con seguridad de tipos descritos `CMapStringToOb`en el párrafo anterior o puede llamar a los miembros de la clase .

> [!NOTE]
> Si especifica una **clase** o un tipo **de estructura** para el parámetro *VALUE,* en lugar de un puntero o una referencia al tipo, la clase o estructura debe tener un constructor de copias.

Para obtener más información, consulte [Cómo crear una colección con seguridad](../mfc/how-to-make-a-type-safe-collection.md)de tipos .

## <a name="see-also"></a>Consulte también

[Colecciones](../mfc/collections.md)
