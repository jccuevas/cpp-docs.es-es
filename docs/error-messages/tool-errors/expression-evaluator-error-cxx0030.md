---
title: "Error del evaluador de expresiones CXX0030 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0030"
  - "CXX0030"
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del evaluador de expresiones CXX0030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

expresión no evaluable  
  
 El evaluador de la expresión del depurador no pudo obtener un valor para la expresión escrita.  Una causa posible es que la expresión hace referencia a memoria externa al espacio de direcciones del programa \(la desreferenciación a un puntero nulo es un ejemplo\).  Windows no permite el acceso a memoria externa al espacio de direcciones del programa.  
  
 Quizá desee volver a escribir la expresión con paréntesis para controlar el orden de evaluación.  
  
 Este error es idéntico a CAN00030.