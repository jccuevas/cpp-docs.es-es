---
title: "Sample Container (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases container"
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Sample Container (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema se trata en la documentación de Visual C++ como un ejemplo funcional de los contenedores utilizados en la biblioteca estándar de C++. Para obtener más información, consulte [contenedores STL](../standard-library/stl-containers.md).  
  
 Describe un objeto que controla una secuencia de longitud variable de elementos, normalmente de tipo **Ty**. La secuencia se almacena en diferentes maneras, dependiendo del contenedor real.  
  
 Una función de constructor o un miembro de contenedor puede encontrar la ocasión para llamar al constructor **Ty**(**const Ty &**) o la función **Ty::operator =**(**const Ty &**). Si esta llamada inicia una excepción, el objeto contenedor está obligado a mantener su integridad y volver a producir cualquier excepción que detecta. Sin riesgos puede intercambiar, asignar a borrar o destruir un objeto contenedor, una vez que se produce una de estas excepciones. En general, sin embargo, de lo contrario, no se puede predecir el estado de la secuencia controlada por el objeto contenedor.  
  
 Algunas advertencias adicionales:  
  
-   Si la expresión **~ Ty** produce una excepción, el estado resultante del objeto contenedor no está definido.  
  
-   Si el contenedor que almacena un objeto de asignador *al*, y *al* produce una excepción distinto de como resultado de una llamada a *al***.allocate**, el estado resultante del objeto contenedor no está definido.  
  
-   Si el contenedor que almacena un objeto de función *comp*, para determinar cómo ordenar la secuencia controlada, y *comp* produce una excepción de cualquier tipo, el estado resultante del objeto contenedor no está definido.  
  
 Las clases de contenedor definidas por STL cumplan varios requisitos adicionales, como se describe en los párrafos siguientes.  
  
 Clase de plantilla contenedor [lista](../standard-library/list-class.md) proporciona un comportamiento determinista y útil, incluso en presencia de las excepciones que se ha descrito anteriormente. Por ejemplo, si se produce una excepción durante la inserción de uno o más elementos, el contenedor permanece inalterado y se vuelve a producir la excepción.  
  
 Para *todos los* las clases de contenedor definidas con STL, si se produce una excepción durante las llamadas a las funciones miembro siguientes:  
  
```  
<A NAME="vclrfcontainerinsert"></A>insert // single element inserted  
<A NAME="vclrfcontainerpushback"></A>push_back  
<A NAME="vclrfcontainerpushfront"></A>push_front  
```  
  
 el contenedor se deja sin modificar y se vuelve a producir la excepción.  
  
 Para *todos los* las clases de contenedor STL definidas, se inicia ninguna excepción durante las llamadas a las funciones miembro siguientes:  
  
```  
<A NAME="vclrfcontainerpopback"></A>pop_back  
<A NAME="vclrfcontainerpopfront"></A>pop_front  
```  
  
 La función miembro [Borrar](../standard-library/container-class-erase.md) produce una excepción sólo si una operación de copia (construcción de asignación o copia) produce una excepción.  
  
 Además, se inicia ninguna excepción durante la copia de un iterador devuelto por una función miembro.  
  
 La función miembro [intercambio](../standard-library/container-class-swap.md) hace promesas adicionales *todos los* clases de contenedor definidas por STL:  
  
-   La función miembro produce una excepción sólo si el contenedor almacena al objeto de asignador, y `al` produce una excepción cuando se copian.  
  
-   Referencias, punteros y los iteradores que designan los elementos de la secuencia controlada colocarse siguen siendo válidos.  
  
 Un objeto de una clase de contenedor STL definida asigna y libera almacenamiento de la secuencia que controla a través de un objeto almacenado de tipo `Alloc`, que normalmente es un parámetro de plantilla. Este tipo de objeto de asignador debe tener la misma interfaz externa como un objeto de clase **allocator \< Ty>**. En particular, `Alloc` debe ser del mismo tipo que **Alloc::rebind \< value_type >:: otros**  
  
 Para *todos los* clases de contenedor definidas por STL, la función miembro **Alloc get_allocator const;** devuelve una copia del objeto de asignador almacenado. Tenga en cuenta que el objeto de asignador almacenado *no* copia cuando se asigna el objeto contenedor. Todos los constructores inicializan el valor almacenado en **asignador**, a `Alloc` Si el constructor no contiene ningún parámetro de asignador.  
  
 Según el estándar de C++, una clase de contenedor STL definida puede asumir que:  
  
-   Todos los objetos de clase `Alloc` comparación igual.  
  
-   Tipo de **Alloc::const_pointer** es el mismo que **const Ty \***.  
  
-   Tipo de **Alloc::const_reference** es el mismo que **const Ty &**.  
  
-   Tipo de **Alloc::pointer** es el mismo que **Ty \***.  
  
-   Tipo de **Alloc::reference** es el mismo que **Ty &**.  
  
 En esta implementación, sin embargo, los contenedores no hace estas premisas simplificación. Por lo tanto, funcionan correctamente con objetos de asignador que son más ambiciosos:  
  
-   Todos los objetos de clase `Alloc` no necesita comparar igual. (Puede mantener varios grupos de almacenamiento).  
  
-   Tipo de **Alloc::const_pointer** no necesita ser el mismo que **const Ty \***. (Un puntero const puede ser una clase).  
  
-   Tipo de **Alloc::pointer** no necesita ser el mismo que **Ty \***. (Un puntero puede ser una clase).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \< contenedor de ejemplo>  
  
## <a name="see-also"></a>Vea también  
 [\< contenedor de ejemplo>](../standard-library/sample-container.md)

