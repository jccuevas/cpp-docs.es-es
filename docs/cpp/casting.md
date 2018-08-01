---
title: Conversión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c7dfe18c65fcde7cbfa0ea2121234f2896a2723
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405024"
---
# <a name="casting"></a>Conversión
El lenguaje C++ permite que, si una clase se deriva de una clase base que contiene funciones virtuales, se pueda usar un puntero a ese tipo de clase base para llamar a las implementaciones de las funciones virtuales que residen en el objeto de la clase derivada. Una clase que contiene funciones virtuales se denomina a veces “clase polimórfica”.  
  
 Como una clase derivada contiene en su totalidad las definiciones de todas las clases base de la que se deriva, es seguro convertir un puntero a la jerarquía de clases en cualquiera de estas clases base. Dado un puntero a una clase base, es seguro convertir el puntero en cualquier objeto que se encuentre por debajo en la jerarquía. Es seguro si el objeto al que se apunta es de un tipo derivado de la clase base. En este caso, se dice que el objeto real es el "objeto completo" y que el puntero a la clase base apunta a un "subobjeto" del objeto completo. Considere, por ejemplo, la jerarquía de clases que se muestra en la ilustración siguiente.  
  
 ![Jerarquía de clases](../cpp/media/vc38zz1.gif "vc38ZZ1")  
Jerarquía de clases  
  
 Un objeto de tipo `C` se podría visualizar tal y como se muestra en la ilustración siguiente.  
  
 ![Clase C con sub&#45;objetos B y A](../cpp/media/vc38zz2.gif "vc38ZZ2")  
Clase C con subobjeto B y subobjeto A  
  
 Dada una instancia de la clase `C`, hay un subobjeto `B` y un objeto `A`. La instancia de `C`, incluidos los subobjetos `A` y `B`, es el "objeto completo".  
  
 Mediante el uso de información de tipos en tiempo de ejecución, es posible determinar si un puntero apunta realmente a un objeto completo y si se puede realizar una conversión segura para que apunte a otro objeto de su jerarquía. El [dynamic_cast](../cpp/dynamic-cast-operator.md) operador puede usarse para realizar estos tipos de conversiones. También realiza la comprobación en tiempo de ejecución necesaria para que la operación sea segura.  
  
 Para la conversión de tipos no polimórficos, puede usar el [static_cast](../cpp/static-cast-operator.md) operador (este tema explica la diferencia entre las conversiones estáticas y dinámicas, y cuándo es adecuado utilizar cada uno).  
  
 En esta sección se tratan los siguientes temas:  
  
-   [Operadores de conversión](../cpp/casting-operators.md)  
  
-   [Información de tipo de tiempo de ejecución](../cpp/run-time-type-information.md)  
  
## <a name="see-also"></a>Vea también  
 [Expresiones](../cpp/expressions-cpp.md)