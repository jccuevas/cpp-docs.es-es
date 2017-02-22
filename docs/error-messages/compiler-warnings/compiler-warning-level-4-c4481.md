---
title: "Advertencia del compilador (nivel 4) C4481 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4481"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4481"
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Advertencia del compilador (nivel 4) C4481
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se utilizó una extensión no estándar: especificador de reemplazo 'palabra clave'  
  
 Se utilizó una palabra clave que no está en el estándar de C\+\+, por ejemplo, uno de los especificadores de reemplazo que también funciona bajo \/clr.  Para obtener más información, vea  
  
-   [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4481.  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```