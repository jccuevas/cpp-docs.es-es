---
title: "Error del compilador C2153 | Microsoft Docs"
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
  - "C2153"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2153"
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2153
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las constantes hexadecimales deben tener al menos un dígito hexadecimal  
  
 Las constantes hexadecimales 0x, 0X y \\x no son válidas.  Debe existir al menos un dígito hexadecimal después de x o X.  
  
 El código siguiente genera el error C2153:  
  
```  
// C2153.cpp  
int main() {  
   int a= 0x;    // C2153  
   int b= 0xA;   // OK  
}  
```