---
title: "deprecated (C/C++) | Microsoft Docs"
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
  - "vc-pragma.deprecated"
  - "deprecated_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "deprecated (pragma)"
  - "pragma (directivas), deprecated"
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# deprecated (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La pragma **deprecated** permite indicar que un tipo de función, o cualquier otro identificador puede deje de admitirse en una versión futura o no debe seguir utilizándose.  
  
## Sintaxis  
  
```  
  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## Comentarios  
 Cuando el compilador encuentra un símbolo desusado, emite [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).  
  
 Puede desusar nombres de macro.  Coloque el nombre de la macro entre comillas; de lo contrario se producirá la expansión de la macro.  
  
 El modificador [deprecated](../cpp/deprecated-cpp.md) `__declspec` permite especificar el estado desusado para formas concretas de funciones sobrecargadas.  
  
## Ejemplo  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 En el ejemplo siguiente se muestra cómo desusar una clase:  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)