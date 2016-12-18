---
title: "&lt; numeric &gt; | Microsoft Docs"
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
  - "std::<numeric>"
  - "std.<numeric>"
  - "<numeric>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "encabezado < numeric >"
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; numeric &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las funciones de plantilla contenedor que realizan algoritmos para el procesamiento numérico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <numeric>  
```  
  
## <a name="remarks"></a>Comentarios  
 Los algoritmos son similares a los algoritmos de la Biblioteca de plantillas estándar (STL), pero forman parte de la biblioteca estándar de C++. Sin embargo, son compatibles con STL y, como los algoritmos de STL, pueden operar sobre diversas estructuras de datos. Estos incluyen clases contenedoras de STL, por ejemplo, [vector](vector%20Class.md) y [lista](../standard-library/list-class.md), y estructuras de datos definidos por el programa y matrices de elementos que cumplen los requisitos de un algoritmo determinado. Para lograr este nivel de generalidad, los algoritmos acceden a los elementos de un contenedor y los recorren indirectamente mediante iteradores. Los algoritmos procesan los intervalos de iteradores que se suelen especificar por sus posiciones inicial o final. Los intervalos a los que se hace referencia deben ser válidos en el sentido de que todos los punteros de los intervalos se deben poder desreferenciar y, dentro de las secuencias de cada intervalo, se debe poder llegar a la última posición desde la primera mediante incrementos.  
  
 Los algoritmos extienden las acciones que admiten las operaciones y las funciones miembro de cada uno de los contenedores de STL y permiten la interacción con diferentes tipos de objetos contenedores al mismo tiempo.  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[acumular](../Topic/%3Cnumeric%3E%20functions.md#accumulate)|Calcula la suma de todos los elementos de un intervalo especificado, incluido algún valor inicial, mediante el cálculo de sumas parciales sucesivas, o calcula el resultado de los resultados parciales sucesivos obtenidos mediante el uso de una operación binaria determinada en lugar de la operación de suma.|  
|[adjacent_difference](../Topic/%3Cnumeric%3E%20functions.md#adjacent_difference)|Calcula las diferencias sucesivas entre cada elemento y su predecesor en un intervalo de entrada y pone los resultados en un intervalo de destino, o calcula el resultado de un procedimiento generalizado donde la operación de diferencia se reemplaza por otra operación binaria especificada.|  
|[inner_product](../Topic/%3Cnumeric%3E%20functions.md#inner_product)|Calcula la suma del producto de elementos de dos intervalos y la agrega a un valor inicial especificado, o calcula el resultado de un procedimiento general donde las operaciones de suma y de producto se reemplazan con otras operaciones binarias especificadas.|  
|[Iota](../Topic/%3Cnumeric%3E%20functions.md#iota)|Almacena un valor inicial, empezando por el primer elemento y rellenando con incrementos sucesivos del valor (`value++`) en cada uno de los elementos del intervalo `[first, last)`.|  
|[partial_sum](../Topic/%3Cnumeric%3E%20functions.md#partial_sum)|Calcula una serie de sumas en un intervalo de entrada desde el primer elemento hasta el **elemento th y almacena el resultado de cada suma en el **elemento de un intervalo de destino, o calcula el resultado de un procedimiento generalizado donde la operación de suma se reemplaza por otra operación binaria especificada.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

