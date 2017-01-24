---
title: "Compiler Warning (level 1) C4669 | Microsoft Docs"
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
  - "C4669"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4669"
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Warning (level 1) C4669
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'cast': conversión no segura: 'class' es un objeto de tipo administrado o WinRT  
  
 Una conversión contiene un tipo administrado o de Windows en tiempo de ejecución.  El compilador completa la conversión con una copia bit a bit de un puntero a otro, pero no realiza ninguna otra comprobación.  Para resolver esta advertencia, no convierta las clases que contienen miembros administrados o tipos de Windows en tiempo de ejecución.  
  
 El ejemplo siguiente genera el error C4669 y muestra cómo corregirlo:  
  
```  
// C4669.cpp  
// compile with: /clr /W1  
ref struct A {  
   int i;  
   Object ^ pObj;   // remove the managed member to fix the warning  
};  
  
ref struct B {  
   int j;  
};  
  
int main() {  
   A ^ a = gcnew A;  
   B ^ b = reinterpret_cast<B ^>(a);   // C4669  
}  
```