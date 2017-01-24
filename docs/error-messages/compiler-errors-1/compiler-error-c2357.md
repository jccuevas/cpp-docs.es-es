---
title: "Error del compilador C2357 | Microsoft Docs"
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
  - "C2357"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2357"
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2357
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : debe ser una función de tipo 'tipo'  
  
 El código declara una versión de la función `atexit` que no coincide con la versión declarada internamente por el compilador.  Declare `atexit` de la siguiente forma:  
  
```  
int __cdecl atexit(void (__cdecl *)());  
```  
  
 Para obtener más información, vea [init\_seg](../../preprocessor/init-seg.md).  
  
 El código siguiente genera el error C2357:  
  
```  
// C2357.cpp  
// compile with: /c  
// C2357 expected  
#pragma warning(disable : 4075)  
// Uncomment the following line to resolve.  
// int __cdecl myexit(void (__cdecl *)());  
#pragma init_seg(".mine$m",myexit)  
```