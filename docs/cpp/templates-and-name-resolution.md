---
title: "Plantillas y resoluci&#243;n de nombres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 519ba7b5-cd25-4549-865a-9a7b9dffdc28
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Plantillas y resoluci&#243;n de nombres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En las definiciones de plantilla, hay tres tipos de nombres.  
  
-   Nombres declarados localmente, como el nombre de la propia plantilla y cualquier nombre declarado dentro de la definición de plantilla.  
  
-   Nombres del ámbito de inclusión fuera de la definición de plantilla.  
  
-   Nombres que dependen de alguna manera de los argumentos de plantilla, denominados nombres dependientes.  
  
 Mientras que los dos primeros nombres pertenecen también a ámbitos de clase y función, en las definiciones de plantillas se requieren reglas especiales de resolución de nombres para tratar la complejidad agregada de los nombres dependientes.  Esto se debe a que el compilador apenas tiene conocimiento de estos nombres hasta que se crea una instancia de la plantilla, ya que pueden ser tipos totalmente diferentes en función de los argumentos de plantilla que se usen.  Los nombres no dependientes se buscan de acuerdo con las reglas habituales y en el punto de definición de la plantilla.  Estos nombres, que son independientes de los argumentos de plantilla, se buscan una sola vez para todas las especializaciones de plantilla.  Los nombres dependientes no se buscan hasta que se crea una instancia de la plantilla y se buscan por separado para cada especialización.  
  
 Un tipo es dependiente si depende de los argumentos de plantilla.  En concreto, un tipo es dependiente si es:  
  
-   El propio argumento de plantilla:  
  
    ```  
    T  
    ```  
  
-   Un nombre completo con una clasificación que incluye un tipo dependiente:  
  
    ```  
    T::myType  
    ```  
  
-   Un nombre completo si la parte incompleta identifica un tipo dependiente:  
  
    ```  
    N::T  
    ```  
  
-   Un tipo const o volatile para el que el tipo base es un tipo dependiente:  
  
    ```  
    const T  
    ```  
  
-   Un tipo de puntero, referencia, matriz o puntero de función basado en un tipo dependiente:  
  
    ```  
    T *, T &, T [10], T (*)()  
    ```  
  
-   Una matriz cuyo tamaño se basa en un parámetro de plantilla:  
  
    ```  
    template <int arg> class X {  
    int x[arg] ; // dependent type  
    }  
    ```  
  
-   Un tipo de plantilla creado a partir de un parámetro de plantilla:  
  
    ```  
    T<int>, MyTemplate<T>  
    ```  
  
## Dependencia de tipos y dependencia de valores  
 Los nombres y las expresiones dependientes de un parámetro de plantilla se clasifican como dependientes del tipo o dependientes del valor, en función de si el parámetro de plantilla es un parámetro de tipo o un parámetro de valor.  Además, cualquier identificador declarado en una plantilla con un tipo dependiente del argumento de plantilla se considera dependiente del valor, como en el caso de un tipo de entero o de enumeración inicializado con una expresión dependiente del valor.  
  
 Las expresiones dependientes del tipo y dependientes del valor son expresiones que implican variables dependientes del tipo o dependientes del valor.  Estas expresiones pueden tener una semántica diferente en función de los parámetros utilizados para la plantilla.  
  
## Vea también  
 [Plantillas](../cpp/templates-cpp.md)