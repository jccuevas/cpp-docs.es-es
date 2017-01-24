---
title: "2.6.3 barrier Directive | Microsoft Docs"
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
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.3 barrier Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la directiva de **barrera** sincroniza todos los subprocesos en un equipo.  Cuando se encuentra, cada subproceso del equipo espera hasta que todos los demás hayan alcanzado este punto.  La sintaxis de la directiva de **barrera** es la siguiente:  
  
```  
#pragma omp barrier new-line  
```  
  
 Después de que todos los subprocesos del equipo hayan encontrado la barrera, cada subproceso del equipo se inicia ejecutando las instrucciones después de la directiva de la barrera en paralelo.  Dado que la directiva de **barrera** no tiene instrucciones de lenguaje de C\/C\+\+. como parte de la sintaxis, hay algunas restricciones en su posición dentro de un programa.  Vea [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) para la gramática formal.  El ejemplo siguiente muestra estas restricciones.  
  
```  
/* ERROR - The barrier directive cannot be the immediate  
*          substatement of an if statement  
*/  
if (x!=0)  
   #pragma omp barrier  
...  
  
/* OK - The barrier directive is enclosed in a  
*      compound statement.  
*/  
if (x!=0) {  
   #pragma omp barrier  
}  
```