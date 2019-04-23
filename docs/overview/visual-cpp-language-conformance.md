---
title: Conformidad del lenguaje Visual C++
ms.date: 11/15/2017
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 69591186550a915edb49889617740e454817f154
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58898809"
---
# <a name="visual-c-language-conformance"></a>Conformidad del lenguaje Visual C++

En este tema se resume la conformidad con los estándares del lenguaje ISO C++03, C++11, C++14, C++17 y el borrador C++20 de las características del compilador y de las características de la biblioteca estándar del Compilador de Microsoft Visual C++ en Visual Studio 2017 y versiones anteriores. El nombre de cada una de las características del compilador y de la biblioteca estándar vincula al documento de propuesta del estándar ISO C++ que describe la característica, si hubiera alguno disponible en el momento de la publicación. La columna Compatible muestra la versión de Visual Studio en la que aparece por primera vez la compatibilidad de la característica.

Para obtener detalles sobre las mejoras de conformidad y otros cambios en Visual Studio 2017, consulte [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements.md) y [Novedades de Visual C++ en Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md). Para conocer los cambios de conformidad en versiones anteriores, consulte [Historial de cambios en Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md) y [Novedades de Visual C++ de 2003 a 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Para mantenerse al tanto de las noticias actuales del equipo de C++, visite el [blog del equipo de Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

> [!NOTE]
> No existen cambios principales binarios entre Visual Studio 2015 y Visual Studio 2017.

## <a name="compiler-features"></a>Características del compilador

|Área de características| |
|----|---|
|__Características principales del lenguaje C++03/11__|__Compatible__|
|&nbsp;&nbsp;Todo lo demás|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;Búsqueda de nombres en dos fases|VS 2017 15.7 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 Expresión SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[N1653 Preprocesador C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Parcialmente <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[N1988 Tipos enteros extendidos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|N/D <sup>[E](#note_E)</sup>|
|__Características principales del lenguaje C++14__|__Compatible__|
|&nbsp;&nbsp;[N3323 Redacción modificada para conversiones contextuales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 Literales binarios](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 Tipos de valor devuelto auto y decltype(auto)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init-captures](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 Lambdas genéricas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 Atributo [[deprecated]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Desasignación de tamaño](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 Separadores de dígitos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 Plantillas de variables](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 constexpr extendido](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[N3653 NSDMI para agregados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 Evitar/fusionar asignaciones](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|N/D <sup>[F](#note_F)</sup>|
|__Características principales del lenguaje C++17__|__Compatible__|
|&nbsp;&nbsp;[N4086 Eliminación de trígrafos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 Nuevas reglas para auto con listas de inicialización entre llaves](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 typename en parámetros de plantilla](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4266 Atributos de espacios de nombres y enumeradores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 Literales de caracteres de u8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4230 Definiciones de espacio de nombres anidadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 static_assert breve](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 Bucles for basados en intervalos generalizados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 Atributo [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 Quitar la palabra clave register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 Quitar operator++ para bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 Captura de *this por valor](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 Uso de espacios de nombres de atributo sin repetición](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 Inicialización de lista directa de enumeraciones fijas de enteros](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 Lambdas de constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 Atributo [[nodiscard]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 Atributo [[maybe_unused]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 Enlaces estructurados](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 Instrucciones if constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[G](#note_G)</sup>|
|&nbsp;&nbsp;[P0305R1 Instrucciones de selección con inicializadores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Literales Hexfloat](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268 Permitir más argumentos de plantilla sin tipo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 Expresiones plegadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 Quitar especificaciones de excepción dinámicas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 Agregar noexcept al sistema de tipos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 Asignación de memoria dinámica alineada en exceso](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 Variables insertadas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 Coincidencia de parámetros de plantilla con argumentos compatibles](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 Quitar algunos pliegues unarios vacíos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 Corregir conversiones de cualificación](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0017R1 Inicialización de agregados extendidos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0091R3 Deducción de argumentos de plantilla para plantillas de clase](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[P0512R0 Problemas de deducción de argumento para plantilla de clase](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 Declarar parámetros de plantilla sin tipo con auto](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 Elisión de copia garantizada](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0136R1 Nueva redacción de constructores de herencia](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0145R3 Refinar el orden de evaluación de expresiones](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 Orden de evaluación de los argumentos de función](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0195R2 Expansiones del paquete en declaraciones using](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 Omitir atributos no reconocidos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|

|Área de características| |
|----|---|
|__Características principales del lenguaje C++17 Core (informes de defectos)__|__Compatible__|
|&nbsp;&nbsp;[P0702R1 Corrección de deducción de argumento de plantilla para constructores initializer-list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 Simplifying implicit lambda capture](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html) (Simplificación de la captura de lambda implícita)|No|
|&nbsp;&nbsp;[CWG 1581: When are constexpr member functions defined?](https://wg21.cmeerw.net/cwg/issue1581) (¿Cuándo se definen las funciones miembro de las expresiones constantes?)|No|
|&nbsp;&nbsp;[P0962R1 Relaxing the structured bindings customization point finding rules](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html) (Relajación de las reglas de búsqueda de punto de personalización de los enlaces estructurados)|No|
|&nbsp;&nbsp;[P0962R2 Relaxing the range-for loop customization point finding rules](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html) (Relajación de las reglas de búsqueda de punto de personalización de los bucles range-for)|No|
|&nbsp;&nbsp;[P0969R0 Allowing structured bindings to accessible members](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf) (Permitir enlaces estructurados para miembros accesibles)|No|

|Área de características| |
|----|---|
|__Características principales del lenguaje C++20__|__Compatible__|
|&nbsp;&nbsp;[P0306R4 Incorporación de &#95;&#95;VA_OPT&#95;&#95; para la omisión y la eliminación de comas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0306r4.html)|No|
|&nbsp;&nbsp;[P0329R4 Inicialización designada](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|No|
|&nbsp;&nbsp;[P0409R2 Se permite lambda-capture [=, this]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|No|
|&nbsp;&nbsp;[P0428R2 Sintaxis de plantilla familiar para expresiones lambda genéricas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|No|
|&nbsp;&nbsp;[P0683R1 Inicializadores de miembro predeterminado para los campos de bits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html)|No|
|&nbsp;&nbsp;[P0704R1 Correción de los punteros const lvalue ref-qualified a los miembros](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|No|
|&nbsp;&nbsp;[P0734R0 Conceptos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf)|No|

## <a name="standard-library-features"></a>Características de la biblioteca estándar

|Área de características| |
|---|---|
|__Características de la biblioteca estándar de C++20__|__Compatible__|
|&nbsp;&nbsp; [P0777R1 Avoiding Unnecessary Decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) (Evitar la decadencia innecesaria)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|No|
|&nbsp;&nbsp;[P0674R1 make_shared() para matrices](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|No|
|&nbsp;&nbsp;[P0858R0 Constexpr Iterator Requirements](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html) (Requisitos del iterador de expresiones constantes)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0809R0 Comparing Unordered Containers](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf) (Comparación de contenedores sin ordenar)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp; [P0020R3 atomic\<float>, atomic\<double>, atomic\<long double>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|No|
|&nbsp;&nbsp; [P0053R7 \<syncstream>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br />&nbsp;&nbsp; [P0753R2 osyncstream Manipulators](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf) (Manipuladores de osyncstream)|No|
|&nbsp;&nbsp; [P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|No|
|&nbsp;&nbsp; [P0202R3 constexpr For \<algorithm> And exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html) (Expresión constante para <algoritmo> y exchange())|No|
|&nbsp;&nbsp; [P0355R7 \<chrono> Calendars And Time Zones](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html) (Calendarios y zonas horarias de <chrono>)|No|
|&nbsp;&nbsp; [P0415R1 constexpr For \<complex> (Again)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html) (Expresión constante para <complex>)|No|
|&nbsp;&nbsp; [P0439R0 enum class memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html) (Clase de enumeración memory_order)|No|
|&nbsp;&nbsp; [P0457R2 starts_with()/ends_with() For basic_string/basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html) (starts_with()/ends_with() para basic_string/basic_string_view)|No|
|&nbsp;&nbsp; [P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|No|
|&nbsp;&nbsp; [P0551R3 Thou Shalt Not Specialize std Function Templates!](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0551r3.pdf) (No especializar las plantillas de función std)|No|
|&nbsp;&nbsp; [P0600R1 \[\[nodiscard\]\] For The STL, Part 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf) (\[\[nodiscard\]\] para STL, parte 1)|No|
|&nbsp;&nbsp; [P0616R0 Using move() In \<numeric>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf) (Uso de move() en <numeric>)|No|
|&nbsp;&nbsp; [P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|No|
|&nbsp;&nbsp; [P0718R2 atomic\<shared_ptr\<T>>, atomic\<weak_ptr\<T>>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|No|
|&nbsp;&nbsp; [P0754R2 \<version>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|No|
|&nbsp;&nbsp; [P0767R1 Deprecating is_pod](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html) (is_pod en desuso)|No|
|&nbsp;&nbsp; [P0768R1 Library Support For The Spaceship Comparison Operator \<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf) (Compatibilidad con bibliotecas para el operador de comparación de nave espacial)|No|
|&nbsp;&nbsp; [P0966R1 string::reserve() Should Not Shrink](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0966r1.html) (string::reserve() no debe reducirse)|No|
|__Características de la biblioteca estándar de C++17__|__Compatible__|
|&nbsp;&nbsp;[P0433R2 Integración de deducción de plantilla para plantillas de clase en la biblioteca estándar](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[P0739R0 Mejora de la integración de deducción de argumento de plantilla de clase en la biblioteca estándar](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0426R1 constexpr para char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0220R1 Elementos fundamentales de biblioteca V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15.6 <sup>[J](#note_J)</sup>|
|&nbsp;&nbsp;[P0067R5 Conversiones de cadenas elementales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15.7 <sup>[charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[P0337R0 Eliminar la asignación de polymorphic_allocator](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0024R2 Algoritmos paralelos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[P0336R1 Cambiar el nombre de directivas de ejecución en paralelo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[P0394R4 Los algoritmos paralelos deben invocar terminate() para las excepciones](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[P0452R1 Unificación de algoritmos paralelos \<numeric>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0226R1 Funciones matemáticas especiales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 Rutas de acceso relativas para el sistema de archivos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[P0317R1 Almacenamiento en caché de entrada de directorio para el sistema de archivos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br />&nbsp;&nbsp;[P0392R0 Compatibilidad con string_view en las rutas de acceso del sistema de archivos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[P0430R2 Compatibilidad con sistemas de archivos no POSIX](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 Resolución de comentarios NB para el sistema de archivos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup>[K](#note_K)</sup>|
|&nbsp;&nbsp;[P0003R5 Quitar especificaciones de excepción dinámicas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 Correcciones para not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0033R1 Nueva redacción de enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0083R3 Insertar asignaciones y conjuntos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[P0508R0 Aclarar insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 Dejar en desuso vestigios de elementos de biblioteca](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0302R1 Quitar la compatibilidad con el asignador en std::function](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[P0497R0 Corregir shared_ptr para matrices](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 Dejar en desuso shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 Variables insertadas para la biblioteca estándar](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 \<codecvt>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html) en desuso|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: búsqueda Boyer-Moore()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Corregir tipos de valor devueltos de buscadores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 constexpr para \<array> (otra vez) e \<iterator>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0040R3 Extender herramientas de administración de memoria](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 Tipo de valor devuelto emplace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size, etc.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R2 Cambio de nombre de lock\_guard to scoped\_lock](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html) variádico|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup>[L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15.3 <sup>[17](#note_17), [byte](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 Archivos UDL para \<string_view> ("meow"sv, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0418R2 Requisitos atómicos de compare_exchange memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0435R1 Revisión de common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[P0548R1 Ajuste de common\_type y duration](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 constexpr para \<chrono> (otra vez)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0513R0 Hash de tipo "poisoning"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[P0599R1 Hash noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 Marcar la copia de shared_future como noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 Construir future_error a partir de future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0558R1 Resolución de incoherencias de clase con nombre atómicas<T>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0604R0 Cambio de\_callable/result\_of To invoke\_result, es\_invocable, es\_nothrow\_invocable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<algorithm> sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<any>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 |
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
|&nbsp;&nbsp;[N4387 Mejorar pair y tuple](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (no cronometrado)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0004R1 Quitar alias Iostreams en desuso](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 Plantillas de variables para rasgos de tipos (is_same_v, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 Rasgos de tipos de operadores lógicos (conjunción, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<chrono> floor(), ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R0 lock_guard variádico](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 Conversiones seguras en unique_ptr\<T[]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 Quitar auto_ptr, random_shuffle() y elementos \<functional> antiguos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 Limpiezas de noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 reference_wrapper que se puede copiar de forma trivial](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() para map/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size(), empty(), data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 Asignación unique_ptr con restricción precisa](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0063R3 Biblioteca estándar de C11](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 Admitir tipos incompletos en vector/list/forward_list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
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

__No__ significa que aún no se ha implementado.<br/>
__Parcial__ significa que la implementación en Visual Studio 2017 está incompleta. Para más detalles, consulte la sección Notas.<br/>
__N/D__ significa que los documentos de propuestas no describen las características. En estos documentos se modificaba el lenguaje del estándar, pero no se generaba trabajo adicional para los implementadores. Se incluyen aquí para proporcionar información completa.<br/>
__VS 2010__ indica las características que se admiten en Visual Studio 2010.<br/>
__VS 2013__ indica las características que se admiten en Visual Studio 2013.<br/>
__VS 2015__ indica las características que se admiten en Visual Studio 2015 RTM.<br/>
__VS 2015.2__ y __VS 2015.3__ indican las características que se admiten en Visual Studio 2015 Update 2 y Visual Studio 2015 Update 3, respectivamente.<br/>
__VS 2017__ indica las características que se admiten en Visual Studio 2017 RTM.<br/>
__VS 2017 15.3__ indica las características que se admiten en Visual Studio 2017 versión 15.3.<br/>
__VS 2017 15.5__ indica las características que se admiten en Visual Studio 2017, versión 15.5.<br/>
__VS 2017 15.7__ indica las características que se admiten en Visual Studio 2017, versión 15.7.<br/>

### <a name="notes"></a>Notas

<a name="note_A"></a>__A__ En el modo /std:c++14, las especificaciones de excepción dinámicas permanecen sin implementar y throw() se sigue tratando como un sinónimo de \_\_declspec(nothrow). En C++ 17, las especificaciones de excepción dinámicas se quitaron principalmente por P0003R5, dejando un vestigio: throw() está en desuso y se debe comportar como un sinónimo de noexcept. En el modo /std:c++17, MSVC ahora se ajusta al Estándar otorgando a throw() el mismo comportamiento que noexcept, es decir, cumplimiento a través de la terminación.

La opción del compilador /Zc:noexceptTypes-solicita el comportamiento anterior de \_\_declspec(nothrow). Es probable que throw() se quite en C++20. Para ayudar a migrar el código en respuesta a estos cambios en el Estándar y la implementación, se agregaron advertencias del compilador nuevas para problemas de especificación de excepciones en **/std:c++17** y **/permissive-**.

<a name="note_B"></a>__B__ Se admite en el modo /permissive-en Visual Studio 2017, versión 15.7. Vea [Two-phase name lookup support comes to MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/) (Compatibilidad con la búsqueda de nombres en dos fases para MSVC) para obtener más información.

<a name="note_C"></a>__C__ La compatibilidad del compilador para la expresión SFINAE ha sido suficiente para la biblioteca estándar desde Visual Studio 2015 Update 2. Se admite en Visual Studio 2017 15.7, con independencia de que se establezca el modo /permissive-. Hay algunos errores pendientes de corregirse. La solución alternativa de "tipo de etiqueta único" ya no es necesaria, y se ha quitado de la implementación de STL.

<a name="note_D"></a>__D__ La compatibilidad del compilador con las reglas del preprocesador C99 es incompleta en Visual Studio 2017. Se admiten las macros variádicas, pero se producen muchos errores en el comportamiento del preprocesador.  Se va a revisar el preprocesador y esos cambios se incluirán pronto de manera experimental en el modo **/permissive-**.

<a name="note_E"></a>__E__ Se ha marcado como N/D (No disponible) porque se permiten los compiladores, aunque no son necesarios, para admitir los tipos enteros extendidos.  Como GCC y Clang, hemos decidido no admitirlos.

<a name="note_F"></a>__F__ Del mismo modo, se ha marcado como N/D (No disponible) porque se permiten los compiladores, aunque no son necesarios, para implementar esta optimización.

<a name="note_G"></a>__G__ Compatible con [/std:c++14](../build/reference/std-specify-language-standard-version.md) con una advertencia que se puede suprimir.

<a name="note_J"></a>__J__ Las características que no se completaron en Visual Studio 2015 se dividen en otra parte de esta tabla.

<a name="note_K"></a>__K__ Esta es una implementación totalmente nueva, incompatible con la versión anterior de std::experimental, debido a la compatibilidad con symlink, las correcciones de errores y los cambios en el comportamiento requerido estándar. Actualmente, la inclusión de \<filesystem > proporciona la versión nueva de std::filesystem y la versión anterior de std::experimental::filesystem, y la inclusión de \<experimental/filesystem> solo proporciona la implementación experimental anterior. La implementación experimental se QUITARÁ en la próxima versión sin ABI de las bibliotecas.

<a name="note_L"></a>__L__ Compatible con una función intrínseca de compilador.

<a name="note_14"></a>__14__ Estas características de C++17/20 siempre están habilitadas, incluso cuando se especifica [/std:c++14](../build/reference/std-specify-language-standard-version.md) (el valor predeterminado). Esto se debe a que la característica se implementó antes de la introducción de las opciones **/std**, o bien porque la implementación condicional era indeseablemente compleja.

<a name="note_17"></a>__17__ Estas características están habilitadas por la opción del compilador [/std:c++17](../build/reference/std-specify-language-standard-version.md) (o [/std:c++latest](../build/reference/std-specify-language-standard-version.md)).

<a name="note_byte"></a>__byte__ `std::byte` está habilitada por [/std:c++17](../build/reference/std-specify-language-standard-version.md) (o [/std:c++latest](../build/reference/std-specify-language-standard-version.md)), pero como en algunos casos puede entrar en conflicto con los encabezados de Windows SDK, tiene una macro de desactivación específica. Se puede deshabilitar si se define `_HAS_STD_BYTE` como `0`.

<a name="note_C11"></a>__C11__ Universal CRT implementó los elementos de la biblioteca estándar C11 que se requieren en C++17, a excepción de los especificadores de conversión alternativos de E/O `strftime()` de C99, el modo exclusivo de `fopen()` de C11 y `aligned_alloc()` de C11. Es poco probable implementar esta última opción, porque C11 especificó `aligned_alloc()` de una manera no compatible con la implementación de Microsoft de `free()`, es decir, que `free()` debe poder controlar asignaciones altamente alineadas.

<a name="note_rem"></a>__rem__ Las características se quitan cuando se especifica la opción de compilador [/std:c++17](../build/reference/std-specify-language-standard-version.md) (o [/std:c++latest](../build/reference/std-specify-language-standard-version.md)). Estas características tienen macros de desactivación: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS` y `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ from_chars() y to_chars() están disponibles para los números enteros. Actualmente se está trabajando en from_chars() de punto flotante, y después seguirá to_chars() de punto flotante.

<a name ="note_parallel"></a> __parallel__  La biblioteca de algoritmos paralelos de C++17 se ha completado. Tenga en cuenta que esto no significa que todos los algoritmos se paralelicen en todos los casos; se han paralelizado los algoritmos más importantes y se proporcionan firmas de directiva de ejecución incluso cuando los algoritmos no están paralelizados. El encabezado interno central de nuestra implementación de STL, yvals.h, contiene las siguientes "Notas de algoritmos paralelos": C++ permite que una implementación implemente algoritmos paralelos como llamadas a algoritmos en serie.   Esta implementación paraleliza varias llamadas de algoritmo comunes, pero no todas.

Se paralelizan los algoritmos siguientes:

- adjacent_difference, adjacent_find, all_of, any_of, count, count_if, equal, exclusive_scan, find, find_end, find_first_of, find_if, for_each, for_each_n, inclusive_scan, mismatch, none_of, reduce, remove, remove_if, search, search_n, sort, stable_sort, transform, transform_exclusive_scan, transform_inclusive_scan, transform_reduce.

Los siguientes no se paralelizan en la actualidad:

- Ninguna mejora de rendimiento de paralelismo aparente en el hardware de destino; todos los algoritmos que simplemente copian o permutan elementos sin ramas suelen tener ancho de banda de memoria limitado:
  - copy, copy_backward, copy_n, fill, fill_n, move, move_backward, remove, remove_if, replace, replace_if, reverse, reverse_copy, rotate, rotate_copy, swap_ranges
- Existe confusión sobre los requisitos de paralelismo de usuario; es probable que al menos en la categoría anterior:
  - generate, generate_n
- El paralelismo efectivo parece no ser viable:
  - partial_sort, partial_sort_copy
- Todavía sin evaluar; es posible que el paralelismo se implemente en una versión futura y se sospecha que sea beneficioso:
  - copy_if, includes, inplace_merge, is_heap, is_heap_until, is_partitioned, is_sorted, is_sorted_until, lexicographical_compare, max_element, merge, min_element, minmax_element, nth_element, partition_copy, remove_copy, remove_copy_if, replace_copy, replace_copy_if, set_difference, set_intersection, set_symmetric_difference, set_union, stable_partition, unique, unique_copy

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Mejoras de conformidad de C++ en Visual Studio](cpp-conformance-improvements.md)<br/>
[Novedades de Visual C++ en Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Novedades de Visual C++ de 2003 a 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Novedades de Visual C++ de 2003 a 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[Blog del equipo de Visual C++](https://blogs.msdn.microsoft.com/vcblog/)
