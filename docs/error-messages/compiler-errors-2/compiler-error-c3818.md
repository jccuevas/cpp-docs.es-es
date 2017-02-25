---
title: "Error del compilador C3818 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3818"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3818"
ms.assetid: f9502f6a-0690-4135-ab88-cc97cf490f5c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3818
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la declaración de propiedad de matriz 'propiedad1' no debe sobrecargar una propiedad Index 'propiedad2'  
  
 No es posible la sobrecarga en propiedad donde una es indizadora y la otra es una propiedad de matriz.  Vea [\_\_property](../../misc/property.md) para obtener más información.  
  
 Sólo se puede reproducir el error C3818 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3818:  
  
```  
// C3818.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class X {  
public:  
   __property int get_Int(int index) {  
      Console::WriteLine(S"Called indexed property");  
      return m_value;  
   }  
  
   __property int get_Int() __gc[] {   // C3818, rename a property  
      Console::WriteLine(S"Called array property");  
      return m_arr;  
   }  
  
   int m_arr __gc[];  
   int m_value;  
};  
  
int main() {  
   X* x = new X;  
   x->m_arr = new int __gc[3];  
   x->m_value = 3;  
  
   x->Int[0];  
}  
```