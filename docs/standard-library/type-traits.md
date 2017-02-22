---
title: "&lt;type_traits&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<type_traits>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typetrait (encabezado) [TR1]"
  - "type_traits"
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
caps.latest.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 35
---
# &lt;type_traits&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las plantillas que proporcionan constantes en tiempo de compilación que proporcionan información acerca de las propiedades de sus argumentos de tipo o generar transforman los tipos.  
  
## Sintaxis  
  
```  
#include <type_traits>  
```  
  
## Comentarios  
 Las clases y plantillas de `<type_traits>` se utilizan para admitir la inferencia de tipos, la clasificación y la transformación en tiempo de compilación para detectar errores relacionados con el tipo y que le ayudarán a optimizar el código genérico. Estas clases y las plantillas incluyen unario rasgos de tipos que describen una propiedad de un tipo de rasgos de tipo binario que describen la relación entre los tipos y características de transformación que se modifican una propiedad de un tipo.  
  
 Para admitir características de tipos, una clase auxiliar, `integral_constant`, se define. Tiene especializaciones de plantilla `true_type` y `false_type` que forman las clases base para los predicados de tipo. Un *predicado de tipo* es una plantilla que toma uno o más argumentos de tipo. Cuando un predicado de tipo *contiene true*, se deriva públicamente \(ya sea de forma directa o indirecta\) de [true\_type](../Topic/true_type%20Typedef.md). Cuando un predicado de tipo *contiene false*, se deriva públicamente \(ya sea de forma directa o indirecta\) de [false\_type](../Topic/false_type%20Typedef.md).  
  
 Un *modificador de tipo* o *rasgo de transformación* es una plantilla que toma uno o más argumentos de plantilla y tiene un miembro `type`, que es un sinónimo del tipo modificado.  
  
### Plantillas de alias  
 Para simplificar expresiones de rasgos de tipo, [plantillas de alias](../cpp/aliases-and-typedefs-cpp.md) para `typename some_trait<T>::type` se proporcionan, donde " `some_trait`" es el nombre de clase de plantilla. Por ejemplo, [add\_const](../standard-library/add-const-class.md) tiene una plantilla de alias para su tipo, `add_const_t`, definido como:  
  
```cpp  
template<class T>  
    using add_const_t = typename add_const<T>::type;  
```  
  
|||||  
|-|-|-|-|  
|add\_const\_t|aligned\_storage\_t|make\_signed\_t|remove\_pointer\_t|  
|add\_cv\_t|aligned\_union\_t|make\_unsigned\_t|remove\_reference\_t|  
|add\_lvalue\_reference\_t|common\_type\_t|remove\_all\_extents\_t|remove\_volatile\_t|  
|add\_pointer\_t|conditional\_t|remove\_const\_t|result\_of\_t|  
|add\_rvalue\_reference\_t|decay\_t|remove\_cv\_t|underlying\_type\_t|  
|add\_volatile\_t|enable\_if\_t|remove\_extent\_t||  
  
### Clases  
 Definiciones de tipos y la clase auxiliar  
  
|||  
|-|-|  
|[integral\_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Crea un entero constante de un tipo y un valor.|  
|[true\_type](../Topic/true_type%20Typedef.md)|Contiene la constante integral con valor true.|  
|[false\_type](../Topic/false_type%20Typedef.md)|Contiene la constante integral con valor false.|  
  
 Categorías de tipo principal  
  
|||  
|-|-|  
|[is\_void](../standard-library/is-void-class.md)|Comprueba si el tipo es `void`.|  
|[is\_null\_pointer](../standard-library/is-null-pointer-class.md)|Comprueba si el tipo es `std::nullptr_t`.|  
|[is\_integral](../standard-library/is-integral-class.md)|Comprueba si el tipo es integral.|  
|[is\_floating\_point](../standard-library/is-floating-point-class.md)|Comprueba si el tipo es un punto flotante.|  
|[is\_array](../standard-library/is-array-class.md)|Comprueba si el tipo es una matriz.|  
|[is\_pointer](../standard-library/is-pointer-class.md)|Comprueba si el tipo es un puntero.|  
|[is\_lvalue\_reference](../standard-library/is-lvalue-reference-class.md)|Comprueba si el tipo es una referencia a un valor L.|  
|[is\_rvalue\_reference](../standard-library/is-rvalue-reference-class.md)|Comprueba si el tipo es una referencia a un valor R.|  
|[is\_member\_object\_pointer](../standard-library/is-member-object-pointer-class.md)|Comprueba si el tipo es un puntero a un objeto miembro.|  
|[is\_member\_function\_pointer](../standard-library/is-member-function-pointer-class.md)|Comprueba si el tipo es un puntero a una función miembro.|  
|[is\_enum](../standard-library/is-enum-class.md)|Comprueba si el tipo es una enumeración.|  
|[is\_union](../standard-library/is-union-class.md)|Comprueba si el tipo es una unión.|  
|[is\_class](../standard-library/is-class-class.md)|Comprueba si el tipo es una clase.|  
|[is\_function](../standard-library/is-function-class.md)|Comprueba si el tipo es un tipo de función.|  
  
 Categorías de tipo compuesto  
  
|||  
|-|-|  
|[is\_reference](../standard-library/is-reference-class.md)|Comprueba si el tipo es una referencia.|  
|[is\_arithmetic](../standard-library/is-arithmetic-class.md)|Comprueba si el tipo es aritmético.|  
|[is\_fundamental](../standard-library/is-fundamental-class.md)|Comprueba si el tipo es `void` o aritmético.|  
|[is\_object](../standard-library/is-object-class.md)|Comprueba si el tipo es un tipo de objeto.|  
|[is\_scalar](../standard-library/is-scalar-class.md)|Comprueba si el tipo es escalar.|  
|[is\_compound](../standard-library/is-compound-class.md)|Comprueba si el tipo no es escalar.|  
|[is\_member\_pointer](../standard-library/is-member-pointer-class.md)|Comprueba si el tipo es un puntero a un miembro.|  
  
 Propiedades de tipo  
  
|||  
|-|-|  
|[is\_const](../standard-library/is-const-class.md)|Comprueba si el tipo es `const`.|  
|[is\_volatile](../standard-library/is-volatile-class.md)|Comprueba si el tipo es `volatile`.|  
|[is\_trivial](../standard-library/is-trivial-class.md)|Comprueba si el tipo es trivial.|  
|[is\_trivially\_copyable](../standard-library/is-trivially-copyable-class.md)|Comprueba si el tipo es copiar de forma trivial.|  
|[is\_standard\_layout](../standard-library/is-standard-layout-class.md)|Comprueba si el tipo es un tipo de diseño estándar.|  
|[is\_pod](../standard-library/is-pod-class.md)|Comprueba si el tipo es POD.|  
|[is\_literal\_type](../standard-library/is-literal-type-class.md)|Comprueba si el tipo puede ser un `constexpr` variable o usados en un `constexpr` \(función\).|  
|[is\_empty](../standard-library/is-empty-class.md)|Comprueba si el tipo es una clase vacía.|  
|[is\_polymorphic](../standard-library/is-polymorphic-class.md)|Comprueba si el tipo es una clase polimórfica.|  
|[is\_abstract](../standard-library/is-abstract-class.md)|Comprueba si el tipo es una clase abstracta.|  
|[is\_final](../standard-library/is-final-class.md)|Comprueba si el tipo es un tipo de clase marcado `final`.|  
|[is\_signed](../standard-library/is-signed-class.md)|Comprueba si el tipo es un entero con signo.|  
|[is\_unsigned](../standard-library/is-unsigned-class.md)|Comprueba si el tipo es un entero sin signo.|  
|[is\_constructible](../standard-library/is-constructible-class.md)|Comprueba si el tipo es puede construir con tipos de argumento especificados.|  
|[is\_default\_constructible](../standard-library/is-default-constructible-class.md)|Comprueba si el tipo tiene un constructor predeterminado.|  
|[is\_copy\_constructible](../standard-library/is-copy-constructible-class.md)|Comprueba si el tipo tiene un constructor de copias.|  
|[is\_move\_constructible](../standard-library/is-move-constructible-class.md)|Comprueba si el tipo tiene un constructor de movimiento.|  
|[is\_assignable](../standard-library/is-assignable-class.md)|Comprueba si el primer tipo puede asignarse un valor del segundo tipo.|  
|[is\_copy\_assignable](../standard-library/is-copy-assignable-class.md)|Comprueba si se puede asignar un valor de referencia const del tipo de un tipo.|  
|[is\_move\_assignable](../standard-library/is-move-assignable-class.md)|Comprueba si un tipo se puede asignar una referencia a valor r del tipo.|  
|[is\_destructible](../standard-library/is-destructible-class.md)|Comprueba si el tipo es puedan destruir.|  
|[is\_trivially\_constructible](../standard-library/is-trivially-constructible-class.md)|Comprueba si el tipo no utiliza ninguna operación no trivial cuando se construye utilizando los tipos especificados.|  
|[is\_trivially\_default\_constructible](../standard-library/is-trivially-default-constructible-class.md)|Comprueba si el tipo no utiliza ninguna operación no trivial al construir el valor predeterminado.|  
|[is\_trivially\_copy\_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Comprueba si el tipo no utiliza ninguna operación no trivial al construir la copia.|  
|[is\_trivially\_move\_constructible](../standard-library/is-trivially-move-constructible-class.md)|Comprueba si el tipo no utiliza ninguna operación no trivial al construir el movimiento.|  
|[is\_trivially\_assignable](../standard-library/is-trivially-assignable-class.md)|Comprueba si los tipos asignables y la asignación utiliza ninguna operación no trivial.|  
|[is\_trivially\_copy\_assignable](../standard-library/is-trivially-copy-assignable-class.md)|Comprueba si el tipo no es asignable de copia y la asignación utiliza ninguna operación no trivial.|  
|[is\_trivially\_move\_assignable](../standard-library/is-trivially-move-assignable-class.md)|Comprueba si el tipo no es asignable de movimiento y la asignación utiliza ninguna operación no trivial.|  
|[is\_trivially\_destructible](../standard-library/is-trivially-destructible-class.md)|Comprueba si el tipo es puedan destruir y el destructor no usa ninguna operación no trivial.|  
|[is\_nothrow\_constructible](../standard-library/is-nothrow-constructible-class.md)|Comprueba si el tipo es construir mediante y se sabe que no inician cuando se construye utilizando los tipos especificados.|  
|[is\_nothrow\_default\_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Pruebas si el tipo es default puede construir y se conoce no se produce cuando construido de forma predeterminada.|  
|[is\_nothrow\_copy\_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Comprueba si el tipo es construir mediante copia y se conoce el constructor de copias no se iniciará.|  
|[is\_nothrow\_move\_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Comprueba si el tipo es mover puede construir y se conoce el constructor de movimiento no se iniciará.|  
|[is\_nothrow\_assignable](../standard-library/is-nothrow-assignable-class.md)|Comprueba si el tipo es asignable utilizando el tipo especificado y se conoce la asignación no se iniciará.|  
|[is\_nothrow\_copy\_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Comprueba si el tipo es asignable de copia y se conoce la asignación no se iniciará.|  
|[is\_nothrow\_move\_assignable](../standard-library/is-nothrow-move-assignable-class.md)|Comprueba si el tipo es asignable de movimiento y se conoce la asignación no se iniciará.|  
|[is\_nothrow\_destructible](../standard-library/is-nothrow-destructible-class.md)|Comprueba si el tipo es puedan destruir y se conoce el destructor no se iniciará.|  
|[has\_virtual\_destructor](http://msdn.microsoft.com/es-es/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|Comprueba si el tipo tiene un destructor virtual.|  
  
 Consultas de tipo de propiedad  
  
|||  
|-|-|  
|[alignment\_of](../standard-library/alignment-of-class.md)|Obtiene la alineación de un tipo.|  
|[rank](../standard-library/rank-class.md)|Obtiene el número de dimensiones de matriz.|  
|[extent](../standard-library/extent-class.md)|Obtiene el número de elementos de la dimensión de la matriz especificada.|  
  
 Relaciones de tipo  
  
|||  
|-|-|  
|[is\_same](../standard-library/is-same-class.md)|Comprueba si dos tipos son iguales.|  
|[is\_base\_of](../standard-library/is-base-of-class.md)|Comprueba si un tipo es una base de otro.|  
|[is\_convertible](../standard-library/is-convertible-class.md)|Comprueba si un tipo es convertible en otro.|  
  
 Modificaciones de const y volatile  
  
|||  
|-|-|  
|[add\_const](../standard-library/add-const-class.md)|Genera un `const` tipo de tipo.|  
|[add\_volatile](../standard-library/add-volatile-class.md)|Genera un `volatile` tipo de tipo.|  
|[add\_cv](../standard-library/add-cv-class.md)|Genera un `const``volatile` tipo de tipo.|  
|[remove\_const](../standard-library/remove-const-class.md)|Genera un tipo no const de tipo.|  
|[remove\_volatile](../standard-library/remove-volatile-class.md)|Genera un tipo no volátil de tipo.|  
|[remove\_cv](../standard-library/remove-cv-class.md)|Genera un tipo de no volátil no constantes de tipo.|  
  
 Modificaciones de referencia  
  
|||  
|-|-|  
|[add\_lvalue\_reference](../standard-library/add-lvalue-reference-class.md)|Genera una referencia al tipo de tipo.|  
|[add\_rvalue\_reference](../standard-library/add-rvalue-reference-class.md)|Genera una referencia a valor r al tipo de tipo|  
|[remove\_reference](../standard-library/remove-reference-class.md)|Genera un tipo de referencia no es de tipo.|  
  
 Modificaciones de inicio de sesión  
  
|||  
|-|-|  
|[make\_signed](../standard-library/make-signed-class.md)|Genera el tipo si firma o el tipo menor con signo mayor o igual tamaño al tipo.|  
|[make\_unsigned](../standard-library/make-unsigned-class.md)|Genera el tipo si sin signo o el tipo más pequeño sin signo mayor o igual en tamaño al tipo.|  
  
 Modificaciones de la matriz  
  
|||  
|-|-|  
|[remove\_all\_extents](../standard-library/remove-all-extents-class.md)|Genera un tipo de matriz no es de un tipo de matriz.|  
|[remove\_extent](../standard-library/remove-extent-class.md)|Genera el tipo de elemento de un tipo de matriz.|  
  
 Modificaciones de puntero  
  
|||  
|-|-|  
|[add\_pointer](../standard-library/add-pointer-class.md)|Genera un puntero al tipo de tipo.|  
|[remove\_pointer](../standard-library/remove-pointer-class.md)|Genera un tipo de un puntero al tipo.|  
  
 Otras transformaciones  
  
|||  
|-|-|  
|[aligned\_storage](../standard-library/aligned-storage-class.md)|Asigna memoria sin inicializar para un tipo alineado.|  
|[aligned\_union](../standard-library/aligned-union-class.md)|Asigna memoria sin inicializar para una unión alineada con un destructor o un constructor no trivial.|  
|[common\_type](../standard-library/common-type-class.md)|Genera el tipo común de todos los tipos de paquete de parámetros.|  
|[conditional](../standard-library/conditional-class.md)|Si la condición es true, produce el primer tipo especificado, de lo contrario, el segundo tipo especificado.|  
|[decay](../standard-library/decay-class.md)|Genera el tipo tal y como se pasan por valor. Crea un tipo que no es de referencia, const o volatile, o bien convierte un puntero al tipo.|  
|[enable\_if](../standard-library/enable-if-class.md)|Si la condición es true, no genera el tipo especificado, de lo contrario, ningún tipo.|  
|[result\_of](../standard-library/result-of-class1.md)|Determina el tipo de valor devuelto del tipo que se puede llamar que toma los tipos de argumento especificados.|  
|[underlying\_type](../standard-library/underlying-type-class.md)|Genera el tipo entero subyacente para un tipo de enumeración.|  
  
## Vea también  
 [\<functional\>](../standard-library/functional.md)