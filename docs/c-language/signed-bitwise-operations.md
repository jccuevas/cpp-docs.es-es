---
title: "Operaciones bit a bit con signo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operaciones bit a bit"
  - "operaciones bit a bit con signo"
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operaciones bit a bit con signo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.3** Resultados de operaciones bit a bit en enteros con signo  
  
 Las operaciones bit a bit en enteros con signo funcionan igual que las operaciones bit a bit en enteros sin signo.  Por ejemplo, `–16 & 99` puede expresarse en formato binario como  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 El resultado de AND bit a bit es 96.  
  
## Vea también  
 [Enteros](../c-language/integers.md)