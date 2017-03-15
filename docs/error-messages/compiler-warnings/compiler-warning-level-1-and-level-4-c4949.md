---
title: "Advertencia del compilador (niveles 1 y 4) C4949 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4949"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4949"
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (niveles 1 y 4) C4949
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las pragmas 'managed' y 'unmanaged' solamente son significativas cuando se compilan con '\/clr\[:opción\]'  
  
 El compilador omite las directivas pragma [managed](../../preprocessor/managed-unmanaged.md) y unmanaged si el código fuente no se compila con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  Esta advertencia sólo tiene valor informativo.  
  
 El código siguiente genera el error C4949:  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 Cuando **\#pragma unmanaged** se utiliza sin **\/clr**, C4949 es una advertencia de nivel 4.  
  
 El código siguiente genera el error C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```