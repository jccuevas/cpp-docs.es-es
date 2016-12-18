---
title: "Advertencia del compilador (nivel 3) C4792 | Microsoft Docs"
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
  - "C4792"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4792"
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4792
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

función 'function' declarada usando sysimport a la que se hace referencia desde código nativo; biblioteca de importación necesaria para vincular  
  
 Se llamó a una función nativa importada en el programa con DllImport desde una función no administrada. Por lo tanto, debe vincular a la biblioteca de importación del archivo DLL.  
  
 Esta advertencia no se puede resolver  en el código ni cambiando la forma de realizar la compilación. Para deshabilitar esta advertencia, use la pragma [warning](../../preprocessor/warning.md).  
  
 El ejemplo siguiente genera la advertencia C4792:  
  
```  
// C4792.cpp // compile with: /clr /W3 // C4792 expected using namespace System::Runtime::InteropServices; [DllImport("msvcrt")] extern "C" int __cdecl puts(const char *); int main() {} // Uncomment the following line to resolve. // #pragma warning(disable : 4792) #pragma unmanaged void func(void){ puts("test"); }  
```