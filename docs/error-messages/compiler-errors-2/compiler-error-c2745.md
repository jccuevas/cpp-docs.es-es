---
title: "Error del compilador C2745 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2745"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2745"
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2745
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'token' : este símbolo no se puede convertir en identificador  
  
 Los identificadores deben estar compuestos de caracteres válidos.  
  
 El código siguiente genera el error C2745:  
  
```  
// C2745.cpp  
// compile with: /clr  
int main() {  
   int __identifier([));   // C2745  
}  
```