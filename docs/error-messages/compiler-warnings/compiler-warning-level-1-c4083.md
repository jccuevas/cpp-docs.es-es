---
title: "Advertencia del compilador (nivel 1) C4083 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4083"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4083"
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4083
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se espera 'símbolo \(token\)'; se encontró el identificador 'identificador'  
  
 Hay un identificador en un lugar incorrecto de una instrucción **\#pragma**.  
  
## Ejemplo  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 Compruebe la sintaxis de las directivas [\#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).