---
title: "Error del compilador C2137 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2137"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2137"
ms.assetid: 984687ee-7766-4f6b-ae15-0c9a010e2366
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2137
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

constante de caracteres vacía  
  
 La constante de carácter vacío \(' '\) no está permitida.  
  
 El ejemplo siguiente genera la advertencia C2137:  
  
```  
// C2137.cpp int main() { char c = '';   // C2137 char d = ' ';   // OK }  
```