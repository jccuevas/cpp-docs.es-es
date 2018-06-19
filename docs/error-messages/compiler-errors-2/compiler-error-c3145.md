---
title: Error del compilador C3145 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3145
dev_langs:
- C++
helpviewer_keywords:
- C3145
ms.assetid: f165c874-0f51-45c7-85e8-ebe321cbc168
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2654fca05941ab8c934891a9f95375fca1a6b82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246746"
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
