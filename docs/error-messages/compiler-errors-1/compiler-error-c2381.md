---
title: "Error del compilador C2381 | Microsoft Docs"
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
  - "C2381"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2381"
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2381
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : nueva definición; \_\_declspec\(noreturn\) es diferente  
  
 Se declaró una función y después se definió, pero la definición utiliza el modificador [noreturn](../../cpp/noreturn.md) `__declspec`.  El uso de `noreturn` constituye una nueva definición de la función; la declaración y la definición deben coincidir en el uso de `noreturn`.  
  
 El código siguiente genera el error C2381:  
  
```  
// C2381.cpp  
// compile with: /c  
void f1();  
void __declspec(noreturn) f1() {}   // C2381  
void __declspec(noreturn) f2() {}   // OK  
```