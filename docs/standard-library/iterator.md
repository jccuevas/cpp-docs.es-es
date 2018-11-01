---
title: '&lt;iterator&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: 1582f6167d8aae3a9d5a318726cc7404c7e1ea62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640367"
---
# <a name="ltiteratorgt"></a>&lt;iterator&gt;

Define las primitivas de iterador, iteradores predefinidos e iteradores de secuencia, así como varias plantillas auxiliares. Entre los iteradores predefinidos se incluyen adaptadores de inserción y de inversión. Hay tres clases de adaptadores de iterador de inserción: frontal, posterior y general. Proporcionan la semántica de inserción en lugar de la semántica de sobrescritura que los iteradores de funciones miembro contenedoras proporcionan.

## <a name="syntax"></a>Sintaxis

```cpp
#include <iterator>

```

## <a name="remarks"></a>Comentarios

Los iteradores son una generalización de los punteros; realizan una abstracción de sus requisitos de forma que un programa de C++ puede trabajar con estructuras de datos diferentes de manera uniforme. Los iteradores actúan como intermediarios entre los contenedores y los algoritmos genéricos. En lugar de trabajar sobre tipos de datos específicos, los algoritmos se definen para que funcionen sobre un intervalo especificado por un tipo de iterador. Entonces, el algoritmo puede trabajar con cualquier estructura de datos que satisfaga los requisitos del iterador. Hay cinco tipos o categorías de iterador, cada uno de los cuales dispone de su propio conjunto de requisitos y de funcionalidad resultante:

- Salida: desplazamiento hacia delante, puede almacenar pero no recuperar valores, proporcionado por el ostream y el insertador.

- Entrada: desplazamiento hacia delante, puede recuperar pero no almacenar valores, proporcionado por el istream.

- Adelante: desplazamiento hacia delante, puede almacenar y recuperar valores.

- Bidireccional: desplazamiento hacia delante y hacia atrás, puede almacenar y recuperar valores, proporcionado por list, set, multiset, map y multimap.

- Acceso aleatorio: acceso a los elementos en cualquier orden, puede almacenar y recuperar valores, proporcionado por vector, deque, string y array.

Los iteradores que tienen mayores requisitos y por tanto tienen un acceso más eficaz a los elementos se pueden usar en lugar de los iteradores con menos requisitos. Por ejemplo, si se llama a un iterador hacia delante, se puede utilizar en su lugar un iterador de acceso aleatorio.

Visual Studio ha agregado extensiones a los iteradores de la Biblioteca estándar de C++ para admitir varias situaciones en modo depuración para los iteradores comprobados y no comprobados. Para obtener más información, vea [Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[advance](../standard-library/iterator-functions.md#advance)|Incrementa un iterador un número especificado de posiciones.|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|Crea un iterador que puede insertar elementos en la parte posterior de un contenedor especificado.|
|[begin](../standard-library/iterator-functions.md#begin)|Recupera un iterador en el primer elemento de un contenedor especificado.|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|Recupera un iterador constante en el primer elemento de un contenedor especificado.|
|[cend](../standard-library/iterator-functions.md#cend)|Recupera un iterador constante en el elemento que sigue al último elemento del contenedor especificado.|
|[distance](../standard-library/iterator-functions.md#distance)|Determina el número de incrementos entre las posiciones direccionadas por dos iteradores.|
|[end](../standard-library/iterator-functions.md#end)|Recupera un iterador en el elemento que sigue al último elemento del contenedor especificado.|
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|Crea un iterador que puede insertar elementos en la parte delantera de un contenedor especificado.|
|[inserter](../standard-library/iterator-functions.md#inserter)|Adaptador de iterador que agrega un nuevo elemento a un contenedor en un punto especificado de inserción.|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|Crea un [checked_array_iterator](../standard-library/checked-array-iterator-class.md) que pueden usar otros algoritmos. **Nota:** Esta función es una extensión de Microsoft de la biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|Devuelve un iterador de movimiento que contiene el iterador proporcionado como su iterador base almacenado.|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|Crea un [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) que pueden usar otros algoritmos. **Nota:** Esta función es una extensión de Microsoft de la biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.|
|[next](../standard-library/iterator-functions.md#next)|Procesa una iteración un número especificado de veces y devuelve la nueva posición del iterador.|
|[prev](../standard-library/iterator-functions.md#prev)|Procesa una iteración en dirección inversa un número especificado de veces y devuelve la nueva posición del iterador.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator!=](../standard-library/iterator-operators.md#op_neq)|Comprueba si el objeto iterador del lado izquierdo del operador no es igual que el objeto iterador del lado derecho.|
|[operator==](../standard-library/iterator-operators.md#op_eq_eq)|Comprueba si el objeto iterador del lado izquierdo del operador es igual que el objeto iterador del lado derecho.|
|[operator<](../standard-library/iterator-operators.md#op_lt)|Comprueba si el objeto iterador del lado izquierdo del operador es menor que el objeto iterador del lado derecho.|
|[operator\<=](../standard-library/iterator-operators.md#op_gt_eq)|Comprueba si el objeto iterador del lado izquierdo del operador es menor o igual que el objeto iterador del lado derecho.|
|[operator>](../standard-library/iterator-operators.md#op_gt)|Comprueba si el objeto iterador del lado izquierdo del operador es mayor que el objeto iterador del lado derecho.|
|[operator>=](../standard-library/iterator-operators.md#op_gt_eq)|Comprueba si el objeto iterador del lado izquierdo del operador es mayor o igual que el objeto iterador del lado derecho.|
|[operator+](../standard-library/iterator-operators.md#op_add)|Agrega un desplazamiento a un iterador y devuelve el nuevo `reverse_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|
|[operator-](../standard-library/iterator-operators.md#operator-)|Resta un iterador de otro y devuelve la diferencia.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida. Inserta elementos en un contenedor de tipo `Container`, que se accede mediante protegido `pointer` objeto que almacena denominado contenedor.|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|Una clase que proporciona un tipo de valor devuelto para un `iterator_category` función que representa un iterador bidireccional.|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|Clase que tiene acceso a una matriz mediante un iterador comprobado de acceso aleatorio. **Nota:** Esta clase es una extensión de Microsoft de la biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|Una clase que proporciona un tipo de valor devuelto para un `iterator_category` función que representa un iterador hacia delante.|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida. Inserta elementos en un contenedor de tipo `Container`, que se accede mediante protegido `pointer` objeto que almacena denominado contenedor.|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|Una clase que proporciona un tipo de valor devuelto para un `iterator_category` función que representa un iterador de entrada.|
|[insert_iterator](../standard-library/insert-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida. Inserta elementos en un contenedor de tipo `Container`, que se accede mediante protegido `pointer` objeto que almacena denominado contenedor. También almacena protegido `iterator` objeto de clase `Container::iterator`, llamado `iter`.|
|[istream_iterator](../standard-library/istream-iterator-class.md)|La clase de plantilla describe un objeto iterador de entrada. Extrae objetos de clase `Ty` desde un flujo de entrada, que se accede mediante un objeto que almacena, de tipo puntero a `basic_istream` \< **Elem**, **Tr**>.|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|La clase de plantilla describe un objeto iterador de entrada. Inserta elementos de la clase `Elem` en un búfer de secuencia de salida, que tiene acceso a través de un objeto que almacena, de tipo `pointer` a `basic_streambuf` \< **Elem**, **Tr** >.|
|[iterator](../standard-library/iterator-struct.md)|La clase de plantilla se usa como tipo base para todos los iteradores.|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|Clase de plantilla del asistente que proporciona los tipos críticos asociados a diferentes tipos de iterador para que se pueda hacer referencia a ellos de la misma manera.|
|[move_iterator](../standard-library/move-iterator-class.md)|Un objeto `move_iterator` almacena un iterador de acceso aleatorio de tipo `RandomIterator`. Se comporta como un iterador de acceso aleatorio, excepto cuando se desreferencia. El resultado de `operator*` se convierte implícitamente a `value_type&&:` para crear `rvalue reference`.|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida. Inserta objetos de clase `Type` en un flujo de salida, que tiene acceso a través de un objeto que almacena, de tipo `pointer` a `basic_ostream` \< **Elem**, **Tr**>.|
|[ostreambuf_iterator (Clase)](../standard-library/ostreambuf-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida. Inserta elementos de la clase `Elem` en un búfer de secuencia de salida, que se accede mediante un objeto que almacena, de tipo puntero a `basic_streambuf` \< **Elem**, **Tr**>.|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|Una clase que proporciona un tipo de valor devuelto para `iterator_category` función que representa un iterador de salida.|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|Una clase que proporciona un tipo de valor devuelto para `iterator_category` función que representa un iterador de acceso aleatorio.|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|La clase de plantilla describe un objeto que se comporta como un iterador de acceso aleatorio, solo en orden inverso.|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|Clase que tiene acceso a una matriz mediante un iterador no comprobado de acceso aleatorio. **Nota:** Esta clase es una extensión de Microsoft de la biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
