---
title: "Advertencia del compilador (nivel 4) C4339 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4339"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4339"
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Advertencia del compilador (nivel 4) C4339
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': se detectó el uso de un tipo no definido en los metadatos de WinRT o CLR; el uso de este tipo puede provocar una excepción en tiempo de ejecución  
  
 No se definió un tipo en el código que se compiló para Windows en tiempo de ejecución o Common Language Runtime.  Defina el tipo para evitar una posible excepción en tiempo de ejecución.  
  
 De forma predeterminada, esta advertencia está desactivada.  Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para obtener más información.  
  
 El ejemplo siguiente genera el error C4339 y muestra cómo corregirlo:  
  
```  
// C4339.cpp  
// compile with: /W4 /clr /c  
// C4339 expected  
#pragma warning(default : 4339)  
  
// Delete the following line to resolve.  
class A;  
  
// Uncomment the following line to resolve.  
// class A{};  
  
class X {  
public:  
   X() {}  
  
   virtual A *mf() {  
      return 0;  
   }  
};  
  
X * f() {  
   return new X();  
}  
```