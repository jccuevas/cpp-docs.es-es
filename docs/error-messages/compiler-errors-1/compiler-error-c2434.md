---
title: "Error del compilador C2434 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2434"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2434"
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C2434
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' : un símbolo declarado con \_\_declspec\(proceso\) no se puede inicializar dinámicamente en el modo \/clr:pure  
  
 No es posible de inicializar dinámicamente una variable por proceso con **\/clr:pure**.  Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) y [proceso](../../cpp/process.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2434.  
  
```  
// C2434.cpp  
// compile with: /clr:pure /c  
int f() { return 0; }  
__declspec(process) int i = f();   // C2434  
__declspec(process) int i2 = 0;   // OK  
```