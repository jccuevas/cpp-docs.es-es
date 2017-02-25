---
title: "R6008 de Error de tiempo de ejecuci&#243;n de C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6008"
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error en tiempo de ejecuci&#243;n de C R6008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

espacio insuficiente para argumentos  
  
 Hay memoria suficiente para cargar el programa pero es insuficiente para crear la matriz **argv**.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Aumentar la cantidad de memoria disponible para el programa.  
  
2.  Reducir el número y el tamaño de los argumentos de línea de comandos.  
  
3.  Reducir el tamaño del entorno quitando variables innecesarias.