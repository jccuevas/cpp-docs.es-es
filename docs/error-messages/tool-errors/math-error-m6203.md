---
title: "Error matem&#225;tico M6203 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6203"
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error matem&#225;tico M6203
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : error \_OVERFLOW  
  
 El resultado de la función dada es demasiado largo para representarse.  
  
 Este error invoca la función `_matherr` con el nombre de la función, sus argumentos y el tipo de error.  Se puede volver a escribir la función `_matherr` para personalizar el control de algunos errores matemáticos de punto flotante en tiempo de ejecución.