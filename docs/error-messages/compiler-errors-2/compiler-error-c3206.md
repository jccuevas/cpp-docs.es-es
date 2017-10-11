---
title: Error del compilador C3206 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3206
dev_langs:
- C++
helpviewer_keywords:
- C3206
ms.assetid: d62995b5-e349-4418-bbe8-8a5e776ca7b0
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 600ea77821fc457a631f96d48b2416f958dce667
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3206"></a>Error del compilador C3206
'function': argumento de tipo no válido para 'param', falta la lista de argumentos de tipo en el tipo de clase 'typename'  
  
 Se ha definido una función de plantilla que toma un argumento de tipo de plantilla. Sin embargo, se pasó un argumento de plantilla.  
  
 El ejemplo siguiente genera la advertencia C3206:  
  
```  
// C3206.cpp  
template <class T>  
void f() {}  
  
template <class T>  
struct S {};  
  
void f1() {  
   f<S>();   // C3206  
   // try the following line instead  
   // f<S<int> >();  
}  
```  
  
 Posible solución:  
  
```  
// C3206b.cpp  
// compile with: /c  
template <class T>  
void f() {}  
  
template <class T>  
struct S {};  
  
void f1() {  
   f<S<int> >();  
}  
```  
  
 También se puede producir el error C3206 al usar genéricos:  
  
```  
// C3206c.cpp  
// compile with: /clr  
generic <class GT1>  
void gf() {}  
  
generic <class T>  
value struct GS {};  
  
int main() {  
   gf<GS>();   // C3206  
}  
```  
  
 Posible solución:  
  
```  
// C3206d.cpp  
// compile with: /clr  
generic <class GT1>  
void gf() {}  
  
generic <class T>  
value struct GS {};  
  
int main() {  
   gf<GS<int> >();  
}  
```  
  
 Este error también se puede generar como resultado del trabajo de conformidad del compilador de Visual C++ .NET 2003, donde no se permiten plantillas de clase como argumentos de tipo de plantilla.  
  
 No se permite una plantilla de clase como argumento de tipo de plantilla. Esto funcionaba en Visual C++ .NET 2003, pero es válido en C++.  
  
 El ejemplo siguiente se compila en Visual C++ .NET 2002, pero se producirá un error en Visual C++ .NET 2003:  
  
```  
// C3206e.cpp  
template <class T>  
struct S {};  
  
template <class T>  
void func() {   // takes a type  
   T<int> t;  
}  
  
int main() {  
   func<S>();   // C3206 S is not a type.  
}  
```  
  
 Posible solución:  
  
```  
// C3206f.cpp  
template <class T>  
struct S {};  
  
template <class T>  
void func() {   // takes a type  
   T t;  
}  
  
int main() {  
   func<S<int> >();  
}  
```  
  
 Si es necesario un parámetro de plantilla, la resolución del error que es válida en las versiones de Visual C++ .NET 2002 y Visual C++ .NET 2003 requieren ajustar la función en una clase de plantilla que toma un parámetro de plantilla:  
  
```  
// C3206g.cpp  
template <class T>  
struct S {};  
  
template<template<class> class TT>  
struct X {  
   static void func() {  
      TT<int> t1;  
      TT<char> t2;  
   }  
};  
  
int main() {  
   X<S>::func();  
}  
```
