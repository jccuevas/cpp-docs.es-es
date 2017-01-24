---
title: "once_flag (Estructura) | Microsoft Docs"
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
  - "mutex/std::once_flag"
dev_langs: 
  - "C++"
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# once_flag (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa `struct` que se utiliza con la función [call\_once](../Topic/call_once%20Function.md) de plantilla para garantizar que el código de inicialización se invoca solo una vez, incluso en presencia de varios subprocesos de ejecución.  
  
## Sintaxis  
  
```cpp  
struct once_flag  
{  
   constexpr once_flag() noexcept;  
   once_flag(const once_flag&);  
   once_flag& operator=(const once_flag&);  
};  
```  
  
## Comentarios  
 `once_flag` `struct` sólo tiene un constructor predeterminado.  
  
 Los objetos de `once_flag` tipo pueden ser creados, pero no se puede copiar.  
  
## Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)