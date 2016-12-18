---
title: "Error del compilador C2100 | Microsoft Docs"
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
  - "C2100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2100"
ms.assetid: 9ed5ea11-9d55-4ddf-8b1a-162c74f3c390
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

direccionamiento indirecto no válido  
  
 El operador de direccionamiento indirecto \( `*` \) se ha aplicado a un valor que no es un puntero.  
  
 El código siguiente genera el error C2100:  
  
```  
// C2100.cpp  
int main() {  
   int r = 0, *s = 0;  
   s = &r;  
   *r = 200;   // C2100  
   *s = 200;   // OK  
}  
```