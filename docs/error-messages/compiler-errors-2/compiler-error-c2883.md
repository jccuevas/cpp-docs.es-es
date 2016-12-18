---
title: "Error del compilador C2883 | Microsoft Docs"
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
  - "C2883"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2883"
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2883
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre': la declaración de función entra en conflicto con 'identificador', utilizado en la declaración using  
  
 Se intentó definir una función más de una vez.  La primera definición se hizo desde un espacio de nombres con una declaración `using`.  La segunda era una definición local.  
  
 El código siguiente genera el error C2883:  
  
```  
// C2883.cpp  
namespace A {  
   void z(int);  
}  
  
int main() {  
   using A::z;  
   void z(int);   // C2883  z is already defined  
}  
```