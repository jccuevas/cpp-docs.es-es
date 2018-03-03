---
title: Clases basadas en plantillas | Documentos de Microsoft
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2beb417bdedab6196ff6d27a387c4b61f083c4ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="template-based-classes"></a>Clases basadas en plantillas
Este artículo explica las clases de colección basadas en plantillas de seguridad de tipos en MFC versión 3.0 y versiones posterior. Uso de estas plantillas para crear colecciones con seguridad de tipos es más cómodo y ayuda a proporciona seguridad de tipos de forma más eficaz que el uso de las clases de colección no basadas en plantillas.  
  
 MFC predefine dos categorías de colecciones basadas en plantillas:  
  
-   [Simple clases de matriz, lista y mapa](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [Matrices, listas y mapas de punteros con tipo](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 Las clases de colección simple se derivan de la clase `CObject`, por lo que heredan la serialización, la creación dinámica y otras propiedades de `CObject`. Las clases de colección de puntero con tipo requieren que se especifique la clase se deriva de, que debe ser una de las colecciones de puntero sin plantilla predefinidas por MFC, como `CPtrList` o `CPtrArray`. La nueva clase de colección se hereda de la clase base especificada, y funciones de miembro de la nueva clase utilizan llamadas encapsuladas a los miembros de clase base para exigir la seguridad de tipos.  
  
 Para obtener más información acerca de las plantillas de C++, vea [plantillas](../cpp/templates-cpp.md) en el *referencia del lenguaje C++*.  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Usar plantillas de mapa, lista y matriz Simple  
 Para utilizar las plantillas de colección simple, debe saber qué tipo de datos puede almacenar en estas colecciones y qué parámetros que se usarán en las declaraciones de la colección.  
  
###  <a name="_core_simple_array_and_list_usage"></a>Uso de la lista y matriz simple  
 La matriz simple y la lista de clases, [CArray](../mfc/reference/carray-class.md) y [CList](../mfc/reference/clist-class.md), toman dos parámetros: *tipo* y `ARG_TYPE`. Estas clases pueden almacenar cualquier tipo de datos, que se especifica en el *tipo* parámetro:  
  
-   Tipos de datos fundamentales de C++, como `int`, `char`, y **float**  
  
-   Las clases y estructuras de C++  
  
-   Otros tipos que se definen  
  
 Por comodidad y eficacia, puede usar el `ARG_TYPE` para especificar el tipo de argumentos de función. Normalmente, se especifica `ARG_TYPE` como una referencia al tipo especificado en el *tipo* parámetro. Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]  
  
 El primer ejemplo declara una colección de matriz, `myArray`, que contiene `int`s. El segundo ejemplo declara una colección de lista, `myList`, que almacena `CPerson` objetos. Algunas funciones de miembro de las clases de colección aceptan argumentos cuyo tipo se especifica mediante el `ARG_TYPE` parámetro de plantilla. Por ejemplo, el **agregar** función miembro de clase `CArray` toma una `ARG_TYPE` argumento:  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a>Uso de asignación simple  
 La clase map simple, [CMap](../mfc/reference/cmap-class.md), toma cuatro parámetros: *clave*, `ARG_KEY`, *valor*, y `ARG_VALUE`. Al igual que las clases de matriz y lista, las clases de asignación pueden almacenar cualquier tipo de datos. A diferencia de las matrices y listas, que indizan y ordenan los datos que almacenan, los mapas asocian claves y valores: tener acceso a un valor almacenado en un mapa especificando la clave asociada al valor. El *clave* parámetro especifica el tipo de datos de las claves utilizadas para tener acceso a los datos almacenados en el mapa. Si el tipo de *clave* es una estructura o clase, el `ARG_KEY` parámetro normalmente es una referencia al tipo especificado en *clave*. El *valor* parámetro especifica el tipo de los elementos almacenados en el mapa. Si el tipo de `ARG_VALUE` es una estructura o clase, el `ARG_VALUE` parámetro normalmente es una referencia al tipo especificado en *valor*. Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]  
  
 El primer ejemplo almacena `MY_STRUCT` valores, tiene acceso a ellos mediante `int` claves y devuelve acceso `MY_STRUCT` elementos por referencia. El segundo ejemplo almacena `CPerson` valores, tiene acceso a ellos mediante `CString` claves y devuelve referencias a los elementos que se accede. En este ejemplo podría representar una libreta de direcciones simple, en el que se buscan personas por apellido.  
  
 Dado que el *clave* parámetro es de tipo `CString` y la *KEY_TYPE* parámetro es de tipo `LPCSTR`, las claves se almacenan en el mapa como elementos de tipo `CString` , pero se hace referencia en las funciones como `SetAt` mediante punteros de tipo `LPCSTR`. Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a>Uso de plantillas de la colección de puntero con tipo  
 Para utilizar las plantillas de la colección de puntero con tipo, necesitará saber qué tipos de datos puede almacenar en estas colecciones y qué parámetros que se usarán en las declaraciones de la colección.  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a>Matriz de puntero con tipo y el uso de la lista  
 La matriz de puntero con tipo y la lista de clases, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) y [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), toman dos parámetros: `BASE_CLASS` y *tipo*. Estas clases pueden almacenar cualquier tipo de datos, que se especifica en el *tipo* parámetro. Se derivan de una de las clases de colección no es de plantilla que almacena punteros; Especifique esta clase base en `BASE_CLASS`. Para las matrices, use `CObArray` o `CPtrArray`. Para las listas, use `CObList` o `CPtrList`.  
  
 De hecho, cuando se declara una colección basada en, diga `CObList`, la nueva clase hereda no solo los miembros de su clase base, sino que también declara un número del miembro adicional de seguridad de tipos de funciones y operadores que ayudan a proporcionar seguridad de tipos encapsulando llamadas a los miembros de clase base. Estas encapsulaciones administran todas las conversión de tipos necesaria. Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]  
  
 El primer ejemplo declara una matriz de puntero con tipo, `myArray`, derivado del `CObArray`. La matriz almacena y devuelve punteros a `CPerson` objetos (donde `CPerson` es una clase derivada de `CObject`). Puede llamar a cualquier `CObArray` función miembro, o se puede llamar a la seguridad de tipos nuevos `GetAt` y `ElementAt` las funciones o utilizar la seguridad de tipos **[]** operador.  
  
 El segundo ejemplo declara una lista de puntero con tipo, `myList`, derivado del `CPtrList`. La lista almacena y devuelve punteros a `MY_STRUCT` objetos. Una clase basada en `CPtrList` se utiliza para almacenar punteros a objetos no derivados de `CObject`. `CTypedPtrList`tiene un número de funciones miembro de la seguridad de tipos: `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev`, y `GetAt`.  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a>Uso de mapa de puntero con tipo  
 La clase map de puntero con tipo, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), toma tres parámetros: `BASE_CLASS`, *clave*, y *valor*. El `BASE_CLASS` parámetro especifica la clase del que se deriva de la nueva clase: `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`, y así sucesivamente. *CLAVE* es análogo a *clave* en `CMap`: especifica el tipo de la clave utilizada para las búsquedas. *VALOR* es análogo a *valor* en `CMap`: especifica el tipo de objeto almacenado en el mapa. Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]  
  
 El primer ejemplo es un mapa basado en **CMapPtrToPt**r: usa `CString` claves asignadas a punteros a `MY_STRUCT`. Puede buscar un puntero almacenado mediante una llamada a un tipo seguro `Lookup` función miembro. Puede usar el **[]** operador para buscar un puntero almacenado y agregarlo si no se encuentra. Y puede recorrer en iteración la asignación mediante la seguridad de tipos `GetNextAssoc` función. También puede llamar a otro miembro funciones de la clase `CMapPtrToPtr`.  
  
 El segundo ejemplo es un mapa basado en **CMapStringToO**b, utiliza las claves de cadena asignadas a punteros almacenados a `CMyObject` objetos. Puede usar los mismos miembros con seguridad de tipos se describe en el párrafo anterior, o puede llamar a los miembros de clase `CMapStringToOb`.  
  
> [!NOTE]
>  Si especifica un **clase** o `struct` escriba para la *valor* parámetro, en lugar de un puntero o referencia al tipo, la clase o estructura debe tener un constructor de copias.  
  
 Para obtener más información, consulte [cómo crear una colección con seguridad de tipos](../mfc/how-to-make-a-type-safe-collection.md).  
  
## <a name="see-also"></a>Vea también  
 [Colecciones](../mfc/collections.md)

