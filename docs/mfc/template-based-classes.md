---
title: "Clases basadas en plantillas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], clases"
  - "matrices [C++], punteros"
  - "matrices [C++], basadas en plantillas"
  - "CArray (clase), clases basadas en plantillas"
  - "CList (clase), clases basadas en plantillas"
  - "clases de colección, basadas en plantillas"
  - "colecciones, puntero con tipo"
  - "CTypedPtrArray (clase), clases basadas en plantillas"
  - "CTypedPtrList (clase), clases basadas en plantillas"
  - "CTypedPtrMap (clase), clases basadas en plantillas"
  - "clases de la colección MFC, basadas en plantillas"
  - "punteros, colecciones de tipado"
  - "clases de colección de matriz simple"
  - "clases de colección de lista simple"
  - "colecciones basadas en plantillas simples"
  - "clases de colección basadas en plantillas"
  - "punteros con tipo"
  - "punteros con tipo, colecciones de"
  - "colecciones de tipo seguras"
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases basadas en plantillas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica las clases de colección plantilla\- basadas tipo\- seguras en MFC versión 3.0 y posterior.  Mediante estas plantillas crear colecciones con seguridad de tipos es más conveniente y ayuda proporcionan seguridad de tipos más eficazmente que utilizar las clases de colección no basadas en las plantillas.  
  
 MFC predefine dos categorías de colecciones plantilla\-basadas:  
  
-   [Matriz simple, lista, y clases asignadas](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [Matrices, listas, y mapas de punteros escritos](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 Las clases de colección simples todas se derivan de la clase `CObject`, por lo que heredan la serialización, la creación dinámica, y otras propiedades de `CObject`.  Las clases de colección con tipo de puntero es necesario especificar la clase que se deriva de \)que debe ser una de las colecciones de puntero de segunda predefinidas por MFC, como `CPtrList` o `CPtrArray`.  La nueva clase de colección hereda de la clase base especificada, y las llamadas encapsuladas uso de las funciones miembro de la nueva clase a los miembros de la clase base para aplicar la seguridad de tipos.  
  
 Para obtener más información sobre las plantillas de C\+\+, vea [Plantillas](../cpp/templates-cpp.md) en *la referencia del lenguaje C\+\+*.  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> Mediante la matriz, la lista, plantillas de mapa sencillo  
 Para utilizar plantillas simples de la colección, debe saber qué tipo de datos puede almacenar en estas colecciones y qué parámetros a utilizar en las declaraciones de la colección.  
  
###  <a name="_core_simple_array_and_list_usage"></a> Matriz simple y Uso enumerado  
 La matriz simple y clases mostradas, [CArray](../mfc/reference/carray-class.md) y [CList](../mfc/reference/clist-class.md), toman dos parámetros: *TYPE* y `ARG_TYPE`.  Estas clases pueden almacenar cualquier tipo de datos, que se especifica en *el parámetro de tipo* :  
  
-   Tipos de datos fundamentales de C\+\+, como `int`, `char`, y **flotante**  
  
-   Estructuras y clases de C\+\+  
  
-   Otros tipos que defina  
  
 Para mayor comodidad y la eficacia, puede utilizar el parámetro de `ARG_TYPE` para especificar el tipo de argumentos de función.  Normalmente, se especifica `ARG_TYPE` como referencia al tipo que se llama en *el parámetro de tipo* .  Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/CPP/template-based-classes_1.cpp)]  
  
 El primer ejemplo declara una colección de matriz, `myArray`, que contiene s para `int`.  El segundo ejemplo declara una colección de listas, `myList`, que almacena los objetos de `CPerson` .  Algunas funciones miembro de las clases de colección toman argumentos del parámetro de plantilla de `ARG_TYPE` especifica un tipo.  Por ejemplo, la función miembro de **Add** de la clase `CArray` toma un argumento de `ARG_TYPE` :  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/CPP/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a> Uso sencillo de mapa  
 La clase simple de mapa, [CMap](../mfc/reference/cmap-class.md), toma cuatro parámetros: *TECLA*, `ARG_KEY`, *DEFAULT*, y `ARG_VALUE`.  Como matriz y clases mostradas, las clases de mapa pueden almacenar cualquier tipo de datos.  A diferencia de matrices y listas, que el índice y orden los datos que almacena, las claves de asociar maps y valores: Tiene acceso a un valor en un mapa especificando la clave asociada al valor.  El parámetro *DOMINANTE* especifica el tipo de datos de las claves utilizadas para tener acceso a los datos del mapa.  Si el tipo *de TECLA* es una estructura o clase, el parámetro de `ARG_KEY` es normalmente una referencia al tipo especificado en *TECLA*.  El parámetro *de QUE* especifica el tipo de los elementos almacenados en el mapa.  Si el tipo de `ARG_VALUE` es una estructura o clase, el parámetro de `ARG_VALUE` es normalmente una referencia al tipo especificado en *DEFAULT*.  Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/CPP/template-based-classes_3.cpp)]  
  
 El primer ejemplo almacena los valores de `MY_STRUCT` , se tiene acceso por las claves de `int` , y devuelve los elementos desde `MY_STRUCT` por referencia.  El segundo ejemplo almacena los valores de `CPerson` , se tiene acceso por las claves de `CString` , y devuelve referencias a elementos acceso.  Este ejemplo podría representar una libreta de direcciones simple, en la que se busca a personas por apellido.  
  
 Dado que el parámetro *DOMINANTE* es de `CString` escrito y el parámetro *de KEY\_TYPE* es de `LPCSTR`tipo, las claves se almacenan en el mapa como elementos de `CString` tipo pero se hace referencia en funciones como `SetAt` con punteros de `LPCSTR`escrito.  Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/CPP/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> Mediante plantillas de la colección de Escribir\- puntero  
 Para utilizar las plantillas de la colección de escribir\- puntero, debe saber qué tipo de datos puede almacenar en estas colecciones y qué parámetros a utilizar en las declaraciones de la colección.  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> Matriz de Escribir\- puntero y Uso enumerado  
 La matriz y las clases mostradas, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) y [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)de escribir\- puntero, toman dos parámetros: `BASE_CLASS` y *TYPE*.  Estas clases pueden almacenar cualquier tipo de datos, que se especifica en *el parámetro de tipo* .  Se derivan de alguna de las clases de colección de segunda que almacena punteros; especifica esta clase base en `BASE_CLASS`.  Para las matrices, utilice `CObArray` o `CPtrArray`.  Para las listas, utilice `CObList` o `CPtrList`.  
  
 En efecto, cuando se declara una colección basada en, supongamos `CObList`, la nueva clase no solo hereda miembros de su clase base, pero también declara a varios miembro tipo\- seguro adicional las funciones y operadores que ayuda proporciona seguridad de tipos encapsulan llamadas a miembros de clase base.  Estas encapsulaciones administran toda la conversión de tipos necesaria.  Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/CPP/template-based-classes_5.cpp)]  
  
 El primer ejemplo se declara una matriz de escribir\- puntero, `myArray`, derivado de `CObArray`.  La matriz almacena y devuelve punteros a objetos de `CPerson` \(donde es una clase `CPerson` derivada de `CObject`\).  Puede llamar a la función miembro de `CObArray` , o a nuevos `GetAt` y funciones tipo\- seguros de `ElementAt` o utilizar el operador tipo\- seguro de \#\#\#\[\#\#\#\].  
  
 El segundo ejemplo declara una lista de escribir\- puntero, `myList`, derivado de `CPtrList`.  La lista almacena y devuelve punteros a objetos de `MY_STRUCT` .  Una clase basada en `CPtrList` se utiliza para almacenar los punteros a objetos no derivados de `CObject`.  `CTypedPtrList` tiene varias funciones tipo\- seguras de miembro: `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev`, y `GetAt`.  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a> Uso del mapa del Escribir\- puntero  
 La clase del mapa del escribir\- puntero, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), toma tres parámetros: `BASE_CLASS`, *TECLA*, y *DEFAULT*.  El parámetro de `BASE_CLASS` especifica la clase de la que deriva la nueva clase: `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`, etc.  *La TECLA* es análoga *CERRAR* en `CMap`: Especifica el tipo de la clave utilizada para las búsquedas.  *El QUE* es análogo *a DEFAULT* en `CMap`: Especifica el tipo de objeto en el mapa.  Por ejemplo:  
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/CPP/template-based-classes_6.cpp)]  
  
 El primer ejemplo es un mapa según la r de **CMapPtrToPt**— utiliza las teclas de `CString` asignadas a punteros a `MY_STRUCT`.  Puede buscar un puntero almacenado llamando a una función tipo\- segura del miembro de `Lookup` .  Puede utilizar el operador de \#\#\#\[\#\#\#\]para buscar un puntero almacenado y agregarlo si no encontrado.  Y puede recorrer el mapa mediante la función tipo\- segura de `GetNextAssoc` .  También puede llamar a otras funciones miembro de clases `CMapPtrToPtr`.  
  
 El segundo ejemplo es un mapa según el b **CMapStringToO**— utilizan claves de cadena asignadas a punteros almacenados en los objetos de `CMyObject` .  Puede utilizar los mismos miembros tipo\- seguros descritos en el párrafo anterior, o puede llamar a los miembros de la clase `CMapStringToOb`.  
  
> [!NOTE]
>  Si especifica **clase** o `struct` escribe para el parámetro *de DEFAULT* , en lugar de un puntero o una referencia al tipo, la clase o estructura debe tener un constructor de copia.  
  
 Para obtener más información, vea [Cómo crear una colección de tipo](../mfc/how-to-make-a-type-safe-collection.md).  
  
## Vea también  
 [Colecciones](../mfc/collections.md)