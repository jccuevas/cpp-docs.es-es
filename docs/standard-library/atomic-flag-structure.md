---
title: "atomic_flag (Estructura) | Microsoft Docs"
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
  - "atomic/std::atomic_flag"
dev_langs: 
  - "C++"
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atomic_flag (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que establece y borra una marca `bool` de forma atómica.  Las operaciones sobre marcas atómicas nunca tienen bloqueos.  
  
## Sintaxis  
  
```  
struct atomic_flag;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[atomic\_flag::clear \(Método\)](../Topic/atomic_flag::clear%20Method.md)|Establece la marca almacenada en `false`.|  
|[atomic\_flag::test\_and\_set \(Método\)](../Topic/atomic_flag::test_and_set%20Method.md)|Establece la marca almacenada en `true` y devuelve el valor inicial de la marca.|  
  
## Comentarios  
 Se pueden pasar objetos `atomic_flag` a las funciones no miembro [atomic\_flag\_clear](../Topic/atomic_flag_clear%20Function.md), [atomic\_flag\_clear\_explicit](../Topic/atomic_flag_clear_explicit%20Function.md), [atomic\_flag\_test\_and\_set](../Topic/atomic_flag_test_and_set%20Function.md) y [atomic\_flag\_test\_and\_set\_explicit](../Topic/atomic_flag_test_and_set_explicit%20Function.md).  Se pueden inicializar con el valor `ATOMIC_FLAG_INIT`.  
  
## Requisitos  
 **Encabezado:** atomic  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<atomic\>](../standard-library/atomic.md)