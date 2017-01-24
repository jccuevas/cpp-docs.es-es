---
title: "2.7.2.2 firstprivate | Microsoft Docs"
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
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.2 firstprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La cláusula de **firstprivate** proporciona un superconjunto de la funcionalidad proporcionada por la cláusula de **private** .  La sintaxis de la cláusula de **firstprivate** es la siguiente:  
  
```  
firstprivate(variable-list)  
```  
  
 Las variables especificadas en *variable\-lista* tienen una semántica de cláusula de **private** , como se describe en [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25.  La inicialización o la construcción ocurre como si se hizo una vez por el subproceso, antes de la ejecución del subproceso de la construcción.  Para una cláusula de **firstprivate** en una construcción paralela, el valor inicial del nuevo objeto privado es el valor del objeto original que existe inmediatamente antes de la construcción paralela para el subproceso que lo encuentra.  Para una cláusula de **firstprivate** en una construcción de división del trabajo, el valor inicial del nuevo objeto privado para cada subproceso que se ejecute la construcción de división de trabajo es el valor del objeto original que existe antes del punto en el tiempo que el mismo subproceso encuentra la construcción de la división del trabajo.  Además, para objetos de C\+\+, el nuevo objeto privado para cada subproceso es copia construida del objeto original.  
  
 Restricciones de la cláusula de **firstprivate** son los siguientes:  
  
-   La variable especificada en una cláusula de **firstprivate** no debe tener un tipo incompleto o un tipo de referencia.  
  
-   Una variable con un tipo de clase se especifica mientras **firstprivate** debe tener un constructor accesible, inequívoca de copia.  
  
-   Las variables que son privadas dentro de una región paralela o que aparecen en la cláusula de **informe detallado** de una directiva de **Paralelo** no se pueden especificar en una cláusula de **firstprivate** en una directiva de división del trabajo que se enlaza a la construcción paralela.