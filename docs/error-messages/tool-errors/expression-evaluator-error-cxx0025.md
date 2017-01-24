---
title: "Error del evaluador de expresiones CXX0025 | Microsoft Docs"
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
  - "CXX0025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0025"
  - "CXX0025"
ms.assetid: 3e2fb541-63b3-46ac-9f93-3dadb253bcf6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el operador necesita struct\/union  
  
 Se ha aplicado un operador que toma una expresión del tipo `struct` o **union** a una expresión que no es `struct` o **union**.  
  
 Los componentes de variables de clase, de estructura o de unión deben tener un nombre completo.  Los componentes no se deben escribir sin especificarlos completamente.  
  
 Este error es idéntico a CAN00025.