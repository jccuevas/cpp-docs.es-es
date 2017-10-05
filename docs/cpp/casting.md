---
title: "Conversión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- casting
- coercion
- virtual functions, in derived classes
- static cast operator
- dynamic cast operator
- polymorphic classes
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 590022e41c13031e6ef5c78d4672521713002af1
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="casting"></a>Conversión
El lenguaje C++ permite que, si una clase se deriva de una clase base que contiene funciones virtuales, se pueda usar un puntero a ese tipo de clase base para llamar a las implementaciones de las funciones virtuales que residen en el objeto de la clase derivada. Una clase que contiene funciones virtuales se denomina a veces “clase polimórfica”.  
  
 Como una clase derivada contiene en su totalidad las definiciones de todas las clases base de la que se deriva, es seguro convertir un puntero a la jerarquía de clases en cualquiera de estas clases base. Dado un puntero a una clase base, es seguro convertir el puntero en cualquier objeto que se encuentre por debajo en la jerarquía. Es seguro si el objeto al que se apunta es de un tipo derivado de la clase base. En este caso, se dice que el objeto real es el "objeto completo" y que el puntero a la clase base apunta a un "subobjeto" del objeto completo. Considere, por ejemplo, la jerarquía de clases que se muestra en la ilustración siguiente.  
  
 ![Jerarquía de clases](../cpp/media/vc38zz1.gif "vc38ZZ1")  
Jerarquía de clases  
  
 Un objeto de tipo `C` se podría visualizar tal y como se muestra en la ilustración siguiente.  
  
 ![Clase C con sub &#45; los objetos B y A](../cpp/media/vc38zz2.gif "vc38ZZ2")  
Clase C con subobjeto B y subobjeto A  
  
 Dada una instancia de la clase `C`, hay un subobjeto `B` y un objeto `A`. La instancia de `C`, incluidos los subobjetos `A` y `B`, es el "objeto completo".  
  
 Mediante el uso de información de tipos en tiempo de ejecución, es posible determinar si un puntero apunta realmente a un objeto completo y si se puede realizar una conversión segura para que apunte a otro objeto de su jerarquía. El [dynamic_cast](../cpp/dynamic-cast-operator.md) operador puede usarse para realizar estos tipos de conversiones. También realiza la comprobación en tiempo de ejecución necesaria para que la operación sea segura.  
  
 Para la conversión de tipos no polimórficos, puede usar el [static_cast](../cpp/static-cast-operator.md) operador (este tema explica la diferencia entre las conversiones estáticas y dinámicas, y cuándo es adecuado utilizar cada uno).  
  
 En esta sección se tratan los siguientes temas:  
  
-   [Operadores de conversión](../cpp/casting-operators.md)  
  
-   [Información de tipo de tiempo de ejecución](../cpp/run-time-type-information.md)  
  
## <a name="see-also"></a>Vea también  
 [Expresiones](../cpp/expressions-cpp.md)
