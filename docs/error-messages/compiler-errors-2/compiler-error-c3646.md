---
title: "Error del compilador C3646 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3646"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3646"
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3646
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'especificador' : especificador de reemplazo desconocido  
  
 El compilador ha encontrado un símbolo \(token\) en la posición en la que esperaba encontrar un especificador de reemplazo, pero el compilador no ha reconocido el símbolo \(token\).  
  
 Para obtener más información, vea [Especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3646:  
  
```  
// C3646.cpp  
// compile with: /clr /c  
ref class C {  
   void f() unknown;   // C3646  
   // try the following line instead  
   // virtual void f() abstract;  
};  
```