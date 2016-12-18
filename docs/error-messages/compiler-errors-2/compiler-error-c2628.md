---
title: "Error del compilador C2628 | Microsoft Docs"
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
  - "C2628"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2628"
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2628
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo1' seguido de 'tipo2' no es válido \(¿ha olvidado ';'?\)  
  
 Puede que falte un punto y coma.  
  
 El código siguiente genera el error C2628:  
  
```  
// C2628.cpp  
class CMyClass {}  
int main(){}   // C2628 error  
```  
  
 Posible solución:  
  
```  
// C2628b.cpp  
class CMyClass {};  
int main(){}  
```