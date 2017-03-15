---
title: "Advertencia del compilador (nivel 1) C4288 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4288"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4288"
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 1) C4288
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : 'variable' : la variable de control de bucles declarada en el bucle For se utiliza fuera del ámbito del bucle For; origina conflictos con la declaración en el ámbito externo  
  
 Al compilar con [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) y **\/Zc:forscope\-**, se utilizó una variable declarada en un bucle **for** más allá del ámbito del bucle [for](../../cpp/for-statement-cpp.md).  Una extensión de Microsoft del lenguaje C\+\+ permite que esta variable permanezca dentro del ámbito, y la advertencia C4288 recuerda que no se utiliza la primera declaración de la variable.  
  
 Vea [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) para obtener información sobre cómo especificar la extensión de Microsoft en los bucles **for** mediante \/Ze.  
  
 El código siguiente genera el error C4288:  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```