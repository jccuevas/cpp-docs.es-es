---
title: "Multiple Dual Interfaces | Microsoft Docs"
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
  - "COM_INTERFACE_ENTRY_IID macro"
  - "COM_INTERFACE_ENTRY2 macro"
  - "interfaces duales, exposing multiple"
  - "IDispatchImpl (clase), multiple dual interfaces"
  - "multiple dual interfaces"
  - "multiple dual interfaces, exposing with ATL"
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Multiple Dual Interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede que desee combinar las ventajas de una interfaz dual \(es decir, la flexibilidad de vtable y el enlace en tiempo de ejecución, para crear la clase disponible para lenguajes de scripting así como C\+\+\) con las técnicas de herencia múltiple.  
  
 Aunque es posible exponer interfaces duales de un solo objeto COM, no se recomienda.  Si hay interfaces duales múltiples, debe haber una interfaz de `IDispatch` expuesta.  Las técnicas disponibles asegurarse que este es el caso contienen las reducciones como pérdida de función o de una mayor complejidad del código.  El desarrollador que vea este enfoque debe considerar cuidadosamente las ventajas y desventajas.  
  
## Exponer una interfaz Single IDispatch  
 Es posible exponer interfaces duales de un solo objeto derivando de dos o más especializaciones de `IDispatchImpl`.  Sin embargo, si permite que los clientes para obtener la interfaz de `IDispatch` , deberá utilizar la macro de [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md) \(o [COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md)\) para especificar qué clase base a utilizar para la implementación de `IDispatch`.  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/CPP/multiple-dual-interfaces_1.h)]  
  
 Porque se expone sólo una interfaz de `IDispatch` , los clientes que pueden tener acceso a los objetos a través de la interfaz de `IDispatch` no podrán obtener acceso a los métodos o propiedades en cualquier otra interfaz.  
  
## Combinar las interfaces de Varias Dual en una implementación Single IDispatch  
 ATL no proporciona compatibilidad para combinar interfaces duales varios en una única implementación de `IDispatch`.  Sin embargo, hay varios enfoques conocidos manualmente para combinar las interfaces, como crear una clase de plantilla que contiene una unión de las interfaces independientes de `IDispatch` , creando un nuevo objeto para realizar la función de `QueryInterface` , o mediante una implementación typeinfo\-basada de objetos anidados para crear la interfaz de `IDispatch` .  
  
 Estos enfoques tienen problemas con conflictos potenciales del espacio de nombres, así como complejidad y mantenimiento del código.  No se recomienda crear interfaces duales múltiples.  
  
## Vea también  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)