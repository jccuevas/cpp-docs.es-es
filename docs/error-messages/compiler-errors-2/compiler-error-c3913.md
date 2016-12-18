---
title: "Error del compilador C3913 | Microsoft Docs"
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
  - "C3913"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3913"
ms.assetid: a678bfce-9524-470d-9f23-7d08ecb972c8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3913
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una propiedad predeterminada debe estar indizada  
  
 Se ha definido incorrectamente una propiedad predeterminada.  
  
 Para obtener más información, vea [propiedad](../../windows/property-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3913:  
  
```  
// C3913.cpp  
// compile with: /clr /c  
ref struct X {  
   property int default {   // C3913  
   // try the following line instead  
   // property int default[int] {  
      int get(int) { return 0; }  
      void set(int, int) {}  
   }  
};  
```