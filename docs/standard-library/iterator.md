---
title: "&lt;iterator&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<iterator>"
  - "std.<iterator>"
  - "<iterator>"
  - "iterator/std::<iterator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator (encabezado)"
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# &lt;iterator&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las primitivas de iterador, iteradores predefinidos e iteradores de secuencia, así como varias plantillas auxiliares.  Entre los iteradores predefinidos se incluyen adaptadores de inserción y de inversión.  Hay tres clases de adaptadores de iterador de inserción: frontal, posterior y general.  Proporcionan la semántica de inserción en lugar de la semántica de sobrescritura que los iteradores de funciones miembro contenedoras proporcionan.  
  
## Sintaxis  
  
```  
  
#include <iterator>  
  
```  
  
## Comentarios  
 Los iteradores son una generalización de los punteros; realizan una abstracción de sus requisitos de forma que un programa de C\+\+ puede trabajar con estructuras de datos diferentes de manera uniforme.  Los iteradores actúan como intermediarios entre los contenedores y los algoritmos genéricos.  En lugar de trabajar sobre tipos de datos específicos, los algoritmos se definen para que funcionen sobre un intervalo especificado por un tipo de iterador.  Entonces, el algoritmo puede trabajar con cualquier estructura de datos que satisfaga los requisitos del iterador.  Hay cinco tipos o categorías de iterador, cada uno de los cuales dispone de su propio conjunto de requisitos y de funcionalidad resultante:  
  
-   Salida: desplazamiento hacia delante, puede almacenar pero no recuperar valores, proporcionado por el ostream y el insertador.  
  
-   Entrada: desplazamiento hacia delante, puede recuperar pero no almacenar valores, proporcionado por el istream.  
  
-   Adelante: desplazamiento hacia delante, puede almacenar y recuperar valores.  
  
-   Bidireccional: desplazamiento hacia delante y hacia atrás, puede almacenar y recuperar valores, proporcionado por list, set, multiset, map y multimap.  
  
-   Acceso aleatorio: acceso a los elementos en cualquier orden, puede almacenar y recuperar valores, proporcionado por vector, deque, string y array.  
  
 Los iteradores que tienen mayores requisitos y por tanto tienen un acceso más eficaz a los elementos se pueden usar en lugar de los iteradores con menos requisitos.  Por ejemplo, si se llama a un iterador hacia delante, se puede utilizar en su lugar un iterador de acceso aleatorio.  
  
 Visual Studio ha agregado extensiones a los iteradores de la Biblioteca estándar de C\+\+ para admitir varias situaciones en modo depuración para los iteradores comprobados y no comprobados.  Para obtener más información, vea [Bibliotecas seguras: Biblioteca estándar de C\+\+](../standard-library/safe-libraries-cpp-standard-library.md).  
  
### Funciones  
  
|||  
|-|-|  
|[advance](../Topic/advance.md)|Incrementa un iterador un número especificado de posiciones.|  
|[back\_inserter](../Topic/back_inserter.md)|Crea un iterador que puede insertar elementos en la parte posterior de un contenedor especificado.|  
|[begin](../Topic/begin.md)|Recupera un iterador en el primer elemento de un contenedor especificado.|  
|[cbegin](../Topic/cbegin.md)|Recupera un iterador constante en el primer elemento de un contenedor especificado.|  
|[cend](../Topic/cend.md)|Recupera un iterador constante en el elemento que sigue al último elemento del contenedor especificado.|  
|[distance](../Topic/distance.md)|Determina el número de incrementos entre las posiciones direccionadas por dos iteradores.|  
|[end](../Topic/end.md)|Recupera un iterador en el elemento que sigue al último elemento del contenedor especificado.|  
|[front\_inserter](../Topic/front_inserter.md)|Crea un iterador que puede insertar elementos en la parte delantera de un contenedor especificado.|  
|[inserter](../Topic/inserter.md)|Adaptador de iterador que agrega un nuevo elemento a un contenedor en un punto especificado de inserción.|  
|[make\_checked\_array\_iterator](../Topic/make_checked_array_iterator.md)|Crea un [checked\_array\_iterator](../standard-library/checked-array-iterator-class.md) que pueden usar otros algoritmos. **Note:**  Esta función es una extensión de Microsoft de la Biblioteca estándar de C\+\+.  El código implementado mediante esta función no es portable a los entornos de compilación estándar de C\+\+ que no admiten esta extensión de Microsoft.|  
|[make\_move\_iterator](../Topic/make_move_iterator.md)|Devuelve un iterador de movimiento que contiene el iterador proporcionado como su iterador base almacenado.|  
|[make\_unchecked\_array\_iterator](../Topic/make_unchecked_array_iterator.md)|Crea un [unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md) que pueden usar otros algoritmos. **Note:**  Esta función es una extensión de Microsoft de la Biblioteca estándar de C\+\+.  El código implementado mediante esta función no es portable a los entornos de compilación estándar de C\+\+ que no admiten esta extensión de Microsoft.|  
|[next](../Topic/next.md)|Procesa una iteración un número especificado de veces y devuelve la nueva posición del iterador.|  
|[prev](../Topic/prev.md)|Procesa una iteración en dirección inversa un número especificado de veces y devuelve la nueva posición del iterador.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Citerator%3E\).md)|Comprueba si el objeto iterador del lado izquierdo del operador no es igual que el objeto iterador del lado derecho.|  
|[operator\=\=](../Topic/operator==%20\(%3Citerator%3E\).md)|Comprueba si el objeto iterador del lado izquierdo del operador es igual que el objeto iterador del lado derecho.|  
|[':?'.\<](../Topic/operator%3C%20\(%3Citerator%3E\).md)|Comprueba si el objeto iterador del lado izquierdo del operador es menor que el objeto iterador del lado derecho.|  
|[operator\<\=](../Topic/operator%3C=%20\(%3Citerator%3E\).md)|Comprueba si el objeto iterador del lado izquierdo del operador es menor o igual que el objeto iterador del lado derecho.|  
|[':?'.\>](../Topic/operator%3E%20\(%3Citerator%3E\).md)|Comprueba si el objeto iterador del lado izquierdo del operador es mayor que el objeto iterador del lado derecho.|  
|[operator\>\=](../Topic/operator%3E=%20\(%3Citerator%3E\).md)|Comprueba si el objeto iterador del lado izquierdo del operador es mayor o igual que el objeto iterador del lado derecho.|  
|[operator\+](../Topic/operator+%20\(%3Citerator%3E\).md)|Agrega un desplazamiento a un iterador y devuelve el nuevo `reverse_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|  
|[operator\-](../Topic/operator-%20\(%3Citerator%3E\).md)|Resta un iterador de otro y devuelve la diferencia.|  
  
### Clases  
  
|||  
|-|-|  
|[back\_insert\_iterator](../standard-library/back-insert-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida.  Inserta elementos en un contenedor de tipo **Container**, que tiene acceso a través del objeto **pointer** protegido que almacena denominado contenedor.|  
|[bidirectional\_iterator\_tag](../standard-library/bidirectional-iterator-tag-struct.md)|Clase que proporciona un tipo de valor devuelto para una función **iterator\_category** que representa un iterador bidireccional.|  
|[checked\_array\_iterator](../standard-library/checked-array-iterator-class.md)|Clase que tiene acceso a una matriz mediante un iterador comprobado de acceso aleatorio. **Note:**  Esta clase es una extensión de Microsoft de la Biblioteca estándar de C\+\+.  El código implementado mediante esta función no es portable a los entornos de compilación estándar de C\+\+ que no admiten esta extensión de Microsoft.|  
|[forward\_iterator\_tag](../standard-library/forward-iterator-tag-struct.md)|Clase que proporciona un tipo de valor devuelto para una función **iterator\_category** que representa un iterador hacia delante.|  
|[front\_insert\_iterator](../standard-library/front-insert-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida.  Inserta elementos en un contenedor de tipo **Container**, que tiene acceso a través del objeto **pointer** protegido que almacena denominado contenedor.|  
|[input\_iterator\_tag](../standard-library/input-iterator-tag-struct.md)|Clase que proporciona un tipo de valor devuelto para una función **iterator\_category** que representa un iterador de entrada.|  
|[insert\_iterator](../standard-library/insert-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida.  Inserta elementos en un contenedor de tipo **Container**, que tiene acceso a través del objeto **pointer** protegido que almacena denominado contenedor.  También almacena el objeto **iterador** protegido, de clase **Container::iterator**, denominado **iter**.|  
|[istream\_iterator](../standard-library/istream-iterator-class.md)|La clase de plantilla describe un objeto iterador de entrada.  Extrae objetos de clase **Ty** de un flujo de entrada, al que tiene acceso a través de un objeto que almacena, de tipo puntero a `basic_istream`\<**Elem**, **Tr**\>.|  
|[istreambuf\_iterator](../standard-library/istreambuf-iterator-class.md)|La clase de plantilla describe un objeto iterador de entrada.  Inserta elementos de clase **Elem** en un búfer de flujo de salida, al que tiene acceso mediante un objeto que almacena, de tipo **puntero** a `basic_streambuf`\<**Elem**, **Tr**\>.|  
|[iterator](../standard-library/iterator-struct.md)|La clase de plantilla se usa como tipo base para todos los iteradores.|  
|[iterator\_traits](../standard-library/iterator-traits-struct.md)|Clase de plantilla auxiliar que proporciona los tipos críticos asociados a diferentes tipos de iterador para que se pueda hacer referencia a ellos de la misma manera.|  
|[move\_iterator](../standard-library/move-iterator-class.md)|Un objeto `move_iterator` almacena un iterador de acceso aleatorio de tipo `RandomIterator`.  Se comporta como un iterador de acceso aleatorio, excepto cuando se desreferencia.  El resultado de `operator*` se convierte implícitamente a `value_type&&:` para crear `rvalue reference`.|  
|[ostream\_iterator](../standard-library/ostream-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida.  Inserta objetos de clase **Type** en un flujo de salida, al que tiene acceso mediante un objeto que almacena, de tipo **puntero** a `basic_ostream`\<**Elem**, **Tr**\>.|  
|[ostreambuf\_iterator](../standard-library/ostreambuf-iterator-class.md)|La clase de plantilla describe un objeto iterador de salida.  Inserta elementos de clase **Elem** en un búfer de flujo de salida, al que tiene acceso mediante un objeto que almacena, de tipo puntero a `basic_streambuf`\<**Elem**, **Tr**\>.|  
|[output\_iterator\_tag](../standard-library/output-iterator-tag-struct.md)|Clase que proporciona un tipo de valor devuelto para una función **iterator\_category** que representa un iterador de salida.|  
|[random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md)|Clase que proporciona un tipo de valor devuelto para una función **iterator\_category** que representa un iterador de acceso aleatorio.|  
|[reverse\_iterator](../standard-library/reverse-iterator-class.md)|La clase de plantilla describe un objeto que se comporta como un iterador de acceso aleatorio, solo en orden inverso.|  
|[unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md)|Clase que tiene acceso a una matriz mediante un iterador no comprobado de acceso aleatorio. **Note:**  Esta clase es una extensión de Microsoft de la Biblioteca estándar de C\+\+.  El código implementado mediante esta función no es portable a los entornos de compilación estándar de C\+\+ que no admiten esta extensión de Microsoft.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)