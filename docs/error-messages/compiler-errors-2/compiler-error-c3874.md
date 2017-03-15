---
title: "Error del compilador C3874 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3874"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3874"
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3874
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el tipo de valor devuelto de 'función' debería ser 'int' en lugar de 'tipo'  
  
 Una función no tiene el tipo de valor devuelto que espera el compilador.  
  
 El código siguiente genera el error C3874:  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```