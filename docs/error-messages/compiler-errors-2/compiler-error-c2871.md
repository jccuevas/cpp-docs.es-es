---
title: "Error del compilador C2871 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2871"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2871"
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2871
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre' : no existe ningún espacio de nombres con este nombre  
  
 Este error se produce al pasar un identificador que no es un espacio de nombres a una directiva [using](../Topic/using%20Directive%20\(C%23%20Reference\).md).  
  
 El código siguiente genera el error C2871:  
  
```  
// C2871.cpp  
// compile with: /c  
using namespace d;   // C2871 d is not a namespace  
using namespace System;   // OK  
```