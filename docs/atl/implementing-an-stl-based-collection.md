---
title: "Implementing an STL-Based Collection | Microsoft Docs"
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
  - "ICollectionOnSTLImpl interface"
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Implementing an STL-Based Collection
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL proporciona la interfaz de `ICollectionOnSTLImpl` que permite implementar rápidamente interfaces de intercalación Biblioteca\-basadas plantilla \(STL\) estándar en los objetos.  Para entender cómo funciona esta clase, trabajará con un ejemplo simple \(abajo\) que utiliza esta clase para implementar los clientes dirigidos colección de solo lectura de una automatización.  
  
 El código de ejemplo es de [Ejemplo ATLCollections](../top/visual-cpp-samples.md).  
  
 Para completar este procedimiento, debe:  
  
-   [Genera un nuevo objeto sencillo](#vccongenerating_an_object).  
  
-   [Edite el archivo IDL](#vcconedit_the_idl) para la interfaz generada.  
  
-   [cree cinco typedefs](#vcconstorage_and_exposure_typedefs) que describe cómo se almacenan los elementos de colección y cómo se van a exponer a los clientes mediante interfaces COM.  
  
-   [Cree dos definiciones de tipos para las clases de directivas de copia](#vcconcopy_classes).  
  
-   [Crear tipos para implementaciones de enumerador y colección](#vcconenumeration_and_collection).  
  
-   [Edite el código generado por el asistente de C\+\+ para utilizar typedef de colección](#vcconedit_the_generated_code).  
  
-   [Agregue código para rellenar la colección](#vcconpopulate_the_collection).  
  
##  <a name="vccongenerating_an_object"></a> Generar un objeto New Simple  
 Cree un nuevo proyecto, asegurarse de que el cuadro de los atributos en la configuración de la aplicación está desactivada.  Utilice el ATL agregan el cuadro de diálogo de la clase y agregue el asistente para objetos de Simple para generar un objeto sencillo denominado `Words`.  Asegúrese de que una interfaz dual denominada `IWords` se genera.  Los objetos de la clase generada se utilizarán para representar una colección de palabras \(es decir, cadenas\).  
  
##  <a name="vcconedit_the_idl"></a> Editar el archivo IDL  
 Ahora, abra el archivo IDL y agrega las tres propiedades necesarias girar `IWords` en una interfaz de intercalación de sólo lectura, como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/CPP/implementing-an-stl-based-collection_1.idl)]  
  
 Éste es el formulario estándar para una interfaz de intercalación de sólo lectura diseñada con clientes de automatización en mente.  Los comentarios numerados en esta definición de interfaz corresponden a los comentarios a continuación:  
  
1.  Las interfaces de intercalación son normalmente duales porque los clientes de automatización tienen acceso a la propiedad de `_NewEnum` mediante **IDispatch::Invocar**.  Sin embargo, los clientes de automatización pueden tener acceso a los métodos restantes mediante vtable, de modo que las interfaces duales son preferibles a dispinterfaces.  
  
2.  Si una interfaz dual o dispinterface no es extendida en tiempo de ejecución \(es decir, no proporcionará otros métodos o propiedades mediante **IDispatch::Invocar**\), debe aplicar el atributo de **nonextensible** a la definición.  Este atributo permite a los clientes de automatización para realizar la comprobación completa del código en tiempo de compilación.  En este caso, la interfaz no se extenderá.  
  
3.  El identificador de envío correcto es importante si desea que los clientes de automatización para poder usar esta propiedad.  \(Observe que sólo hay un subrayado en **DISPID\_NEWENUM**.\)  
  
4.  Puede proporcionar cualquier valor como el identificador de envío de la propiedad de **Elemento** .  Sin embargo, **Elemento** utiliza normalmente **DISPID\_VALUE** para convertirla en la propiedad predeterminada de la colección.  Esto permite que los clientes de automatización hacen referencia a la propiedad sin llamarla explícitamente.  
  
5.  El tipo de datos utilizado por el valor devuelto de la propiedad de **Elemento** es el tipo del elemento almacenado en la colección por lo que los clientes COM.  La interfaz devuelve las cadenas, por lo que debe utilizar el tipo string COM estándar, `BSTR`.  Puede almacenar los datos en un formato diferente internamente como verá pronto.  
  
6.  El valor utilizado para el identificador de envío de la propiedad de **Cuenta** es totalmente arbitrario.  No hay estándar DISPID para esta propiedad.  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> Crear definiciones de tipos para el almacenamiento y Exposición  
 Una vez que la interfaz de intercalación se define, debe decidir cómo los datos se almacenan, y cómo los datos se expuestos a través del enumerador.  
  
 Las respuestas a estas preguntas pueden suministrarse en forma de varios typedefs, que puede agregar cerca de la parte superior del archivo de encabezado para la clase creada recientemente:  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/CPP/implementing-an-stl-based-collection_2.h)]  
  
 En este caso, se almacenará los datos como **std:: vector** de s para **std:: cadena**.  **std:: vector** es una clase de contenedor de STL que se comporta como una matriz administrada.  **std:: cadena** es la clase de cadena estándar de la biblioteca de C\+\+.  Estas clases facilitan el trabajo con una colección de cadenas.  
  
 Puesto que la compatibilidad de Visual Basic es vital para el éxito de esta interfaz, el enumerador devuelto por la propiedad de `_NewEnum` debe admitir la interfaz de **IEnumVARIANT** .  Esta es la única interfaz de enumerador entendida por Visual Basic.  
  
##  <a name="vcconcopy_classes"></a> Crear definiciones de tipos para las clases de directivas de copia  
 Tipos que ha creado hasta ahora proporcionan toda la información necesita crear otros typedefs para las clases de la copia que usarán el enumerador y la colección:  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/CPP/implementing-an-stl-based-collection_3.h)]  
  
 En este ejemplo, puede utilizar la clase personalizada de `GenericCopy` definida en VCUE\_Copy.h y VCUE\_CopyString.h de ejemplo de [ATLCollections](../top/visual-cpp-samples.md) .  Puede utilizar esta clase en otro código, pero puede que necesite definir otras especializaciones de `GenericCopy` para admitir los tipos de datos utilizados en dispone de colecciones.  Para obtener más información, vea [Clases de directivas de copia ATL](../atl/atl-copy-policy-classes.md).  
  
##  <a name="vcconenumeration_and_collection"></a> Crear definiciones de tipos para Enumeration y la colección  
 Ahora todos los parámetros de plantilla necesarios especializar las clases de `CComEnumOnSTL` y de `ICollectionOnSTLImpl` de esta situación se han proporcionado en forma de definiciones de tipos.  Para simplificar el uso de especializaciones, cree dos más typedefs como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/CPP/implementing-an-stl-based-collection_4.h)]  
  
 Ahora `CollectionType` es un sinónimo de una especialización de `ICollectionOnSTLImpl` que implemente el anterior definido de la interfaz de `IWords` y proporciona un enumerador que admite **IEnumVARIANT**.  
  
##  <a name="vcconedit_the_generated_code"></a> Modificar el código generado por el asistente  
 Ahora debe derivar `CWords` de implementación de la interfaz representada por typedef de `CollectionType` en lugar de `IWords`, como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/CPP/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> Agregar código para rellenar la colección  
 Lo único que queda es rellenar el vector con datos.  En este ejemplo, puede agregar algunas palabras a la colección en el constructor para la clase:  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/CPP/implementing-an-stl-based-collection_6.h)]  
  
 Ahora, puede probar el código con el cliente de la opción.  
  
## Vea también  
 [Colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)   
 [Ejemplo ATLCollections](../top/visual-cpp-samples.md)   
 [ATL Copy Policy Classes](../atl/atl-copy-policy-classes.md)