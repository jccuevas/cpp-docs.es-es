---
title: C2653 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cc7990614283a20e9d07f52187258dbccad7c075
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2653"></a>C2653 de Error del compilador
'identificador': no es un nombre de clase o espacio de nombres  
  
Sintaxis requiere una clase, estructura, unión o nombre de espacio de nombres.  
  
El ejemplo siguiente genera C2653:  
  
```cpp  
// C2653.cpp  
// compile with: /c  
class yy {  
   void func1(int i);  
};  
  
void xx::func1(int m) {}   // C2653  
void yy::func1(int m) {}   // OK  
```  
  
También es posible si se intenta definir C2653 una *espacio de nombres compuesto*, un espacio de nombres que contiene uno o más nombres de espacio de nombres con ámbito anidado, cuando se utiliza una versión de Visual C++ anteriores a Visual Studio 2015 Update 3. Compuesta espacio de nombres no se permiten definiciones en C++ antes de C ++ 17. A partir de Visual C++ 2015 Update 3, el compilador admite las definiciones de espacio de nombres compuestos cuando el [/std:c ++ más reciente](../../build/reference/std-specify-language-standard-version.md) se especifica la opción del compilador:  
```cpp  
// C2653b.cpp  
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,  
                          // C2429 thereafter. Use /std:c++latest to fix.
namespace a {  
   namespace b {  
      int i;  
   }  
}  
  
int main() {  
   a::b::i = 2;  
}  
```  
