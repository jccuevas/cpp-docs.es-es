---
title: "Error del compilador C2170 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2170"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2170"
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2170
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : no declarado como función, no puede ser intrínseco  
  
### Posibles causas del error:  
  
1.  La pragma `intrinsic` se está utilizando para un elemento que no es una función.  
  
2.  La pragma `intrinsic` se está utilizando para una función sin forma intrínseca.