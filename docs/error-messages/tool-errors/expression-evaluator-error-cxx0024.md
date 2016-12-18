---
title: "Error del evaluador de expresiones CXX0024 | Microsoft Docs"
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
  - "CXX0024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0024"
  - "CXX0024"
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0024
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la operación necesita un valor L  
  
 Se ha especificado una expresión que no se evalúa para un valor L para una operación que requiere un valor L.  
  
 Un valor L \(denominado así porque aparece en el lado izquierdo de una declaración de asignación\) es una expresión que hace referencia a una ubicación de memoria.  
  
 Por ejemplo, `buffer[count]` es un valor L válido porque señala a una ubicación de memoria específica.  La comparación lógica `zed != 0` no es un valor L válido porque se evalúa como TRUE o FALSE, no como una dirección de memoria.  
  
 Este error es idéntico a CAN00024.