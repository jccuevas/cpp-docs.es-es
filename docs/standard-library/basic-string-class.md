---
title: "basic_string (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_string"
  - "std::basic_string"
  - "basic_string"
  - "xstring/std::basic_string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_string (clase)"
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_string (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las secuencias controladas por un objeto de clase de plantilla `basic_string` son la clase de cadena de C\+\+ estándar y se suelen llamar “cadenas”, pero no se deben confundir con las cadenas de estilo C terminadas en null que se utilizan en toda la biblioteca estándar de C\+\+.  La cadena de C\+\+ estándar es un contenedor que permite usar cadenas como tipos normales: por ejemplo, las operaciones de comparación y concatenación, los iteradores, los algoritmos STL y la copia y la asignación con la memoria administrada del asignador de clases.  Si necesita convertir una cadena de C\+\+ estándar en una cadena de estilo C terminada en null, utilice el miembro[basic\_string::c\_str](../Topic/basic_string::c_str.md).  
  
## Sintaxis  
  
```  
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>> class basic_string;  
```  
  
#### Parámetros  
 `CharType`  
 El tipo de datos de un carácter único que se almacenará en la cadena.  La biblioteca estándar de C\+\+ proporciona especializaciones de esta clase de plantilla, con las definiciones de tipo [string](../Topic/string%20\(C++%20STL%20%3Cstring%3E\).md) para elementos de tipo `char`, [wstring](../Topic/wstring.md) para `wchar_t`, [u16string](../Topic/u16string.md) para `char16_t` y [u32string](../Topic/u32string.md) para `char32_t`.  
  
 `Traits`  
 La clase **Traits** describe diversas propiedades importantes de los elementos **CharType** de una especialización de basic\_string.  El valor predeterminado es `char_traits`\<`CharType`\>.  
  
 `Allocator`  
 El tipo que representa el objeto asignador almacenado que encapsula los detalles sobre la asignación y la desasignación de memoria de la cadena.  El valor predeterminado es **allocator**\<`CharType`\>.  
  
### Constructores  
  
|||  
|-|-|  
|[basic\_string](../Topic/basic_string::basic_string.md)|Crea una cadena que está vacía, que inicializan caracteres específicos o que es una copia total o parcial de algún otro objeto de cadena o alguna otra cadena de C.|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_string::allocator_type.md)|Tipo que representa la clase `allocator` para un objeto de cadena.|  
|[const\_iterator](../Topic/basic_string::const_iterator.md)|Tipo que proporciona un iterador de acceso aleatorio que puede acceder a un elemento `const` de la cadena y leerlo.|  
|[const\_pointer](../Topic/basic_string::const_pointer.md)|Tipo que proporciona un puntero a un elemento `const` de una cadena.|  
|[const\_reference](../Topic/basic_string::const_reference.md)|Tipo que proporciona una referencia a un elemento `const` almacenado en una cadena para leer y realizar operaciones de `const`.|  
|[const\_reverse\_iterator](../Topic/basic_string::const_reverse_iterator.md)|Tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento `const` de la cadena.|  
|[difference\_type](../Topic/basic_string::difference_type.md)|Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos de la misma cadena.|  
|[iterator](../Topic/basic_string::iterator.md)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de una cadena.|  
|[npos](../Topic/basic_string::npos.md)|Un valor integral sin signo que se inicializa en –1 e indica “no se encontró” o “todos los caracteres restantes” cuando se produce un error en una función de búsqueda.|  
|[puntero](../Topic/basic_string::pointer.md)|Tipo que proporciona un puntero a un elemento de carácter de una cadena o una matriz de caracteres.|  
|[reference](../Topic/basic_string::reference.md)|Tipo que proporciona una referencia a un elemento almacenado en una cadena.|  
|[reverse\_iterator](../Topic/basic_string::reverse_iterator.md)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar un elemento de una cadena invertida.|  
|[size\_type](../Topic/basic_string::size_type.md)|Tipo entero sin signo para el número de elementos de una cadena.|  
|[traits\_type](../Topic/basic_string::traits_type.md)|Tipo de los rasgos de carácter de los elementos almacenados en una cadena.|  
|[value\_type](../Topic/basic_string::value_type.md)|Tipo que representa el tipo de caracteres que se almacenan en una cadena.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[append](../Topic/basic_string::append.md)|Agrega caracteres al final de una cadena.|  
|[assign](../Topic/basic_string::assign.md)|Asigna nuevos valores de caracteres al contenido de una cadena.|  
|[at](../Topic/basic_string::at.md)|Devuelve una referencia al elemento situado en una ubicación especificada de la cadena.|  
|[back](../Topic/basic_string::back.md)||  
|[begin](../Topic/basic_string::begin.md)|Devuelve un iterador que dirige al primer elemento de la cadena.|  
|[c\_str](../Topic/basic_string::c_str.md)|Convierte el contenido de una cadena en una cadena de estilo C terminada en null.|  
|[capacity](../Topic/basic_string::capacity.md)|Devuelve el número máximo de elementos que podrían almacenarse en una cadena sin aumentar la asignación de memoria de la cadena.|  
|[cbegin](../Topic/basic_string::cbegin.md)|Devuelve un iterador constante que dirige al primer elemento de la cadena.|  
|[cend](../Topic/basic_string::cend.md)|Devuelve un iterador constante que dirige a la ubicación que sigue al último elemento de una cadena.|  
|[clear](../Topic/basic_string::clear.md)|Borra todos los elementos de una cadena.|  
|[compare](../Topic/basic_string::compare.md)|Compara una cadena con una cadena especificada para determinar si las dos cadenas son iguales o si una es lexicográficamente menor que la otra.|  
|[copy](../Topic/basic_string::copy.md)|Copia, como máximo, un número especificado de caracteres de una posición indexada de una cadena de origen a una matriz de caracteres de destino.  Desusado.  Utilice [basic\_string::\_Copy\_s](../Topic/basic_string::_Copy_s.md) en su lugar.|  
|[crbegin](../Topic/basic_string::crbegin.md)|Devuelve un iterador constante que dirige al primer elemento de una cadena invertida.|  
|[crend](../Topic/basic_string::crend.md)|Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una cadena invertida.|  
|[\_Copy\_s](../Topic/basic_string::_Copy_s.md)|Copia, como máximo, un número especificado de caracteres de una posición indexada de una cadena de origen a una matriz de caracteres de destino.|  
|[datos](../Topic/basic_string::data.md)|Convierte el contenido de una cadena en una matriz de caracteres.|  
|[empty](../Topic/basic_string::empty.md)|Comprueba si la cadena contiene caracteres.|  
|[end](../Topic/basic_string::end.md)|Devuelve un iterador que dirige a la ubicación siguiente al último elemento de una cadena.|  
|[erase](../Topic/basic_string::erase.md)|Quita un elemento o un intervalo de elementos de una cadena de una posición especificada.|  
|[find](../Topic/basic_string::find.md)|Busca hacia delante en una cadena la primera aparición de una subcadena que coincide con una secuencia especificada de caracteres.|  
|[find\_first\_not\_of](../Topic/basic_string::find_first_not_of.md)|Busca en una cadena el primer carácter que no es ningún elemento de una cadena especificada.|  
|[find\_first\_of](../Topic/basic_string::find_first_of.md)|Busca en una cadena el primer carácter que coincide con algún elemento de una cadena especificada.|  
|[find\_last\_not\_of](../Topic/basic_string::find_last_not_of.md)|Busca en una cadena el último carácter que no es ningún elemento de una cadena especificada.|  
|[find\_last\_of](../Topic/basic_string::find_last_of.md)|Busca en una cadena el último carácter que es un elemento de una cadena especificada.|  
|[front](../Topic/basic_string::front.md)|Devuelve una referencia al primer elemento de una cadena.|  
|[get\_allocator](../Topic/basic_string::get_allocator.md)|Devuelve una copia del objeto `allocator` que se usa para construir la cadena.|  
|[insert](../Topic/basic_string::insert.md)|Inserta un elemento, varios elementos o un intervalo de elementos en la cadena en una posición especificada.|  
|[length](../Topic/basic_string::length.md)|Devuelve el número actual de elementos de una cadena.|  
|[max\_size](../Topic/basic_string::max_size.md)|Devuelve el número máximo de caracteres que puede contener una cadena.|  
|[pop\_back](../Topic/basic_string::pop_back.md)|Borra el último elemento de la cadena.|  
|[push\_back](../Topic/basic_string::push_back.md)|Agrega un elemento al final de la cadena.|  
|[rbegin](../Topic/basic_string::rbegin.md)|Devuelve un iterador al primer elemento de una cadena invertida.|  
|[rend](../Topic/basic_string::rend.md)|Devuelve un iterador que apunta al lugar inmediatamente posterior al último elemento de una cadena invertida.|  
|[replace](../Topic/basic_string::replace.md)|Reemplaza los elementos de una cadena situados en la posición especificada por los caracteres especificados o los caracteres copiados de otros intervalos, cadenas o cadenas de C.|  
|[reserve](../Topic/basic_string::reserve.md)|Configura la capacidad de la cadena con un número que es, al menos, tan alto como un número especificado.|  
|[resize](../Topic/basic_string::resize.md)|Especifica un nuevo tamaño para una cadena y anexa o borra elementos según sea necesario.|  
|[rfind](../Topic/basic_string::rfind.md)|Busca hacia atrás en una cadena la primera aparición de una subcadena que coincide con una secuencia especificada de caracteres.|  
|[shrink\_to\_fit](../Topic/basic_string::shrink_to_fit.md)|Descarta el exceso de capacidad de la cadena.|  
|[size](../Topic/basic_string::size.md)|Devuelve el número actual de elementos de una cadena.|  
|[substr](../Topic/basic_string::substr.md)|Copia una subcadena de, como máximo, un número de caracteres de una cadena, empezando desde la posición especificada.|  
|[swap](../Topic/basic_string::swap.md)|Intercambie el contenido de dos cadenas.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\+\=](../Topic/basic_string::operator+=.md)|Anexa caracteres a una cadena.|  
|[operador \=](../Topic/basic_string::operator=.md)|Asigna nuevos valores de caracteres al contenido de una cadena.|  
|[operator&#91;&#93;](../Topic/basic_string::operator.md)|Proporciona una referencia al carácter de una cadena que tiene el índice especificado.|  
  
## Comentarios  
 Si se pide a una función que genere una secuencia de más de [max\_size](../Topic/basic_string::max_size.md) elementos, la función informa de un error de longitud lanzando un objeto del tipo [length\_error](../standard-library/length-error-class.md).  
  
 Las referencias, los punteros y los iteradores que designan los elementos de la secuencia controlada pueden perder su validez después de que se realice una llamada a una función que modifique la secuencia controlada o después de la primera llamada a una función miembro no **const**.  
  
## Requisitos  
 **Encabezado:** \<string\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<string\>](../standard-library/string.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)