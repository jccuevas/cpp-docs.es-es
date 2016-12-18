---
title: "Convertir | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "convertir"
  - "clases [C++], polimorfismo"
  - "conversión"
  - "operador de conversión dinámico"
  - "clases polimórficas"
  - "operador de conversión estático"
  - "funciones virtuales, en clases derivadas"
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Convertir
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El lenguaje C\+\+ permite que, si una clase se deriva de una clase base que contiene funciones virtuales, se pueda usar un puntero a ese tipo de clase base para llamar a las implementaciones de las funciones virtuales que residen en el objeto de la clase derivada.  Una clase que contiene funciones virtuales se denomina a veces “clase polimórfica”.  
  
 Como una clase derivada contiene en su totalidad las definiciones de todas las clases base de la que se deriva, es seguro convertir un puntero a la jerarquía de clases en cualquiera de estas clases base.  Dado un puntero a una clase base, es seguro convertir el puntero en cualquier objeto que se encuentre por debajo en la jerarquía.  Es seguro si el objeto al que se apunta es de un tipo derivado de la clase base.  En este caso, se dice que el objeto real es el "objeto completo" y que el puntero a la clase base apunta a un "subobjeto" del objeto completo.  Considere, por ejemplo, la jerarquía de clases que se muestra en la ilustración siguiente.  
  
 ![Jerarquía de clases](../cpp/media/vc38zz1.png "vc38ZZ1")  
Jerarquía de clases  
  
 Un objeto de tipo `C` se podría visualizar tal y como se muestra en la ilustración siguiente.  
  
 ![Clase C con subobjetos B y A](../cpp/media/vc38zz2.png "vc38ZZ2")  
Clase C con subobjeto B y subobjeto A  
  
 Dada una instancia de la clase `C`, hay un subobjeto `B` y un objeto `A`.  La instancia de `C`, incluidos los subobjetos `A` y `B`, es el "objeto completo".  
  
 Mediante el uso de información de tipos en tiempo de ejecución, es posible determinar si un puntero apunta realmente a un objeto completo y si se puede realizar una conversión segura para que apunte a otro objeto de su jerarquía.  El operador [dynamic\_cast](../cpp/dynamic-cast-operator.md) se puede utilizar para realizar estos tipos de conversiones.  También realiza la comprobación en tiempo de ejecución necesaria para que la operación sea segura.  
  
 Para la conversión de tipos que no son polimórficos, puede usar el operador [static\_cast](../cpp/static-cast-operator.md) \(en este tema se explica la diferencia entre las conversiones estáticas y dinámicas, y cuándo es adecuado utilizar cada una de ellas\).  
  
 En esta sección se tratan los siguientes temas:  
  
-   [Operadores de conversión](../cpp/casting-operators.md)  
  
-   [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)  
  
## Vea también  
 [Expresiones](../cpp/expressions-cpp.md)