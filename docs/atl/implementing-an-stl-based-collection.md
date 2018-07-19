---
title: Implementación de una colección de basada en la biblioteca estándar de C++ | Documentos de Microsoft
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
ms.openlocfilehash: 14a09f54598b525346a65b56a335711f114878cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359680"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>Implementación de una colección de basada en la biblioteca estándar de C++
ATL proporciona el `ICollectionOnSTLImpl` interfaz que le permite implementar rápidamente interfaces de colección basada en la biblioteca estándar de C++ en los objetos. Para entender cómo funciona esta clase, funcionará a través de un ejemplo simple (a continuación) que usa esta clase para implementar una colección de solo lectura dirigida a los clientes de automatización.  
  
 El código de ejemplo está tomado del [ejemplo ATLCollections](../visual-cpp-samples.md).  
  
 Para completar este procedimiento, aprenderá lo siguiente:  
  
-   [Generar un nuevo objeto Simple](#vccongenerating_an_object).  
  
-   [Edite el archivo IDL](#vcconedit_the_idl) para la interfaz generada.  
  
-   [Crear cinco typedefs](#vcconstorage_and_exposure_typedefs) que describe cómo se almacenan los elementos de recopilación y cómo se expondrán a los clientes a través de interfaces COM.  
  
-   [Crear clases de directivas de dos definiciones de tipo de copia](#vcconcopy_classes).  
  
-   [Crear definiciones de tipo para las implementaciones de enumeradores y colecciones](#vcconenumeration_and_collection).  
  
-   [Modifique el código de C++ generados por el Asistente para usar la definición de tipo de colección](#vcconedit_the_generated_code).  
  
-   [Agregue código para rellenar la colección](#vcconpopulate_the_collection).  
  
##  <a name="vccongenerating_an_object"></a> Generar un nuevo objeto Simple  
 Cree un nuevo proyecto, asegurándose de que está desactivada la casilla atributos en configuración de la aplicación. Utilice el cuadro de diálogo Agregar clase de ATL y agregar Asistente para objetos simples para generar un objeto Simple denominado `Words`. Asegúrese de que llama a una interfaz dual `IWords` se genera. Objetos de la clase generada se utilizará para representar una colección de palabras (es decir, cadenas).  
  
##  <a name="vcconedit_the_idl"></a> Editar el archivo IDL  
 Ahora, abra el archivo IDL y agregue las tres propiedades necesarias activar `IWords` en una interfaz de colección de solo lectura, tal y como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]  
  
 Esta es la forma estándar para una interfaz de colección de solo lectura diseñada teniendo en cuenta los clientes de automatización. Los comentarios numerados en esta definición de interfaz corresponden a los siguientes comentarios:  
  
1.  Interfaces de colección acostumbran a ser duales porque tiene acceso los clientes de automatización la `_NewEnum` propiedad a través de **IDispatch:: Invoke**. Sin embargo, los clientes de automatización pueden tener acceso a los métodos restantes a través de la vtable, por lo que las interfaces duales son preferibles a las interfaces dispinterface.  
  
2.  Si una interfaz dual o dispinterface no se extiende en tiempo de ejecución (es decir, si no se ofrecen métodos ni propiedades a través de extra **IDispatch:: Invoke**), debe aplicar la **nonextensible** atribuir a la definición. Este atributo permite a los clientes de automatización realizar la comprobación de código completo en tiempo de compilación. En este caso, no debe extenderse la interfaz.  
  
3.  El DISPID correcto es importante si desea que los clientes de automatización para poder utilizar esta propiedad. (Tenga en cuenta que hay solo un carácter de subrayado en **DISPID_NEWENUM**.)  
  
4.  Puede proporcionar cualquier valor como el DISPID de la **elemento** propiedad. Sin embargo, **elemento** normalmente usa **DISPID_VALUE** para que sea la propiedad predeterminada de la colección. Esto permite a los clientes de automatización de la referencia a la propiedad sin darle el nombre explícitamente.  
  
5.  El tipo de datos utilizado para el valor devuelto de la **elemento** propiedad es el tipo de elemento almacenado en la colección en lo que los clientes COM están interesados. La interfaz devuelve cadenas, por lo que debe usar el tipo de cadena COM estándar, `BSTR`. Puede almacenar los datos en un formato diferente internamente como verá en breve.  
  
6.  El valor utilizado para el DISPID de la **recuento** propiedad es totalmente arbitraria. No hay ningún DISPID estándar para esta propiedad.  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> Crear definiciones de tipo para el almacenamiento y la exposición  
 Una vez que se define la interfaz de colección, debe decidir cómo se almacenarán los datos y cómo se expondrán los datos a través del enumerador.  
  
 Las respuestas a estas preguntas pueden proporcionarse en forma de un número de definiciones de tipos, que puede agregar en la parte superior del archivo de encabezado para la clase recién creada:  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]  
  
 En este caso, almacenará los datos como un **std:: vector** de **std:: String**s. **std:: vector** es una clase de contenedor de la biblioteca estándar de C++ que se comporta como una matriz administrada. **std:: String** es la clase de cadena de la biblioteca estándar de C++. Estas clases facilitan el trabajo con una colección de cadenas.  
  
 Puesto que la compatibilidad con Visual Basic es vital para el éxito de esta interfaz, el enumerador devuelto por la `_NewEnum` propiedad debe admitir la **IEnumVARIANT** interfaz. Esta es la interfaz de enumerador solo entendida por Visual Basic.  
  
##  <a name="vcconcopy_classes"></a> Crear definiciones de tipos para las clases de directiva de copia  
 Las definiciones de tipo que ha creado hasta ahora proporcionan toda la información que necesita crear otros typedefs para las clases de copia que se usará en el enumerador y la colección:  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]  
  
 En este ejemplo, puede usar la opción de instalación `GenericCopy` clase definida en VCUE_Copy.h y VCUE_CopyString.h desde el [ATLCollections](../visual-cpp-samples.md) ejemplo. Puede utilizar esta clase en otro código, pero puede que necesite definir más especializaciones de `GenericCopy` para admitir tipos de datos utilizados en sus propias colecciones. Para obtener más información, consulte [clases de directiva de copia de ATL](../atl/atl-copy-policy-classes.md).  
  
##  <a name="vcconenumeration_and_collection"></a> Crear definiciones de tipo de enumeración y colección  
 Ahora todos los parámetros de plantilla necesarios para especializar la `CComEnumOnSTL` y `ICollectionOnSTLImpl` clases para esta situación se han proporcionado en forma de definiciones de tipo. Para simplificar el uso de las especializaciones, cree dos typedefs más como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]  
  
 Ahora `CollectionType` es un sinónimo de una especialización de `ICollectionOnSTLImpl` que implementa el `IWords` interfaz definida anteriormente y proporciona un enumerador que admite **IEnumVARIANT**.  
  
##  <a name="vcconedit_the_generated_code"></a> Editar el código generado por el Asistente  
 Ahora debe derivar `CWords` de la implementación de la interfaz representada por la `CollectionType` (typedef) en lugar de `IWords`, tal y como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> Agregar código para rellenar la colección  
 Lo único que queda es rellenar el vector con datos. En este sencillo ejemplo, puede agregar algunas palabras a la colección en el constructor para la clase:  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]  
  
 Ahora, puede probar el código con el cliente de su elección.  
  
## <a name="see-also"></a>Vea también  
 [Colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)   
 [Ejemplo ATLCollections](../visual-cpp-samples.md)   
 [Clases de directivas de copia ATL](../atl/atl-copy-policy-classes.md)

