---
title: "scoped_d3d_access_lock (Clase) | Microsoft Docs"
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
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# scoped_d3d_access_lock (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Contenedor RAII para un bloqueo de acceso de D3D en un objeto accelerator\_view.  
  
## Sintaxis  
  
```  
class scoped_d3d_access_lock;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scoped\_d3d\_access\_lock::scoped\_d3d\_access\_lock \(Constructor\)](../Topic/scoped_d3d_access_lock::scoped_d3d_access_lock%20Constructor.md)|Sobrecargado.  Construye un objeto `scoped_d3d_access_lock`.  Se libera el bloqueo cuando este objeto queda fuera del ámbito.|  
|[scoped\_d3d\_access\_lock::~scoped\_d3d\_access\_lock \(Destructor\)](../Topic/scoped_d3d_access_lock::~scoped_d3d_access_lock%20Destructor.md)|Libera el bloqueo de acceso de D3D en el objeto `accelerator_view` asociado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scoped\_d3d\_access\_lock::operator\= \(Operador\)](../Topic/scoped_d3d_access_lock::operator=%20Operator.md)|Toma posesión de un bloqueo de otro objeto `scoped_d3d_access_lock`.|  
  
## Jerarquía de herencia  
 `scoped_d3d_access_lock`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** concurrency::direct3d  
  
## Vea también  
 [Concurrency::direct3d \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)