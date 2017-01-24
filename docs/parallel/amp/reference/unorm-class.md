---
title: "unorm (Clase) | Microsoft Docs"
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
  - "amp_short_vectors/Concurrency::graphics::unorm"
  - "amp/Concurrency::graphics::unorm"
dev_langs: 
  - "C++"
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unorm (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa un número unorm.  Cada elemento es un número en coma flotante en el rango de \[0,0f, 1.0f\].  
  
## Sintaxis  
  
```  
class unorm;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[unorm::unorm \(Constructor\)](../Topic/unorm::unorm%20Constructor.md)|Sobrecargado.  Constructor predeterminado.  Inicializar a 0,0f.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|Operador unorm::operator\-\-||  
|Operador flotante unorm::operator|Operador de conversión.  Convierta el número unorm a un valor en coma flotante.|  
|Operador unorm::operator\*\=||  
|Operador unorm::operator\/\=||  
|Operador unorm::operator\+\+||  
|Operador unorm::operator\+\=||  
|Operador unorm::operator\=||  
|Operador unorm::operator\-\=||  
  
## Jerarquía de herencia  
 `unorm`  
  
## Requisitos  
 **Encabezado:** amp\_short\_vectors.h  
  
 **Espacio de nombres:** Concurrency::graphics  
  
## Vea también  
 [Concurrency::graphics \(Espacio de nombres\)](../../../parallel/amp/reference/concurrency-graphics-namespace.md)