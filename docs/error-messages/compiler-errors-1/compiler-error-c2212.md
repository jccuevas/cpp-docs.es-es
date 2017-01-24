---
title: "Error del compilador C2212 | Microsoft Docs"
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
  - "C2212"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2212"
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2212
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : \_\_based no está disponible para punteros a funciones  
  
 Los punteros a funciones no pueden declararse `__based`.  Si necesita datos basados en el código, utilice la palabra clave `__declspec` o la directiva pragma `data_seg`.