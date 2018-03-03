---
title: Error del compilador C3145 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3145
dev_langs:
- C++
helpviewer_keywords:
- C3145
ms.assetid: f165c874-0f51-45c7-85e8-ebe321cbc168
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9fb45f3fc90a0586f0f5b08dd12f0a244dd2332
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3145"></a>Error del compilador C3145
'object': es posible que la variable global o estática no tenga un tipo WinRT o administrado 'type'  
  
 Solo se pueden definir objetos CLR o WinRT en el ámbito de función.  
  
 En el ejemplo siguiente se genera el error C3145 y se muestra cómo corregirlo:  
  
```  
// C3145.cpp  
// compile with: /clr  
using namespace System;   
ref class G {};   
  
G ^ ptr;   // C3145  
G ^ ptr2 = gcnew G;   // C3145  
  
ref class GlobalObjects {  
public:  
   static G ^ ptr;   // OK  
   static G ^ ptr2 = gcnew G;   // OK   
};   
  
int main() {  
   G ^ ptr;   // OK  
   G ^ ptr2 = gcnew G;   // OK  
}  
```  
  
 El ejemplo siguiente genera el error C3145:  
  
```  
// C3145b.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   static int data;  
};  
  
interior_ptr<int> p = &(MyClass::data);   // C3145  
  
void Test(interior_ptr<int> x) {}  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   interior_ptr<int> p = &(h_MyClass->data);  
}  
```  
