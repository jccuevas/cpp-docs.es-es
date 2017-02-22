---
title: "Error del compilador C3519 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3519"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3519"
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3519
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parámetro no válido': parámetro no válido para el atributo embedded\_idl  
  
 Se pasó un parámetro al atributo `embedded_idl` de [\#import](../../preprocessor/hash-import-directive-cpp.md), pero el compilador no lo reconoció.  
  
 Los únicos parámetros que se permiten para `embedded_idl` son `emitidl` y `no_emitidl`.  
  
 El código siguiente genera el error C3519:  
  
```  
// C3519.cpp  
// compile with: /LD  
[module(name="MyLib2")];  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")     
// C3519  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")     
// OK  
```