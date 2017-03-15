---
title: "Error del compilador C3764 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3764"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3764"
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3764
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función\_de\_reemplazo': no se puede reemplazar el método de clase base 'función\_de\_clase\_base'  
  
 El compilador ha detectado un reemplazo mal formado.  Por ejemplo, la función de clase base no era `virtual`.  Para obtener más información, vea [override](../../windows/override-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3764.  
  
```  
// C3764.cpp  
// compile with: /clr /c  
public ref struct A {  
   void g(int);  
   virtual void h(int);  
};  
  
public ref struct B : A {  
   virtual void g(int) override {}   // C3764  
   virtual void h(int) override {}   // OK  
};  
```  
  
## Ejemplo  
 El error C3764 también puede aparecer cuando un método de clase base es reemplazado explícitamente y se cambia su nombre.  El ejemplo siguiente genera el error C3764.  
  
```  
// C3764_b.cpp  
// compile with: /clr /c  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : public A {  
   virtual void Test() override {}  
   virtual void Test2() = A::Test {}   // C3764  
};  
```