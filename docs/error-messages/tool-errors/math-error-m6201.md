---
title: "Error matem&#225;tico M6201 | Microsoft Docs"
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
  - "M6201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6201"
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error matem&#225;tico M6201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : error \_DOMAIN  
  
 Un argumento para la función dada no pertenecía al dominio de valores de entrada válidos para esa función.  
  
## Ejemplo  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 Este error invoca la función `_matherr` con el nombre de la función, sus argumentos y el tipo de error.  Se puede volver a escribir la función `_matherr` para personalizar el control de algunos errores matemáticos de punto flotante en tiempo de ejecución.