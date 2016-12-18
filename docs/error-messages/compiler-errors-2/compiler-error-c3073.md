---
title: "Error del compilador C3073 | Microsoft Docs"
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
  - "C3073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3073"
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : la clase de ref no tiene un constructor de copia definido por el usuario  
  
 En una compilación [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md), el compilador no generará un constructor de copias para un tipo de referencia.  En una compilación **\/clr**, debe definir un constructor de copias para un tipo de referencia si espera que se copie una instancia del tipo.  
  
 Para obtener más información, vea [Semántica de pila de C\+\+ para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3073.  
  
```  
// C3073.cpp  
// compile with: /clr  
ref class R {  
public:  
   R(int) {}  
};  
  
ref class S {  
public:  
   S(int) {}  
   S(const S %rhs) {}   // copy constructor  
};  
  
void f(R) {}  
void f2(S) {}  
void f3(R%){}  
  
int main() {  
   R r(1);  
   f(r);   // C3073  
   f3(r);   // OK  
  
   S s(1);  
   f2(s);   // OK  
}  
```