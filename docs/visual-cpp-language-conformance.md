---
title: Conformidad del lenguaje Visual C++ | Microsoft Docs
ms.custom: 
ms.date: 3/1/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
caps.latest.revision: 11
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
translationtype: Human Translation
ms.sourcegitcommit: da3c2e6ce7247d3e8c9a401bc0a133cb8d46a970
ms.openlocfilehash: a13be4d4d32ab0f0bc3cc7b5972e90c4493d06ff
ms.lasthandoff: 03/15/2017

---
# <a name="visual-c-language-conformance"></a>Conformidad del lenguaje Visual C++ 
En este tema se resume la conformidad con los estándares del lenguaje ISO C++03, C++11, C++14 y el borrador C++17 de las características del compilador y de las características de la biblioteca estándar (STL) para Visual C++ en Visual Studio 2017 y versiones anteriores. El nombre de cada una de las características del compilador y de la STL enlaza al documento de propuesta del estándar ISO C++ que describe la característica, si hubiera alguno disponible en el momento de la publicación. La columna Compatible muestra la versión de Visual Studio en la que aparece por primera vez la compatibilidad de la característica.  
  
Para obtener detalles sobre las mejoras de conformidad y otros cambios en Visual Studio 2017, consulte [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements-2017.md) y [Novedades de Visual C++ en Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md). Para conocer los cambios de conformidad en versiones anteriores, consulte [Historial de cambios en Visual C++ 2003-2015](porting/visual-cpp-change-history-2003-2015.md) y [Novedades de Visual C++ de 2003 a 2015](porting/visual-cpp-what-s-new-2003-through-2015.md). Para mantenerse al tanto de las noticias actuales del equipo de C++, visite el [blog del equipo de Visual C++](http://blogs.msdn.microsoft.com/vcblog/).  
  
## <a name="compiler-features"></a>Características del compilador  
  
|Área de características| |  
|----|---|  
|__Características principales del lenguaje C++03/11__|__Compatible__|
|&nbsp;&nbsp;Todo lo demás|VS 2015 <sup>[1](#note_1)</sup>|
|&nbsp;&nbsp;Búsqueda de nombres en dos fases|No|
|&nbsp;&nbsp;[N2634 Expresión SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|Parcial <sup>[2](#note_2)</sup>|
|&nbsp;&nbsp;[N1653 Preprocesador C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Parcial <sup>[3](#note_3)</sup>|
|&nbsp;&nbsp;[N1988 Tipos enteros extendidos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|N/D <sup>[4](#note_4)</sup>|
|__Características principales del lenguaje C++14__|__Compatible__|
|&nbsp;&nbsp;[N3664 Evitar/fusionar asignaciones](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|N/D <sup><sup>[5](#note_5)</sup></sup>|
|&nbsp;&nbsp;[N3323 Redacción modificada para conversiones contextuales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 Literales binarios](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 Tipos de valor devuelto auto y decltype(auto)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init-captures](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 Lambdas genéricas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3651 Plantillas de variables](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 constexpr extendido](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[N3653 NSDMI para agregados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3760 Atributo [[deprecated]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Desasignación de tamaño](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 Separadores de dígitos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|__Características principales del lenguaje C++17__|__Compatible__|
|&nbsp;&nbsp;[N3922 Nuevas reglas para auto con listas de inicialización entre llaves](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015|
|&nbsp;&nbsp;[N3928 static_assert breve](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 [*](#note_star)|
|&nbsp;&nbsp;[N4051 typename en parámetros de plantilla](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015|
|&nbsp;&nbsp;[N4086 Eliminación de trígrafos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010|
|&nbsp;&nbsp;[N4230 Definiciones de espacio de nombres anidadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 [*](#note_star)|
|&nbsp;&nbsp;[N4261 Corregir conversiones de cualificación](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|No|
|&nbsp;&nbsp;[N4266 Atributos de espacios de nombres y enumeradores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015|
|&nbsp;&nbsp;[N4267 Literales de caracteres de u8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015|
|&nbsp;&nbsp;[N4268 Permitir más argumentos de plantilla sin tipo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|No|
|&nbsp;&nbsp;[N4295 Expresiones plegadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|No|
|&nbsp;&nbsp;[P0036R0 Quitar algunos pliegues unarios vacíos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|No|
|&nbsp;&nbsp;[P0001R1 Quitar la palabra clave register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017.x [*](#note_star)|
|&nbsp;&nbsp;[P0002R1 Quitar operator++ para bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|No|
|&nbsp;&nbsp;[P0012R1 Agregar noexcept al sistema de tipos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|No|
|&nbsp;&nbsp;[P0017R1 Inicialización de agregados extendidos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|No|
|&nbsp;&nbsp;[P0018R3 Captura de *this por valor](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017.x [*](#note_star)|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|No|
|&nbsp;&nbsp;[P0136R1 Nueva redacción de constructores de herencia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|No|
|&nbsp;&nbsp;[P0138R2 Inicialización de lista directa de enumeraciones fijas de enteros](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017.x [*](#note_star)|
|&nbsp;&nbsp;[P0170R1 Lambdas de constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|No|
|&nbsp;&nbsp;[P0184R0 Bucles for basados en intervalos generalizados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017|
|&nbsp;&nbsp;[P0188R1 Atributo [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 [*](#note_star)|
|&nbsp;&nbsp;[P0189R1 Atributo [[nodiscard]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|No|
|&nbsp;&nbsp;[P0212R1 Atributo [[maybe_unused]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017.x [*](#note_star)|
|&nbsp;&nbsp;[P0245R1 Literales Hexfloat](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|No|
|&nbsp;&nbsp;[P0028R4 Uso de espacios de nombres de atributo sin repetición](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|No|
|&nbsp;&nbsp;[P0035R4 Asignación de memoria dinámica alineada en exceso](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|No|
|&nbsp;&nbsp;[P0091R3 Deducción de argumentos de plantilla para plantillas de clase](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)|No|
|&nbsp;&nbsp;[P0127R2 Declarar parámetros de plantilla sin tipo con auto](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|No|
|&nbsp;&nbsp;[P0135R1 Elisión de copia garantizada](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|No|
|&nbsp;&nbsp;[P0145R3 Refinar el orden de evaluación de expresiones](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)|No|
|&nbsp;&nbsp;[P0217R3 Enlaces estructurados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|No|
|&nbsp;&nbsp;[P0283R2 Omitir atributos no reconocidos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|No|
|&nbsp;&nbsp;[P0292R2 Instrucciones if constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|No|
|&nbsp;&nbsp;[P0305R1 Instrucciones de selección con inicializadores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|No|
|&nbsp;&nbsp;[P0386R2 Variables insertadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|No|
|&nbsp;&nbsp;[P0522R0 Coincidencia de parámetros de plantilla con argumentos compatibles](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|No|
|&nbsp;&nbsp;[P0003R5 Quitar especificaciones de excepción dinámicas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|No|
|&nbsp;&nbsp;[P0195R2 Expansiones del paquete en declaraciones using](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|No|

## <a name="standard-library--stl-features"></a>Características de la biblioteca estándar (STL)

|Área de características| |
|---|---|
|__Características de la biblioteca estándar de C++17__|__Compatible__|
|&nbsp;&nbsp;P0433R2 Guías de deducción para STL|No|
|&nbsp;&nbsp;P0607R0 Variables insertadas para STL (opciones A y B2)|No|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|No|
|&nbsp;&nbsp;[P0426R1 constexpr para char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|No|
|&nbsp;&nbsp;P0604R0 Cambio de \_callable/result\_of a is\_invocable/invoke\_result (opciones A y B)|No|
|&nbsp;&nbsp;P0156R2 Cambio de nombre de lock\_guard a scoped\_lock variádico|No|
|&nbsp;&nbsp;P0558R1 Resolución de incoherencias<T> de clase con nombre atómicas|No|
|&nbsp;&nbsp;P0298R3 std::byte|No|
|&nbsp;&nbsp;[P0063R3 Biblioteca estándar de C11](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|No|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|No|
|&nbsp;&nbsp;[P0435R1 Revisión de common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;P0548R1 Ajuste de common\_type y duration|No|
|&nbsp;&nbsp;[P0513R0 Hash de tipo "poisoning"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;P0599R1 Hash noexcept|No|
|&nbsp;&nbsp;[P0033R1 Nueva redacción de enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|No|
|&nbsp;&nbsp;[P0220R1 Elementos fundamentales de biblioteca V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|Parcial <sup>[6](#note_6)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[P0497R0 Corregir shared_ptr para matrices](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|No|
|&nbsp;&nbsp;[P0084R2 Tipo de valor devuelto emplace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|No|
|&nbsp;&nbsp;[P0083R3 Insertar asignaciones y conjuntos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[P0508R0 Aclarar insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|No|
|&nbsp;&nbsp;[P0031R0 constexpr para \<array> (otra vez) e \<iterator>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|No|
|&nbsp;&nbsp;[P0505R0 constexpr para \<chrono> (otra vez)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|No|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 Correcciones para not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|No|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|No|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size, etc.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|No|
|&nbsp;&nbsp;[P0067R5 Conversiones de cadenas elementales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|No|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: Boyer-Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Corregir tipos de valor devueltos de buscadores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|No|
|&nbsp;&nbsp;P0618R0 \<codecvt> en desuso|No|
|&nbsp;&nbsp;[P0521R0 Dejar en desuso shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|No|
|&nbsp;&nbsp;[P0174R2 Dejar en desuso vestigios de elementos de biblioteca](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|No|
|&nbsp;&nbsp;[P0003R5 Quitar especificaciones de excepción dinámicas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|No|
|&nbsp;&nbsp;[P0302R1 Quitar la compatibilidad con el asignador en std::function](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|No|
|&nbsp;&nbsp;[P0040R3 Extender herramientas de administración de memoria](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|No|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[P0337R0 Eliminar la asignación de polymorphic_allocator](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|No|
|&nbsp;&nbsp;[P0024R2 Algoritmos paralelos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[P0336R1 Cambiar el nombre de directivas de ejecución en paralelo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[P0394R4 Los algoritmos paralelos deben invocar terminate() para las excepciones](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;P0452R1 Unificación de algoritmos paralelos \<numeric>|No|
|&nbsp;&nbsp;[P0226R1 Funciones matemáticas especiales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|No|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 Rutas de acceso relativas para el sistema de archivos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[P0392R0 Compatibilidad con string_view en las rutas de acceso del sistema de archivos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;P0430R2 Compatibilidad con sistemas de archivos no POSIX<br />&nbsp;&nbsp;P0492R2 Resolución de comentarios NB para el sistema de archivos|No <sup>[7](#note_7)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017.x|
|&nbsp;&nbsp;[P0403R1 Archivos UDL para \<string_view> ("meow"sv, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017.x|
|&nbsp;&nbsp;[P0418R2 Requisitos atómicos de compare_exchange memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017.x|
|&nbsp;&nbsp;[P0516R0 Marcar la copia de shared_future como noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017.x|
|&nbsp;&nbsp;[P0517R0 Construir future_error a partir de future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017.x|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<algorithm> sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<any>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<string_view>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<tuple> apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[P0032R3 Interfaz homogénea para variant/any/optional](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<variant>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0254R2 Integración de string_view y std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 Hacer que mayor igual sea opcional otra vez](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0393R3 Hacer que mayor igual sea variante](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[P0504R0 Revisión de in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[P0510R0 Rechazar variantes de vacío, matrices, referencias y tipos incompletos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 basic_string::data() no constante](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[N4387 Mejorar pair y tuple](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2|
|&nbsp;&nbsp;[N4508 shared_mutex (no cronometrado)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2|
|&nbsp;&nbsp;[P0004R1 Quitar alias Iostreams en desuso](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2|
|&nbsp;&nbsp;[P0006R0 Plantillas de variables para rasgos de tipos (is_same_v, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2|
|&nbsp;&nbsp;[P0013R1 Rasgos de tipos de operadores lógicos (conjunción, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2|
|&nbsp;&nbsp;[P0092R1 \<chrono> floor(), ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2|
|&nbsp;&nbsp;[P0156R0 lock_guard variádico](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015|
|&nbsp;&nbsp;[N4089 Conversiones seguras en unique_ptr\<T[]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015|
|&nbsp;&nbsp;[N4190 Quitar auto_ptr, random_shuffle() y elementos \<functional> antiguos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015|
|&nbsp;&nbsp;[N4258 Limpiezas de noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015|
|&nbsp;&nbsp;[N4277 reference_wrapper que se puede copiar de forma trivial](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015|
|&nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() para map/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015|
|&nbsp;&nbsp;[N4280 size(), empty(), data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015|
|&nbsp;&nbsp;[N4366 Asignación unique_ptr con restricción precisa](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015|
|&nbsp;&nbsp;[N4510 Admitir tipos incompletos en vector/list/forward_list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013|
|&nbsp;&nbsp;[N4284 Iteradores contiguos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4284.html)|N/D|
|&nbsp;&nbsp;[P0175R1 Sinopsis para la biblioteca de C](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0175r1.html)|N/D|
|&nbsp;&nbsp;[P0180R2 Reservar espacios de nombres para la normalización futura](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0180r2.html)|N/D|
|&nbsp;&nbsp;[P0346R1 Retoque de la nomenclatura de \<random>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0346r1.pdf)|N/D|
|&nbsp;&nbsp;[P0371R1 Disuadir del uso de memory_order_consume](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0371r1.html)|N/D|
|&nbsp;&nbsp;P0467R2 Necesidad de iteradores hacia adelante para algoritmos paralelos|N/D|
|&nbsp;&nbsp;[P0502R0 Los algoritmos paralelos deben invocar terminate() para las excepciones (generalmente)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0502r0.html)|N/D|
|&nbsp;&nbsp;[P0503R0 Corrección del uso de la biblioteca del "tipo de literal"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0503r0.html)|N/D|
|&nbsp;&nbsp;[ P0509R1 Actualización de "Restricciones del control de excepciones"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0509r1.pdf)|N/D|
|&nbsp;&nbsp;P0518R1 Copia de elementos Trivially Copy Constructible en algoritmos paralelos|N/D|
|&nbsp;&nbsp;P0523R1 Relajación de requisitos de complejidad de algoritmos paralelos (general)|N/D|
|&nbsp;&nbsp;P0574R1 Relajación de requisitos de complejidad de algoritmos paralelos (específico)|N/D|
|&nbsp;&nbsp;P0623R0 Correcciones de algoritmos de C ++&17; paralelos|N/D|
|__Características de la biblioteca estándar de C++14__|__Compatible__|
|&nbsp;&nbsp;[N3462 result_of compatible con SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr para \<complex>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr para \<chrono>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr para \<array>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr para \<initializer_list>, \<tuple> y \<utility>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 Archivos UDL para \<chrono> y \<string> (1729ms, "meow"s, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Iteradores hacia delante nulos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Búsqueda asociativa heterogénea](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (cronometrado)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 Corregir funciones miembro constexpr sin const](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 equal(), is_permutation() y mismatch() de doble intervalo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Desasignación de tamaño](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 Archivos UDL para \<complex> (3.14i, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr para \<functional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 Cambiar el nombre de shared_mutex (cronometrado) a shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 Requisitos mínimos de elemento contenedor](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 Objetos functor de operador transparentes (less\<>, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 Plantillas de alias para \<type_traits> (decay_t, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 Disuadir del uso de rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|N/D|  
  
El hecho de que unos documentos se enumeren juntos indica que se ha votado la inclusión de una característica en el estándar y que también se ha votado la inclusión de uno o varios documentos para mejorar o expandir dicha característica. Estas características se implementan juntas.  
  
### <a name="supported-values"></a>Valores admitidos  
__No__ significa que aún no se ha implementado.  
__Parcial__ significa que la implementación en Visual Studio 2017 está incompleta. Para más detalles, consulte la sección Notas.  
__N/D__ significa que los documentos de propuestas no describen las características. En estos documentos se modificaba el lenguaje del estándar, pero no se generaba trabajo adicional para los implementadores. Se incluyen aquí para proporcionar información completa.  
__VS 2010__ indica las características que se admiten en Visual Studio 2010.  
__VS 2013__ indica las características que se admiten en Visual Studio 2013.  
__VS 2015__ indica las características que se admiten en Visual Studio 2015 RTM.  
__VS 2015.2__ y __VS 2015.3__ indican las características que se admiten en Visual Studio 2015 Update 2 y Visual Studio 2015 Update 3, respectivamente.  
__VS 2017__ indica las características que se admiten en Visual Studio 2017 RTM.  
__VS 2017.x__ indica las características planeadas para una actualización futura de Visual Studio 2017.  
  
### <a name="notes"></a>Notas  
<a name="note_1"></a>__1__De este modo se omiten las especificaciones de excepción dinámicas de C++03, que han quedado en desuso en C++11. No hay ningún plan para implementarlas, a la espera de que se quiten de un estándar de C++ futuro.  
<a name="note_2"></a>__2__ La compatibilidad del compilador con la expresión SFINAE ha sido suficiente para la biblioteca estándar a partir de Visual Studio 2015 Update 2, pero todavía es incompleta.  
<a name="note_3"></a>__3__ La compatibilidad del compilador con las reglas del preprocesador C99 es incompleta en Visual Studio 2017. Se admiten las macros variádicas, pero se producen muchos errores en el comportamiento del preprocesador.  
<a name="note_4"></a>__4__ Se ha marcado como N/D (No disponible) porque se permiten los compiladores, aunque no son necesarios, para admitir tipos enteros extendidos.  Como GCC y Clang, hemos decidido no admitirlos.  
<a name="note_5"></a>__5__ Del mismo modo, se ha marcado como N/D (No disponible) porque se permiten los compiladores, aunque no son necesarios, para implementar esta optimización.  
<a name="note_6"></a>__6__ Las características que no se completaron en Visual Studio 2015 se dividen en otra parte de esta tabla.  
<a name="note_7"></a>__7__El TS del sistema de archivos se implementa en \<experimental/filesystem> y \<filesystem> por motivos históricos, pero su implementación debe corregirse antes de mover su espacio de nombres. Mientras esto no se lleve a cabo, se indicará que la característica todavía no está implementada.  
<a name="note_star"></a>__*__ Estas características están protegidas por la opción del compilador [/std:c++latest](./build/reference/std-specify-language-standard-version.md).  
  
## <a name="see-also"></a>Vea también  
[Referencia del lenguaje C++](cpp/cpp-language-reference.md)  
[Biblioteca estándar de C++](standard-library/cpp-standard-library-reference.md)   
[Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements-2017.md)  
[Novedades de Visual C++ en Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md)  
[Novedades de Visual C++ de 2003 a 2015](porting/visual-cpp-change-history-2003-2015.md)  
[Novedades de Visual C++ de 2003 a 2015](porting/visual-cpp-what-s-new-2003-through-2015.md)  
[Blog del equipo de Visual C++](http://blogs.msdn.microsoft.com/vcblog/)  

