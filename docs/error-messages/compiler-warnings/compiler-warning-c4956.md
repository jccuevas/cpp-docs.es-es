---
title: "Advertencia del compilador C4956 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4956"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4956"
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4956
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': este tipo no se puede comprobar.  
  
 Esta advertencia se genera cuando se especifica [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) y el código contiene un tipo que no es comprobable.  
  
 Para obtener más información, consulta [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [\/wd](../../build/reference/compiler-option-warning-level.md).  
  
 El ejemplo siguiente genera la advertencia C4956:  
  
```  
// C4956.cpp // compile with: /clr:safe int* p;   // C4956  
```