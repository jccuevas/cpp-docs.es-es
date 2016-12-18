---
title: "Advertencia del compilador (nivel 2) C4302 | Microsoft Docs"
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
  - "C4302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4302"
ms.assetid: f5e1c939-e134-4cca-ba1e-9b15a81549ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4302
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversión' : truncamiento de 'tipo 1' a 'tipo 2'  
  
 El compilador detectó una conversión de un tipo más grande a otro más pequeño.  Puede que se haya producido pérdida de información.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El código siguiente genera el error C4302:  
  
```  
// C4302.cpp  
// compile with: /W2  
#pragma warning(default : 4302)  
int main() {  
   int i;  
   char c = (char) &i;     // C4302  
   short s = (short) &i;   // C4302  
}  
```