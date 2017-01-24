---
title: "Error del compilador C3754 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3754"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3754"
ms.assetid: 14b877bc-9277-40ec-af1c-196a58b45f10
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3754
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

constructor delegado: no se puede llamar a la función miembro 'función' en una instancia de tipo 'tipo'  
  
 Se realizó una llamada a una función a través de un puntero a un tipo que no contiene la función.  
  
 El código siguiente genera el error C3754:  
  
```  
// C3754a.cpp  
// compile with: /clr  
using namespace System;  
  
delegate void MyDel();  
  
interface class MyInterface {};  
  
ref struct MyClass : MyInterface {  
   void f() {}  
};  
  
int main() {  
   MyInterface^ p = gcnew MyClass;  
   MyDel^ q = gcnew MyDel(p, &MyClass::f);   // C3754  
   // try the following line instead  
//   MyDel^ q = gcnew MyDel(safe_cast<MyClass^>(p), &MyClass::f);  
}  
```  
  
 El código siguiente genera el error C3754:  
  
```  
// C3754b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__delegate void MyDel();  
  
__gc __interface MyInterface {};  
  
__gc struct MyClass : MyInterface {  
   void f() {}  
};  
  
int main() {  
   MyInterface* p = new MyClass;  
   MyDel* q = new MyDel(p, &MyClass::f);   // C3754  
   // try the following line instead  
   // MyDel* q = new MyDel(__try_cast<MyClass*>(p), &MyClass::f);  
}  
```