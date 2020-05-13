---
title: Implementación de una colección basada en biblioteca estándar C++
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: e80ce5e7bbc6b9c6be1615dad1ea43c18e03eb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319438"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementación de una colección basada en biblioteca estándar C++

ATL proporciona `ICollectionOnSTLImpl` la interfaz que le permite implementar rápidamente interfaces de colección basadas en la biblioteca estándar de C++ en los objetos. Para comprender cómo funciona esta clase, trabajará a través de un ejemplo sencillo (abajo) que usa esta clase para implementar una colección de solo lectura dirigida a los clientes de Automation.

El código de ejemplo procede del [ejemplo ATLCollections](../overview/visual-cpp-samples.md).

Para completar este procedimiento, deberá:

- [Generar un nuevo objeto simple](#vccongenerating_an_object).

- [Edite el archivo IDL](#vcconedit_the_idl) para la interfaz generada.

- [Cree cinco typedefs](#vcconstorage_and_exposure_typedefs) que describan cómo se almacenan los elementos de colección y cómo se expondrán a los clientes a través de interfaces COM.

- [Cree dos typedefs para las clases](#vcconcopy_classes)de directiva de copia.

- [Cree typedefs para las implementaciones de enumerador y colección.](#vcconenumeration_and_collection)

- [Edite el código C++ generado por el asistente para utilizar la colección typedef](#vcconedit_the_generated_code).

- [Agregue código para rellenar la colección.](#vcconpopulate_the_collection)

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a>Generación de un nuevo objeto simple

Cree un nuevo proyecto, asegurándose de que el cuadro Atributos en Configuración de la aplicación está desactivado. Utilice el cuadro de diálogo Agregar clase de ATL `Words`y el Asistente para agregar objetos simples para generar un objeto simple denominado . Aseegurese que `IWords` se genera una interfaz dual llamada. Los objetos de la clase generada se utilizarán para representar una colección de palabras (es decir, cadenas).

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a>Edición del archivo IDL

Ahora, abra el archivo IDL y agregue `IWords` las tres propiedades necesarias para convertirse en una interfaz de colección de solo lectura, como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Este es el formulario estándar para una interfaz de colección de solo lectura diseñada pensando en los clientes de Automation. Los comentarios numerados en esta definición de interfaz corresponden a los comentarios siguientes:

1. Las interfaces de colección suelen ser duales porque los clientes de Automation acceden a la `_NewEnum` propiedad a través `IDispatch::Invoke`de . Sin embargo, los clientes de automatización pueden acceder a los métodos restantes a través de la vtable, por lo que las interfaces duales son preferibles a las interfaces dispinterfaces.

1. Si una interfaz dual o dispinterface no se extenderá en tiempo de ejecución `IDispatch::Invoke`(es decir, no proporcionará métodos o propiedades adicionales a través de ), debe aplicar el atributo **no extensible** a la definición. Este atributo permite a los clientes de Automation realizar la verificación completa del código en tiempo de compilación. En este caso, la interfaz no debe extenderse.

1. El DISPID correcto es importante si desea que los clientes de Automation puedan utilizar esta propiedad. (Tenga en cuenta que sólo hay un carácter de subrayado en DISPID_NEWENUM.)

1. Puede proporcionar cualquier valor como el `Item` DISPID de la propiedad. Sin `Item` embargo, normalmente usa DISPID_VALUE para convertirla en la propiedad predeterminada de la colección. Esto permite a los clientes de Automation hacer referencia a la propiedad sin nombrarla explícitamente.

1. El tipo de datos utilizado `Item` para el valor devuelto de la propiedad es el tipo del elemento almacenado en la colección en lo que respecta a los clientes COM. La interfaz devuelve cadenas, por lo que debe usar el tipo de cadena COM estándar, BSTR. Puede almacenar los datos en un formato diferente internamente como verá en breve.

1. El valor utilizado para el `Count` DISPID de la propiedad es completamente arbitrario. No hay ningún DISPID estándar para esta propiedad.

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a>Creación de Typedefs para Almacenamiento y Exposición

Una vez definida la interfaz de recopilación, debe decidir cómo se almacenarán los datos y cómo se expondrán los datos a través del enumerador.

Las respuestas a estas preguntas se pueden proporcionar en forma de un número de typedefs, que puede agregar cerca de la parte superior del archivo de encabezado para la clase recién creada:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

En este caso, almacenará los datos como un **std::vector** de **std::string**s. **std::vector** es una clase contenedora de biblioteca estándar C++ que se comporta como una matriz administrada. **std::string** es la clase de cadena de la biblioteca estándar C+++ . Estas clases facilitan el trabajo con una colección de cadenas.

Dado que la compatibilidad con Visual Basic es vital `_NewEnum` para el `IEnumVARIANT` éxito de esta interfaz, el enumerador devuelto por la propiedad debe admitir la interfaz. Esta es la única interfaz de enumerador entendida por Visual Basic.

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a>Creación de Typedefs para las clases de directiva de copia

Las typedefs que ha creado hasta ahora proporcionan toda la información que necesita para crear más typedefs para las clases de copia que usará el enumerador y la colección:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

En este ejemplo, puede `GenericCopy` usar la clase personalizada definida en VCUE_Copy.h y VCUE_CopyString.h del ejemplo [ATLCollections.](../overview/visual-cpp-samples.md) Puede usar esta clase en otro código, pero es `GenericCopy` posible que deba definir otras especializaciones para admitir tipos de datos utilizados en sus propias colecciones. Para obtener más información, consulte Clases de directiva de [copia ATL](../atl/atl-copy-policy-classes.md).

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a>Creación de Typedefs para enumeración y recopilación

Ahora todos los parámetros `CComEnumOnSTL` de `ICollectionOnSTLImpl` plantilla necesarios para especializar y clases para esta situación se han proporcionado en forma de typedefs. Para simplificar el uso de las especializaciones, cree dos typedefs más como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Ahora `CollectionType` es un sinónimo `ICollectionOnSTLImpl` de una `IWords` especialización que implementa la interfaz definida anteriormente y proporciona un enumerador que admite `IEnumVARIANT`.

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a>Edición del código generado por el asistente

Ahora debe `CWords` derivar de la implementación `CollectionType` de la `IWords`interfaz representada por el typedef en lugar de , como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a>Adición de código para rellenar la colección

Lo único que queda es rellenar el vector con datos. En este ejemplo sencillo, puede agregar algunas palabras a la colección en el constructor de la clase:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Ahora, puede probar el código con el cliente de su elección.

## <a name="see-also"></a>Consulte también

[Colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)<br/>
[Ejemplo de ATLCollections](../overview/visual-cpp-samples.md)<br/>
[Clases de política de copia de ATL](../atl/atl-copy-policy-classes.md)
