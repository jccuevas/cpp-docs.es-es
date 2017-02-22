---
title: "Error del compilador C3915 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3915"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3915"
ms.assetid: 2b0a5e5f-3aec-4a4b-9157-233031817084
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3915
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' no tiene propiedad indizada predeterminada \(indizador de clase\)  
  
 Un tipo no tiene una propiedad indizada predeterminada.  
  
 Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3915.  
  
```  
// C3915.cpp  
// compile with: /clr  
ref class X {  
public:  
// uncomment property to resolve this C3915  
//   property int default[]  
//   {  
//      int get(int i)  
//      {  
//         return 863;  
//      }  
//   }  
};  
  
int main() {  
   X^ x = new X;  
   System::Console::WriteLine(x[1]);   // C3915  
}  
```  
  
## Ejemplo  
 El error C3915 también puede producirse si se intenta consumir un indizador predeterminado en el mismo compilando en que se definió con <xref:System.Reflection.DefaultMemberAttribute>.  
  
 El ejemplo siguiente genera el error C3915.  
  
```  
// C3915_b.cpp  
// compile with: /clr  
using namespace System;  
  
[Reflection::DefaultMember("XXX")]  
ref struct A {  
   property Double XXX[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
};  
  
ref struct B {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
};  
  
int main() {  
   A ^ mya = gcnew A();  
   Console::WriteLine("{0}", mya[3]);   // C3915  
  
   B ^ myb = gcnew B();  
   Console::WriteLine("{0}", myb[3]);   // OK  
}  
```