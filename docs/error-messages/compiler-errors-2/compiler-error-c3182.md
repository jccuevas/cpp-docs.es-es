---
title: "Error del compilador C3182 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3182"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3182"
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C3182
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': no se permiten declaraciones using de miembro o declaraciones de acceso dentro de un tipo WinRT o administrado  
  
 Una declaración [using](../../cpp/using-declaration.md) no es válida en todos los formularios de clases administradas.  
  
 En el ejemplo siguiente se genera el error C3182 y se muestra cómo corregirlo:  
  
```  
// C3182a.cpp  
// compile with: /clr /c  
ref struct B {  
   void mf(int) {  
   }  
};  
  
ref struct D : B {  
   using B::mf;   // C3182, delete to resolve  
   void mf(char) {  
   }  
};  
```  
  
 En el ejemplo siguiente se genera el error C3182 y se muestra cómo corregirlo:  
  
```  
// C3182b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc struct B {  
   void mf(int)  
   {  
   }  
};  
  
__gc struct D : B {  
   using B::mf;   // C3182, delete to resolve  
   void mf(char)  
   {  
   }  
};  
  
int main()  
{  
}  
```