---
title: "Advertencia del compilador (nivel 1) C4804 | Microsoft Docs"
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
  - "C4804"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4804"
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4804
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operación' : uso no seguro del tipo 'bool' en la operación  
  
 Esta advertencia se refiere a cuando se utiliza una variable o valor `bool` de forma inesperada.  Por ejemplo, se genera C4804 si se utilizan operadores como el operador unario negativo \(**\-**\) o el operador de complemento \(`~`\).  El compilador evalúa la expresión.  
  
## Ejemplo  
 El código siguiente genera el error C4804:  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```