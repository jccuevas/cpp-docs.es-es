---
title: "duration_values (Estructura) | Microsoft Docs"
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
  - "chrono/std::chrono::duration_values"
dev_langs: 
  - "C++"
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# duration_values (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona valores concretos para el parámetro de plantilla [duration](../standard-library/duration-class.md) `Rep`.  
  
## Sintaxis  
  
```  
template<class Rep>  
   struct duration_values;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[duration\_values::max \(Método\)](../Topic/duration_values::max%20Method.md)|Estático.  Especifica el límite superior para un valor de tipo `Rep`.|  
|[duration\_values::min \(Método\)](../Topic/duration_values::min%20Method.md)|Estático.  Especifica el límite inferior para un valor de tipo `Rep`.|  
|[duration\_values::zero \(Método\)](../Topic/duration_values::zero%20Method.md)|Estático.  Devuelve `Rep(0)`.|  
  
## Requisitos  
 **Encabezado:** chrono  
  
 **Espacio de nombres:** std::chrono  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)