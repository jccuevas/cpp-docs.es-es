---
title: "Error del compilador C2888 | Microsoft Docs"
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
  - "C2888"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2888"
ms.assetid: 244f593e-ff25-4dad-b31f-84dafa3bc84a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2888
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': el símbolo no se puede definir en el espacio de nombres 'espacio de nombres'  
  
 Un símbolo perteneciente al espacio de nombres A se debe definir en un espacio de nombres que englobe a A.  
  
 El código siguiente genera el error C2888:  
  
```  
// C2888.cpp  
// compile with: /c  
namespace M {  
   namespace N {  
      void f1();  
      void f2();  
   }  
  
   void N::f1() {}   // OK: namspace M encloses N  
}  
  
namespace O {  
   void M::N::f2() {}   // C2888 namespace O does not enclose M  
}  
```