---
title: "Advertencia del compilador (nivel 1) C4548 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4548"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4548"
ms.assetid: 2cee817e-e463-4d90-bbd2-de120d48c101
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4548
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios  
  
 El compilador ha detectado una expresión de coma mal formada.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El código siguiente genera el error C4548:  
  
```  
// C4548.cpp  
// compile with: /W1  
#pragma warning (default : 4548)  
int main()  
{  
   int i = 0, k = 0;  
  
   if ( i, k )   // C4548  
   // try the following line instead  
   // if ( i = 0, k )  
      i++;  
}  
```