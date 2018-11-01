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
ms.openlocfilehash: 8bd64e1c5efd1f80f43cb3460719326f30d5416c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557864"
---
# <a name="template-based-classes"></a>Clases basadas en plantillas

En este artículo se explica las clases de colección basadas en plantillas de seguridad de tipos en MFC 3.0 y versiones posteriores. Uso de estas plantillas para crear colecciones seguras para el tipo es más conveniente y ayuda a proporciona seguridad de tipos de forma más eficaz que el uso de las clases de colección no basadas en plantillas.

MFC predefine dos categorías de colecciones basadas en la plantilla:

- [Simple clases de matriz, lista y mapa](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Las matrices, listas y mapas de punteros con tipo](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Las clases de colección simple se derivan de la clase `CObject`, por lo que heredan de la serialización, la creación dinámica y otras propiedades de `CObject`. Las clases de colección de puntero con tipo requieren que se especifique la clase se deriva de, que debe ser una de las colecciones de puntero sin plantilla predefinidas por MFC, como `CPtrList` o `CPtrArray`. La nueva clase de colección se hereda de la clase base especificada, y las funciones miembro de la nueva clase usan encapsulado las llamadas a los miembros de clase base para exigir la seguridad de tipos.

Para obtener más información acerca de las plantillas de C++, vea [plantillas](../cpp/templates-cpp.md) en el *referencia del lenguaje C++*.

##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> Uso de matriz Simple, lista y mapa plantillas

Para usar las plantillas de colección simple, debe saber qué tipo de datos puede almacenar en estas colecciones y qué parámetros se deben usar en las declaraciones de la colección.

###  <a name="_core_simple_array_and_list_usage"></a> Uso de la lista y matriz simple

La matriz simple y clases de lista, [CArray](../mfc/reference/carray-class.md) y [CList](../mfc/reference/clist-class.md), toman dos parámetros: *tipo* y `ARG_TYPE`. Estas clases pueden almacenar cualquier tipo de datos que se especifica en el *tipo* parámetro:

- Tipos de datos fundamentales de C++, como **int**, **char**, y **float**

- Las clases y estructuras de C++

- Otros tipos que se definen

Por comodidad y la eficacia, puede usar el *ARG_TYPE* parámetro para especificar el tipo de argumentos de función. Normalmente, se especifica *ARG_TYPE* como una referencia al tipo indicado en el *tipo* parámetro. Por ejemplo:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

El primer ejemplo declara una colección de matrices, `myArray`, que contiene **int**s. El segundo ejemplo declara una colección de lista, `myList`, que almacena `CPerson` objetos. Determinadas funciones miembro de las clases de colección aceptan argumentos cuyo tipo se especifica mediante el *ARG_TYPE* parámetro de plantilla. Por ejemplo, el `Add` función miembro de clase `CArray` toma un *ARG_TYPE* argumento:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

###  <a name="_core_simple_map_usage"></a> Uso de asignación simple

La clase de mapa sencilla [CMap](../mfc/reference/cmap-class.md), toma cuatro parámetros: *clave*, *ARG_KEY*, *valor*, y *ARG_VALUE*. Al igual que las clases de matriz y lista, las clases de mapa pueden almacenar cualquier tipo de datos. A diferencia de las matrices y listas, que se indizan y ordenan los datos que almacenan, mapas de asocian las claves y valores: obtener acceso a un valor almacenado en un mapa especificando la clave asociada al valor. El *clave* parámetro especifica el tipo de datos de las claves utilizadas para tener acceso a datos almacenados en el mapa. Si el tipo de *clave* es una estructura o clase, el *ARG_KEY* parámetro normalmente es una referencia al tipo especificado en *clave*. El *valor* parámetro especifica el tipo de los elementos almacenados en el mapa. Si el tipo de *ARG_VALUE* es una estructura o clase, el *ARG_VALUE* parámetro normalmente es una referencia al tipo especificado en *valor*. Por ejemplo:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

El primer ejemplo almacena `MY_STRUCT` valores, tiene acceso a ellos por **int** claves y devuelve acceso `MY_STRUCT` elementos por referencia. El segundo ejemplo almacena `CPerson` valores, tiene acceso a ellos por `CString` de claves y la devuelve referencias a elementos que se tiene acceso. En este ejemplo podría representar una libreta de direcciones simple, en el que se buscan personas por apellido.

Dado que el *clave* parámetro es de tipo `CString` y el *KEY_TYPE* parámetro es de tipo `LPCSTR`, las claves se almacenan en el mapa como elementos de tipo `CString` , pero se hace referencia en las funciones como `SetAt` mediante punteros de tipo `LPCSTR`. Por ejemplo:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> Uso de plantillas de la colección de puntero con tipo

Para usar las plantillas de la colección de puntero con tipo, debe saber qué tipos de datos puede almacenar en estas colecciones y qué parámetros se deben usar en las declaraciones de la colección.

###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> Matriz de puntero con tipo y el uso de la lista

La matriz de puntero con tipo y clases de lista, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) y [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), toman dos parámetros: *$base_class* y *tipo*. Estas clases pueden almacenar cualquier tipo de datos que se especifica en el *tipo* parámetro. Se derivan de una de las clases de colección no es de plantilla que almacena punteros; Especifique esta clase base en *$base_class*. Para las matrices, usar `CObArray` o `CPtrArray`. Para listas, usar `CObList` o `CPtrList`.

De hecho, cuando se declara una colección basada en, por ejemplo `CObList`, la nueva clase hereda no solo los miembros de su clase base, pero también declara un número de miembros adicionales de seguridad de tipos de funciones y operadores que ayudan a proporcionar seguridad de tipos encapsulando llamadas a los miembros de clase base. Estas encapsulaciones administran todas las conversión de tipo necesaria. Por ejemplo:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

El primer ejemplo declara una matriz de puntero con tipo, `myArray`, derivada de `CObArray`. La matriz almacena y devuelve punteros a `CPerson` objetos (donde `CPerson` es una clase derivada de `CObject`). Puede llamar a cualquiera `CObArray` función miembro, o puede llamar al nuevo con seguridad de tipos `GetAt` y `ElementAt` las funciones o utilizar la seguridad de tipos **[]** operador.

El segundo ejemplo declara una lista de puntero con tipo, `myList`, derivada de `CPtrList`. La lista almacena y devuelve punteros a `MY_STRUCT` objetos. Una clase según `CPtrList` se usa para almacenar punteros a objetos no derivados de `CObject`. `CTypedPtrList` tiene un número de funciones miembro de la seguridad de tipos: `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev`, y `GetAt`.

###  <a name="_core_typed.2d.pointer_map_usage"></a> Uso de mapa de puntero con tipo

La clase map de puntero con tipo, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), toma tres parámetros: *$base_class*, *clave*, y *valor*. El *$base_class* parámetro especifica la clase del que se deriva la nueva clase: `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`, y así sucesivamente. *CLAVE* es análogo a *clave* en `CMap`: especifica el tipo de la clave utilizada para las búsquedas. *VALOR* es análogo a *valor* en `CMap`: especifica el tipo de objeto almacenado en el mapa. Por ejemplo:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

El primer ejemplo es un mapa basado en `CMapPtrToPtr` : usa `CString` claves asignadas a punteros a `MY_STRUCT`. Puede buscar un puntero almacenado mediante una llamada a un tipo seguro `Lookup` función miembro. Puede usar el **[]** operador para buscar un puntero almacenado y agregarlo si no se encuentra. Y puede recorrer en iteración la asignación mediante la seguridad de tipos `GetNextAssoc` función. También puede llamar otro miembro de las funciones de clase `CMapPtrToPtr`.

El segundo ejemplo es un mapa basado en `CMapStringToOb` : utiliza las claves de cadena asignadas a punteros almacenados a `CMyObject` objetos. Puede usar los mismos miembros con seguridad de tipos se describe en el párrafo anterior, o puede llamar a los miembros de clase `CMapStringToOb`.

> [!NOTE]
>  Si especifica un **clase** o **struct** tipo para el *valor* parámetro, en lugar de un puntero o referencia al tipo, la clase o estructura debe tener un constructor de copias.

Para obtener más información, consulte [cómo hacer que una colección segura para el tipo](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Vea también

[Colecciones](../mfc/collections.md)

