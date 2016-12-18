---
title: "accelerator_view_removed (Clase) | Microsoft Docs"
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
  - "amprt/Concurrency::accelerator_view_removed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "amprt/Concurrency::accelerator_view_removed (clase)"
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: 6
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# accelerator_view_removed (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La excepción que se produce cuando una llamada de DirectX subyacente falla debido a la detección de tiempo de espera de Windows y el mecanismo de recuperación.  
  
## Sintaxis  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator\_view\_removed::accelerator\_view\_removed \(Constructor\)](../Topic/accelerator_view_removed::accelerator_view_removed%20Constructor.md)|Inicializa una nueva instancia de la clase `accelerator_view_removed`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator\_view\_removed::get\_view\_removed\_reason \(Método\)](../Topic/accelerator_view_removed::get_view_removed_reason%20Method.md)|Devuelve un código de error HRESULT que indica la causa de eliminación del objeto `accelerator_view`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)