---
title: "Opciones, Asistente para componentes de p&#225;ginas Active Server ATL | Microsoft Docs"
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
  - "vc.codewiz.class.atl.asp.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para componentes de páginas Active Server ATL, opciones"
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Opciones, Asistente para componentes de p&#225;ginas Active Server ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice esta página del Asistente para componentes de páginas Active Server ATL para diseñar objetos con eficacia mejorada y compatible con el control de errores.  
  
 Para obtener más información acerca de los proyectos ATL y las clases COM de ATL, vea [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).  
  
 **Modelo de subprocesos**  
 Indica el método de administración de subprocesos.  De forma predeterminada, el proyecto usa el subprocesamiento **controlado**.  
  
 Para obtener más información, vea [Especificar el modelo de subprocesos del proyecto](../../atl/specifying-the-threading-model-for-a-project-atl.md).  
  
|Opción|Descripción|  
|------------|-----------------|  
|`Single`|Especifica que el objeto utiliza el modelo de subprocesos sencillo.  En este modelo, los objetos siempre se ejecutan en el subproceso COM primario.  Vea [Contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) e [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) para obtener más información.|  
|**Apartamento**|Especifica que el objeto utiliza el modelo de subprocesos por apartamento.  Equivale a un apartamento de subproceso sencillo.  A cada uno de los objetos de un componente de subprocesos por apartamento se le asigna un apartamento para su subproceso, durante la vida útil del objeto. Sin embargo, pueden usarse múltiples subprocesos para varios objetos.  Cada apartamento está vinculado a un subproceso específico y posee un suministro de mensajes de Windows \(de forma predeterminada\).<br /><br /> Vea [Contenedores uniproceso](http://msdn.microsoft.com/library/windows/desktop/ms680112) para obtener más información.|  
|**Ambos**|Especifica que el objeto puede usar el modelo de subprocesos libre o de apartamento, dependiendo del tipo de subproceso creado.|  
|**Libre**|Especifica que el objeto utiliza el modelo de subprocesos libre.  El subprocesamiento libre equivale a un modelo de apartamentos multiproceso.  Vea [Apartamentos multiproceso](http://msdn.microsoft.com/library/windows/desktop/ms693421) para obtener más información.|  
|**Neutral** \(sólo Windows 2000\)|Especifica que el objeto sigue las directrices para apartamentos multiproceso, pero puede ejecutarse en cualquier tipo de subproceso.|  
  
 **Agregación**  
 Indica si el objeto utiliza [agregación](http://msdn.microsoft.com/library/windows/desktop/ms686558).  El objeto agregado elige qué interfaces se expondrán a los clientes, y las interfaces se exponen como si el objeto agregado las implementara.  Los clientes del objeto agregado se comunican sólo con éste.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Sí**|Especifica que puede agregarse el objeto.  Es el formato predeterminado.|  
|**No**|Especifica que no se agrega el objeto.|  
|**Sólo**|Especifica que debe agregarse el objeto.|  
  
 **Compatibilidad**  
 \(se agregará una descripción del elemento\).  
  
|Opción|Descripción|  
|------------|-----------------|  
|**ISupportErrorInfo**|Crea compatibilidad con la interfaz [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) para que el objeto pueda devolver información de errores al cliente|  
|**Puntos de conexión**|Habilita puntos de conexión para el objeto al hacer que la clase del objeto derive de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Marshaler de subprocesos libre**|Crea un objeto marshaler de subprocesos libre para calcular las referencias a punteros de interfaz eficazmente entre subprocesos del mismo proceso.  Disponible para los objetos en los que se especifique **Ambos** o **Libre** como modelo de subprocesos.|  
  
## Vea también  
 [Asistente para componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page Component](../../atl/reference/adding-an-atl-active-server-page-component.md)