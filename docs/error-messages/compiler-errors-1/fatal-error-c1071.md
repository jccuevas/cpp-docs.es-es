---
title: "Error irrecuperable C1071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1071"
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error irrecuperable C1071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se esperaba el final de archivo encontrado en el comentario  
  
 El compilador ha alcanzado el final del archivo mientras examinaba un comentario.  
  
### Posibles causas del error:  
  
1.  Falta el terminador de comentario \(\*\/\).  
  
2.  Falta un carácter de nueva línea después de un comentario en la última línea de un archivo de código fuente.  
  
 El código siguiente genera el error C1071:  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```