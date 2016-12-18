---
title: "Error del compilador C3383 | Microsoft Docs"
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
  - "C3383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3383"
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator new' no se admite con \/clr:safe  
  
 El archivo de salida de una compilación **\/clr:safe** es un archivo de seguridad de tipos comprobable y no se admiten punteros.  
  
 Para obtener más información, vea  
  
-   [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problemas comunes de migración a 64 bits en Visual C\+\+](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3383.  
  
```  
// C3383.cpp // compile with: /clr:safe int main() { char* pCharArray = new char[256];  // C3383 }  
```