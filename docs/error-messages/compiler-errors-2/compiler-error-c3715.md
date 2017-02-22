---
title: "Error del compilador C3715 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3715"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3715"
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3715
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'puntero': debe ser un puntero a 'clase'  
  
 Se especificó un puntero en [\_\_hook](../../cpp/hook.md) o [\_\_unhook](../../cpp/unhook.md) que no señala a una clase válida.  Para resolver este error, asegúrese de que las llamadas a `__hook` y `__unhook` especifican punteros a clases válidas.