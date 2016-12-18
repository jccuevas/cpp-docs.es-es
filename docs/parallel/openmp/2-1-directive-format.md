---
title: "2.1 Directive Format | Microsoft Docs"
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
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.1 Directive Format
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La sintaxis de una directiva de OpenMP se especifica formalmente por la gramática en [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md), e informalmente como sigue:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 Cada directiva comienza con **omp \#pragma**, para reducir la posibilidad de un conflicto con otras \(extensiones no\-\-OpenMP o proveedor con OpenMP\) directivas de pragma con los mismos nombres.  El resto de la directiva sigue las convenciones de normas de c y C\+\+ para las directivas de compilador.  En particular, el espacio en blanco se puede utilizar antes y después de **\#**, y el espacio en blanco se debe utilizar a veces para separar las palabras de una directiva.  Los tokens de preprocesamiento que siguen **omp \#pragma** están sujetos al reemplazo macro.  
  
 Las directivas distinguen entre mayúsculas y minúsculas.  El orden en que se van a directivas no es importante.  Las cláusulas de directivas se pueden repetir según sea necesario, sujetos a las restricciones enumeradas en la descripción de cada cláusula.  Si *la variable\-lista* aparece en una cláusula, debe especificar variables.  Sólo un *directiva\-nombre* se puede especificar mediante directiva.  Por ejemplo, la siguiente directiva no se permite:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 Una directiva de OpenMP se aplica a lo sumo una instrucción siguiente, que debe ser un bloque estructurado.