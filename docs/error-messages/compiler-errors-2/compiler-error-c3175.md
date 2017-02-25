---
title: "Error del compilador C3175 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3175"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3175"
ms.assetid: 3f19d513-a05a-4b6c-806f-276fe5c36b90
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3175
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función1' : no se puede llamar un método de un tipo administrado desde la función no administrada 'función2'  
  
 Las funciones no administradas no pueden llamar a funciones miembro de clases administradas.  
  
 El código siguiente genera el error C3175:  
  
```  
// C3175_2.cpp  
// compile with: /clr  
  
ref struct A {  
   static void func() {  
   }  
};  
  
#pragma unmanaged   // remove this line to resolve  
  
void func2() {  
   A::func();   // C3175  
}  
  
#pragma managed  
  
int main() {  
   A ^a = gcnew A;  
   func2();  
}  
```  
  
 El código siguiente genera el error C3175:  
  
```  
// C3175.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc struct A  
{  
   static void func()  
   {  
   }  
};  
  
#pragma unmanaged   // remove this line to resolve  
  
void func2()  
{  
   A::func();   // C3175  
}  
  
#pragma managed  
  
int main()  
{  
   A *a = new A;  
   func2();  
}  
```