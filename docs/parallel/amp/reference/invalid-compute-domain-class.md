---
title: "invalid_compute_domain (Clase) | Microsoft Docs"
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
  - "amprt/Concurrency::invalid_compute_domain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_compute_domain (clase)"
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_compute_domain (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La excepción que se produce cuando el runtime no puede iniciar un kernel utilizando el dominio del cálculo especificado en el sitio de la llamada a [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md).  
  
## Sintaxis  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_compute\_domain::invalid\_compute\_domain \(Constructor\)](../Topic/invalid_compute_domain::invalid_compute_domain%20Constructor.md)|Inicializa una nueva instancia de la clase `invalid_compute_domain`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)