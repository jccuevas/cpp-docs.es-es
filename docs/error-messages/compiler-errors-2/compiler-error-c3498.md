---
title: "Compiler Error C3498 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3498"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3498"
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Compiler Error C3498
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': no se puede capturar una variable que tiene un tipo administrado o WinRT  
  
 No se puede capturar una variable que tiene un tipo administrado o un tipo de Windows en tiempo de ejecución en una expresión lambda.  
  
### Para corregir este error  
  
-   Pase la variable administrada o de Windows en tiempo de ejecución a la lista de parámetros de la expresión lambda.  
  
## Ejemplo  
 El ejemplo siguiente genera C3498 porque una variable que tiene un tipo administrado aparece en la lista de captura de una expresión lambda:  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente resuelve C3498 al pasar la variable administrada `s` a la lista de parámetros de la expresión lambda:  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)