---
title: "multi_link_registry (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::multi_link_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multi_link_registry (clase)"
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# multi_link_registry (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El objeto `multi_link_registry` es un `network_link_registry` que administra varios bloques de origen o varios bloques de destino.  
  
## Sintaxis  
  
```  
template<  
   class _Block  
>  
class multi_link_registry : public network_link_registry<_Block>;  
```  
  
#### Parámetros  
 `_Block`  
 El tipo de datos de bloque que se almacenan en el objeto `multi_link_registry`.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[multi\_link\_registry::multi\_link\_registry \(Constructor\)](../Topic/multi_link_registry::multi_link_registry%20Constructor.md)|Construye un objeto `multi_link_registry`.|  
|[multi\_link\_registry::~multi\_link\_registry \(Destructor\)](../Topic/multi_link_registry::~multi_link_registry%20Destructor.md)|Destruye el objeto `multi_link_registry`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[multi\_link\_registry::add \(Método\)](../Topic/multi_link_registry::add%20Method.md)|Agrega un vínculo al objeto `multi_link_registry`. \(Invalida [network\_link\_registry::add](../Topic/network_link_registry::add%20Method.md).\)|  
|[multi\_link\_registry::begin \(Método\)](../Topic/multi_link_registry::begin%20Method.md)|Devuelve un iterador al primer elemento en el objeto `multi_link_registry`. \(Invalida [network\_link\_registry::begin](../Topic/network_link_registry::begin%20Method.md).\)|  
|[multi\_link\_registry::contains \(Método\)](../Topic/multi_link_registry::contains%20Method.md)|Busca el objeto `multi_link_registry` para un bloque especificado. \(Invalida [network\_link\_registry::contains](../Topic/network_link_registry::contains%20Method.md).\)|  
|[multi\_link\_registry::count \(Método\)](../Topic/multi_link_registry::count%20Method.md)|Cuenta el número de elementos del objeto `multi_link_registry`. \(Invalida [network\_link\_registry::count](../Topic/network_link_registry::count%20Method.md).\)|  
|[multi\_link\_registry::remove \(Método\)](../Topic/multi_link_registry::remove%20Method.md)|Quita un vínculo del objeto `multi_link_registry`. \(Invalida [network\_link\_registry::remove](../Topic/network_link_registry::remove%20Method.md).\)|  
|[multi\_link\_registry::set\_bound \(Método\)](../Topic/multi_link_registry::set_bound%20Method.md)|Establece un límite superior en el número de vínculos que el objeto `multi_link_registry` puede contener.|  
  
## Jerarquía de herencia  
 [network\_link\_registry](../../../parallel/concrt/reference/network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry \(Clase\)](../../../parallel/concrt/reference/single-link-registry-class.md)