---
title: "Error del compilador C2307 | Microsoft Docs"
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
  - "C2307"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2307"
ms.assetid: ce6c8033-a673-4679-9883-bedec36ae385
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2307
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

pragma 'pragma' debe estar fuera de la función si la compilación incremental está habilitada  
  
 Se debe colocar la pragma `data_seg` entre funciones cuando se está usando la compilación incremental.