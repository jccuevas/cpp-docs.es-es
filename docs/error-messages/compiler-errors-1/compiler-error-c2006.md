---
title: "Error del compilador C2006 | Microsoft Docs"
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
  - "C2006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2006"
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'directiva' se esperaba un nombre de archivo, se ha encontrado 'token'  
  
 Las directivas como [\#include](../../preprocessor/hash-include-directive-c-cpp.md) o [\#import](../../preprocessor/hash-import-directive-cpp.md) requieren un nombre de archivo.  Para corregir el error, asegúrese de que *token* es un nombre de archivo válido.  Además, el nombre de archivo deberá ir entre comillas dobles o corchetes angulares.  
  
 El código siguiente genera el error C2006:  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 Posible solución:  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```