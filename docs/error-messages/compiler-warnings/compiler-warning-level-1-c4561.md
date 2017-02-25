---
title: "Advertencia del compilador (nivel 1) C4561 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4561"
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Advertencia del compilador (nivel 1) C4561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\_\_fastcall' es incompatible con la opción '\/clr': se va a realizar la conversión a '\_\_stdcall'  
  
 La convención de llamada de funciones [\_\_fastcall](../../cpp/fastcall.md) no puede utilizarse con la opción del compilador [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  El compilador omite las llamadas a `__fastcall`.  Para corregir esta advertencia, quite las llamadas a **\_\_fastcall** o compile sin **\/clr**.  
  
 El código siguiente genera el error C4561:  
  
```  
// C4561.cpp  
// compile with: /clr /W1 /c  
// processor: x86  
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve  
```