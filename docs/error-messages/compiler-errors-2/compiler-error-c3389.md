---
title: "Error del compilador C3389 | Microsoft Docs"
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
  - "C3389"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3389"
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3389
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_declspec\(palabra clave\) no se puede utilizar con \/clr:pure o \/clr:safe  
  
 Un modificador [\_\_declspec](../../cpp/declspec.md) utilizado implica un estado por proceso.  [\/clr:pure](../../build/reference/clr-common-language-runtime-compilation.md) implica un estado por [appdomain](../../cpp/appdomain.md).  Por tanto, no se permite declarar una variable con el modificador **\_\_declspec** `keyword` y compilar con **\/clr:pure**.  
  
 El código siguiente genera el error C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```