---
title: "single_link_registry (Clase) | Microsoft Docs"
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
  - "agents/concurrency::single_link_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single_link_registry (clase)"
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# single_link_registry (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El objeto `single_link_registry` es un `network_link_registry` que administra un solo bloque de origen o bloque de destino.  
  
## Sintaxis  
  
```  
template<  
   class _Block  
>  
class single_link_registry : public network_link_registry<_Block>;  
```  
  
#### Parámetros  
 `_Block`  
 El tipo de datos de bloque que se almacenan en el objeto `single_link_registry`.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[single\_link\_registry::single\_link\_registry \(Constructor\)](../Topic/single_link_registry::single_link_registry%20Constructor.md)|Construye un objeto `single_link_registry`.|  
|[single\_link\_registry::~single\_link\_registry \(Destructor\)](../Topic/single_link_registry::~single_link_registry%20Destructor.md)|Destruye el objeto `single_link_registry`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[single\_link\_registry::add \(Método\)](../Topic/single_link_registry::add%20Method.md)|Agrega un vínculo al objeto `single_link_registry`. \(Invalida [network\_link\_registry::add](../Topic/network_link_registry::add%20Method.md).\)|  
|[single\_link\_registry::begin \(Método\)](../Topic/single_link_registry::begin%20Method.md)|Devuelve un iterador al primer elemento en el objeto `single_link_registry`. \(Invalida [network\_link\_registry::begin](../Topic/network_link_registry::begin%20Method.md).\)|  
|[single\_link\_registry::contains \(Método\)](../Topic/single_link_registry::contains%20Method.md)|Busca el objeto `single_link_registry` para un bloque especificado. \(Invalida [network\_link\_registry::contains](../Topic/network_link_registry::contains%20Method.md).\)|  
|[single\_link\_registry::count \(Método\)](../Topic/single_link_registry::count%20Method.md)|Cuenta el número de elementos del objeto `single_link_registry`. \(Invalida [network\_link\_registry::count](../Topic/network_link_registry::count%20Method.md).\)|  
|[single\_link\_registry::remove \(Método\)](../Topic/single_link_registry::remove%20Method.md)|Quita un vínculo del objeto `single_link_registry`. \(Invalida [network\_link\_registry::remove](../Topic/network_link_registry::remove%20Method.md).\)|  
  
## Jerarquía de herencia  
 [network\_link\_registry](../../../parallel/concrt/reference/network-link-registry-class.md)  
  
 `single_link_registry`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [multi\_link\_registry \(Clase\)](../../../parallel/concrt/reference/multi-link-registry-class.md)