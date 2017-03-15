---
title: "Error del compilador C2524 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2524"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2524"
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2524
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'destructor' : un destructor\/finalizador debe tener una lista de parámetros 'void'  
  
 El destructor o finalizador tiene una lista de parámetros que no es [void](../../cpp/void-cpp.md).  No se permiten otros tipos de parámetros.  
  
## Ejemplo  
 El código siguiente reproduce el error C2524.  
  
```  
// C2524.cpp  
// compile with: /c  
class A {  
   A() {}  
   ~A(int i) {}    // C2524  
   // try the following line instead  
   // ~A() {}  
};  
```  
  
## Ejemplo  
 El código siguiente reproduce el error C2524.  
  
```  
// C2524_b.cpp  
// compile with: /clr /c  
ref struct I1 {  
protected:  
   !I1(int i);   // C2524  
   // try the following line instead  
   // !I1();  
};  
```