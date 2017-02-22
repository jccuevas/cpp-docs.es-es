---
title: "Error del compilador C2897 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2897"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2897"
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2897
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

un destructor\/finalizador no puede ser una plantilla de función  
  
 Los destructores o finalizadores no se pueden sobrecargar, de manera que no se permite declarar un destructor como una plantilla \(lo cual definiría una serie de destructores\).  
  
 El código siguiente genera el error C2897:  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2897.  
  
```  
// C2897.cpp  
// compile with: /c  
class X {  
public:  
   template<typename T> ~X() {}   // C2897  
};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2897.  
  
```  
// C2897_b.cpp  
// compile with: /c /clr  
ref struct R2 {  
protected:  
   template<typename T> !R2(){}   // C2897 error  
};  
```