---
title: "Error del compilador C2441 | Microsoft Docs"
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
  - "C2441"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2441"
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2441
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : un símbolo declarado con \_\_declspec\(proceso\) debe ser constante en el modo \/clr:pure  
  
 De manera predeterminada, las variables son por dominio de aplicación con **\/clr:pure**.  Una variable marcada `__declspec(process)` con **\/clr:pure** dará errores si se modifica en un dominio de aplicación y se lee en otro.  
  
 Por consiguiente, el compilador obliga a que las variables de proceso sean `const` con **\/clr:pure**, y las hace de sólo lectura en todos los dominios de aplicación.  
  
 Para obtener más información, vea [proceso](../../cpp/process.md) y [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2441.  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```