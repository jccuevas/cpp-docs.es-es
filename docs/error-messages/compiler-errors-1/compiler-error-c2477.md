---
title: "Error del compilador C2477 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2477"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2477"
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2477
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro': no se puede inicializar el miembro de datos estático mediante una clase derivada  
  
 Se ha inicializado incorrectamente un miembro de datos estático de una clase de plantilla.  Esto representa un cambio importante respecto a las versiones del compilador de Visual C\+\+ anteriores a Visual Studio .NET 2003, para lograr la compatibilidad con el estándar ISO C\+\+.  
  
 El código siguiente genera el error C2477:  
  
```  
// C2477.cpp  
// compile with: /Za /c  
template <class T>  
struct S {  
   static int n;  
};  
  
struct X {};  
struct A: S<X> {};  
  
int A::n = 0;   // C2477  
  
template<>  
int S<X>::n = 0;  
```