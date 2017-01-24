---
title: "3.1.6 omp_in_parallel Function | Microsoft Docs"
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
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.6 omp_in_parallel Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de **omp\_in\_parallel** devuelve un valor distinto de cero si se denomina dentro de la extensión dinámica de una región paralela que se ejecutan en paralelo, de lo contrario, devuelve 0.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Esta función devuelve un valor distinto de cero cuando se llama desde un área que se ejecutan en paralelo, incluidas las regiones anidados que están serializadas.