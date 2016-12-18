---
title: "Marca de direcci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.flags"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "marca de dirección"
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Marca de direcci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El indicador de la dirección es una específica del indicador de CPU a los procesadores Intel 80x86.  Se aplica a todas las instrucciones de ensamblado que utilizan el prefijo de representante \(repetición\), como MOVS, MOVSD, MOVSW, y otros.  Se aumentan las direcciones proporcionaban instrucciones aplicables si desactiva el indicador de dirección.  
  
 Las rutinas de c se supone que el indicador de la dirección está desactivada.  Si usa otras funciones con las funciones en tiempo de ejecución de C, debe asegurarse de que las otras funciones salgan de indicador de la dirección único o restaurar su condición original.  Esperando que el indicador de la dirección está claro entrada hace el código en tiempo de ejecución más rápida y eficaz.  
  
 Las funciones de la biblioteca en tiempo de ejecución de C, como la cadena\- manipulación y rutinas de la búfer\- manipulación, esperan que el indicador de dirección esté claro.  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)