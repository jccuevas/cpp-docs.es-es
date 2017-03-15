---
title: "1.4 Conformidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.4 Conformidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Es una implementación de la API de C o C++ OpenMP *compatible con OpenMP* Si reconoce y conserva la semántica de todos los elementos de esta especificación, como se definen en los capítulos 1, 2, 3, 4, y apéndice C. apéndices A, B, D, E y F son solo para fines informativos y no forman parte de la especificación. Las implementaciones que incluyen sólo un subconjunto de la API no son compatibles con OpenMP.  
  
 El de OpenMP C y C++ API es una extensión para el idioma base admitido por una implementación. Si el idioma base no admite una construcción de lenguaje o la extensión que aparece en este documento, la implementación de OpenMP no es necesario para admitirla.  
  
 Todas las funciones integradas y funciones de biblioteca estándar de C y C++ (es decir, que el compilador tiene un conocimiento específico de funciones) debe ser seguro para subprocesos. Uso no sincronizada de subproceso: funciones seguras para subprocesos diferentes dentro de una región paralela no produce un comportamiento indefinido. Sin embargo, el comportamiento puede no ser el mismo que en una región de la serie. (Una función de generación de números aleatorios es un ejemplo).  
  
 La API de C o C++ OpenMP especifica que es cierto comportamiento *definido por la implementación.* Una implementación compatible de OpenMP es necesaria para definir y documentar su comportamiento en estos casos. Consulte [Apéndice E](../Topic/E.%20Implementation-Defined%20Behaviors%20in%20OpenMP%20C-C++.md), página 97, para obtener una lista de comportamientos definidos por la implementación.