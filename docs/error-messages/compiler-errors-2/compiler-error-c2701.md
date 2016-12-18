---
title: "Error del compilador C2701 | Microsoft Docs"
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
  - "C2701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2701"
ms.assetid: 31cf2ab7-ced9-4f75-aa51-e169e20407fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2701
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : plantilla de función no puede ser una función friend de una clase local  
  
 Una clase local no puede tener una función de plantilla como función friend.  
  
 El código siguiente genera el error C2701:  
  
```  
// C2701.cpp  
// compile with: /c  
template<typename T>   // OK  
void f1(const T &);  
  
void MyFunction() {  
   class MyClass {  
      template<typename T> friend void f2(const T &);   // C2701  
   };  
}  
```