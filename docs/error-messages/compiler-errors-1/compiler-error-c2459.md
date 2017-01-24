---
title: "Error del compilador C2459 | Microsoft Docs"
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
  - "C2459"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2459"
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2459
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : se está definiendo; no se puede agregar como miembro anónimo  
  
 Una clase, estructura o unión ha sido definida de nuevo en su propio ámbito por un miembro de una unión anónima.  
  
 El código siguiente genera el error C2459:  
  
```  
// C2459.cpp  
// compile with: /c  
class C {  
   union { int C; };   // C2459  
   union { int D; };  
};  
```