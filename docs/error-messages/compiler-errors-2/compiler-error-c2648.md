---
title: "Error del compilador C2648 | Microsoft Docs"
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
  - "C2648"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2648"
ms.assetid: ce338337-9154-4f85-bb61-b05fdbfad75d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2648
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : el uso de miembro como parámetro predeterminado requiere un miembro static  
  
 Se utilizó un miembro no estático como parámetro predeterminado.  
  
 El código siguiente genera el error C2648:  
  
```  
// C2648.cpp  
// compile with: /c  
class C {  
public:  
   int i;  
   static int j;  
   void func1( int i = i );  // C2648  i is not static  
   void func2( int i = j );  // OK  
};  
```