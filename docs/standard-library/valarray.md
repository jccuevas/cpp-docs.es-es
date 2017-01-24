---
title: "&lt;valarray&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<valarray>"
  - "valarray/std::<valarray>"
  - "std::<valarray>"
  - "<valarray>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray (encabezado)"
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;valarray&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define la clase de plantilla valarray y numerosas funciones y clases de plantilla auxiliares.  
  
## Sintaxis  
  
```  
  
#include <valarray>  
  
```  
  
## Comentarios  
 A estas funciones y clases de plantilla se les permite una latitud inusual con el fin de mejorar el rendimiento.  En concreto, cualquier función que devuelva el tipo **valarray \<**T1**\>** puede devolver un objeto de algún otro tipo T2.  En ese caso, cualquier función que acepte uno o más argumentos de tipo **valarray \<**T2**\>** debe tener sobrecargas que acepten combinaciones arbitrarias de esos argumentos, donde cada cual se sustituirá por un argumento de tipo T2.  
  
### Funciones  
  
|||  
|-|-|  
|[abs](../Topic/abs%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al valor absoluto de los elementos de la valarray de entrada.|  
|[acos](../Topic/acos%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al arcocoseno de los elementos de la valarray de entrada.|  
|[asin](../Topic/asin%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al arcoseno de los elementos de la valarray de entrada.|  
|[atan](../Topic/atan%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al principal valor del arcotangente de los elementos de la valarray de entrada.|  
|[atan2](../Topic/atan2%20\(%3Cvalarray%3E\).md)|Devuelve una valarray cuyos elementos son iguales al arcotangente de los componentes cartesianos especificados por una combinación de constantes y elementos de valarrays.|  
|[cos](../Topic/cos%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al coseno de los elementos de la valarray de entrada.|  
|[cosh](../Topic/cosh%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al coseno hiperbólico de los elementos de la valarray de entrada.|  
|[exp](../Topic/exp%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al exponencial natural de los elementos de la valarray de entrada.|  
|[log](../Topic/log%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al logaritmo natural de los elementos de la valarray de entrada.|  
|[log10](../Topic/log10%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al logaritmo común o de base 10 de los elementos de la valarray de entrada.|  
|[pow](../Topic/pow%20\(%3Cvalarray%3E\).md)|Opera en los elementos de constantes y valarrays de entrada, devolviendo una valarray cuyos elementos son iguales a una base especificada mediante los elementos de una valarray de entrada o constante elevada a un exponente especificado por los elementos de una valarray de entrada o una constante.|  
|[sin](../Topic/sin%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al seno de los elementos de la valarray de entrada.|  
|[sinh](../Topic/sinh%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales al seno hiperbólico de los elementos de la valarray de entrada.|  
|[sqrt](../Topic/sqrt%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales a la raíz cuadrada de los elementos de la valarray de entrada.|  
|[swap](../Topic/swap%20\(%3Cvalarray%3E\).md)||  
|[tan](../Topic/tan%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales a la tangente de los elementos de la valarray de entrada.|  
|[tanh](../Topic/tanh%20\(%3Cvalarray%3E\).md)|Opera en los elementos de una valarray de entrada, devolviendo una valarray cuyos elementos son iguales a la tangente hiperbólica de los elementos de la valarray de entrada.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cvalarray%3E\).md)|Comprueba si los elementos correspondientes de dos valarrays de igual tamaño no son iguales o si todos los elementos de una valarray no son iguales a un valor especificado del tipo de elemento de la valarray.|  
|[operator%](../Topic/operator%25.md)|Obtiene el resto de dividir los elementos correspondientes de dos valarrays de igual tamaño o de dividir una valarray por un valor especificado del tipo de elemento de la valarray o de dividir un valor especificado por una valarray.|  
|[operator&](../Topic/operator&.md)|Obtiene el **AND** bit a bit entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.|  
|[operator&&](../Topic/operator&&.md)|Obtiene el **AND** lógico entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de valarray.|  
|[operador \>](../Topic/operator%3E%20\(%3Cvalarray%3E\).md)|Comprueba si los elementos de una valarray son mayores que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o menores que un valor especificado del tipo de elemento de la valarray.|  
|[operator\>\=](../Topic/operator%3E=%20\(%3Cvalarray%3E\).md)|Comprueba si los elementos de una valarray son mayores o iguales que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o iguales o menores que un valor especificado.|  
|[operador \>\>](../Topic/operator%3E%3E%20\(%3Cvalarray%3E\).md)|Desplaza hacia la derecha los bits de cada elemento de una valarray un número especificado de posiciones o una cantidad de elementos especificada por una segunda valarray.|  
|[operador \<](../Topic/operator%3C%20\(%3Cvalarray%3E\).md)|Comprueba si los elementos de una valarray son menores que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o menores que un valor especificado.|  
|[operator\<\=](../Topic/operator%3C=%20\(%3Cvalarray%3E\).md)|Comprueba si los elementos de una valarray son menores o iguales que los elementos de una valarray de igual tamaño, o si todos los elementos de una valarray son mayores, iguales o menores que un valor especificado.|  
|[operador \<\<](../Topic/operator%3C%3C%20\(%3Cvalarray%3E\).md)|Desplaza hacia la izquierda los bits de cada elemento de una valarray un número especificado de posiciones o una cantidad de elementos especificada por una segunda valarray.|  
|[operator\*](../Topic/operator*%20\(%3Cvalarray%3E\).md)|Obtiene el producto de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|  
|[operator\+](../Topic/operator+%20\(%3Cvalarray%3E\).md)|Obtiene la suma de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|  
|[operator\-](../Topic/operator-%20\(%3Cvalarray%3E\)2.md)|Obtiene la diferencia de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|  
|[operator\/](../Topic/operator-%20\(%3Cvalarray%3E\)1.md)|Obtiene el cociente de elementos entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de la valarray.|  
|[operator\=\=](../Topic/operator==%20\(%3Cvalarray%3E\).md)|Comprueba si los elementos correspondientes de dos valarrays de igual tamaño son iguales o si todos los elementos de una valarray son iguales a un valor especificado del tipo de elemento de la valarray.|  
|[operator^](../Topic/operator%5E.md)|Obtiene el `OR` exclusivo bit a bit entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.|  
|[operator&#124;](../Topic/operator%7C.md)|Obtiene el `OR` bit a bit entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.|  
|[operator&#124;&#124;](../Topic/operator%7C%7C.md)|Obtiene el `OR` lógico entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de valarray.|  
  
### Clases  
  
|||  
|-|-|  
|[gslice \(Clase\)](../standard-library/gslice-class.md)|Clase de utilidad para valarray que se usa para definir segmentos multidimensionales de una valarray.|  
|[gslice\_array \(Clase\)](../standard-library/gslice-array-class.md)|Clase de plantilla auxiliar e interna que admite objetos de segmentos generales proporcionando operaciones entre matrices de subconjuntos definidas por el segmento general de una valarray.|  
|[indirect\_array \(Clase\)](../standard-library/indirect-array-class.md)|Clase de plantilla auxiliar e interna que admite objetos que son subconjuntos de valarrays proporcionando operaciones entre matrices de subconjuntos definidas especificando un subconjunto de índices de una valarray principal.|  
|[mask\_array \(Clase\)](../standard-library/mask-array-class.md)|Clase de plantilla auxiliar e interna que admite objetos que son subconjuntos de valarrays principales, especificados con una expresión booleana, proporcionando operaciones entre matrices de subconjuntos.|  
|[slice \(Clase\)](../standard-library/slice-class.md)|Clase de utilidad para valarray que se usa para definir subconjuntos unidimensionales de tipo vector de una valarray.|  
|[slice\_array \(Clase\)](../standard-library/slice-array-class.md)|Clase de plantilla auxiliar e interna que admite objetos de segmentos proporcionando operaciones entre matrices de subconjuntos definidas por el segmento de una valarray.|  
|[valarray \(Clase\)](../standard-library/valarray-class.md)|Clase de plantilla que describe un objeto que controla una secuencia de elementos de tipo **Type** que se almacenan como una matriz y que se diseñan para realizar operaciones matemáticas de alta velocidad, optimizadas para ofrecer un alto rendimiento a la hora de realizar cálculos.|  
  
### Especializaciones  
  
|||  
|-|-|  
|[valarray\<bool\> \(Clase\)](../standard-library/valarray-bool-class.md)|Versión especializada de la clase de plantilla valarray \<**Type**\> para elementos de tipo `bool`.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)