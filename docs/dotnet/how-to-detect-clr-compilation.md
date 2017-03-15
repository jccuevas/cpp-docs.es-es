---
title: "C&#243;mo: Detectar la compilaci&#243;n de /clr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], detectar el uso"
  - "compilación, detectar en /clr"
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Detectar la compilaci&#243;n de /clr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice la macro `_MANAGED` o `_M_CEE` para ver si un módulo se compila con **\/clr**.  Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Para obtener más información sobre macros, vea [Macros predefinidas](../preprocessor/predefined-macros.md).  
  
## Ejemplo  
  
```  
// detect_CLR_compilation.cpp  
// compile with: /clr  
#include <stdio.h>  
  
int main() {  
   #if (_MANAGED == 1) || (_M_CEE == 1)  
      printf_s("compiling with /clr\n");  
   #else  
      printf_s("compiling without /clr\n");  
   #endif  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)