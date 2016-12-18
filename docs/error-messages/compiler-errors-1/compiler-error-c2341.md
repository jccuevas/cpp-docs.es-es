---
title: "Error del compilador C2341 | Microsoft Docs"
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
  - "C2341"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2341"
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2341
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre de sección' : se debe definir el segmento utilizando \#pragma data\_seg, code\_seg o una sección antes de su uso  
  
 Una instrucción [allocate](../../cpp/allocate.md) hace referencia a un segmento aún no definido por pragmas [code\_seg](../../preprocessor/code-seg.md), [data\_seg](../../preprocessor/data-seg.md) o [section](../../preprocessor/section.md).  
  
 El código siguiente genera el error C2341:  
  
```  
// C2341.cpp  
// compile with: /c  
__declspec(allocate(".test"))   // C2341  
int j = 1;  
```  
  
 Posible solución:  
  
```  
// C2341b.cpp  
// compile with: /c  
#pragma data_seg(".test")  
__declspec(allocate(".test"))  
int j = 1;  
```