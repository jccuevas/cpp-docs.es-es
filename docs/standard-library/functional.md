---
title: "&lt; funcional &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<functional>"
  - "functional/std::<functional>"
  - "std.<functional>"
  - "std::<functional>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "functors"
  - "functional (encabezado)"
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; funcional &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las funciones de biblioteca estándar que ayudan a construir *objetos de función*también denominados functors y sus enlazadores. Un objeto de función es un objeto de un tipo que define `operator()`. Un objeto de función puede ser un puntero a función, pero por lo general el objeto se utiliza para almacenar información adicional a la que se puede tener acceso durante una llamada de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <functional>  
```  
  
## <a name="remarks"></a>Comentarios  
 Los algoritmos necesitan dos tipos de objetos de función: unarios y binarios. Los objetos de función unaria requieren un argumento y los objetos de función binaria requieren dos argumentos. Se pueden pasar un objeto de función y punteros a función como un predicado para un algoritmo, pero los objetos de función también son adaptables y aumentan el ámbito, la flexibilidad y la eficacia de la STL. Por ejemplo, si un valor necesita estar enlazado a una función para que se pueda pasar a un algoritmo, no se puede usar un puntero a función. Los adaptadores de función convierten los punteros a función en objetos de función adaptables que se pueden enlazar a un valor. El encabezado \< funcional> también contiene adaptadores de funciones miembro que permiten llamar como objetos de función adaptables a funciones de miembro. Las funciones son adaptables si tienen declaraciones de tipo anidadas que especifican sus tipos de argumento y de valor devuelto. El estándar de C++ requiere implementar esta adaptabilidad haciendo que todas las clases de objetos estándar hereden de las clases base unary_function o binary_function. Los objetos de función y sus adaptadores permiten que la STL actualice aplicaciones existentes y ayudan a integrar la STL en el entorno de programación de C++.  
  
 El [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] implementación de los objetos de función en \< funcional> incluye *funciones de operador transparentes*, que son especializaciones de estándar de objetos de función y no toman ningún parámetro de plantilla y realizar el reenvío directo de los argumentos de función y la devolución perfecta del resultado. Esta característica forma parte de la especificación del borrador del estándar C++14. Estas especializaciones de plantilla no requieren que se especifiquen tipos de argumentos cuando se invocan funciones de operadores aritméticos, de comparación, lógicos y bit a bit. Se pueden sobrecargar operadores aritméticos, de comparación, lógicos o bit a bit para sus propios tipos, o para combinaciones heterogéneas de tipos, y utilizar después las funciones de operador transparentes como argumentos de función. Por ejemplo, si el tipo *MyType* implementa `operator<`, puede llamar a `sort(my_collection.begin(), my_collection.end(), less<>())` en lugar de especificar explícitamente el tipo `sort(my_collection.begin(), my_collection.end(), less<MyType>())`.  
  
## <a name="c11c14-implementation"></a>Implementación de C++11/C++14  
 Se han agregado las características siguientes en la implementación de Visual C++ de C++11/C++14:  
  
-   Un *signatura de llamada* es el nombre de un tipo de valor devuelto seguido de una lista separada por comas entre paréntesis de cero o más tipos de argumento.  
  
-   A *tipo que se puede llamar* es un puntero a función, un puntero a una función miembro, un puntero a datos de miembro o un tipo de clase cuyos objetos pueden aparecer inmediatamente a la izquierda del operador de llamada de función.  
  
-   Un *objeto que se puede llamar* es un objeto de un tipo que se puede llamar.  
  
-   A *tipo contenedor de llamadas* es un tipo que contiene un objeto que se puede llamar y es compatible con una operación de llamada que reenvía a ese objeto.  
  
-   Un *contenedor de llamadas* es un objeto de un tipo de contenedor de llamadas.  
  
-   Un *objeto de destino* es el objeto que se puede llamar mantenido por un objeto de contenedor de llamadas.  
  
 La pseudofunción `INVOKE(f, t1, t2, ..., tN)` significa una de las cosas siguientes:  
  
- `(t1.*f)(t2, ..., tN)` cuando `f` es un puntero a una función miembro de clase `T` y `t1` es un objeto de tipo `T`, una referencia a un objeto de tipo `T` o una referencia a un objeto de un tipo derivado de `T`.  
  
- `((*t1).*f)(t2, ..., tN)` cuando `f` es un puntero a una función miembro de clase `T` y `t1` no es uno de los tipos descritos en el elemento anterior.  
  
- `t1.*f` cuando N == 1 y `f` es un puntero a datos de miembro de una clase `T` y `t1` es un objeto de tipo `T`, una referencia a un objeto de tipo `T` o una referencia a un objeto de un tipo derivado de `T`.  
  
- `(*t1).*f` cuando N == 1 y `f` es un puntero a datos de miembro de una clase `T` y `t1` no es uno de los tipos descritos en el elemento anterior.  
  
- `f(t1, t2, ..., tN)` en todos los demás casos.  
  
 La pseudofunción `INVOKE(f, t1, t2, ..., tN, R)` significa `INVOKE(f, t1, t2, ..., tN)` convertido implícitamente en `R`.  
  
 Si tiene un contenedor de llamadas un *tipo de resultado débil*, el tipo de su tipo de miembro `result_type` se basa en el tipo de `T` el objeto de destino del contenedor, como se indica a continuación:  
  
-   Si `T` es puntero a función, `result_type` es un sinónimo del tipo de valor devuelto de `T`.  
  
-   Si `T` es puntero a función miembros, `result_type` es un sinónimo para el tipo de valor devuelto de `T`.  
  
-   Si `T` es un tipo de clase que tiene un tipo de miembro `result_type`, `result_type` es un sinónimo de `T::result_type`.  
  
-   De lo contrario, no hay ningún miembro `result_type`.  
  
 Cada contenedor de llamadas tiene un constructor de movimientos y un constructor de copias. Un *contenedor de llamadas simple* es un contenedor de llamadas que tiene una asignación de operador y cuyo constructor de copias, constructor de movimiento y operador de asignación no produce excepciones. Un *contenedor de llamadas de reenvío* es un contenedor de llamadas que se puede llamar mediante una lista de argumentos arbitraria y que entrega los argumentos al objeto contenedor CCW como referencias. Todos los argumentos de valor R se entregan como referencias rvalue y los argumentos de valor L se envían como referencias lvalue.  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[bad_function_call)](../standard-library/bad-function-call-class.md)|Una clase que describe una excepción que se produce para indicar que una llamada a `operator()` en un [función](../standard-library/function-class.md) Error del objeto porque el objeto estaba vacío.|  
|[binary_negate](../standard-library/binary-negate-class.md)|Clase de plantilla que proporciona una función miembro que niega el valor devuelto de una función binaria especificada.|  
|[binder1st](../standard-library/binder1st-class.md)|Clase de plantilla que proporciona un constructor que convierte un objeto de función binaria en un objeto de función unaria enlazando el primer argumento de la función binaria a un valor especificado.|  
|[binder2nd](../standard-library/binder2nd-class.md)|Clase de plantilla que proporciona un constructor que convierte un objeto de función binaria en un objeto de función unaria enlazando el segundo argumento de la función binaria a un valor especificado.|  
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|Clase de adaptadores que permite llamar a una función miembro const que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia.|  
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|Clase de adaptadores que permite llamar a una función miembro const que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de puntero.|  
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|Clase de adaptadores que permite llamar a una función miembro const que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de referencia.|  
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|Clase de adaptadores que permite llamar a una función miembro const que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero.|  
|[(función)](../standard-library/function-class.md)|Clase que contiene un objeto al que se puede llamar.|  
|[hash](hash%20Class.md)|Clase que calcula un código hash para un valor.|  
|[is_bind_expression)](../standard-library/is-bind-expression-class.md)|Clase que prueba si se genera un tipo concreto llamando a `bind`.|  
|[is_placeholder)](../standard-library/is-placeholder-class.md)|Clase que prueba si un tipo determinado es un marcador de posición.|  
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|Una clase de adaptador que permite un **non_const** función miembro que no toma ningún argumento a llamarse como un objeto de función unaria cuando se inicializa con un argumento de referencia.|  
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|Una clase de adaptador que permite un **non_const** función miembro que no toma ningún argumento a llamarse como un objeto de función unaria cuando se inicializa con un argumento de puntero.|  
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|Una clase de adaptador que permite un **non_const** función miembro que toma un único argumento que se pueden llamar como un objeto de función binaria cuando se inicializa con un argumento de referencia.|  
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|Una clase de adaptador que permite un **non_const** función miembro que toma un único argumento que se pueden llamar como un objeto de función binaria cuando se inicializa con un argumento de puntero.|  
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|Convierte un puntero a función binaria en una función binaria adaptable.|  
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|Convierte un puntero a función unaria en una función unaria adaptable.|  
|[reference_wrapper)](../standard-library/reference-wrapper-class.md)|Clase que contiene una referencia.|  
|[result_of)](../standard-library/result-of-class2.md)|Struct que contiene el tipo de valor devuelto de un objeto contenido al que se puede llamar.|  
|[unary_negate](../standard-library/unary-negate-class.md)|Clase de plantilla que proporciona una función miembro que niega el valor devuelto de una función unaria especificada.|  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[enlazar](../Topic/%3Cfunctional%3E%20functions.md#bind_function)|Enlaza argumentos a un objeto al que se puede llamar.|  
|[bind1st](../Topic/%3Cfunctional%3E%20functions.md#bind1st_function)|Función de plantilla auxiliar que crea un adaptador para convertir un objeto de función binaria en un objeto de función unaria enlazando el primer argumento de la función binaria a un valor especificado.|  
|[bind2nd](../Topic/%3Cfunctional%3E%20functions.md#bind2nd_function)|Función de plantilla auxiliar que crea un adaptador para convertir un objeto de función binaria en un objeto de función unaria enlazando el segundo argumento de la función binaria a un valor especificado.|  
|[bit_and)](../Topic/%3Cfunctional%3E%20functions.md#bit_and_function)|Devuelve el AND lógico bit a bit (operador binario&) de los dos parámetros.|  
|[bit_not)](../Topic/%3Cfunctional%3E%20functions.md#bit_not_function)|Devuelve el complemento lógico bit a bit (operador~) del parámetro.|  
|[bit_or)](../Topic/%3Cfunctional%3E%20functions.md#bit_or_function)|Devuelve el operador lógico OR bit a bit (operador &#124;) de los dos parámetros.|  
|[bit_xor)](../Topic/%3Cfunctional%3E%20functions.md#bit_xor_function)|Devuelve el XOR lógico bit a bit (operador ^) de los dos parámetros.|  
|[cref](../Topic/%3Cfunctional%3E%20functions.md#cref_function)|Construye un `reference_wrapper` const a partir de un argumento.|  
|[mem_fn)](../Topic/%3Cfunctional%3E%20functions.md#mem_fn_function)|Genera un contenedor de llamadas simple.|  
|[mem_fun)](../Topic/%3Cfunctional%3E%20functions.md#mem_fun_function)|Funciones de plantilla auxiliar utilizadas para construir adaptadores de objeto de función para las funciones miembro cuando se inicializan con argumentos de puntero.|  
|[mem_fun_ref)](../Topic/%3Cfunctional%3E%20functions.md#mem_fun_ref_function)|Función de plantilla auxiliar utilizada para construir adaptadores de objeto de función para las funciones miembro cuando se inicializan con argumentos de referencia.|  
|[not1](../Topic/%3Cfunctional%3E%20functions.md#not1_function)|Devuelve el complemento de un predicado unario.|  
|[not2](../Topic/%3Cfunctional%3E%20functions.md#not2_function)|Devuelve el complemento de un predicado binario.|  
|[ptr_fun)](../Topic/%3Cfunctional%3E%20functions.md#ptr_fun_function)|Función de plantilla auxiliar utilizada para convertir punteros a funciones unarias y binarias, respectivamente, en funciones unarias y binarias adaptables.|  
|[ref](../Topic/%3Cfunctional%3E%20functions.md#ref_function)|Construye un `reference_wrapper` a partir de un argumento.|  
|[swap](../Topic/%3Cfunctional%3E%20functions.md#swap_function)|Intercambia dos objetos `function`.|  
  
### <a name="structs"></a>Estructuras  
  
|||  
|-|-|  
|[binary_function](../standard-library/binary-function-struct.md)|Clase base vacía que define los tipos que puede heredar la clase derivada que proporciona un objeto de función binaria.|  
|[divide](../standard-library/divides-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación aritmética de división sobre elementos de un tipo de valor especificado.|  
|[equal_to](../standard-library/equal-to-struct.md)|Predicado binario que prueba si un valor de un tipo especificado es igual que otro valor de ese tipo.|  
|[mayor](../standard-library/greater-struct.md)|Predicado binario que prueba si un valor de un tipo especificado es mayor que otro valor de ese tipo.|  
|[greater_equal](../standard-library/greater-equal-struct.md)|Predicado binario que prueba si un valor de un tipo especificado es mayor o igual que otro valor de ese tipo.|  
|[menos](../standard-library/less-struct.md)|Predicado binario que prueba si un valor de un tipo especificado es menor que otro valor de ese tipo.|  
|[less_equal](../standard-library/less-equal-struct.md)|Predicado binario que prueba si un valor de un tipo especificado es menor o igual que otro valor de ese tipo.|  
|[logical_and](../standard-library/logical-and-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación lógica de conjunción sobre elementos de un tipo de valor especificado y prueba si el resultado es verdadero o falso.|  
|[logical_not](../standard-library/logical-not-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación lógica de negación sobre elementos de un tipo de valor especificado y prueba si el resultado es verdadero o falso.|  
|[logical_or](../standard-library/logical-or-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación lógica de disyunción sobre elementos de un tipo de valor especificado y prueba si el resultado es verdadero o falso.|  
|[signo menos](../standard-library/minus-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación aritmética de resta sobre elementos de un tipo de valor especificado.|  
|[módulo](../standard-library/modulus-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación aritmética de módulo sobre elementos de un tipo de valor especificado.|  
|[Multiplica](../standard-library/multiplies-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación aritmética de multiplicación sobre elementos de un tipo de valor especificado.|  
|[negativo](../standard-library/negate-struct.md)|La clase proporciona un objeto de función predefinido que devuelve el valor negativo de un valor de elemento.|  
|[Not_Equal_To](../standard-library/not-equal-to-struct.md)|Predicado binario que prueba si un valor de un tipo especificado no es igual que otro valor de ese tipo.|  
|[signo más](../standard-library/plus-struct.md)|La clase proporciona un objeto de función predefinido que realiza la operación aritmética de suma sobre elementos de un tipo de valor especificado.|  
|[unary_function](../standard-library/unary-function-struct.md)|Clase base vacía que define los tipos que puede heredar la clase derivada que proporciona un objeto de función unaria.|  
  
### <a name="objects"></a>de la empresa  
  
|||  
|-|-|  
|[_1.._M](../standard-library/1-object.md)|Marcadores de posición para argumentos reemplazables.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador ==](../Topic/%3Cfunctional%3E%20operators.md#operator_eq_eq)|No permite la comparación de igualdad de objetos a los que se puede llamar.|  
|[operador! =](../Topic/%3Cfunctional%3E%20operators.md#operator_neq)|No permite la comparación de desigualdad de objetos a los que se puede llamar.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

