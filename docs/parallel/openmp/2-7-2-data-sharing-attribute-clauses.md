---
title: "2.7.2 Data-Sharing Attribute Clauses | Microsoft Docs"
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
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2 Data-Sharing Attribute Clauses
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Varias directivas aceptan las cláusulas que permiten a un usuario controlar los atributos de las variables durante la región.  Las cláusulas de atributo de uso compartido sólo se aplican a las variables en la extensión léxica de la directiva en la que la cláusula aparece.  No todas las cláusulas siguientes se admiten en todas las directivas.  La lista de cláusulas que son válidas en una directiva determinada se describe con la directiva.  
  
 Si una variable es visible cuando se encuentra un paralelo o construcción de división del trabajo, y la variable no se especifica en una cláusula de atributo de uso compartido o directiva de **threadprivate** , se comparte la variable.  Las variables estáticas declaradas dentro de la extensión dinámica de una región paralela comparten.  Se comparte la memoria asignada pila \(por ejemplo, mediante **malloc \(\)** en C o C\+\+ o el operador de **nuevo** en C\+\+\).  \(El puntero se en esta memoria, sin embargo, puede ser privado o compartido\). Las variables con la duración automática de almacenamiento declarada dentro de la extensión dinámica de una región paralela son privados.  
  
 La mayoría de las cláusulas aceptan un argumento *de la variable\-lista* , que es una lista separada por comas de variables que estén visibles.  Si una variable a la que se hace referencia en una cláusula de atributo de uso compartido de datos tiene un tipo derivado de una plantilla, y no hay otras referencias que variable del programa, el comportamiento es indefinido.  
  
 Todas las variables que aparecen en cláusulas directivas deben ser visibles.  Las cláusulas se pueden repetir según sea necesario, pero ninguna variable se puede especificar en más de una cláusula, excepto que una variable se puede especificar en **firstprivate** y una cláusula de **lastprivate** .  
  
 Las secciones siguientes describen las cláusulas de atributo de uso compartido de datos:  
  
-   **private**, [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en la página 25.  
  
-   **firstprivate**, [sección 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) en la página 26.  
  
-   **lastprivate**, [sección 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) en la página 27.  
  
-   **compartido**, [sección 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) en la página 27.  
  
-   **predeterminado**, [sección 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) en la página 28.  
  
-   **informe detallado**, [sección 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) en la página 28.  
  
-   **copyin**, [sección 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) en la página 31.  
  
-   **copyprivate**, [sección 2.7.2.8](../Topic/2.7.2.8%20copyprivate.md) en la página 32.