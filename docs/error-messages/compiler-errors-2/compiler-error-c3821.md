---
title: "Error del compilador C3821 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3821"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3821"
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C3821
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': una función o tipo administrado no se puede utilizar en una función no administrada  
  
 Las funciones con ensamblado en línea o [setjmp](../../c-runtime-library/reference/setjmp.md) no pueden contener tipos de valor o clases administradas.  Para corregir este error, quite el ensamblado en línea y `setjmp` o quite los objetos administrados.  
  
 El error C3821 también puede producirse si se intenta utilizar el almacenamiento automático en una función vararg.  Para obtener más información, vea [Listas de argumentos de variables \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md) y [Semántica de pila de C\+\+ para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3821.  
  
```  
// C3821a.cpp  
// compile with: /clr /c  
public ref struct R {};  
void test1(...) {  
   R r;   // C3821  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3821.  
  
```  
// C3821b.cpp  
// compile with: /clr  
// processor: /x86  
ref class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A ^a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3821.  
  
```  
// C3821c.cpp  
// compile with: /clr:oldSyntax  
// processor: /x86  
__gc  class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A *a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```