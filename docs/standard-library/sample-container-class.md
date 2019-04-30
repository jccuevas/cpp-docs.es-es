---
title: Sample Container (Clase)
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: dbfa076756b9e4829898d38e0277ad90106ba579
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410998"
---
# <a name="sample-container-class"></a>Sample Container (Clase)

> [!NOTE]
> Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).

Describe un objeto que controla una secuencia de longitud variable de elementos, normalmente de tipo `Ty`. La secuencia se almacena de diferentes maneras, dependiendo del contenedor real.

Un constructor de contenedor o una función miembro puede encontrar la ocasión de llamar al constructor **Ty**(**const Ty&**) o la función **Ty::operator=**(**const Ty&**). Si esta llamada inicia una excepción, el objeto contenedor está obligado a mantener su integridad y reiniciar cualquier excepción que detecte. Puede intercambiar, asignar, borrar o destruir un objeto contenedor de forma segura después de que inicie una de estas excepciones. Pero en general, no hay otra forma de predecir el estado de la secuencia controlada por el objeto contenedor.

Algunas advertencias adicionales:

- Si la expresión `~Ty` inicia una excepción, el estado resultante del objeto contenedor no está definido.

- Si el contenedor almacena un objeto de asignador *al*, y *al* produce una excepción distinto como resultado de una llamada a `al.allocate`, el estado resultante del objeto contenedor no está definido.

- Si el contenedor almacena un objeto de función *comp*, para determinar cómo ordenar la secuencia controlada, y *comp* inicia una excepción de cualquier tipo, el estado resultante del objeto contenedor no está definido.

Las clases de contenedor definidas por la biblioteca estándar de C++ cumplen varios requisitos adicionales, como se describe en los párrafos siguientes.

La clase de plantilla contenedor [list](../standard-library/list-class.md) proporciona un comportamiento determinista y útil, incluso en presencia de las excepciones descritas anteriormente. Por ejemplo, si se inicia una excepción durante la inserción de uno o más elementos, el contenedor permanece inalterado y se reinicia la excepción.

Para *todas* las clases de contenedor definidas por la biblioteca estándar de C++, si se produce una excepción durante las llamadas a las siguientes funciones de miembro, `insert`, `push_back`, o `push_front`, el contenedor se deja sin modificar y el se vuelve a producir la excepción.

Para *todas* las clases de contenedor definidas por la biblioteca estándar de C++, se produce ninguna excepción durante las llamadas a las funciones miembro siguientes: `pop_back`, `pop_front`.

la función miembro [erase](../standard-library/container-class-erase.md) inicia una excepción solo si una operación de copia (construcción de asignación o copia) inicia una excepción.

Además, no se inicia ninguna excepción durante la copia de un iterador devuelto por una función miembro.

La función miembro [swap](../standard-library/container-class-swap.md) hace promesas adicionales para *todas* las clases de contenedor definidas por la biblioteca estándar de C++:

- La función miembro inicia una excepción solo si el contenedor almacena un objeto de asignador al, y `al` inicia una excepción cuando se copia.

- Las referencias, los punteros y los iteradores que designan elementos de las secuencias controladas que se intercambia siguen siendo válidos.

Un objeto de una clase de contenedor definida por la biblioteca estándar de C++ asigna y libera almacenamiento de la secuencia que controla a través de un objeto almacenado de tipo `Alloc`, que normalmente es un parámetro de plantilla. Este tipo de objeto de asignador debe tener la misma interfaz externa que un objeto de clase `allocator<Ty>`. En concreto, `Alloc` debe ser del mismo tipo que `Alloc::rebind<value_type>::other`

Para *todas* clases de contenedor definidas por la biblioteca estándar de C++, la función miembro `Alloc get_allocator const;` devuelve una copia del objeto de asignador almacenado. Tenga en cuenta que el objeto de asignador almacenado *no* se copia cuando se asigna el objeto contenedor. Todos los constructores inicializan el valor almacenado en `allocator`a `Alloc` si el constructor no contiene ningún parámetro de asignador.

Según el estándar de C++, una clase de contenedor definida por la biblioteca estándar de C++ puede asumir que:

- Todos los objetos de la clase `Alloc` se comparan igual.

- Tipo `Alloc::const_pointer` es el mismo que `const Ty *`.

- Tipo `Alloc::const_reference` es el mismo que `const Ty&`.

- Tipo `Alloc::pointer` es el mismo que `Ty *`.

- Tipo `Alloc::reference` es el mismo que `Ty&`.

Pero en esta implementación, los contenedores no hacen estas suposiciones tan simples. Por tanto, funcionan correctamente con objetos de asignador que son más ambiciosos:

- No es necesario que todos los objetos de la clase `Alloc` se comparen igual. (Puede mantener varios grupos de almacenamiento).

- Tipo `Alloc::const_pointer` no debe ser el mismo que `const Ty *`. (Un puntero const puede ser una clase).

- Tipo `Alloc::pointer` no debe ser el mismo que `Ty *`. (Un puntero puede ser una clase).

## <a name="requirements"></a>Requisitos

**Encabezado**: \<contenedor de ejemplo>

## <a name="see-also"></a>Vea también

[\<sample container>](../standard-library/sample-container.md)<br/>
