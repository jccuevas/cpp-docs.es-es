---
title: "Error en tiempo de ejecuci&#243;n de C R6009 | Microsoft Docs"
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
  - "R6009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6009"
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error en tiempo de ejecuci&#243;n de C R6009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

espacio insuficiente para entornos  
  
 Hay memoria suficiente para cargar el programa pero es insuficiente para crear la matriz **envp**.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Aumentar la cantidad de memoria disponible para el programa.  
  
2.  Reducir el número y el tamaño de los argumentos de línea de comandos.  
  
3.  Reducir el tamaño del entorno quitando variables innecesarias.