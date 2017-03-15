---
title: "Advertencia del compilador (nivel 4) C4668 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4668"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4668"
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 4) C4668
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' no está definido como macro de preprocesador y se reemplaza por '0' para 'directivas'  
  
 Se utilizó un símbolo no definido con una directiva de preprocesador.  El símbolo se evaluará como false.  Un símbolo se puede definir mediante la [directiva \#define](../../preprocessor/hash-define-directive-c-cpp.md) o la opción [\/D](../../build/reference/d-preprocessor-definitions.md) del compilador.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Ejemplo  
 El código siguiente genera el error C4668:  
  
```  
// C4668.cpp  
// compile with: /W4  
#include <stdio.h>  
  
#pragma warning (default : 4668)   // turn warning on  
  
int main()   
{  
    #if q   // C4668, q is not defined  
        printf_s("defined");  
    #else  
        printf_s("undefined");  
    #endif  
}  
```