---
title: "Error del compilador C2087 | Microsoft Docs"
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
  - "C2087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2087"
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : falta el subíndice  
  
 A la definición de una matriz con varios subíndices le falta un valor de subíndice para una dimensión cuyo valor es superior a uno.  
  
 El código siguiente genera el error C2087:  
  
```  
// C2087.cpp  
int main() {  
   char a[10][];   // C2087  
}  
```  
  
 Posible solución:  
  
```  
// C2087b.cpp  
int main() {  
   char b[4][5];  
}  
```