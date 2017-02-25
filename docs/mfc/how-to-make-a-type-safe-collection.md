---
title: "C&#243;mo: Crear una colecci&#243;n con seguridad de tipos | Microsoft Docs"
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
  - "clases de colección, derivar de funciones que no son de la plantilla"
  - "clases de colección, basadas en plantillas"
  - "clases de colección, seguridad de tipos"
  - "serialización [C++], clases de colección"
  - "SerializeElements (función)"
  - "seleccionar elementos de clase de colección"
  - "colecciones de tipo seguras"
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# C&#243;mo: Crear una colecci&#243;n con seguridad de tipos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo hacer que las colecciones con seguridad de tipos para por tipos de datos.  Entre los temas se incluyen los siguientes:  
  
-   [Mediante las clases plantilla\- basadas para la seguridad de tipos](#_core_using_template.2d.based_classes_for_type_safety)  
  
-   [Implementar funciones auxiliares](#_core_implementing_helper_functions)  
  
-   [Utilizar clases de colección de segunda](#_core_using_nontemplate_collection_classes)  
  
 La biblioteca Microsoft Foundation Class proporciona colecciones con seguridad de tipos predefinidas basadas en las plantillas de C\+\+.  Porque son plantillas, la ayuda de estas clases proporcionan seguridad de tipos y facilidad de uso sin la porque no es necesario y otro trabajo adicional que surgen al utilizar una clase que no es de plantilla con este fin.  El ejemplo [GET](../top/visual-cpp-samples.md) de MFC ilustra el uso de clases de colección plantilla\- basadas en una aplicación MFC.  Utilice normalmente estas clases siempre que escribir nuevo código de colecciones.  
  
##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> Mediante las clases Plantilla\- basadas para la seguridad de tipos  
  
#### Para utilizar clases plantilla\-basadas  
  
1.  Declare una variable de tipo de clase de colección.  Por ejemplo:  
  
     [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_1.cpp)]  
  
2.  Llama a las funciones miembro del objeto de colección.  Por ejemplo:  
  
     [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_2.cpp)]  
  
3.  En caso necesario, implemente [funciones auxiliares](../mfc/reference/collection-class-helpers.md) y [SerializeElements](../Topic/SerializeElements.md).  Para obtener información sobre la implementación de estas funciones, vea [Implementar funciones auxiliares](#_core_implementing_helper_functions).  
  
 En este ejemplo se muestra la declaración de una lista de enteros.  El primer parámetro del paso 1 es el tipo de datos almacenados como elementos de la lista.  El segundo parámetro especifica a cómo se van pasado y volver de las funciones miembro de clases de colección, como **Add** y `GetAt`.  
  
##  <a name="_core_implementing_helper_functions"></a> Implementar funciones auxiliares  
 Las clases de colección plantilla\- basadas `CArray`, `CList`, y funciones globales auxiliares de uso cinco de `CMap` que puede personalizar según sea necesario para la clase de colección derivada.  Para obtener información sobre estas funciones auxiliares, vea [Aplicaciones auxiliares de la clase de colección](../mfc/reference/collection-class-helpers.md) en *la referencia de MFC*.  La implementación de la función de la serialización es necesaria para la mayoría usos de las clases de colección plantilla\- basadas en.  
  
###  <a name="_core_serializing_elements"></a> Serialización de elementos  
 `CArray`, `CList`, y las clases de `CMap` llama `SerializeElements` para guardar elementos de la colección a o para leer de un archivo.  
  
 La implementación predeterminada de la función auxiliar de `SerializeElements` realiza una escritura bit a bit de los objetos al archivo, o una lectura bit a bit del archivo a los objetos, dependiendo de si los objetos se están almacenando en o se recupera del archivo.  Reemplace `SerializeElements` si esta acción no es adecuado.  
  
 Si la colección almacena objetos derivados de `CObject` y utilice la macro de `IMPLEMENT_SERIAL` en la implementación de la clase de elemento de la colección, puede aprovechar la funcionalidad de serialización compilada en `CArchive` y `CObject`:  
  
 [!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_3.cpp)]  
  
 Los operadores sobrecargados de inserción para `CArchive` llama `CObject::Serialize` \(o un reemplazo de esa función\) para cada objeto de **CPerson** .  
  
##  <a name="_core_using_nontemplate_collection_classes"></a> Mediante las clases de colección de Segunda  
 MFC también admite las clases de colección introducidas con la versión 1.0 de MFC.  Estas clases no se basan en las plantillas.  Se pueden utilizar para contener datos de los tipos admitidos `CObject*`, **UINT**, `DWORD`, y `CString`.  Puede utilizar estas colecciones predefinidas \(como `CObList`\) para contener colecciones de cualquier objeto derivado de `CObject`.  MFC también ofrece otras colecciones predefinidas para detener tipos primitivos como **UINT** y punteros vacíos \(`void`\*\).  Sin embargo, en general es a menudo útil definir dispone de colecciones con seguridad de tipos para contener objetos de una clase más específica y sus derivados.  Observe que lo hace con las clases de colección no basadas en las plantillas es más trabajo que utilizar las clases plantilla\- basadas en.  
  
 Hay dos maneras de crear colecciones con seguridad de tipos con colecciones de segunda:  
  
1.  Usar las colecciones que no es de plantilla, con la conversión escrito en caso necesario.  Este es el método más fácil.  
  
2.  Derive de y extender una colección de tipo que no es de plantilla.  
  
#### Para utilizar las colecciones que no es de plantilla con la conversión de tipo  
  
1.  Utilice una de las clases de segunda, como `CWordArray`, directamente.  
  
     Por ejemplo, puede crear `CWordArray` y agregar cualquier valor de 32 bits a, después se recupera.  No hay nada más hacer.  Simplemente utiliza la funcionalidad predefinida.  
  
     También puede utilizar una colección predefinida, como `CObList`, para almacenar cualquier objeto derivado de `CObject`.  Una colección de `CObList` se define para contener punteros a `CObject`.  Cuando se recupera un objeto de lista, puede que tenga que convertir el resultado al tipo adecuado como las funciones de `CObList` devuelven punteros a `CObject`.  Por ejemplo, si almacena los objetos de `CPerson` en una colección de `CObList` , tiene que convertir un elemento recuperado para ser un puntero a un objeto de `CPerson` .  El ejemplo siguiente utiliza una colección de `CObList` para contener los objetos de `CPerson` :  
  
     [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_4.cpp)]  
  
     Esta técnica de utilizar un tipo de colección predefinido y release según sea necesario puede ser adecuada para muchas de la colección.  Si necesita funcionalidad adicional o más seguridad de tipos, utilice una clase plantilla\- basada, o siga el siguiente procedimiento.  
  
#### Para derivar y extender una colección de tipo que no es de plantilla  
  
1.  Derive poseen la clase de colección a partir de una de las clases predefinidas que no es de plantilla.  
  
     Cuando se deriva de la clase, puede agregar funciones de contenedor tipo\- seguras para proporcionar una interfaz tipo\- segura a funciones existentes.  
  
     Por ejemplo, si se derivó una lista de `CObList` para contener los objetos de `CPerson` , puede agregar funciones de contenedor `AddHeadPerson` y `GetHeadPerson`, como se muestra a continuación.  
  
     [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_5.h)]  
  
     Estas invocaciones de funciones proporcionan una manera tipo\- segura de agregar y recuperar los objetos de `CPerson` de lista derivada.  Puede ver que para la función de `GetHeadPerson` , se encapsulan simplemente la conversión de tipos.  
  
     También puede agregar nueva funcionalidad definiendo las nuevas funciones que amplían las funciones de colección en lugar de simplemente ajustando la funcionalidad existente en contenedores tipo\- seguros.  Por ejemplo, el caso [Eliminar objetos Todo en una colección de CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) describe una función para eliminar todos los objetos incluidos en una lista.  Esta función se puede agregar a la clase derivada como función miembro.  
  
## Vea también  
 [Colecciones](../mfc/collections.md)