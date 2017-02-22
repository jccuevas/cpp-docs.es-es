---
title: "Error del evaluador de expresiones CXX0022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0022"
  - "CXX0022"
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del evaluador de expresiones CXX0022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

llamada a la función antes de \_main  
  
 El evaluador de la expresión C no puede evaluar una función antes de que el depurador haya escrito la función **\_main**.  El programa no se inicializa correctamente hasta que se haya llamado a **\_main**.  
  
 Este error es idéntico a CAN00022.