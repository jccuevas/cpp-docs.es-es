---
title: "Opciones, Asistente para objetos simples ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.simple.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para objetos simples ATL, opciones"
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Opciones, Asistente para objetos simples ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice esta página del Asistente para objetos simples ATL para diseñar objetos con eficacia mejorada y compatibles con el control de errores.  
  
 Para obtener más información acerca de los proyectos ATL y las clases COM de ATL, vea [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).  
  
 **Modelo de subprocesos**  
 Indica el método de administración de subprocesos.  De forma predeterminada, el proyecto usa el subprocesamiento **controlado**.  
  
 Para obtener más información, vea [Especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md).  
  
|Opción|Descripción|  
|------------|-----------------|  
|`Single`|Especifica que el objeto siempre se ejecuta en el subproceso COM primario.  Vea [Contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) e [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) para obtener más información.|  
|**Apartamento**|Especifica que el objeto utiliza el modelo de subprocesos por apartamento.  Equivale a un apartamento de subproceso sencillo.  A cada uno de los objetos de un componente de subprocesos por apartamento se le asigna un apartamento para su subproceso, durante la vida útil del objeto. Sin embargo, pueden usarse múltiples subprocesos para varios objetos.  Cada apartamento está vinculado a un subproceso específico y posee un suministro de mensajes de Windows \(de forma predeterminada\).<br /><br /> Vea [Contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) para obtener más información.|  
|**Ambos**|Especifica que el objeto puede usar el modelo de subprocesos libre o de apartamento, dependiendo del tipo de subproceso creado.|  
|**Libre**|Especifica que el objeto utiliza el modelo de subprocesos libre.  El subprocesamiento libre equivale a un modelo de apartamentos multiproceso.  Vea [Apartamentos multiproceso](http://msdn.microsoft.com/library/windows/desktop/ms693421) para obtener más información.|  
|**Neutral** \(sólo Windows 2000\)|Especifica que el objeto sigue las directrices para apartamentos multiproceso, pero puede ejecutarse en cualquier tipo de subproceso.|  
  
 **Agregación**  
 Indica si el objeto utiliza [agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558).  El objeto agregado elige qué interfaces se expondrán a los clientes, y las interfaces se exponen como si el objeto agregado las implementara.  Los clientes del objeto agregado se comunican sólo con éste.  
  
|Opción|Descripción|  
|------------|-----------------|  
|Sí|Especifica que puede agregarse el objeto.  Es el formato predeterminado.|  
|No|Especifica que no se agrega el objeto.|  
|Sólo|Especifica que debe agregarse el objeto.|  
  
 **Interfaz**  
 Indica el tipo de interfaz que admite el objeto.  De forma predeterminada, el objeto admite una interfaz dual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Doble**|Especifica que el objeto admite una interfaz doble \(su tabla vtable posee funciones de interfaz personalizada y métodos `IDispatch`de enlace en tiempo de ejecución\).  Permite tanto a clientes COM como a [controladores de automatización](../../mfc/automation-clients.md) el acceso al objeto.  Es el formato predeterminado.|  
|**Personalizar**|Especifica que el objeto admite una interfaz personalizada \(su tabla vtable posee funciones de interfaz personalizada\).  Una interfaz personalizada puede ser más rápida que una interfaz doble, en especial entre límites de procesos.<br /><br /> -   Controladores de automatización de**Automation compatible** Permiso para tener acceso a un objeto que tiene compatibilidad de interfaz personalizado.|  
  
 **Compatibilidad**  
 Indica compatibilidad adicional para el objeto.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**ISupportErrorInfo**|Crea compatibilidad con la interfaz [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) para que el objeto pueda devolver información de errores al cliente|  
|**Puntos de conexión**|Habilita puntos de conexión para el objeto al hacer que la clase del objeto derive de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Marshaler de subprocesos libre**|Crea un objeto marshaler de subprocesos libre para calcular las referencias a punteros de interfaz eficazmente entre subprocesos del mismo proceso.  Disponible para los objetos que especifican **Ambos** como modelo de subprocesos.|  
|**IObjectWithSite \(compatibilidad con objetos de IE\)**|Implementa [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), que proporciona una forma sencilla de habilitar la comunicación entre un objeto y su sitio en un contenedor.|  
  
## Vea también  
 [Asistente para objetos simples ATL](../../atl/reference/atl-simple-object-wizard.md)   
 [ATL Simple Object](../../atl/reference/adding-an-atl-simple-object.md)   
 [Problemas de subprocesamiento de servidor en proceso](http://msdn.microsoft.com/library/windows/desktop/ms687205)