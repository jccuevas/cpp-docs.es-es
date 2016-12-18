---
title: "Advertencia del compilador (nivel 4) C4571 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4571"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4571"
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4571
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Información: la semántica de catch\(...\) cambió desde Visual C\+\+ 7.1; ya no se detectan excepciones estructuradas \(SEH\)  
  
 La advertencia C4571 se genera para cada bloque catch\(...\) al compilar con **\/EHs**.  
  
 Cuando se compila con **\/EHs**, un bloque catch\(...\) no detecta una excepción estructurada \(por ejemplo, dividir por cero, o un puntero nulo\); un bloque catch\(...\) únicamente detectará excepciones de C\+\+ que se hayan producido explícitamente.  Para obtener más información, vea [Control de excepciones](../../cpp/exception-handling-in-visual-cpp.md).  
  
 De forma predeterminada, esta advertencia está desactivada.  Active esta advertencia para garantizar que cuando se compile con **\/EHs**, los bloques catch\(...\) no tratarán de detectar excepciones estructuradas.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Para resolver la advertencia C4571, siga uno de estos procedimientos:  
  
-   Compile con **\/EHa** si todavía desea que los bloques catch\(...\) detecten excepciones estructuradas.  
  
-   No habilite C4571 si no quiere que los bloques catch\(...\) detecten excepciones estructuradas, pero todavía desea utilizar bloques catch\(...\).  Puede detectar las excepciones estructuradas mediante las palabras clave de control de excepciones estructuradas \(**\_\_try**, **\_\_except** y **\_\_finally**\).  Pero recuerde que, después de la compilación, sólo se llamará a los destructores **\/EHs** cuando se produzca una excepción de C\+\+, no cuando se produzca una excepción SEH.  
  
-   Reemplace el bloque catch\(...\) por bloques catch para excepciones de C\+\+ específicas y, si lo desea, agregue un control de excepciones estructuradas en torno al control de excepciones de C\+\+ \(**\_\_try**, **\_\_except** y **\_\_finally**\).  Para obtener más información, vea [Control de excepciones estructurado](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Para obtener más información, vea [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4571.  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```