---
title: Implementación de una colección de basada en la biblioteca estándar de C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d414df9d5e5f7d930497d42b5ec73d92a65ac3cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116716"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementación de una colección de basada en la biblioteca estándar de C++

ATL proporciona el `ICollectionOnSTLImpl` interfaz para que pueda implementar rápidamente interfaces de colección basadas en la biblioteca estándar de C++ en los objetos. Para comprender el funcionamiento de esta clase, funcionará a través de un ejemplo sencillo (abajo) que usa esta clase para implementar una colección de solo lectura dirigida a los clientes de automatización.

El código de ejemplo procede del [ejemplo ATLCollections](../visual-cpp-samples.md).

Para completar este procedimiento, hará lo siguiente:

- [Generar un nuevo objeto Simple](#vccongenerating_an_object).

- [Edite el archivo IDL](#vcconedit_the_idl) para la interfaz generada.

- [Crear cinco typedefs](#vcconstorage_and_exposure_typedefs) que describen cómo se almacenan los elementos de recopilación y cómo verá expuestos a clientes a través de interfaces COM.

- [Crear clases de directivas de dos definiciones de tipo de copia](#vcconcopy_classes).

- [Crear definiciones de tipo para las implementaciones de enumerador y colección](#vcconenumeration_and_collection).

- [Editar el código de C++ generado por el Asistente para usar la definición de tipo de colección](#vcconedit_the_generated_code).

- [Agregue código para rellenar la colección](#vcconpopulate_the_collection).

##  <a name="vccongenerating_an_object"></a> Generar un nuevo objeto Simple

Cree un nuevo proyecto, lo que garantiza que está desactivada la casilla atributos en configuración de la aplicación. Utilice el cuadro de diálogo Agregar clase de ATL y agregar Asistente para objetos simples para generar un objeto Simple denominado `Words`. Asegúrese de que se llama una interfaz dual `IWords` se genera. Objetos de la clase generada se usará para representar una colección de palabras (es decir, cadenas).

##  <a name="vcconedit_the_idl"></a> Editar el archivo IDL

Ahora, abra el archivo IDL y agregue las tres propiedades necesarias activar `IWords` en una interfaz de colección de solo lectura, tal como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

Este es el formato estándar para una interfaz de colección de solo lectura diseñado teniendo en mente los clientes de automatización. Los comentarios numerados en esta definición de interfaz corresponden a los siguientes comentarios:

1. Interfaces de colección son normalmente duales porque tiene acceso los clientes de automatización la `_NewEnum` propiedad a través de `IDispatch::Invoke`. Sin embargo, los clientes de automatización pueden tener acceso a los métodos restantes a través de la tabla vtable, por lo que las interfaces duales son preferibles a las interfaces dispinterface.

2. Si no se extiende una interfaz dual o dispinterface en tiempo de ejecución (es decir, si no se ofrecen métodos adicionales ni propiedades a través de `IDispatch::Invoke`), debe aplicar el **nonextensible** a la definición de atributo. Este atributo permite a los clientes de automatización realizar la comprobación de código completo en tiempo de compilación. En este caso, no se debe extender la interfaz.

3. El DISPID correcto es importante si desea que los clientes de automatización para poder usar esta propiedad. (Tenga en cuenta que hay solo un carácter de subrayado en DISPID_NEWENUM.)

4. Puede proporcionar cualquier valor como el DISPID de la `Item` propiedad. Sin embargo, `Item` suele utilizar DISPID_VALUE para que sea la propiedad predeterminada de la colección. Esto permite a los clientes de automatización hacer referencia a la propiedad sin darle explícitamente.

5. El tipo de datos utilizado para el valor devuelto de la `Item` propiedad es el tipo de elemento almacenado en la colección en cuanto los clientes COM están interesados. La interfaz devuelve cadenas, por lo que debe usar el tipo de cadena COM estándar, BSTR. Puede almacenar internamente los datos en un formato diferente como verá en breve.

6. El valor utilizado para el DISPID de la `Count` propiedad es completamente arbitraria. No hay ningún DISPID estándar para esta propiedad.

##  <a name="vcconstorage_and_exposure_typedefs"></a> Creación de definiciones de tipo para el almacenamiento y exposición

Una vez que se define la interfaz de colección, debe decidir cómo se almacenarán los datos y cómo los datos se expondrá a través del enumerador.

Las respuestas a estas preguntas pueden proporcionarse en forma de un número de definiciones de tipos, que puede agregar la parte superior del archivo de encabezado para la clase recién creada:

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

En este caso, se almacenarán los datos como un **std:: vector** de **std:: String**s. **std:: vector** es una clase de contenedor de la biblioteca estándar de C++ que se comporta como una matriz administrada. **std:: String** es la clase de cadena de la biblioteca estándar de C++. Estas clases facilitan trabajar con una colección de cadenas.

Puesto que la compatibilidad con Visual Basic es vital para el éxito de esta interfaz, el enumerador devuelto por la `_NewEnum` propiedad debe admitir la `IEnumVARIANT` interfaz. Esta es la interfaz de enumerador solo entendida Visual Basic.

##  <a name="vcconcopy_classes"></a> Creación de definiciones de tipos para clases de directivas de copia

Las definiciones de tipo que ha creado hasta ahora proporcionan toda la información que necesita crear otros typedefs para las clases de copia que se usará en el enumerador y la colección:

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

En este ejemplo, puede usar personalizado `GenericCopy` clase definida en VCUE_Copy.h y VCUE_CopyString.h desde el [ATLCollections](../visual-cpp-samples.md) ejemplo. Puede usar esta clase en otro código, pero es posible que deba definir más especializaciones de `GenericCopy` para admitir tipos de datos utilizados en sus propias recopilaciones. Para obtener más información, consulte [clases de directivas de copia ATL](../atl/atl-copy-policy-classes.md).

##  <a name="vcconenumeration_and_collection"></a> Creación de definiciones de tipos de enumeración y colección

Ahora todos los parámetros de plantilla necesarios para especializar el `CComEnumOnSTL` y `ICollectionOnSTLImpl` se han proporcionado en el formulario de definiciones de clases para esta situación. Para simplificar el uso de las especializaciones, cree dos typedefs más como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

Ahora `CollectionType` es un sinónimo de una especialización de `ICollectionOnSTLImpl` que implementa el `IWords` interfaz definidas anteriormente y proporciona un enumerador que admite `IEnumVARIANT`.

##  <a name="vcconedit_the_generated_code"></a> Editar el código generado por el Asistente

Ahora debe derivar `CWords` desde la implementación de la interfaz representada por el `CollectionType` typedef lugar `IWords`, tal y como se muestra a continuación:

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

##  <a name="vcconpopulate_the_collection"></a> Agregar código para rellenar la colección

Lo único que queda es rellenar el vector con datos. En este sencillo ejemplo, puede agregar algunas palabras a la colección en el constructor para la clase:

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

Ahora, puede probar el código con el cliente de su elección.

## <a name="see-also"></a>Vea también

[Las colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)<br/>
[Ejemplo ATLCollections](../visual-cpp-samples.md)<br/>
[Clases de directivas de copia ATL](../atl/atl-copy-policy-classes.md)

