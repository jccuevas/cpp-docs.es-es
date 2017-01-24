---
title: "2.4.3 single Construct | Microsoft Docs"
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
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4.3 single Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de **solo** identifica una construcción que especifique que el bloque estructurado asociado se ejecutan en sólo un subproceso del equipo \(no necesariamente el subproceso principal\).  La sintaxis de la directiva de **solo** es la siguiente:  
  
```  
#pragma omp single [clause[[,] clause] ...] new-line  
   structured-block  
```  
  
 La cláusula es:  
  
 *variable\-lista* **\)**de**private \(**  
  
 *variable\-lista* **\)**de**firstprivate \(**  
  
 *variable\-lista* **\)**de**copyprivate \(**  
  
 **nowait**  
  
 hay una barrera implícita después de la construcción de **solo** a menos que se especifique una cláusula de **nowait** .  
  
 Restricciones de la directiva de **solo** son los siguientes:  
  
-   Una sola cláusula de **nowait** puede aparecer en una directiva de **solo** .  
  
-   la cláusula de **copyprivate** no se debe utilizar con la cláusula de **nowait** .  
  
## referencias cruzadas:  
  
-   **private**, **firstprivate**, y las cláusulas de **copyprivate** , vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.