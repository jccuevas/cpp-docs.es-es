---
title: "Error del compilador C3185 | Microsoft Docs"
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
  - "C3185"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3185"
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3185
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'typeid' usado en un tipo ’type’ administrado o de WinRT; use 'operator' en su lugar  
  
 No se puede aplicar el operador [typeid](../../cpp/typeid-operator.md) a un tipo administrado o de WinRT; use [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) en su lugar.  
  
 El ejemplo siguiente genera el error C3185 y muestra cómo corregirlo:  
  
```  
// C3185a.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
  
int main() {  
   Derived ^ pd = gcnew Derived;  
   Base ^pb = pd;  
   const type_info & t1 = typeid(pb);   // C3185  
   System::Type ^ MyType = Base::typeid;   // OK  
};  
```  
  
 **Extensiones administradas de C\+\+**  
  
 No se puede aplicar [typeid](../../cpp/typeid-operator.md) a un tipo administrado; use [\_\_typeof](../../misc/typeof.md) en su lugar.  
  
 El ejemplo siguiente genera el error C3185:  
  
```  
// C3185b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__gc class Base {};  
__gc class Derived : public Base {};  
  
int main() {  
   Derived *pd = new Derived;  
   Base *pb = pd;  
   const type_info & t1 = typeid(*pb);   // C3185  
  
   // OK  
   Type * t = __typeof(Base);  
   Type * t1 = __typeof(Derived);  
};  
```