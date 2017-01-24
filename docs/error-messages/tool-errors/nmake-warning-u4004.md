---
title: "Advertencia de NMAKE U4004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U4004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4004"
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de NMAKE U4004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

demasiadas reglas para el destino 'nombrededestino'  
  
 Se ha especificado más de un bloque de descripciones para el destino dado usando signos de dos puntos \(**:**\) como separadores.  NMAKE ha ejecutado los comandos en el primer bloque de descripciones y ha omitido los bloques posteriores.  
  
 Para especificar el mismo destino en varias dependencias se ha de utilizar el signo doble de dos puntos \(`::`\) como separador en cada línea de dependencia.