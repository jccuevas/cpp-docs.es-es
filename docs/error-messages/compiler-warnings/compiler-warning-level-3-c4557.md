---
title: "Advertencia del compilador (nivel 3) C4557 | Microsoft Docs"
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
  - "C4557"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4557"
ms.assetid: 7d9db716-03b2-4ee5-9b09-ba8aa5aa7e4c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4557
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\_\_assume' contiene el efecto 'efecto'  
  
 El valor pasado a una instrucción [\_\_assume](../../intrinsics/assume.md) se modificó.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El código siguiente genera el error C4557:  
  
```  
// C4557.cpp  
// compile with: /W3  
#pragma warning(default : 4557)  
int main()  
{  
   int i;  
   __assume(i++);   // C4557  
}  
```