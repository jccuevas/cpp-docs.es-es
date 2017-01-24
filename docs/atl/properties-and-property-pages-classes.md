---
title: "Properties and Property Pages Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.properties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "propiedades [ATL]"
  - "propiedades [ATL], clases"
  - "páginas de propiedades, clases"
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Properties and Property Pages Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las propiedades admiten y páginas de propiedades de las clases siguientes:  
  
-   Recupera o conjuntos de[CComDispatchDriver](../Topic/CComDispatchDriver.md) las propiedades de un objeto a través de un puntero de `IDispatch` .  
  
-   [CStockPropImpl](../atl/reference/cstockpropimpl-class.md) implementa las propiedades comunes compatibles con ATL.  
  
-   [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md) tiene acceso a la información en las páginas de propiedades de un objeto.  
  
-   [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md) almacena las propiedades de un objeto en un contenedor de propiedades cliente\-proporcionado.  
  
-   [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md) administra una página de propiedades particular de una hoja de propiedades.  
  
-   [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md) Similar a `IPropertyPageImpl`, pero también permite que un cliente seleccione una propiedad específica en una página de propiedades.  
  
-   [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) Obtains el CLSID para las páginas de propiedades admitidas por un objeto.  
  
## artículos relacionados  
 [tutorial de ATL](../atl/active-template-library-atl-tutorial.md)  
  
 [Páginas de propiedades ATL COM](../atl/atl-com-property-pages.md)  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)   
 [Property Map Macros](../atl/reference/property-map-macros.md)