---
title: "Error matem&#225;tico M6108 | Microsoft Docs"
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
  - "M6108"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6108"
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error matem&#225;tico M6108
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

raíz cuadrada  
  
 El operando en una operación de raíz cuadrada es negativo.  
  
 El programa termina con el código de salida 136.  
  
> [!NOTE]
>  La función `sqrt` de la biblioteca en tiempo de ejecución de C y la función intrínseca **SQRT** de FORTRAN no generan este error.  La función `sqrt` de C comprueba el argumento antes de realizar la operación y devuelve un valor de error si el operando es negativo.  La función **SQRT** de FORTRAN genera el error DOMAIN [M6201](../../error-messages/tool-errors/math-error-m6201.md) en lugar de este error.