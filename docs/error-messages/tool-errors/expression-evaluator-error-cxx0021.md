---
title: "Error del evaluador de expresiones CXX0021 | Microsoft Docs"
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
  - "CXX0021"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0021"
  - "CXX0021"
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0021
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

struct o union utilizadas como escalar  
  
 Se ha utilizado una expresión en una estructura o unión, pero no se especificó ningún elemento.  
  
 Cuando se manipula una variable de estructura o de unión, debe aparecer el nombre de la variable por si mismo, sin un calificador de campo.  Si en una expresión se utiliza una estructura o unión, debe estar calificada con el elemento específico deseado.  
  
 Se especifica el elemento cuyo valor se utiliza en la expresión.  
  
 Este error es idéntico a CAN00021.