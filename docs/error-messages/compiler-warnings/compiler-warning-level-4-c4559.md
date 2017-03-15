---
title: "Advertencia del compilador (nivel 4) C4559 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4559"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4559"
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 4) C4559
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : redefinición; la función gains \_\_declspec\(modificador\)  
  
 Se volvió a definir o a declarar una función y la segunda definición o declaración agregó un modificador \_\_**declspec**\(***modificador***\).  Esta advertencia sólo tiene valor informativo.  Para corregir esta advertencia, elimine una de las definiciones.  
  
 El código siguiente genera el error C4559:  
  
```  
// C4559.cpp  
// compile with: /W4 /LD  
void f();  
__declspec(noalias) void f();   // C4559  
```