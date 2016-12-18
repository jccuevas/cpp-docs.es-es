---
title: "Error del compilador C3842 | Microsoft Docs"
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
  - "C3842"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3842"
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3842
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': no se admiten calificadores 'const' y 'volatile' en funciones miembro de WinRT o tipos administrados  
  
 [const](../../cpp/const-cpp.md) y [volatile](../../cpp/volatile-cpp.md) no se admiten en las funciones miembro de Windows en tiempo de ejecución o tipos administrados.  
  
 El siguiente ejemplo genera el error C3842:  
  
```  
// C3842a.cpp  
// compile with: /clr /c  
public ref struct A {  
   void f() const {}   // C3842  
   void f() volatile {}   // C3842  
  
   void f() {}  
};  
  
```