---
title: "Advertencia del compilador (nivel 1) C4369 | Microsoft Docs"
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
  - "C4369"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4369"
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4369
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'enumerador' : el valor del enumerador 'valor' no se puede representar como 'tipo', el valor es 'new\_value'  
  
 Un enumerador se calculó para ser mayor que el valor máximo para el tipo subyacente especificado.  Esto produjo un desbordamiento y el compilador ajustó el valor del enumerador al valor más bajo posible para el tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4369.  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```