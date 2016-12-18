---
title: "network_link_registry (Clase) | Microsoft Docs"
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
  - "agents/concurrency::network_link_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "network_link_registry (clase)"
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# network_link_registry (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase base abstracta `network_link_registry` que administra los vínculos entre los bloques de origen y de destino.  
  
## Sintaxis  
  
```  
template<  
   class _Block  
>  
class network_link_registry;  
```  
  
#### Parámetros  
 `_Block`  
 El tipo de datos de bloque que se almacenan en `network_link_registry`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`const_pointer`|Un tipo que proporciona un puntero a un elemento `const` en un objeto `network_link_registry`.|  
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en un objeto `network_link_registry` para leer y realizar operaciones const.|  
|`iterator`|Un tipo que proporciona un iterador que puede leer o modificar cualquier elemento en un objeto `network_link_registry`.|  
|`type`|Un tipo que representa el tipo de bloque almacenado en el objeto `network_link_registry`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[network\_link\_registry::add \(Método\)](../Topic/network_link_registry::add%20Method.md)|Cuando se invalida en una clase derivada, agrega un vínculo al objeto `network_link_registry`.|  
|[network\_link\_registry::begin \(Método\)](../Topic/network_link_registry::begin%20Method.md)|Cuando se invalida en una clase derivada, devuelve un iterador al primer elemento del objeto `network_link_registry`.|  
|[network\_link\_registry::contains \(Método\)](../Topic/network_link_registry::contains%20Method.md)|Cuando se invalida en una clase derivada, busca el objeto `network_link_registry` para un bloque específico.|  
|[network\_link\_registry::count \(Método\)](../Topic/network_link_registry::count%20Method.md)|Cuando se invalida en una clase derivada, devuelve el número de elementos del objeto `network_link_registry`.|  
|[network\_link\_registry::remove \(Método\)](../Topic/network_link_registry::remove%20Method.md)|Cuando se invalida en una clase derivada, quita un bloque especificado del objeto `network_link_registry`.|  
  
## Comentarios  
 `network link registry` no es seguro para acceso simultáneo.  
  
## Jerarquía de herencia  
 `network_link_registry`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry \(Clase\)](../../../parallel/concrt/reference/single-link-registry-class.md)   
 [multi\_link\_registry \(Clase\)](../../../parallel/concrt/reference/multi-link-registry-class.md)