---
title: "source_link_manager (Clase) | Microsoft Docs"
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
  - "agents/concurrency::source_link_manager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source_link_manager (clase)"
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
caps.latest.revision: 17
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# source_link_manager (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El objeto `source_link_manager` administra los vínculos de red del bloque de mensajería para los bloques `ISource`.  
  
## Sintaxis  
  
```  
template<  
   class _LinkRegistry  
>  
class source_link_manager;  
```  
  
#### Parámetros  
 `_LinkRegistry`  
 El Registro del vínculo de red.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`const_pointer`|Un tipo que proporciona un puntero a un elemento `const` en un objeto `source_link_manager`.|  
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en un objeto `source_link_manager` para leer y realizar operaciones const.|  
|`iterator`|Un tipo que proporciona un iterador que puede leer o modificar cualquier elemento en el objeto `source_link_manager`.|  
|`type`|El tipo de Registro del vínculo que es administrado por el objeto `source_link_manager`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source\_link\_manager::source\_link\_manager \(Constructor\)](../Topic/source_link_manager::source_link_manager%20Constructor.md)|Construye un objeto `source_link_manager`.|  
|[source\_link\_manager::~source\_link\_manager \(Destructor\)](../Topic/source_link_manager::~source_link_manager%20Destructor.md)|Destruye el objeto `source_link_manager`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source\_link\_manager::add \(Método\)](../Topic/source_link_manager::add%20Method.md)|Agrega un vínculo de origen al objeto `source_link_manager`.|  
|[source\_link\_manager::begin \(Método\)](../Topic/source_link_manager::begin%20Method.md)|Devuelve un iterador al primer elemento en el objeto `source_link_manager`.|  
|[source\_link\_manager::contains \(Método\)](../Topic/source_link_manager::contains%20Method.md)|Busca `network_link_registry` en este objeto `source_link_manager` para un bloque especificado.|  
|[source\_link\_manager::count \(Método\)](../Topic/source_link_manager::count%20Method.md)|Cuenta el número de bloques vinculados del objeto `source_link_manager`.|  
|[source\_link\_manager::reference \(Método\)](../Topic/source_link_manager::reference%20Method.md)|Adquiere una referencia en el objeto `source_link_manager`.|  
|[source\_link\_manager::register\_target\_block \(Método\)](../Topic/source_link_manager::register_target_block%20Method.md)|Registra el bloque de destino que contiene este objeto `source_link_manager`.|  
|[source\_link\_manager::release \(Método\)](../Topic/source_link_manager::release%20Method.md)|Libera la referencia en el objeto `source_link_manager`.|  
|[source\_link\_manager::remove \(Método\)](../Topic/source_link_manager::remove%20Method.md)|Quita un vínculo del objeto `source_link_manager`.|  
|[source\_link\_manager::set\_bound \(Método\)](../Topic/source_link_manager::set_bound%20Method.md)|Establece el número máximo de vínculos de origen que se pueden agregar a este objeto `source_link_manager`.|  
  
## Comentarios  
 Actualmente, los bloques de origen son contadores de referencia.  Este es un contenedor en un objeto `network_link_registry` que permite el acceso simultáneo a los vínculos y proporciona la capacidad de hacer referencia a los vínculos a través de devoluciones de llamada.  Los bloques de mensaje \(`target_block`s o `propagator_block`s\) deberían usar esta clase para sus vínculos de origen.  
  
## Jerarquía de herencia  
 `source_link_manager`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry \(Clase\)](../../../parallel/concrt/reference/single-link-registry-class.md)   
 [multi\_link\_registry \(Clase\)](../../../parallel/concrt/reference/multi-link-registry-class.md)