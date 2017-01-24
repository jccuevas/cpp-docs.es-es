---
title: "Algoritmos | Microsoft Docs"
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
helpviewer_keywords: 
  - "convenciones de la biblioteca de C++ para las funciones de plantilla de algoritmo"
  - "algoritmos [C++], C++"
  - "convenciones [C++], algoritmo de C++"
  - "bibliotecas [C++], convenciones de los algoritmos de C++"
  - "Biblioteca estándar de C++, algoritmos"
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Algoritmos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los algoritmos son una parte fundamental de la biblioteca de plantillas estándar.  Los algoritmos no funcionan con los contenedores en sí, sino con iteradores.  Por lo tanto, la mayoría de los contenedores STL, si no todos, pueden utilizar un mismo algoritmo.  Esta sección describe las convenciones y terminología de los algoritmos STL.  
  
## Comentarios  
 La descripción de las funciones de plantilla de algoritmo emplea varias frases de forma abreviada:  
  
-   La frase "en el intervalo \[*A*, *B*\)" significa la secuencia de cero o más valores discretos que comienzan con *A* y terminan con *B*, sin incluirlo.  Un intervalo es válido únicamente si *B* es accesible desde *A;* puede almacenar *A* en un objeto *N* \(*N* \= *A*\), incrementar el objeto cero o más veces \(\+\+*N*\) y hacer que el objeto sea igual a *B* después de un número finito de incrementos \(N \=\= B*\).*  
  
-   La frase "cada *N* en el intervalo \[*A*, *B*\)" significa que *N* comienza con el valor *A* y se incrementa cero o más veces hasta que sea igual que el valor *B*.  El caso *N* \=\= *B* no está en el intervalo.  
  
-   La frase "el valor más bajo de *N* en el intervalo \[*A*, *B*\) tal que *X*" significa que la condición *X* se comprueba para cada *N* del intervalo \[*A*, *B*\) hasta que la condición *X* se cumple.  
  
-   La frase "el valor más alto de *N* en el intervalo \[*A*, *B*\) tal que *X*" significa que *X* se comprueba para cada *N* del intervalo \[*A*, *B*\).  La función almacena en `K` una copia de *N* cada vez que la condición *X* se cumple.  Si se produce cualquier almacenamiento de este tipo, la función sustituye el valor final de *N*, que es igual a *B*, con el valor de `K`.  Para un iterador de acceso aleatorio o bidireccional, sin embargo, también puede significar que *N* comienza con el valor más alto del intervalo y va disminuyendo en el intervalo hasta que la condición *X* se cumple.  
  
-   Expresiones como *X* \- *Y*, donde *X* e *Y* pueden ser iteradores distintos de los iteradores de acceso aleatorio, se ha diseñado en el sentido matemático.  La función no evalúa necesariamente operador**\-** si debe determinar dicho valor.  Lo mismo ocurre con expresiones como *X* \+ *N* y *X* \- *N*, donde *N* es de tipo entero.  
  
 Varios algoritmos hacen uso de un predicado que realiza una comparación en pares, como con `operator==`, para producir un resultado `bool`.  La función de predicado `operator==`, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos.  Debe producir el mismo resultado `bool` cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.  
  
 Varios algoritmos hacen uso de un predicado que debe imponer una ordenación débil estricta en pares de elementos de una secuencia.  Para el predicado `pr`\(*X*, *Y*\):  
  
-   Estricta significa que `pr`\(*X*, *X*\) es falso.  
  
-   Débil significa que *X* e *Y* tienen una ordenación equivalente si \!`pr`\(*X*, *Y*\) && \!`pr`\(*Y*, *X*\) \(no es necesario definir *X* \=\= *Y*\).  
  
-   La ordenación significa que `pr`\(*X*, *Y*\) & & `pr`\(*Y*, Z\) implica `pr`\(*X*, Z\).  
  
 Algunos de estos algoritmos utilizan implícitamente el predicado *X* \< *Y*.  Otros predicados que normalmente cumplen el requisito de ordenación débil estricta son *X* \> *Y*, **menos**\(*X*, *Y*\) y `greater`\(*X*, *Y*\).  Pero tenga en cuenta que predicados como *X* \<\= *Y* y *X* \>\= *Y* no cumplen este requisito.  
  
 Una secuencia de elementos designados por los iteradores del intervalo \[`First`, `Last`\) es una secuencia ordenada por operator**\<** si, para cada *N* del intervalo \[0, `Last` \- `First`\) y para cada *M* del intervalo \(N, `Last` \- `First`\), el predicado. \(\*\(`First` \+ *M*\) \< \*\(*First* \+ *N*\)\) es verdadero.  \(Tenga en cuenta que los elementos se ordenan en orden ascendente\). La función de predicado **operator\<**, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos.  Debe producir el mismo resultado `bool` cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.  Además, debe imponer una ordenación débil estricta en los operandos que compara.  
  
 Una secuencia de elementos designados por los iteradores del intervalo \[`First`, `Last`\) es una secuencia de montón ordenada por **operator\<** si, para cada *N* en el intervalo \[1, `Last` \- `First`\) el predicado. \(\*`First` \< \*\(`First` \+ *N*\)\) es verdadero.  \(El primer elemento es el mayor\). De lo contrario, solo conocen su estructura interna las funciones de plantilla [make\_heap](../Topic/make_heap.md), [pop\_heap](../Topic/pop_heap.md), y [push\_heap](../Topic/push_heap.md).  Al igual que con una secuencia ordenada, la función de predicado **operator\<**, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos, y debe imponer una ordenación débil estricta en los operandos que compara.  Debe producir el mismo resultado `bool` cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.  
  
 Los algoritmos de STL se encuentran en los archivos de encabezado [\<algorithm\>](../standard-library/algorithm.md) y [\<numeric\>](../standard-library/numeric.md).  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)