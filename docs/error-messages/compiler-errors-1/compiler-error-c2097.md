---
title: "Error del compilador C2097 | Microsoft Docs"
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
  - "C2097"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2097"
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2097
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

inicialización no válida  
  
### Posibles causas del error:  
  
1.  Se ha inicializado una variable con un valor que no es una constante.  
  
2.  Se ha inicializado una dirección corta con una dirección larga.  
  
3.  Se ha inicializado una estructura, una unión o una matriz local con una expresión que no es constante al compilar con **\/Za**.  
  
4.  Se ha inicializado una expresión que contiene un operador coma.  
  
5.  Se ha inicializado una expresión que ni es constante ni simbólica.