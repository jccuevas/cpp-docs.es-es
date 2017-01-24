---
title: "Error del evaluador de expresiones CXX0017 | Microsoft Docs"
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
  - "CXX0017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0017"
  - "CXX0017"
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo no se encuentra  
  
 No se pudo encontrar un símbolo especificado en una expresión.  
  
 Una posible causa de este error es una no coincidencia de mayúsculas y minúsculas en el nombre del símbolo.  Como C y C\+\+ son lenguajes que diferencian entre mayúsculas y minúsculas, un nombre de símbolo debe especificarse en el tipo de letra mayúscula o minúscula exacto a como se defina en el código fuente.  
  
 Este error puede darse al intentar convertir el tipo de una variable para observarla durante la depuración.  `typedef` declara un nuevo nombre para un tipo, pero no define un nuevo tipo.  La conversión de tipos que se ha intentado en el depurador requiere el nombre de un tipo definido.  
  
 Este error es idéntico a CAN0017.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Asegúrese de que el símbolo ya esté declarado en el lugar del programa donde se utiliza.  
  
2.  Utilice un nombre de tipo actual para convertir variables en el depurador, en lugar de un nombre definido por `typedef`