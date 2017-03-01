---
title: Clase de contenedor de ejemplo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- container classes
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
caps.latest.revision: 10
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 0f45ecbb6746c8d660e699ac0f7c08ecfb5dbb68
ms.lasthandoff: 02/24/2017

---
# <a name="sample-container-class"></a>Sample Container (Clase)
> [!NOTE]
>  Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).  
  
 Describe un objeto que controla una secuencia de elementos de longitud variable, normalmente de tipo **Ty**. La secuencia se almacena de diferentes maneras, dependiendo del contenedor real.  
  
 Un constructor de contenedor o una función miembro puede encontrar la ocasión de llamar al constructor **Ty**(**const Ty&**) o la función **Ty::operator=**(**const Ty&**). Si esta llamada inicia una excepción, el objeto contenedor está obligado a mantener su integridad y reiniciar cualquier excepción que detecte. Puede intercambiar, asignar, borrar o destruir un objeto contenedor de forma segura después de que inicie una de estas excepciones. Pero en general, no hay otra forma de predecir el estado de la secuencia controlada por el objeto contenedor.  
  
 Algunas advertencias adicionales:  
  
-   Si la expresión **~ Ty** inicia una excepción, el estado resultante del objeto contenedor no está definido.  
  
-   Si el contenedor almacena un objeto de asignador *al*, y *al* inicia una excepción que no sea como resultado de una llamada a *al***.allocate**, el estado resultante del objeto contenedor no está definido.  
  
-   Si el contenedor almacena un objeto de función *comp*, para determinar cómo ordenar la secuencia controlada, y *comp* inicia una excepción de cualquier tipo, el estado resultante del objeto contenedor no está definido.  
  
 Las clases de contenedor definidas por la biblioteca estándar de C++ cumplen varios requisitos adicionales, como se describe en los párrafos siguientes.  
  
 La clase de plantilla contenedor [list](../standard-library/list-class.md) proporciona un comportamiento determinista y útil, incluso en presencia de las excepciones descritas anteriormente. Por ejemplo, si se inicia una excepción durante la inserción de uno o más elementos, el contenedor permanece inalterado y se reinicia la excepción.  
  
 Para *todas* las clases de contenedor definidas por la biblioteca estándar de C++, si se inicia una excepción durante las llamadas a las funciones miembro siguientes:  
  
```  
<A NAME="vclrfcontainerinsert"></A>insert // single element inserted  
<A NAME="vclrfcontainerpushback"></A>push_back  
<A NAME="vclrfcontainerpushfront"></A>push_front  
```  
  
 el contenedor permanece inalterado y se reinicia la excepción.  
  
 Para *todas* las clases de contenedor definidas por la biblioteca estándar de C++, no se inicia ninguna excepción durante las llamadas a las funciones miembro siguientes:  
  
```  
<A NAME="vclrfcontainerpopback"></A>pop_back  
<A NAME="vclrfcontainerpopfront"></A>pop_front  
```  
  
 la función miembro [erase](../standard-library/container-class-erase.md) inicia una excepción solo si una operación de copia (construcción de asignación o copia) inicia una excepción.  
  
 Además, no se inicia ninguna excepción durante la copia de un iterador devuelto por una función miembro.  
  
 La función miembro [swap](../standard-library/container-class-swap.md) hace promesas adicionales para *todas* las clases de contenedor definidas por la biblioteca estándar de C++:  
  
-   La función miembro inicia una excepción solo si el contenedor almacena un objeto de asignador al, y `al` inicia una excepción cuando se copia.  
  
-   Las referencias, los punteros y los iteradores que designan elementos de las secuencias controladas que se intercambia siguen siendo válidos.  
  
 Un objeto de una clase de contenedor definida por la biblioteca estándar de C++ asigna y libera almacenamiento de la secuencia que controla a través de un objeto almacenado de tipo `Alloc`, que normalmente es un parámetro de plantilla. Ese objeto de asignador debe tener la misma interfaz externa que un objeto de clase **allocator\<Ty>**. En particular, `Alloc` debe ser del mismo tipo que **Alloc::rebind<value_type>::other**.  
  
 Para *todas las* clases de contenedor definidas por la biblioteca estándar de C++, la función miembro **Alloc get_allocator const;** devuelve una copia del objeto de asignador almacenado. Tenga en cuenta que el objeto de asignador almacenado *no* se copia cuando se asigna el objeto contenedor. Todos los constructores inicializan el valor almacenado en **allocator** a `Alloc` si el constructor no contiene ningún parámetro de asignador.  
  
 Según el estándar de C++, una clase de contenedor definida por la biblioteca estándar de C++ puede asumir que:  
  
-   Todos los objetos de la clase `Alloc` se comparan igual.  
  
-   El tipo **Alloc::const_pointer** es igual que **const Ty \***.  
  
-   El tipo **Alloc::const_reference** es igual que **const Ty&**.  
  
-   El tipo **Alloc::pointer** es igual que **Ty \***.  
  
-   El tipo **Alloc::reference** es igual que **Ty&**.  
  
 Pero en esta implementación, los contenedores no hacen estas suposiciones tan simples. Por tanto, funcionan correctamente con objetos de asignador que son más ambiciosos:  
  
-   No es necesario que todos los objetos de la clase `Alloc` se comparen igual. (Puede mantener varios grupos de almacenamiento).  
  
-   El tipo **Alloc::const_pointer** no es necesario que sea igual que **const Ty \***. (Un puntero const puede ser una clase).  
  
-   El tipo **Alloc::pointer** no es necesario que sea igual que **Ty \***. (Un puntero puede ser una clase).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \<contenedor de ejemplo>  
  
## <a name="see-also"></a>Vea también  
 [\<sample container>](../standard-library/sample-container.md)


