---
title: "sampler (Clase) | Microsoft Docs"
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
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# sampler (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase de muestra agrega información de configuración de muestreo que se utilizará para el muestreo de textura.  
  
## Sintaxis  
  
```  
class sampler;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[sampler::sampler \(Constructor\)](../Topic/sampler::sampler%20Constructor.md)|Sobrecargado.  Construye una instancia de muestra.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[sampler::get\_address\_mode \(Método\)](../Topic/sampler::get_address_mode%20Method.md)|Devuelve el objeto `address_mode` asociado con el objeto de muestra.|  
|[sampler::get\_border\_color \(Método\)](../Topic/sampler::get_border_color%20Method.md)|Devuelve el color del borde asociado al objeto de muestra.|  
|[sampler::get\_filter\_mode \(Método\)](../Topic/sampler::get_filter_mode%20Method.md)|Devuelve el objeto `filter_mode` asociado con el objeto de muestra.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[sampler::operator\= \(Operador\)](../Topic/sampler::operator=%20Operator.md)|Sobrecargado.  Operador de asignación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[sampler::address\_mode \(Miembro de datos\)](../Topic/sampler::address_mode%20Data%20Member.md)|Obtiene el modo de dirección del objeto `sampler`.|  
|[sampler::border\_color \(Miembro de datos\)](../Topic/sampler::border_color%20Data%20Member.md)|Obtiene el color del borde del objeto `sampler`.|  
|[sampler::filter\_mode \(Miembro de datos\)](../Topic/sampler::filter_mode%20Data%20Member.md)|Obtiene el modo de filtro del objeto `sampler`.|  
  
## Jerarquía de herencia  
 `sampler`  
  
## Requisitos  
 **Encabezado:** amp\_graphics.h  
  
 **Espacio de nombres:** concurrency::graphics  
  
## Vea también  
 [Concurrency::graphics \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-graphics-namespace.md)