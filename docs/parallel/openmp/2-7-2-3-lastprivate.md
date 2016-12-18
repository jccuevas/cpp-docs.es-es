---
title: "2.7.2.3 lastprivate | Microsoft Docs"
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
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.3 lastprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La cláusula de `lastprivate` proporciona un superconjunto de la funcionalidad proporcionada por la cláusula de `private` .  La sintaxis de la cláusula de `lastprivate` es la siguiente:  
  
```  
lastprivate(variable-list)  
```  
  
 Las variables especificadas en *la variable\-lista* tienen una semántica de cláusula de `private` .  Cuando una cláusula de `lastprivate` aparece en la directiva que identifica una construcción de división del trabajo, el valor de cada variable de `lastprivate` de iteración secuencialmente del bucle asociado, o la directiva léxico de la última sección, se asigna al objeto original de la variable.  Las variables que no están asignadas un valor por la última iteración de **Para** o de **paralelo para**, o por la sección léxico de la última directiva de **secciones** o de **secciones paralelas** , tienen valores indeterminados después de la construcción.  Los objetos secundarios no asignados también tienen un valor indeterminado después de la construcción.  
  
 Restricciones de la cláusula de `lastprivate` son los siguientes:  
  
-   Todas las restricciones de `private` aplican.  
  
-   Una variable con un tipo de clase se especifica mientras `lastprivate` debe tener un operador de asignación accesible, inequívoca de copia.  
  
-   Las variables que son privadas dentro de una región paralela o que aparecen en la cláusula de `reduction` de una directiva de **Paralelo** no se pueden especificar en una cláusula de `lastprivate` en una directiva de división del trabajo que se enlaza a la construcción paralela.