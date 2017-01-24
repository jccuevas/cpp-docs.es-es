---
title: "1.3 Execution Model | Microsoft Docs"
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
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.3 Execution Model
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP utiliza el modelo de bifurcación\-unión de la ejecución en paralelo.  Aunque este modelo de bifurcación\-unión puede ser útil para resolver diversos problemas, se hacen algo para las aplicaciones matriz\-basadas grandes.  OpenMP está destinada a los programas admiten que se ejecuten correctamente como programas paralelos \(varios subprocesos de ejecución y una biblioteca completa de soporte de OpenMP\) y como programas secuenciales \(las directivas omitirán y un OpenMP simple tropieza la biblioteca\).  Sin embargo, es posible y permite desarrollar un programa que no se comporte correctamente cuando se ejecuta secuencialmente.  Además, diferentes grados de paralelismo puede producir resultados diferentes numéricos debido a cambios en la asociación de operaciones numéricas.  Por ejemplo, un informe detallado de suma serie puede tener otro modelo de las asociaciones de suma que un informe detallado paralela.  Estas distintas asociaciones pueden cambiar los resultados de la adición de coma flotante.  
  
 Un programa escrito con la ejecución de comienza de OpenMP C\/C\+\+ API como un subproceso de ejecución denominado *el subproceso principal*.  El subproceso principal se ejecuta en una región en serie hasta que encuentra la primera construcción paralela.  en el OpenMP C\/C\+\+ API, la directiva de **Paralelo** constituye una construcción paralela.  Cuando se encuentra una construcción paralela, el subproceso principal crea un equipo de subprocesos, y el master hace responsable de equipo.  Cada subproceso del equipo ejecuta las instrucciones de la extensión dinámica de una región paralela, excepto las construcciones de división del trabajo.  Las construcciones de división de trabajo deben encontrar todos los subprocesos en el equipo en el mismo orden, e instrucciones dentro del bloque estructurado asociado se ejecutan en uno o más de los subprocesos.  La barrera implícitamente al final de una construcción de división de trabajo sin una cláusula de `nowait` es ejecutada por todos los subprocesos del equipo.  
  
 Si un subproceso modifica un objeto compartido, afecta no solo a su propio entorno de ejecución, sino también los de otros subprocesos del programa.  La modificación se garantiza que se completa, desde el punto de vista de uno de los otros subprocesos, en el punto de secuencia siguiente \(como definido en el lenguaje base\) si el objeto se declara como volatile.  Si no, la modificación se garantiza que se completa después primero de subproceso de modificación y, a continuación \(o en paralelo\) los otros subprocesos, busque una directiva de **vaciado** que especifique el objeto \(implícita o explícitamente\).  Observe que cuando las directivas de **vaciado** que son implícitamente en otras directivas de OpenMP no son suficientes para garantizar el orden deseado de efectos secundarios, es responsabilidad del programador proporcionar las directivas adicionales, explícitas de **vaciado** .  
  
 Al completar la construcción paralela, los subprocesos del equipo sincronizan en una barrera implícito, y sólo el subproceso principal continúa la ejecución.  Cualquier número de construcciones paralelas se puede especificar en un único programa.  Como resultado, un programa puede bifurcar y combinar varias veces durante la ejecución.  
  
 El OpenMP C\/C\+\+ API permite que los programadores utilizan directivas en funciones denominadas dentro de construcciones paralelas.  Las directivas que no aparecen en la extensión léxica de una construcción paralela pero pueden mentir en la extensión dinámica se denominan las directivas *dejadas huérfano* .  Las directivas de protección destinada huérfano permiten a los programadores la posibilidad de ejecutar partes importantes del programa en paralelo sólo a cambios mínimos programar secuencial.  Con esta funcionalidad, los usuarios pueden construcciones paralelas de código en los niveles superiores de las directivas del árbol de llamadas y el uso del programa controlar la ejecución de funciones que cualquiera de las.  
  
 Las llamadas asincronizadas a la salida de c y C\+\+ funcionan esa etiqueta al mismo archivo puede dar lugar a resultados en el que los datos escritos por diferentes subprocesos aparece en orden no determinista.  De forma similar, las llamadas desincronizadas a las funciones de entrada que se leen desde el mismo archivo pueden leer datos en orden no determinista.  El uso asincronizado de E\/S, de manera que cada subproceso tiene acceso a un archivo diferente, genera los mismos resultados que la ejecución en serie de E\/S.