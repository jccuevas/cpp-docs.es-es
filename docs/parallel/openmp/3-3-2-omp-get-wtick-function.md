---
title: "3.3.2 omp_get_wtick Function | Microsoft Docs"
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
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.3.2 omp_get_wtick Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de `omp_get_wtick` devuelve un valor de doble precisión de punto flotante igual al número de segundos entre los tic\-tac de reloj sucesivos.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
double omp_get_wtick(void);  
```