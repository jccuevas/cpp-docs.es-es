---
title: "2.4.2 sections Construct | Microsoft Docs"
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
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4.2 sections Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de **secciones** identifica una construcción noniterative de división del trabajo que especifica un conjunto de construcciones que se dividen entre los subprocesos en un equipo.  Cada sección se ejecuta una vez por un subproceso en el equipo.  La sintaxis de la directiva de **secciones** es la siguiente:  
  
```  
#pragma omp sections [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-line  
      structured-block ]  
...  
}  
```  
  
 La cláusula es:  
  
 *variable\-lista* **\)**de**private \(**  
  
 *variable\-lista* **\)**de**firstprivate \(**  
  
 *variable\-lista* **\)**de**lastprivate \(**  
  
 *variable\-lista* **\)**de**:** de*operador de***detallado \(**  
  
 **nowait**  
  
 Cada sección va precedida por una directiva de **sección** , aunque la directiva de **sección** es opcional para la primera sección.  las directivas de **sección** deben aparecer dentro de la extensión léxica de la directiva de **secciones** .  Hay una barrera implícita al final de una construcción de **secciones** , a menos que se especifique **nowait** .  
  
 Restricciones de la directiva de **secciones** son los siguientes:  
  
-   Una directiva de **sección** no debe aparecer fuera de extensión léxica de la directiva de **secciones** .  
  
-   Una sola cláusula de **nowait** puede aparecer en una directiva de **secciones** .  
  
## referencias cruzadas:  
  
-   **private**, **firstprivate**, **lastprivate**, y las cláusulas de **informe detallado** , vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.