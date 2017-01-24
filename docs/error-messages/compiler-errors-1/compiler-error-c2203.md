---
title: "Error del compilador C2203 | Microsoft Docs"
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
  - "C2203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2203"
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2203
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el operador delete no puede especificar límites para una matriz  
  
 Con la opción **\/Za** \(ANSI\), el operador `delete` puede eliminar una matriz completa pero no partes o miembros específicos de la misma.  
  
 El código siguiente genera el error C2203:  
  
```  
// C2203.cpp  
// compile with: /Za  
int main() {  
   int *ar = new int[10];  
   delete [4] ar;   // C2203  
   // try the following line instead  
   // delete [] ar;  
}  
```