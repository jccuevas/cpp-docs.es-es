---
title: "Error del evaluador de expresiones CXX0015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0015"
  - "CXX0015"
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del evaluador de expresiones CXX0015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

expresión demasiado compleja \(desbordamiento de pila\)  
  
 La expresión escrita es demasiado compleja o está demasiado anidada para el espacio de almacenamiento disponible para el evaluador de la expresión C.  
  
 Suele producirse desbordamiento debido al exceso de cálculos pendientes.  
  
 Reorganice la expresión de forma que cada componente de ésta se pueda evaluar según se encuentra, en lugar de tener que esperar a calcular otras partes de la expresión.  
  
 Divida la expresión en varios comandos.  
  
 Este error es idéntico a CAN0015.