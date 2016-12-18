---
title: "Error del compilador C2682 | Microsoft Docs"
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
  - "C2682"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2682"
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2682
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede utilizar operador\_de\_conversión para convertir de 'tipo1' en 'tipo2'  
  
 Un operador de conversión intentó realizar una conversión entre tipos incompatibles.  Por ejemplo, no se puede usar el operador [dynamic\_cast](../../cpp/dynamic-cast-operator.md) para convertir un puntero a una referencia.  El operador `dynamic_cast` no se puede utilizar para convertir calificadores.  Todos los calificadores de los tipos deben coincidir.  
  
 Se puede usar el operador `const_cast` para quitar atributos como `const`, `volatile` o `__unaligned`.  
  
 El código siguiente genera el error C2682:  
  
```  
// C2682.cpp  
class A { virtual void f(); };  
class B: public A {};  
  
void g(A* pa) {  
    B& rb = dynamic_cast<B&>(pa); // C2682  
}  
```  
  
 El código siguiente genera el error C2682:  
  
```  
// C2682b.cpp  
// compile with: /clr  
ref struct R{};  
ref struct RR : public R{};  
ref struct H {  
   RR^ r ;  
   short s;  
   int i;  
};  
  
int main() {  
   H^ h = gcnew H();    
   interior_ptr<int>lr = &(h->i);  
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682  
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK  
}  
```