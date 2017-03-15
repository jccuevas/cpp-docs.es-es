---
title: "Error del compilador C3611 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3611"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3611"
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3611
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': una función sealed no puede tener un especificador puro  
  
 Se ha declarado incorrectamente una función sealed.  Para obtener más información, vea [sellado](../../windows/sealed-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3611.  
  
```  
// C3611.cpp  
// compile with: /clr /c  
  
ref struct V {  
   virtual void Test() sealed = 0;   // C3611  
   virtual void Test2() sealed;   // OK  
   virtual void Test3() = 0;   // OK  
};  
```