---
title: "Error del compilador C2117 | Microsoft Docs"
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
  - "C2117"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2117"
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2117
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : desbordamiento de límites de matriz  
  
 Una matriz tiene demasiados inicializadores:  
  
-   Los elementos y los inicializadores de la matriz no coinciden en tamaño y cantidad.  
  
-   El terminador nulo no tiene espacio en una cadena.  
  
 El código siguiente genera el error C2117:  
  
```  
// C2117.cpp  
int main() {  
   char abc[4] = "abcd";   // C2117  
   char def[4] = "abd";   // OK  
}  
```