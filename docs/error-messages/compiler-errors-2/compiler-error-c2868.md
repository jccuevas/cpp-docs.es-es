---
title: "Error del compilador C2868 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2868"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2868"
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2868
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : sintaxis no válida para la declaración using; se esperaba un nombre completo  
  
 Una [declaración using](../../cpp/using-declaration.md) requiere un [nombre completo](http://msdn.microsoft.com/es-es/3fefb16d-8120-4627-8b3f-3d90fbdcd1df).  
  
 El código siguiente genera el error C2868:  
  
```  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```