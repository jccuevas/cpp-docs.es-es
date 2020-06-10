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
ms.openlocfilehash: 6ee4603f03ef8a95c218b0fe040e9606aab99ebb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620009"
---
# <a name="how-to-make-a-type-safe-collection"></a>Cómo: Crear una colección con seguridad de tipos

En este artículo se explica cómo crear colecciones con seguridad de tipos para sus propios tipos de datos. Contenido de los temas:

- [Usar clases basadas en plantillas para la seguridad de tipos](#_core_using_template.2d.based_classes_for_type_safety)

- [Implementar funciones auxiliares](#_core_implementing_helper_functions)

- [Usar clases de colección que no son de plantilla](#_core_using_nontemplate_collection_classes)

En el biblioteca MFC se proporcionan colecciones con seguridad de tipos predefinidas basadas en plantillas de C++. Dado que son plantillas, estas clases ayudan a proporcionar seguridad de tipos y facilidad de uso sin la conversión de tipos y otros trabajos adicionales implicados en el uso de una clase que no es de plantilla para este fin. En el ejemplo de MFC [Collect](../overview/visual-cpp-samples.md) se muestra el uso de clases de colección basadas en plantillas en una aplicación MFC. En general, use estas clases cada vez que escriba código de colecciones nuevo.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a>Usar clases basadas en plantillas para la seguridad de tipos

#### <a name="to-use-template-based-classes"></a>Para usar clases basadas en plantillas

1. Declare una variable del tipo de clase de colección. Por ejemplo:

   [!code-cpp[NVC_MFCCollections#7](codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. Llame a las funciones miembro del objeto de colección. Por ejemplo:

   [!code-cpp[NVC_MFCCollections#8](codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. Si es necesario, implemente las [funciones auxiliares](reference/collection-class-helpers.md) y [SerializeElements](reference/collection-class-helpers.md#serializeelements). Para obtener información sobre la implementación de estas funciones, vea [implementar funciones auxiliares](#_core_implementing_helper_functions).

En este ejemplo se muestra la declaración de una lista de enteros. El primer parámetro del paso 1 es el tipo de datos almacenados como elementos de la lista. El segundo parámetro especifica cómo se van a pasar y devolver los datos de las funciones miembro de la clase de colección, como `Add` y `GetAt` .

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a>Implementar funciones auxiliares

Las clases de colección basadas en plantilla `CArray` , `CList` y `CMap` utilizan cinco funciones auxiliares globales que se pueden personalizar según sea necesario para la clase derivada de la colección. Para obtener información sobre estas funciones auxiliares, vea [aplicaciones auxiliares de clase de colección](reference/collection-class-helpers.md) en la *referencia de MFC*. La implementación de la función de serialización es necesaria para la mayoría de los usos de las clases de colección basadas en plantillas.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a>Serializar elementos

Las `CArray` `CList` clases, y `CMap` llaman `SerializeElements` a para almacenar elementos de la colección en un archivo o leerlos de él.

La implementación predeterminada de la `SerializeElements` función auxiliar realiza una escritura bit a bit de los objetos en el archivo o una lectura bit a bit del archivo a los objetos, en función de si los objetos se almacenan o se recuperan del archivo. Invalide `SerializeElements` si esta acción no es adecuada.

Si la colección almacena objetos derivados de `CObject` y usa la `IMPLEMENT_SERIAL` macro en la implementación de la clase de elemento de colección, puede aprovechar la funcionalidad de serialización integrada en `CArchive` y `CObject` :

[!code-cpp[NVC_MFCCollections#9](codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

Los operadores de inserción sobrecargados para la `CArchive` llamada `CObject::Serialize` (o una invalidación de esa función) para cada `CPerson` objeto.

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a>Usar clases de colección que no son de plantilla

MFC también admite las clases de colección introducidas con MFC versión 1,0. Estas clases no se basan en plantillas. Se pueden usar para contener datos de los tipos admitidos `CObject*` , `UINT` , `DWORD` y `CString` . Puede usar estas colecciones predefinidas (como `CObList` ) para contener colecciones de cualquier objeto derivado de `CObject` . MFC también proporciona otras colecciones predefinidas para contener tipos primitivos como `UINT` y punteros void ( `void` *). En general, sin embargo, a menudo resulta útil definir colecciones con seguridad de tipos para contener objetos de una clase más específica y sus derivados. Tenga en cuenta que, al hacerlo, las clases de colección no basadas en plantillas son más trabajo que el uso de las clases basadas en plantillas.

Hay dos maneras de crear colecciones con seguridad de tipos con las colecciones que no son de plantilla:

1. Use las colecciones que no son de plantilla, con conversión de tipos si es necesario. Este es el enfoque más sencillo.

1. Derive de y extienda una colección con seguridad de tipos que no sea de plantilla.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>Para usar las colecciones que no son de plantilla con conversión de tipos

1. Use una de las clases que no son de plantilla, como `CWordArray` , directamente.

   Por ejemplo, puede crear un `CWordArray` y agregarle valores de 32 bits y, a continuación, recuperarlos. No hay nada más que hacer. Solo se usa la funcionalidad predefinida.

   También puede usar una colección predefinida, como `CObList` , para contener cualquier objeto derivado de `CObject` . `CObList`Se define una colección para contener punteros a `CObject` . Al recuperar un objeto de la lista, es posible que tenga que convertir el resultado al tipo adecuado, ya que las `CObList` funciones devuelven punteros a `CObject` . Por ejemplo, si almacena `CPerson` objetos en una `CObList` colección, tendrá que convertir un elemento recuperado para que sea un puntero a un `CPerson` objeto. En el ejemplo siguiente se usa una `CObList` colección para contener `CPerson` objetos:

   [!code-cpp[NVC_MFCCollections#10](codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   Esta técnica de usar un tipo de colección predefinida y convertirla según sea necesario puede ser adecuada para muchas de las necesidades de la colección. Si necesita más funcionalidad o más seguridad de tipos, use una clase basada en plantilla o siga el procedimiento siguiente.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>Para derivar y extender una colección con seguridad de tipos que no es de plantilla

1. Derive su propia clase de colección de una de las clases predefinidas que no son de plantilla.

   Al derivar la clase, puede agregar funciones contenedoras con seguridad de tipos para proporcionar una interfaz con seguridad de tipos a las funciones existentes.

   Por ejemplo, si ha derivado una lista de `CObList` para contener `CPerson` objetos, puede Agregar las funciones de contenedor `AddHeadPerson` y `GetHeadPerson` , como se muestra a continuación.

   [!code-cpp[NVC_MFCCollections#11](codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   Estas funciones contenedoras proporcionan una manera con seguridad de tipos de agregar y recuperar `CPerson` objetos de la lista derivada. Puede ver que para la `GetHeadPerson` función, simplemente está encapsulando la conversión de tipos.

   También puede Agregar una nueva funcionalidad definiendo nuevas funciones que amplían las capacidades de la colección en lugar de ajustar simplemente la funcionalidad existente en contenedores con seguridad de tipos. Por ejemplo, el artículo [eliminar todos los objetos de una colección CObject](deleting-all-objects-in-a-cobject-collection.md) describe una función para eliminar todos los objetos incluidos en una lista. Esta función se podría agregar a la clase derivada como una función miembro.

## <a name="see-also"></a>Consulte también

[Colecciones](collections.md)
