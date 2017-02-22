---
title: "Advertencia del compilador (nivel 3) C4161 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4161"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4161"
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 3) C4161
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma pragma\(pop...\): hay más extracciones que inserciones  
  
 Como el código fuente contiene una extracción más que inserciones hay para la pragma ***pragma***, es posible que la pila no tenga el comportamiento esperado. Para evitar la advertencia, asegúrese de que el número de extracciones no supera el número de inserciones.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4161:  
  
```  
// C4161.cpp // compile with: /W3 /LD #pragma pack(push, id) #pragma pack(pop, id) #pragma pack(pop, id)   // C4161, an extra pop #pragma bss_seg(".my_data1") int j; #pragma bss_seg(push, stack1, ".my_data2") int l; #pragma bss_seg(pop, stack1) int m; #pragma bss_seg(pop, stack1)   // C4161  
```