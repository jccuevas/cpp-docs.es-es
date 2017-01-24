---
title: "Advertencia del compilador (nivel 2) C4307 | Microsoft Docs"
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
  - "C4307"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4307"
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4307
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : desbordamiento de constante integral  
  
 El operador se utiliza en una expresión que da como resultado una constante entera que desborda el espacio asignado.  Puede que sea necesario usar un tipo mayor para la constante.  Un tipo **signed int** contiene un valor más pequeño que otro `unsigned int`, porque el tipo **signed int** utiliza un bit para representar el signo.  
  
 El código siguiente genera el error C4307:  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```