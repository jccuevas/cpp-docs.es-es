---
title: 'Cómo: crear una colección con seguridad de tipos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bcd1fbce9e6dda649da8fe2e53fc7dc70db1da33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354444"
---
# <a name="how-to-make-a-type-safe-collection"></a>Cómo: Crear una colección con seguridad de tipos
En este artículo se explica cómo hacer que las colecciones con seguridad de tipos para sus propios tipos de datos. Entre los temas se incluyen los siguientes:  
  
-   [Utilizar clases basadas en plantillas de seguridad de tipos](#_core_using_template.2d.based_classes_for_type_safety)  
  
-   [Implementar funciones auxiliares](#_core_implementing_helper_functions)  
  
-   [Utilizar clases de colección no es de plantilla](#_core_using_nontemplate_collection_classes)  
  
 La biblioteca Microsoft Foundation Class proporciona colecciones con seguridad de tipos predefinidas basadas en plantillas de C++. Dado que son plantillas, estas clases ayudan a proporcionar seguridad de tipos y la facilidad de uso sin la conversión de tipos y otros trabajos adicionales relacionados con el uso de una clase sin plantilla para este propósito. El ejemplo MFC [recopilar](../visual-cpp-samples.md) muestra el uso de clases de colección basadas en plantillas en una aplicación MFC. En general, utilice estas clases cada vez que escriba código nuevo de colecciones.  
  
##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> Utilizar clases basadas en plantillas de seguridad de tipos  
  
#### <a name="to-use-template-based-classes"></a>Utilizar clases basadas en plantillas  
  
1.  Declare una variable del tipo de la clase de colección. Por ejemplo:  
  
     [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]  
  
2.  Llamar al miembro de las funciones del objeto de colección. Por ejemplo:  
  
     [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]  
  
3.  Si es necesario, implemente el [funciones auxiliares](../mfc/reference/collection-class-helpers.md) y [SerializeElements](../mfc/reference/collection-class-helpers.md#serializeelements). Para obtener información sobre la implementación de estas funciones, vea [implementar funciones auxiliares](#_core_implementing_helper_functions).  
  
 En este ejemplo se muestra la declaración de una lista de enteros. El primer parámetro en el paso 1 es el tipo de datos que se almacenan como elementos de la lista. El segundo parámetro especifica cómo los datos se pasarse y devueltos por las funciones miembro de la clase de colección, como **agregar** y `GetAt`.  
  
##  <a name="_core_implementing_helper_functions"></a> Implementar funciones auxiliares  
 Las clases de colección basadas en plantillas `CArray`, `CList`, y `CMap` utilizar cinco funciones auxiliares globales que se pueden personalizar según sea necesario para la clase de colección derivada. Para obtener información sobre estas funciones auxiliares, vea [aplicaciones auxiliares de clase de colección](../mfc/reference/collection-class-helpers.md) en el *referencia de MFC*. Implementación de la función de serialización es necesario para la mayoría de los usos de las clases de colección basadas en plantillas.  
  
###  <a name="_core_serializing_elements"></a> Seleccionar elementos  
 El `CArray`, `CList`, y `CMap` clases llamada `SerializeElements` para almacenar elementos de colección o leerlos desde un archivo.  
  
 La implementación predeterminada de la `SerializeElements` función auxiliar realiza una escritura bit a bit de los objetos en el archivo o lee desde el archivo a los objetos, dependiendo de si los objetos se almacenan en un bit a bit o se recupera desde el archivo. Invalidar `SerializeElements` si esta acción no es adecuada.  
  
 Si la colección almacena objetos derivados de `CObject` y usar el `IMPLEMENT_SERIAL` macro en la implementación de la clase de elemento de colección, se puede aprovechar la funcionalidad de serialización integrada en `CArchive` y `CObject`:  
  
 [!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]  
  
 Los operadores de inserción sobrecargados para `CArchive` llamar a `CObject::Serialize` (o una función de reemplazo) para cada **CPerson** objeto.  
  
##  <a name="_core_using_nontemplate_collection_classes"></a> Utilizar clases de colección no es de plantilla  
 MFC también es compatible con las clases de colección introducidas con la versión 1.0 de MFC. Estas clases no se basan en plantillas. Pueden usarse para contener datos de los tipos admitidos `CObject*`, **UINT**, `DWORD`, y `CString`. Puede usar estas colecciones predefinidas (como `CObList`) para contener colecciones de cualquier objeto derivado de `CObject`. MFC también proporciona otras colecciones predefinidas para contener los tipos primitivos como **UINT** y anular punteros (`void`*). En general, sin embargo, a menudo resulta útil definir sus propias colecciones con seguridad de tipos para almacenar los objetos de una clase más específica y sus derivados. Tenga en cuenta que si lo hace, con las clases de colección no basada en plantillas es más trabajo que el uso de las clases basadas en plantillas.  
  
 Hay dos maneras de crear colecciones con seguridad de tipos con las colecciones sin plantilla:  
  
1.  Utilice las colecciones sin plantilla, con conversión de tipo si es necesario. Se trata de un enfoque más sencillo.  
  
2.  Derivar y ampliar con una colección con seguridad de tipos sin plantilla.  
  
#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Para usar las colecciones sin plantilla con conversión de tipos  
  
1.  Use una de las clases sin plantilla, como `CWordArray`, directamente.  
  
     Por ejemplo, puede crear un `CWordArray` y agregarle los valores de 32 bits, a continuación, recuperarlos. No hay nada más que hacer. Simplemente utilice la funcionalidad predefinida.  
  
     También puede utilizar una colección predefinida, como `CObList`, para contener cualquier objeto derivado de `CObject`. A `CObList` se define una colección para almacenar punteros a `CObject`. Cuando se recupera un objeto de la lista, tendrá que convertir el resultado al tipo apropiado desde el `CObList` funciones devuelven punteros a `CObject`. Por ejemplo, si almacena `CPerson` objetos en un `CObList` colección, tiene que convertir un elemento recuperado para que sea un puntero a un `CPerson` objeto. En el ejemplo siguiente se usa un `CObList` colección donde se almacenan `CPerson` objetos:  
  
     [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]  
  
     Esta técnica del uso de un tipo de colección predefinida y convertir según sea necesario puede ser adecuada para muchas de sus necesidades de la colección. Si necesita una mayor funcionalidad o más seguridad de tipos, utilice una clase basada en plantilla o siga el procedimiento siguiente.  
  
#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Para derivar y extender una colección con seguridad de tipos sin plantilla  
  
1.  Derive su propia clase de colección de una de las clases sin plantilla predefinida.  
  
     Al derivar la clase, puede agregar funciones de contenedor de seguridad de tipos para proporcionar una interfaz de seguridad de tipos para las funciones existentes.  
  
     Por ejemplo, si ha derivado una lista de `CObList` para contener `CPerson` objetos, podría agregar las funciones contenedoras `AddHeadPerson` y `GetHeadPerson`, tal y como se muestra a continuación.  
  
     [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]  
  
     Estas funciones contenedoras proporcionan una manera de seguridad de tipos para agregar y recuperar `CPerson` objetos de la lista derivada. Puede ver que para el `GetHeadPerson` función, simplemente se está encapsulando la conversión de tipos.  
  
     También puede agregar nueva funcionalidad definiendo nuevas funciones que amplían las capacidades de la colección, en lugar de ajustar simplemente la funcionalidad existente en contenedores con seguridad de tipos. Por ejemplo, el artículo [eliminar todos los objetos de una colección CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) describe una función para eliminar todos los objetos incluidos en una lista. Esta función puede agregarse a la clase derivada como una función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Colecciones](../mfc/collections.md)

