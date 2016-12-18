---
title: "2.6.6 ordered Construct | Microsoft Docs"
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
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.6 ordered Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El bloque estructurado que sigue una directiva de **consultar** se ejecuta en el orden en que las iteraciones se ejecutan en un bucle secuencial.  La sintaxis de la directiva de **consultar** es la siguiente:  
  
```  
#pragma omp ordered new-line  
   structured-block  
```  
  
 una directiva de **consultar** debe estar dentro de la extensión dinámica de una construcción de **Para** o de **paralelo para** .  La directiva de **Para** o de **paralelo para** a la que la construcción de **consultar** enlaza debe tener una cláusula de **consultar** especificada como se describe en [sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en la página 11.  En la ejecución de una construcción de **Para** o de **paralelo para** con una cláusula de **consultar** , las construcciones de **consultar** se ejecutan estrictamente en el orden en que se ejecutan en una ejecución secuencial del bucle.  
  
 Restricciones de la directiva de **consultar** son los siguientes:  
  
-   Una iteración de un bucle con una construcción de **Para** no debe ejecutar la misma directiva ordenada más de una vez, y no debe ejecutar más de una directiva de **consultar** .