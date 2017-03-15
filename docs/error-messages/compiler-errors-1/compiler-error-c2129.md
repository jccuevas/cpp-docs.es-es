---
title: "Error del compilador C2129 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2129"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2129"
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2129
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

función static 'función' declarada pero no definida  
  
 Se ha realizado una referencia adelantada a una función `static` sin definir.  
  
 Las funciones `static` deben estar definidas en el ámbito del archivo.  Si se definen en otro archivo, deberán declararse como `extern`.