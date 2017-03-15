---
title: "1.2 Definition of Terms | Microsoft Docs"
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
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.2 Definition of Terms
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

los términos siguientes se utilizan en este documento:  
  
 barrera  
 Un punto de sincronización que debe realizarse por todos los subprocesos en un equipo.  Cada subproceso espera hasta que llegan todos los subprocesos en el equipo en este punto.  hay barreras explícitas identificadas por directivas y barreras implícitas creadas por la implementación.  
  
 construcción  
 una construcción es una instrucción.  Consta de una directiva y el bloque estructurado subsiguiente.  Observe que algunas directivas no forman parte de una construcción.  \(Vea *la openmp\-directiva* en [Apéndice C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)\).  
  
 directiva  
 El C. o C\+\+ **\#pragma** seguido del identificador de **omp** , otro texto, y una nueva línea.  La directiva especifica un comportamiento del programa.  
  
 extensión dinámica  
 Todas las instrucciones de *la extensión léxica*, más cualquier instrucción dentro de una función que se ejecuta como resultado de la ejecución de instrucciones dentro de la extensión léxica.  Una extensión dinámica también se conoce como *región*.  
  
 extensión léxica  
 Instrucciones incluidas léxico dentro *de un bloque estructurado*.  
  
 subproceso principal  
 El subproceso que crea un equipo cuando se escribe *una región paralela* .  
  
 región paralela  
 Instrucciones que se enlazan a una construcción parallel de OpenMP y se pueden ejecutar por varios subprocesos.  
  
 private  
 Nombres de variable privados en el bloque de almacenamiento que es único al subproceso que realiza la referencia.  Observe que hay varias maneras de especificar que una variable es privada: una definición dentro de una región paralela, una directiva de **threadprivate** , **private**, **firstprivate**, **lastprivate**, o cláusula de **informe detallado** , o uso de la variable como variable de control de bucle de **Para**en un bucle de **Para** inmediatamente después de una directiva de **Para** o de **paralelo para** .  
  
 región  
 una extensión dinámica.  
  
 región en serie  
 Instrucciones ejecutadas solo por *el subproceso principal* fuera de extensión dinámica de cualquier *región paralela*.  
  
 serialice  
 Para ejecutar una construcción paralela con un equipo de subprocesos que consistían en un único subproceso \(el subproceso principal para esa construcción paralela\), con el orden de ejecución de ejecución de las instrucciones dentro del bloque estructurado \(el mismo orden como si el bloque no fuera parte de una construcción paralela\), y sin efecto en el valor devuelto por **omp\_in\_parallel \(\)** \(aparte de los efectos de las construcciones paralelas anidadas\).  
  
 compartido  
 Nombres de variable compartidos en solo bloque de almacenamiento.  Todos los subprocesos en un equipo que tienen acceso a esta variable tendrán acceso a este único bloque de almacenamiento.  
  
 bloque estructurado  
 Un bloque estructurado es una instrucción \(único o compuesto\) que tiene una entrada única y una sola salida.  No hay ninguna instrucción un bloque estructurado si hay un salto fuera o dentro de esa instrucción \(llamada incluidos en **longjmp**\(3C\) o el uso de **captura**, sólo una llamada a **Salir** se permite\).  Una instrucción compuesta es un bloque estructurado si su ejecución siempre comienza en **{** y siempre los extremos que abra en **}**cerrado.  Una instrucción de expresiones, la instrucción SELECT, la instrucción de iteración, o de **intento** es un bloque estructurado si la instrucción compuesta correspondiente obtenida agregando lo en **{** y **}**sería un bloque estructurado.  Una instrucción de salto, denominada instrucción, o instrucción de declaración no es un bloque estructurado.  
  
 equipo  
 uno o más subprocesos que cooperan en la ejecución de una construcción.  
  
 Subproceso  
 Una entidad de ejecución que tiene un flujo de serie de control, conjunto de variables privadas, y tener acceso a las variables shared.  
  
 variable  
 Un identificador, calificado opcionalmente por espacios de nombres, esos nombres un objeto.