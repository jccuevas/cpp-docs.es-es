---
title: "Error del compilador C2910 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2910"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2910"
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2910
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : no puede estar especializada de forma explícita  
  
 El compilador ha detectado un intento de especializar explícitamente dos veces la misma función.  
  
 El código siguiente genera el error C2910:  
  
```  
// C2910.cpp  
// compile with: /c  
template <class T>  
struct S;  
  
template <> struct S<int> { void f() {} };  
template <> void S<int>::f() {}   // C2910 delete this specialization  
```  
  
 El error C2910 también puede producirse si se intenta especializar explícitamente un miembro que no sea de la plantilla.  Es decir, sólo se puede especializar explícitamente una plantilla de función.  
  
 El código siguiente genera el error C2910:  
  
```  
// C2910b.cpp  
// compile with: /c  
template <class T> struct A {  
   A(T* p);  
};  
  
template <> struct A<void> {  
   A(void* p);  
};  
  
template <class T>  
inline A<T>::A(T* p) {}  
  
template <> A<void>::A(void* p){}   // C2910  
// try the following line instead  
// A<void>::A(void* p){}  
```  
  
 Este error también se producirá como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003:  
  
 Para que el código sea válido en las versiones Visual Studio .NET 2003 y Visual Studio .NET de Visual C\+\+, quite `template <>`.  
  
 El código siguiente genera el error C2910:  
  
```  
// C2910c.cpp  
// compile with: /c  
template <class T> class A {  
   void f();  
};  
  
template <> class A<int> {  
   void f();  
};  
  
template <> void A<int>::f() {}   // C2910  
// try the following line instead  
// void A<int>::f(){}   // OK  
```