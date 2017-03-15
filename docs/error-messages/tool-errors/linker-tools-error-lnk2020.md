---
title: "Error de las herramientas del vinculador LNK2020 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2020"
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# Error de las herramientas del vinculador LNK2020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo \(token\) sin resolver 'token'  
  
 Similar a un error de símbolo externo no definido, salvo que la referencia tiene lugar a través de los metadatos.  En los metadatos, se deben definir todos los datos y funciones.  
  
 Para resolverlo:  
  
-   Defina la función o los datos que faltan, o bien  
  
-   Incluya el archivo objeto o biblioteca donde la función o los datos que faltan ya están definidos.  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK2020.  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## Ejemplo  
 También puede producirse el error LNK2020 si se crea una variable de un tipo de plantilla administrado, pero no se crean también instancias del tipo.  
  
 El ejemplo siguiente genera el error LNK2020.  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```