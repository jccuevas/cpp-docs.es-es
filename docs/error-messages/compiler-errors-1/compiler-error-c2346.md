---
title: "Error del compilador C2346 | Microsoft Docs"
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
  - "C2346"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2346"
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2346
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' no se puede compilar como nativa: razón  
  
 El compilador no ha podido compilar una función en MSIL.  
  
 Para obtener más información, vea [managed, unmanaged](../../preprocessor/managed-unmanaged.md) y [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### Para corregir este error  
  
1.  Quite el código de la función que no puede compilarse en MSIL.  
  
2.  No compile el módulo con **\/clr** o bien marque la función como no administrada con la directiva pragma no administrada.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2346.  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```