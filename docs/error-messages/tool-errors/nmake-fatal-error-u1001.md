---
title: "Error grave de NMAKE U1001 | Microsoft Docs"
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
  - "U1001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1001"
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error grave de NMAKE U1001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : carácter 'carácter' no válido en macro  
  
 El carácter dado aparece en una macro pero no es una letra, un número o un carácter de subrayado.  
  
 Este error puede aparecer si falta un signo de dos puntos en una expansión de macro:  
  
```  
syntax error : illegal character '=' in macro  
```