---
title: "Error en tiempo de ejecuci&#243;n de C R6032 | Microsoft Docs"
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
  - "R6032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6032"
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error en tiempo de ejecuci&#243;n de C R6032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No hay espacio suficiente para la información de configuración regional  
  
 El motor en tiempo de ejecución conserva información sobre la configuración regional en cada subproceso para poder procesar las llamadas a las funciones que dependen de la configuración regional.  Si se produce un error en la asignación de memoria de esta información, el motor en tiempo de ejecución no puede continuar porque muchas de sus funciones básicas dependen de esta información.