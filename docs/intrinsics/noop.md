---
title: "__noop | Microsoft Docs"
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
  - "__noop_cpp"
  - "__noop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__noop (palabra clave) [C++]"
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __noop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Función intrínseca de `__noop` especifica que una función debe omitir y la lista de argumentos está analizada pero no se genera ningún código para los argumentos.  Está pensado para su uso en las funciones globales de depuración que toman un número variable de argumentos.  
  
 El compilador convierte intrínsecos de `__noop` a 0 en tiempo de compilación.  
  
## Ejemplo  
 El código siguiente muestra cómo puede utilizar `__noop`.  
  
```  
// compiler_intrinsics__noop.cpp  
// compile with or without /DDEBUG  
#include <stdio.h>  
  
#if DEBUG  
   #define PRINT   printf_s  
#else  
   #define PRINT   __noop  
#endif  
  
int main() {  
   PRINT("\nhello\n");  
}  
```  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)