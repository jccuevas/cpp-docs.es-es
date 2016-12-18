---
title: "Fundamentals of ATL COM Objects | Microsoft Docs"
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
  - "ATL COM objects"
  - "ATL, COM"
  - "objetos COM, ATL"
  - "COM, y ATL"
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
caps.latest.revision: 25
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Fundamentals of ATL COM Objects
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ilustración siguiente muestra la relación entre las clases e interfaces que se usan para definir un objeto COM ATL.  
  
 ![Estructura ATL](../atl/media/vc307y1.png "vc307Y1")  
  
> [!NOTE]
>  Este diagrama muestra que `CComObject` se deriva de `CYourClass` mientras `CComAggObject` y `CComPolyObject` incluyen `CYourClass` como variable miembro.  
  
 Hay tres formas de definir un objeto COM ATL.  La opción estándar es utilizar la clase de `CComObject` que se deriva de `CYourClass`.  La segunda opción es crear un objeto agregado utilizando la clase de `CComAggObject` .  La tercera opción es utilizar la clase de `CComPolyObject` .  `CComPolyObject` actúa como híbrido: puede funcionar como una clase de `CComObject` o como una clase de `CComAggObject` , dependiendo de cómo se crea por primera vez.  Para obtener más información sobre cómo usar la clase `CComPolyObject`, vea [CComPolyObject Class](../atl/reference/ccompolyobject-class.md).  
  
 Cuando se utiliza el estándar ATL COM, se utilizan dos objetos: un objeto externo y un objeto interno.  Los clientes externos tienen acceso a la funcionalidad del objeto interno con funciones de contenedor que se definen en el objeto externo.  El objeto externo es de `CComObject`escrito.  
  
 Si se utiliza un objeto agregado, el objeto externo no proporciona contenedores para la funcionalidad del objeto interno.  En su lugar, el objeto externo proporciona un puntero que se tiene acceso directamente por los clientes externos.  En este escenario, el objeto externo es de `CComAggObject`escrito.  El objeto interno es una variable miembro del objeto externo, y es de `CYourClass`escrito.  
  
 Dado que el cliente no tiene que pasar por el objeto externo interactuar con el objeto interno, los objetos agregados suelen ser más eficaces.  Además, el objeto externo no tiene que conocer la funcionalidad del objeto agregado, puesto que la interfaz del objeto agregado es directamente disponibles al cliente.  Sin embargo, no todos los objetos se pueden agregar.  Para que un objeto sea agregado, necesita diseñar con la agregación en mente.  
  
 ATL implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) en dos fases:  
  
-   Herramientas de[CComObject](../atl/reference/ccomobject-class.md), de [CComAggObject](../atl/reference/ccomaggobject-class.md), o de [CComPolyObject](../atl/reference/ccompolyobject-class.md) los métodos de **IUnknown** .  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) administra el recuento de referencias y los punteros externos de **IUnknown**.  
  
 Otros aspectos del objeto ATL COM son controlados por otras clases:  
  
-   [CComCoClass](../atl/reference/ccomcoclass-class.md) define el modelo predeterminado de generador y la agregación de la clase del objeto.  
  
-   [IDispatchImpl](../atl/reference/idispatchimpl-class.md) proporciona una implementación predeterminada de la parte de `IDispatch Interface` de cualquier interfaz dual en el objeto.  
  
-   [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementa la interfaz de **ISupportErrorInfo** que garantiza la información de error puede propagar por la cadena de llamadas correctamente.  
  
## En esta sección  
 [implementar CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
 Muestra las entradas del mapa COM de ejemplo para implementar `CComObjectRootEx`.  
  
 [implementar CComObject, CComAggObject, y CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
 Describe cómo las macros de **DECLARE\_\*\_AGGREGATABLE** afectan al uso de `CComObject`, de `CComAggObject`, y de `CComPolyObject`.  
  
 [admitir IDispatch e IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)  
 Muestra las clases de implementación de ATL para utilizar para admitir `IDispatch` y las interfaces de **IErrorInfo** .  
  
 [admitir IDispEventImpl](../atl/supporting-idispeventimpl.md)  
 Describe los pasos para implementar un punto de conexión para la clase.  
  
 [Cambiar el modelo predeterminado del generador y de agregación de clases](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
 Presentación qué macros a utilizar para cambiar el generador y la agregación predeterminada de la clase modelo.  
  
 [crear un objeto agregado](../atl/creating-an-aggregated-object.md)  
 Muestra los pasos para crear un objeto agregado.  
  
## Secciones relacionadas  
 [Crear un proyecto ATL](../atl/reference/creating-an-atl-project.md)  
 Proporciona información sobre cómo crear un objeto COM ATL.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas conceptuales sobre cómo programar utilizando Active Template Library.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)