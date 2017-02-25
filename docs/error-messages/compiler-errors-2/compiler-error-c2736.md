---
title: "Error del compilador C2736 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2736"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2736"
ms.assetid: 95a6bc28-c0cb-49dc-87e6-e993dbbba881
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2736
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permite la palabra clave 'palabra clave' en la conversión  
  
 La palabra clave no es válida en una conversión.  
  
 El código siguiente genera el error C2736:  
  
```  
// C2736.cpp  
int main() {  
   return (virtual) 0;   // C2736  
   // try the following line instead  
   // return 0;  
}  
```