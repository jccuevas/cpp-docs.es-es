---
title: "Compatibilidad con las caracter&#237;sticas de C++11/14/17 (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: dd2d5cbc-caf5-4a11-a057-8c365decba4e
caps.latest.revision: 59
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con las caracter&#237;sticas de C++11/14/17 (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explican las características de C\+\+11\/14\/17 en Visual C\+\+.  
  
##  <a name="top"></a> En este artículo  
  
-   [Lista de características de C++](#featurelist)  
  
    -   [Tabla de características principales del lenguaje C++11](#corelanguagetable)  
  
    -   [Tabla de características principales del lenguaje C++11: simultaneidad](#concurrencytable)  
  
    -   [Características principales del lenguaje C++11: C99](#c99table)  
  
-   [Características principales del lenguaje C++14](#cpp14table)  
  
-   [Características principales propuestas del lenguaje C++17](#cpp17table)  
  
-   [Guía para las tablas de características](#tableguide)  
  
    -   [Referencias a valor R](#rvref)  
  
    -   [Lambdas](#lambdas)  
  
    -   [decltype](#decltype)  
  
    -   [Enumeraciones fuertemente tipadas y declaradas por adelantado](#stronglytyped)  
  
    -   [Alineación](#alignment)  
  
    -   [Tipos de diseño estándar y triviales](#standardlayout)  
  
    -   [Funciones establecidas como valor predeterminado y funciones eliminadas](#defaultedanddeleted)  
  
    -   [override y final](#overrideandfinal)  
  
    -   [Tipos atómicos y más](#atomics)  
  
    -   [__func__ y reglas de preprocesador de C99](#c99)  
  
-   [Características de la biblioteca estándar](#stl)  
  
##  <a name="featurelist"></a> Lista de características de C\+\+  
 Visual C\+\+ implementa la mayoría de las características de la [especificación principal del lenguaje C\+\+11](http://go.microsoft.com/fwlink/p/?LinkID=235092), así como muchas características de la biblioteca de C\+\+14 y algunas de las características propuestas para C\+\+17. En la tabla siguiente se enumeran las características principales del lenguaje C\+\+11\/14\/17 y su estado de implementación para Visual C\+\+ en Visual Studio 2010, [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] y [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], y en Visual Studio 2015.  
  
###  <a name="corelanguagetable"></a> Tabla de características principales del lenguaje C\+\+11  
  
|[Características principales del lenguaje C\+\+11](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2869.html)|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|----------------------------------------------------------------------------------------------------------------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|Referencias a valor R [v0.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1610.html), [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n2118.html), [v2.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2844.html), [v2.1](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html), [v3.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3053.html)|v2.0|v2.1\*|v2.1\*|v3.0|  
|[Calificadores de referencias](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2439.htm)|No|No|No|Sí|  
|[Inicializadores de miembros de datos no estáticos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2756.htm)|No|No|[Sí](../cpp/uniform-initialization-and-delegating-constructors.md)|Sí|  
|Plantillas variádicas [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2242.pdf), [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2555.pdf)|No|No|[Sí](../cpp/ellipses-and-variadic-templates.md)|Sí|  
|[Listas de inicializadores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2672.htm)|No|No|[Sí](../cpp/uniform-initialization-and-delegating-constructors.md)|Sí|  
|[static\_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1720.html)|Sí|Sí|Sí|Sí|  
|auto [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1984.pdf), [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2546.htm)|v1.0|v1.0|v1.0|Sí|  
|[Tipos de valor devueltos finales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2541.htm)|Sí|Sí|Sí|Sí|  
|Lambdas [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2550.pdf), [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2658.pdf), [v1.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2927.pdf)|v1.0|v1.1|v1.1|Sí|  
|decltype [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2343.pdf), [v1.1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3276.pdf)|v1.0|v1.1\*\*|v1.1|Sí|  
|[Corchetes angulares de cierre](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1757.html)|Sí|Sí|Sí|Sí|  
|[Argumentos predeterminados para plantillas de funciones](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html)|No|No|Sí|Sí|  
|[Expresión SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|No|No|No|No|  
|[Plantillas de alias](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2258.pdf)|No|No|[Sí](../cpp/aliases-and-typedefs-cpp.md)|Sí|  
|[Plantillas Extern](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1987.htm)|Sí|Sí|Sí|Sí|  
|[nullptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2431.pdf)|Sí|Sí|Sí|Sí|  
|[Enumeraciones fuertemente tipadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2347.pdf)|Parcial|Sí|Sí|Sí|  
|[Enumeraciones declaradas por adelantado](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2764.pdf)|No|Sí|Sí|Sí|  
|[Atributos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2761.pdf)|No|No|No|Sí|  
|[constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2235.pdf)|No|No|No|Sí|  
|[Alineación](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2341.pdf)|TR1|Parcial|Parcial|Sí|  
|[Constructores de delegación](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1986.pdf)|No|No|[Sí](../cpp/uniform-initialization-and-delegating-constructors.md)|Sí|  
|[Constructores de herencia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2540.htm)|No|No|No|Sí|  
|[Operadores de conversión explícitos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2437.pdf)|No|No|Sí|Sí|  
|[char16\_t\/char32\_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2249.html)|No|No|No|Sí|  
|[Literales de cadena Unicode](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2442.htm)|No|No|No|Sí|  
|[Literales de cadena sin formato](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2442.htm)|No|No|[Sí](../cpp/string-and-character-literals-cpp.md)|Sí|  
|[Nombres de carácter universal en literales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2170.html)|No|No|No|Sí|  
|[Literales definidos por el usuario](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2765.pdf)|No|No|No|Sí|  
|[Tipos de diseño estándar y triviales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2342.htm)|No|Sí|Sí|Sí|  
|[Funciones establecidas como valor predeterminado y funciones eliminadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2346.htm)|No|No|[Sí\*](../cpp/explicitly-defaulted-and-deleted-functions.md)|Sí|  
|[Declaraciones friend extendidas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1791.pdf)|Sí|Sí|Sí|Sí|  
|[Sizeof extendido](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2253.html)|No|No|No|Sí|  
|[Espacios de nombres alineados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2535.htm)|No|No|No|Sí|  
|[Uniones sin restricción](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2544.pdf)|No|No|No|Sí|  
|[Tipos locales y sin nombre como argumentos de plantilla](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2657.htm)|Sí|Sí|Sí|Sí|  
|[Bucle for basado en intervalo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2930.html)|No|Sí|Sí|Sí|  
|override y final [v0.8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2009/n2928.htm), [v0.9](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3206.htm), [v1.0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3272.htm)|Parcial|Sí|Sí|Sí|  
|[Compatibilidad mínima con GC](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2670.htm)|Sí|Sí|Sí|Sí|  
|[noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2010/n3050.html)|No|No|No|Sí|  
  
 \[[En este artículo](#top)\]  
  
###  <a name="concurrencytable"></a> Tabla de características principales del lenguaje C\+\+11: simultaneidad  
  
|Características principales del lenguaje C\+\+11: simultaneidad|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|---------------------------------------------------------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|[Puntos de secuencia modificados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2239.html)|N\/D|N\/D|N\/D|Sí|  
|[Tipos atómicos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2427.html)|No|Sí|Sí|Sí|  
|[Comparación e intercambio seguros](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2748.html)|No|Sí|Sí|Sí|  
|[Barreras bidireccionales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2752.htm)|No|Sí|Sí|Sí|  
|[Modelo de memoria](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2429.htm)|N\/D|N\/D|N\/D|Sí|  
|[Ordenación de dependencia de datos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2664.htm)|No|Sí|Sí|Sí|  
|[Ordenación de dependencia de datos: anotación de función](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2782.htm)|No|No|No|Sí|  
|[exception\_ptr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2179.html)|Sí|Sí|Sí|Sí|  
|[quick\_exit](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2440.htm)|No|No|No|Sí|  
|[Tipos atómicos en controladores de señal](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2547.htm)|No|No|No|No|  
|[Almacenamiento local de subprocesos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2659.htm)|Parcial|Parcial|Parcial|Sí|  
|[Estática mágica](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2660.htm)|No|No|No|Sí|  
  
 \[[En este artículo](#top)\]  
  
###  <a name="c99table"></a> Características principales del lenguaje C\+\+11: C99  
  
|Características principales del lenguaje C\+\+11: C99|Visual Studio 2010|Visual Studio 2012|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|Visual Studio 2015|  
|-----------------------------------------------------------|------------------------|------------------------|--------------------------------------------------------------|------------------------|  
|[\_\_func\_\_](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2340.htm)|Parcial|Parcial|Parcial|Sí|  
|[Preprocesador C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Parcial|Parcial|Parcial|Parcial|  
|[long long](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1811.pdf)|Sí|Sí|Sí|Sí|  
|[Tipos enteros extendidos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|N\/D|N\/D|N\/D|N\/D|  
  
 \[[En este artículo](#top)\]  
  
###  <a name="cpp14table"></a> Características principales del lenguaje C\+\+14  
  
||||  
|-|-|-|  
|Característica|Visual Studio 2013|Visual Studio 2015|  
|Funcionamiento modificado para conversiones contextuales|Sí|Sí|  
|Literales binarios|No|Sí|  
|Tipos devueltos auto y decltype\(auto\)|No|Sí|  
|init\-capture|No|Sí|  
|Lambdas genéricas|No|Sí|  
|Plantillas de variables|No|No|  
|constexpr extendido|No|No|  
|NSDMI para agregados|No|No|  
|Evitar\/fusionar asignaciones|No|No|  
|atributos \[\[deprecated\]\]|No|No|  
|Asignación con tamaño|No|Sí|  
|Separadores de dígitos|No|Sí|  
  
###  <a name="cpp17table"></a> Características principales propuestas del lenguaje C\+\+17  
  
||||  
|-|-|-|  
|Característica|Visual Studio 2013|Visual Studio 2015|  
|Nuevas reglas para auto con listas de inicialización entre llaves|No|No|  
|assert estático breve|No|No|  
|typename en parámetros de plantilla de la plantilla|No|No|  
|Eliminación de trígrafos|Sí|Sí|  
|Definiciones de espacio de nombres anidadas|No|No|  
|N4259 std::uncaught\_exceptions\(\)|No|No|  
|N4261 Corregir conversiones de cualificación|No|No|  
|N4266 Atributos de espacios de nombres y enumeradores|No|No|  
|N4267 Literales de caracteres de u8|No|No|  
|N4268 Permitir más argumentos de plantilla sin tipo|No|No|  
|N4295 Expresiones plegadas|No|No|  
|await\/resume|No|Sí|  
  
##  <a name="tableguide"></a> Guía para las tablas de características  
  
###  <a name="rvref"></a> Referencias a valor R  
  
> [!NOTE]
>  Las designaciones de versión \(v0.1, v1.0, v2.0, v2.1, v3.0\) de las siguientes descripciones se han concebido únicamente para mostrar la evolución de C\+\+11. El propio estándar no las usa.  
  
 El artículo [N1610 sobre la aclaración de inicialización de objetos de clase por los valores R](http://go.microsoft.com/fwlink/p/?LinkID=235093) fue un intento temprano de habilitar la semántica de movimiento sin referencias a valor R.  Para simplificar el debate, lo hemos denominado "Referencias a valor R v0.1". Se reemplazó por "Referencias a valor R [v1.0](http://go.microsoft.com/fwlink/p/?LinkID=235094)". En "Referencias a valor R [v2.0](http://go.microsoft.com/fwlink/p/?LinkID=235095)", que es el trabajo en el que se basó Visual C\+\+ en Visual Studio 2010, se prohíbe que las referencias a valor R se enlacen a valores L y, por tanto, se corrige un problema de seguridad importante.  En "Referencias a valor R [v2.1](http://go.microsoft.com/fwlink/p/?LinkID=235096)" se refina esta regla.  Considere `vector<string>::push_back()`, que tiene las sobrecargas `push_back(const string&)` y `push_back(string&&)`, y la llamada `v.push_back("strval")`.  La expresión `"strval"` es un literal de cadena y es un valor L.  \(Otros literales son valores R, por ejemplo el entero 1729, pero los literales de cadena son especiales porque son matrices\).  Las reglas de "Referencias a valor R v2.0" establecían que `string&&` no se puede enlazar a `"strval"` porque `"strval"` es un valor L y, por consiguiente, `push_back(const string&)` es la única sobrecarga viable.  Esto crearía una clase `std::string` temporal, la copiaría en el vector y, a continuación, destruiría la `std::string` temporal, lo que no era muy eficiente. Las reglas de "Referencias a valor R v2.1" reconocen que enlazar `string&&` a `"strval"` crearía una clase `std::string` temporal, que es un valor R.  Por consiguiente, `push_back(const string&)` y `push_back(string&&)` son viables, y se prefiere `push_back(string&&)`.  Se construye una clase `std::string` temporal y después se mueve al vector.  Esto es más eficaz.  
  
 En "Referencias a valor R [v3.0](http://go.microsoft.com/fwlink/p/?LinkID=235097)" se agregan nuevas reglas para generar automáticamente constructores de movimiento y mover los operadores de asignación en determinadas condiciones. Esto se implementa en Visual Studio 2015.  
  
 \[[En este artículo](#top)\]  
  
###  <a name="lambdas"></a> Lambdas  
 Después de que se votaran las [funciones lambda](../cpp/lambda-expressions-in-cpp.md) en el documento de trabajo \([versión "0.9"](http://go.microsoft.com/fwlink/p/?LinkID=235098)\) y se agregaran las expresiones lambda mutables \([versión "1.0"](http://go.microsoft.com/fwlink/p/?LinkID=235099)\), el comité de estandarización revisó el texto. Esto generaba expresiones lambda [versión "1.1"](http://go.microsoft.com/fwlink/p/?LinkID=235100), que ahora son totalmente compatibles.  El texto de las expresiones lambda v1.1 explica lo que debe ocurrir en los casos extremos, como los referentes a miembros estáticos o expresiones lambda anidadas.  Esto corrige los problemas que las expresiones lambda complejas producían.  Además, las expresiones lambda sin estado se pueden convertir ahora en punteros de función.  Esto no está en el texto de N2927, pero se cuenta como parte de las expresiones lambda v1.1 de todos modos.[C\+\+11](http://go.microsoft.com/fwlink/p/?LinkID=235092) **5.1.2 \[expr.prim.lambda\]\/6** tiene una descripción similar a la siguiente: "El tipo de cierre de una `lambda-expression` sin `lambda-capture` tiene una función de conversión const pública no explícita ni virtual para el puntero a función con los mismos tipos devueltos y de parámetro que el operador de llamada de función del tipo de cierre. El valor devuelto por esta función de conversión será la dirección de una función que, cuando se invoca, tiene el mismo efecto que invocar el operador de llamada de función del tipo de cierre".  \(La implementación de [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] es incluso mejor que esta, dado que hace que las expresiones lambda sin estado se puedan convertir a punteros de función que tienen convenciones de llamada arbitrarias.  Esto es importante cuando se utilizan API que esperan elementos como los punteros de función `__stdcall`\).  
  
 \[[En este artículo](#top)\]  
  
###  <a name="decltype"></a> decltype  
 Después de que se votara decltype en el documento de trabajo \([versión 1.0](http://go.microsoft.com/fwlink/p/?LinkID=235101)\), recibió a última hora una corrección pequeña pero importante \([versión 1.1](http://go.microsoft.com/fwlink/p/?LinkID=235102)\).  Esto es de gran interés para los programadores que trabajan en STL y Boost.  
  
 \[[En este artículo](#top)\]  
  
###  <a name="stronglytyped"></a> Enumeraciones fuertemente tipadas y declaradas por adelantado  
 Las [enumeraciones fuertemente tipadas](http://go.microsoft.com/fwlink/p/?LinkID=235103) se admiten parcialmente para Visual C\+\+ en Visual Studio 2010 \(específicamente, la parte sobre los tipos subyacentes especificados explícitamente\). Ahora están completamente implementadas en Visual Studio y la semántica de C\+\+11 para las [enumeraciones declaradas por adelantado](http://go.microsoft.com/fwlink/p/?LinkID=235104) también está totalmente implementada.  
  
 \[[En este artículo](#top)\]  
  
###  <a name="alignment"></a> Alineación  
 Las palabras clave del lenguaje principal `alignas`\/`alignof` de la [propuesta de alineación](http://go.microsoft.com/fwlink/p/?LinkID=235105) que se votó en el documento de trabajo están implementadas Visual Studio 2015.  Visual C\+\+ en Visual Studio 2010 incluía `aligned_storage` a partir de TR1. En [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] se agregaron `aligned_union` y `std::align()` a la biblioteca estándar y se corrigieron problemas significativos en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)].  
  
 \[[En este artículo](#top)\]  
  
###  <a name="standardlayout"></a> Tipos de diseño estándar y triviales  
 Los cambios expuestos en el artículo [N2342 sobre la revisión de POD para resolver el problema principal 568 \(revisión 5\)](http://go.microsoft.com/fwlink/p/?LinkID=235106) son las incorporaciones de `is_trivial` e `is_standard_layout` en `<type_traits>` de la Biblioteca de plantillas estándar.  \(En N2342 se modificó una gran parte del texto del lenguaje principal, pero no son necesarios cambios del compilador\).  Estos rasgos de tipo estaban disponibles para Visual C\+\+ en Visual Studio 2010, pero simplemente han duplicado `is_pod`. Por consiguiente, en la tabla anterior de este documento la compatibilidad es "No".  Ahora usan la tecnología de los enlaces de compilador que se han diseñado para dar respuestas exactas.  
  
 [common\_type\<\>](../standard-library/common-type-class.md) de la STL recibió una corrección muy necesaria en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)].  La especificación de C\+\+11 para `common_type<>` tuvo consecuencias inesperadas no deseadas; concretamente, hace que `common_type<int, int>::type` devuelva `int&&`. Por consiguiente, [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] implementa la [resolución propuesta para el problema 2141 del grupo de trabajo de biblioteca](http://go.microsoft.com/fwlink/p/?LinkId=320075), que hace que `common_type<int, int>::type` devuelva `int`.  
  
 Un efecto secundario de este cambio es que ya no funciona el caso de identidad \(`common_type<T>` no siempre devuelve un tipo `T`\). Este comportamiento se ajusta a la resolución propuesta, pero interrumpe cualquier código que dependiera del comportamiento anterior.  
  
 Si necesita un tipo de rasgo de identidad, no utilice la clase `std::identity` no estándar que se define en `<type_traits>` porque no funcionará para `<void>`. En su lugar, implemente un rasgo de tipo de identidad propio que se ajuste a sus necesidades. Por ejemplo:  
  
```cpp  
template <typename T> struct Identity { typedef T type; };  
  
```  
  
> [!NOTE]
>  Para conocer otros cambios importantes, vea [Cambios importantes en Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md).  
  
 \[[En este artículo](#top)\]  
  
###  <a name="defaultedanddeleted"></a> Funciones establecidas como valor predeterminado y funciones eliminadas  
 Estos se admiten ahora, pero con esta excepción: para las funciones establecidas de forma predeterminada, no se admite el uso de `=default` para solicitar constructores de movimiento y operadores de asignación de movimiento miembro a miembro. Las copias y los movimientos no interactúan con precisión como se indica en el estándar; por ejemplo, se especifica que la eliminación de movimientos debe suprimir también las copias, pero [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] no las elimina.  
  
 Para obtener información sobre cómo usar las funciones establecidas como valor predeterminado y las funciones eliminadas, vea [Funciones](../cpp/functions-cpp.md).  
  
 \[[En este artículo](#top)\]  
  
###  <a name="overrideandfinal"></a> override y final  
 Estas palabras clave han tenido una evolución corta pero complicada. Originalmente, la [versión 0.8](http://go.microsoft.com/fwlink/p/?LinkID=235108), tenía los atributos \[\[`override`\]\], \[\[`hiding`\]\] y \[\[`base_check`\]\].  Posteriormente, en la [versión 0.9](http://go.microsoft.com/fwlink/p/?LinkID=235109), los atributos se eliminaron y se reemplazaron por palabras clave contextuales.  Por último, en la [versión 1.0](http://go.microsoft.com/fwlink/p/?LinkID=235110), se redujeron a "`final`" en las clases y a "`override`" y "`final`" en las funciones.  Esto crea una extensión ascendida, porque Visual C\+\+ en Visual Studio 2010 ya admitía esta sintaxis de "`override`" en las funciones y tenía una semántica bastante parecida a la de C\+\+11.  "`final`" también se admite, pero con una ortografía diferente "sellada".  La ortografía y la semántica estándar de "`override`" y "`final`" se admiten ahora por completo. Para obtener más información, consulte [override \(especificador\)](../cpp/override-specifier.md) y [final \(especificador\)](../cpp/final-specifier.md).  
  
 \[[En este artículo](#top)\]  
  
###  <a name="atomics"></a> Tipos atómicos y más  
 Los [tipos atómicos](http://go.microsoft.com/fwlink/p/?LinkID=235111), la [comparación e intercambio seguros](http://go.microsoft.com/fwlink/p/?LinkID=235112), las [barreras bidireccionales](http://go.microsoft.com/fwlink/p/?LinkID=235113) y la [ordenación de dependencia de datos](http://go.microsoft.com/fwlink/p/?LinkID=235114) especifican la maquinaria de la biblioteca estándar que se implementa ahora.  
  
 **Encabezados de STL relacionados:** [\<atomic\>](../standard-library/atomic.md), [\<chrono\>](../standard-library/chrono.md), [\<condition\_variable\>](../standard-library/condition-variable.md), [\<future\>](../standard-library/future.md), [\<mutex\>](../standard-library/mutex.md), [\<ratio\>](../standard-library/ratio.md), [\<scoped\_allocator\>](../standard-library/scoped-allocator.md) y [\<thread\>](../standard-library/thread.md).  
  
 \[[En este artículo](#top)\]  
  
###  <a name="c99"></a> \_\_func\_\_ y reglas de preprocesador de C99  
 En la tabla [Características principales del lenguaje C++11: C99](#c99table) hay dos elementos para los que figura una implementación "Parcial". En el caso del identificador predefinido `__func__`, "Parcial" aparece porque existe compatibilidad con las extensiones no estándar `__FUNCDNAME__`, `__FUNCSIG__` y `__FUNCTION__`. Para obtener más información, vea [Macros predefinidas](../preprocessor/predefined-macros.md). En el caso de las reglas de preprocesador de C99, "Parcial" se muestra porque se admiten *macros variádicas*. Para obtener más información, vea [Macros variádicas](../preprocessor/variadic-macros.md).  
  
 \[[En este artículo](#top)\]  
  
###  <a name="stl"></a> Características de la biblioteca estándar  
 Esto cubre el lenguaje principal. En cuanto a la biblioteca estándar de C\+\+11, no tenemos una tabla de características comparadas, pero [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] la implementa, con dos excepciones.  Primero, cuando una característica de biblioteca dependía de una funcionalidad que faltaba en el compilador, se simulaba \(por ejemplo, las plantillas variádicas simuladas para `make_shared<T>()`\) o no se implementaba. \(Hay solo unos pocos casos, el más notable de los cuales es `<initializer_list>`, que estuvieran completamente implementados en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)]\).  Con muy pocas excepciones, C99 se ha implementado en los encabezados de contenedor de [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] y C\+\+ proporcionados. Para obtener más información, vea [Compatibilidad con bibliotecas de C99 en Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=321308).  
  
 A continuación se muestra una lista parcial de los cambios en [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] y [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)]:  
  
 **Emplazamiento:** tal como lo requiere C\+\+11, `emplace()`\/`emplace_front()`\/`emplace_back()`\/`emplace_hint()`\/`emplace_after()` se implementan en todos los contenedores para los números de argumentos "arbitrarios" \(vea la sección "Plantillas variádicas simuladas"\).  Por ejemplo, `vector<T>` incluye "`template <typename... Args> void emplace_back(Args&&... args)`", que construye directamente un elemento de tipo T al final del vector de un número arbitrario de argumentos arbitrarios, reenviados perfectamente.  Esto puede ser más eficaz que `push_back(T&&)`, que implicaría una construcción y una destrucción de movimiento adicionales.  
  
 **Plantillas variádicas:** [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] tenía un esquema para simular plantillas variádicas. En [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], no aparecen las simulaciones y las **plantillas variádicas están totalmente implementadas**. Si el código depende del comportamiento anterior de las plantillas variádicas simuladas, tiene que corregirlo. Sin embargo, el cambio a las plantillas variádicas verdaderas tiene **mejores tiempos de compilación** y **menor consumo de memoria del compilador**.  
  
 **Operadores de conversión explícitos:** en el lenguaje principal, los operadores de conversión explícitos son una característica general, por ejemplo, se puede usar `explicit operator MyClass()`. Sin embargo, la biblioteca estándar utiliza actualmente un único formato: `explicit operator bool()`, que crea clases seguras de pruebas booleanas. \("`operator bool()`", por sí solo, es notablemente peligroso\). Previamente, Visual C\+\+ simulaba `explicit operator bool()` con `operator pointer-to-member()`, que produjo más de un dolor de cabeza y leves ineficiencias. Ahora, esta solución de "falsa comprobación booleana" se ha quitado por completo.  
  
 **Aleatoriedad:** `uniform_int_distribution` es absolutamente imparcial ahora y `shuffle()` está implementado en `<algorithm>`, que acepta directamente los generadores de número aleatorio uniforme como `mersenne_twister`.  
  
 **Resistencia a los operadores address\-of sobrecargados:** C\+\+98\/03 prohibía que un elemento de un contenedor STL sobrecargara su operador address\-of.  Esto es lo que hacen las clases como `CComPtr`, de modo que las clases auxiliares como `CAdapt` eran necesarias para proteger STL de estas sobrecargas.  Durante el desarrollo de Visual C\+\+ en Visual Studio 2010, los cambios en STL hacían que rechazara operadores address\-of sobrecargados incluso en más situaciones. C\+\+11 cambió los requisitos para que los operadores address\-of sobrecargados sean aceptables. C\+\+11 y Visual C\+\+ en Visual Studio 2010 proporcionan la función auxiliar `std::addressof()`, que puede obtener la dirección real de un objeto independientemente de la sobrecarga de operadores.  Antes del lanzamiento de Visual C\+\+ en Visual Studio 2010, intentamos reemplazar las apariciones de "`&elem`" por "`std::addressof(elem)`", que es adecuadamente resistente.[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] fue más allá, así que las clases que sobrecargan su operador address\-of se deben poder usar siempre en STL.  
  
 **[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] fue más allá de C\+\+11 de varias maneras:**  
  
 **Iteradores SCARY:** debido a que se permiten pero no se requieren en el estándar C\+\+11, los iteradores SCARY se han implementado, tal como se describe en los artículos [N2911 sobre la minimización de dependencias dentro de las clases genéricas para programas más rápidos y más pequeños](http://go.microsoft.com/fwlink/p/?LinkID=235115) y [N2980 sobre la asignación e inicialización del iterador SCARY, revisión 1](http://go.microsoft.com/fwlink/p/?LinkID=235116).  
  
 **Filesystem:** se agregó el encabezado `<filesystem>` de [la propuesta TR2](http://go.microsoft.com/fwlink/p/?LinkID=235117). Proporciona `recursive_directory_iterator` y otras características interesantes.  Antes de que el trabajo en TR2 se inmovilizara porque C\+\+0x iba muy lento y se cambiara a C\+\+11, la propuesta de 2006 se derivó de [Boost.Filesystem V2](http://go.microsoft.com/fwlink/p/?LinkID=235118). Posteriormente se convirtió en Boost.Filesystem V3, que se implementó en Visual Studio 2015.  
  
 Y además una optimización importante.  Todos los contenedores son ahora óptimamente pequeños dadas sus representaciones actuales.  Esto hace referencia a los propios objetos contenedores, no a los contenidos a los que señala.  Por ejemplo, `std::vector` contiene tres punteros sin formato.  Para Visual C\+\+ en Visual Studio 2010, el modo de versión x86, `std::vector` era de 16 bytes.  Para [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], es de 12 bytes, que es óptimamente pequeño.  Esto es importante: si hay 100 000 vectores en el programa, [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] ahorra 400 000 bytes.  Un menor uso de memoria ahorra espacio y tiempo.  
  
 Esto se logra al evitar el almacenamiento de asignadores y comparadores vacíos, porque `std::allocator` y `std::less` no tienen estado.  \(Estas optimizaciones también se habilitan para los asignadores o comparadores personalizados, siempre que estén sin estado.  Naturalmente, el almacenamiento de asignadores y comparadores con estado no se puede evitar, pero solo en casos poco frecuentes\).  
  
 **[!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] implementa algunas características clave de la biblioteca de C\+\+14:**  
  
-   “Objetos functor de operador transparentes” `less<>`, `greater<>`, `plus<>`, `multiplies<>`, etc.  
  
-   `make_unique<T>(args...)` y `make_unique<T[]>(n)`  
  
-   Funciones no miembro `cbegin()`\/`cend()`, `rbegin()`\/`rend()` y `crbegin()`\/`crend()`.  
  
 \[[En este artículo](#top)\]  
  
## Vea también  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)   
 [Blog del equipo de Visual C\+\+](http://blogs.msdn.com/b/vcblog/)   
 [Novedades de Visual C\+\+](../top/what-s-new-for-visual-cpp-in-visual-studio-2015.md)   
 [Cambios importantes en Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md)