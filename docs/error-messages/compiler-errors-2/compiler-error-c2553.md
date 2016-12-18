---
title: "Error del compilador C2553 | Microsoft Docs"
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
  - "C2553"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2553"
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2553
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función\_base': el reemplazo del tipo de valor devuelto de la función virtual difiere de 'función\_de\_reemplazo'  
  
 Una función de una clase derivada intentó reemplazar una función virtual de una clase base, pero la función de la clase derivada no tenía el mismo tipo de valor devuelto que la función de la clase base.  La firma de una función de reemplazo debe coincidir con la firma de la función que se va a reemplazar.  
  
 El código siguiente genera el error C2553:  
  
```  
// C2553.cpp  
// compile with: /clr /c  
ref struct C {  
   virtual void f();  
};  
  
ref struct D : C {  
   virtual int f() override ;   // C2553   
  
   // try the following line instead  
   // virtual void f() override;  
};  
```