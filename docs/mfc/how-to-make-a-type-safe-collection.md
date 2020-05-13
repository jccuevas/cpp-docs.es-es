---
title: 'Cómo: Crear una colección con seguridad de tipos'
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: 1901100996a776244b57efe0951795ceec3c630a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377256"
---
# <a name="how-to-make-a-type-safe-collection"></a>Cómo: Crear una colección con seguridad de tipos

En este artículo se explica cómo crear colecciones con seguridad de tipos para sus propios tipos de datos. Contenido de los temas:

- [Uso de clases basadas en plantillas para la seguridad de tipos](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementación de funciones auxiliares](#_core_implementing_helper_functions)

- [Uso de clases de colección que no son de plantilla](#_core_using_nontemplate_collection_classes)

La biblioteca Microsoft Foundation Class proporciona colecciones predefinidas con seguridad de tipos basadas en plantillas C++. Dado que son plantillas, estas clases ayudan a proporcionar seguridad de tipos y facilidad de uso sin el tipo de conversión y otro trabajo adicional involucrado en el uso de una clase que no es de plantilla para este propósito. El ejemplo de MFC [COLLECT](../overview/visual-cpp-samples.md) muestra el uso de clases de colección basadas en plantillas en una aplicación MFC. En general, use estas clases cada vez que escriba código de colecciones nuevos.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>Uso de clases basadas en plantillas para la seguridad de tipos

#### <a name="to-use-template-based-classes"></a>Para usar clases basadas en plantillas

1. Declare una variable del tipo de clase de colección. Por ejemplo:

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Llame a las funciones miembro del objeto de colección. Por ejemplo:

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. Si es necesario, implemente las [funciones auxiliares](../mfc/reference/collection-class-helpers.md) y [SerializeElements](../mfc/reference/collection-class-helpers.md#serializeelements). Para obtener información sobre la implementación de estas funciones, consulte Implementación de [funciones auxiliares](#_core_implementing_helper_functions).

En este ejemplo se muestra la declaración de una lista de enteros. El primer parámetro del paso 1 es el tipo de datos almacenados como elementos de la lista. El segundo parámetro especifica cómo se deben pasar los datos y devolverlos `Add` desde `GetAt`las funciones miembro de la clase de colección, como y .

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>Implementación de funciones auxiliares

Las clases de `CArray` `CList`colección `CMap` basadas en plantillas , , y usar cinco funciones auxiliares globales que puede personalizar según sea necesario para la clase de colección derivada. Para obtener información sobre estas funciones auxiliares, vea auxiliares de [clase de colección](../mfc/reference/collection-class-helpers.md) en la *referencia de MFC*. La implementación de la función de serialización es necesaria para la mayoría de los usos de las clases de colección basadas en plantillas.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>Serialización de elementos

Las `CArray` `CList`clases `CMap` `SerializeElements` , , y para almacenar elementos de colección en un archivo o leerlos.

La implementación `SerializeElements` predeterminada de la función auxiliar realiza una escritura bit a bit desde los objetos en el archivo, o una lectura bit a bit del archivo a los objetos, dependiendo de si los objetos se almacenan en o se recuperan del archivo. Invalide `SerializeElements` si esta acción no es adecuada.

Si la colección almacena `CObject` objetos `IMPLEMENT_SERIAL` derivados y utiliza la macro en la implementación de la `CArchive` `CObject`clase de elemento de colección, puede aprovechar la funcionalidad de serialización integrada en y:

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Los operadores de `CArchive` `CObject::Serialize` inserción sobrecargados para la `CPerson` llamada (o una invalidación de esa función) para cada objeto.

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>Uso de clases de colección que no son de plantilla

MFC también admite las clases de colección introducidas con MFC versión 1.0. Estas clases no se basan en plantillas. Se pueden utilizar para contener datos `CObject*` `UINT`de `DWORD`los `CString`tipos admitidos, , , y . Puede utilizar estas colecciones predefinidas (como `CObList`) para contener `CObject`colecciones de cualquier objeto derivado de . MFC también proporciona otras colecciones predefinidas `UINT` para contener`void`tipos primitivos como y punteros void ( *). En general, sin embargo, a menudo es útil definir sus propias colecciones con seguridad de tipos para contener objetos de una clase más específica y sus derivados. Tenga en cuenta que hacerlo con las clases de colección no basadas en plantillas es más trabajo que usar las clases basadas en plantillas.

Hay dos formas de crear colecciones con seguridad de tipos con las colecciones que no son de plantilla:

1. Utilice las colecciones que no son de plantilla, con la conversión de tipos si es necesario. Este es el enfoque más fácil.

1. Derive de y extienda una colección con seguridad de tipos que no sea de plantilla.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Para utilizar las colecciones que no son de plantilla con la conversión de tipos

1. Utilice una de las clases `CWordArray`que no son de plantilla, como , directamente.

   Por ejemplo, puede `CWordArray` crear un valor de 32 bits y, a continuación, recuperarlos. No hay nada más que hacer. Sólo tiene que utilizar la funcionalidad predefinida.

   También puede utilizar una colección `CObList`predefinida, como , `CObject`para contener los objetos derivados de . Una `CObList` colección se define `CObject`para contener punteros a . Al recuperar un objeto de la lista, es posible que tenga `CObList` que convertir `CObject`el resultado al tipo adecuado, ya que las funciones devuelven punteros a . Por ejemplo, si `CPerson` almacena `CObList` objetos en una colección, debe convertir un `CPerson` elemento recuperado para que sea un puntero a un objeto. En el ejemplo `CObList` siguiente `CPerson` se utiliza una colección para contener objetos:

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Esta técnica de usar un tipo de colección predefinido y la fundición según sea necesario puede ser adecuada para muchas de sus necesidades de recopilación. Si necesita más funcionalidad o más seguridad de tipos, utilice una clase basada en plantilla o siga el siguiente procedimiento.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Para derivar y ampliar una colección con seguridad de tipos que no sea de plantilla

1. Derive su propia clase de colección de una de las clases predefinidas que no son de plantilla.

   Al derivar la clase, puede agregar funciones contenedoras con seguridad de tipos para proporcionar una interfaz con seguridad de tipos a las funciones existentes.

   Por ejemplo, si ha derivado `CObList` una `CPerson` lista de objetos `AddHeadPerson` de `GetHeadPerson`retención, puede agregar las funciones contenedoras y , como se muestra a continuación.

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Estas funciones contenedoras proporcionan una forma `CPerson` segura de agregar y recuperar objetos de la lista derivada. Puede ver que `GetHeadPerson` para la función, simplemente está encapsulando la conversión de tipos.

   También puede agregar nueva funcionalidad definiendo nuevas funciones que amplían las capacidades de la colección en lugar de simplemente ajustar la funcionalidad existente en contenedores con seguridad de tipos. Por ejemplo, el artículo [Eliminación de todos los objetos de una colección CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md) describe una función para eliminar todos los objetos contenidos en una lista. Esta función se podría agregar a la clase derivada como una función miembro.

## <a name="see-also"></a>Consulte también

[Colecciones](../mfc/collections.md)
