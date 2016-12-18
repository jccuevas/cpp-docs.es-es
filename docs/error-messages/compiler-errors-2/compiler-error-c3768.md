---
title: "Error del compilador C3768 | Microsoft Docs"
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
  - "C3768"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3768"
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3768
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede tomar la dirección de una función vararg virtual en código administrado puro  
  
 Al compilar con `/clr:pure`, no se puede tomar la dirección de una función `vararg` virtual.  
  
 El código siguiente genera el error C3768:  
  
```  
// C3768.cpp  
// compile with: /clr:pure  
struct A  
{  
   virtual void f(...);  
};  
  
int main()  
{  
   &(A::f);   // C3768  
}  
```