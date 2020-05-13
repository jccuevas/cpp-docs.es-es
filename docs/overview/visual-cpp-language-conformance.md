---
title: Tabla de conformidad del lenguaje Microsoft C++
description: Tabla de actualizaciones de conformidad de Microsoft C++ por versión de Visual Studio.
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 18f8db28fab83f795baced82a346f07d73256716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365239"
---
# <a name="microsoft-c-language-conformance-table"></a>Tabla de conformidad del lenguaje Microsoft C++

Actualmente, se sigue trabajando en la conformidad con los estándares del compilador de Microsoft C++ en Visual Studio (MSVC). Este es un resumen del estándar ISO del lenguaje C++ y la conformidad de la biblioteca de la versión de Visual Studio. El nombre de cada una de las características del compilador y de la biblioteca estándar vincula al documento de propuesta del estándar ISO C++ que describe la característica, si hubiera alguno disponible en el momento de la publicación. La columna **Compatible** muestra la versión de Visual Studio en la que aparece por primera vez la compatibilidad de la característica.

Para más información sobre las mejoras de conformidad de Visual Studio 2017 o Visual Studio 2019 MSVC, consulte [Mejoras de conformidad de C++ en Visual Studio](cpp-conformance-improvements.md). Para obtener una lista de otros cambios, consulte [Novedades de C++ en Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Para conocer los cambios de conformidad en versiones anteriores, consulte [Historial de cambios en Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md) y [Novedades de Visual C++ de 2003 a 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Para mantenerse al tanto de las noticias actuales del equipo de C++, visite el [blog del equipo de C++](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> No existen cambios importantes binarios entre Visual Studio 2015, Visual Studio 2017 y Visual Studio 2019. Para más información, consulte [Compatibilidad binaria de C++ entre Visual Studio 2015, 2017 y 2019](../porting/binary-compat-2015-2017.md).

## <a name="compiler-features"></a>Características del compilador

|  |  |
|--|--|
| __Características principales del lenguaje C++03/11__ | __Compatible__ |
| &nbsp;&nbsp;Todo lo demás | VS 2015 <sup>[A](#note_A)</sup> |
| &nbsp;&nbsp;Búsqueda de nombres en dos fases | VS 2017 15.7 <sup>[B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 Expresión SFINAE](https://wg21.link/N2634) | VS 2017 15.7 |
| &nbsp;&nbsp;[N1653 Preprocesador C99](https://wg21.link/N1653) | Parcialmente <sup>[C](#note_C)</sup> |
| __Características principales del lenguaje C++14__ | __Compatible__ |
| &nbsp;&nbsp;[N3323 Redacción modificada para conversiones contextuales](https://wg21.link/N3323) | VS 2013 |
| &nbsp;&nbsp;[N3472 Literales binarios](https://wg21.link/N3472) | VS 2015 |
| &nbsp;&nbsp;[N3638 Tipos de valor devuelto auto y decltype(auto)](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-captures](https://wg21.link/n3648) | VS 2015 |
| &nbsp;&nbsp;[N3649 Lambdas genéricas](https://wg21.link/n3649) | VS 2015 |
| &nbsp;&nbsp;[N3760 \[\] Atributo](https://wg21.link/n3760)\[deprecated\] | VS 2015 |
| &nbsp;&nbsp;[N3778 Desasignación de tamaño](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3781 Separadores de dígitos](https://wg21.link/n3781) | VS 2015 |
| &nbsp;&nbsp;[N3651 Plantillas de variables](https://wg21.link/n3651) | VS 2015.2 |
| &nbsp;&nbsp;[N3652 constexpr extendido](https://wg21.link/n3652) | VS 2017 15.0 |
| &nbsp;&nbsp;[N3653 Inicializadores de miembro predeterminados para agregados](https://wg21.link/n3653) | VS 2017 15.0 |
| __Características principales del lenguaje C++17__ | __Compatible__ |
| &nbsp;&nbsp;[N4086 Eliminación de trígrafos](https://wg21.link/n4086) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 Nuevas reglas para auto con listas de inicialización entre llaves](https://wg21.link/n3922) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4051 typename en parámetros de plantilla](https://wg21.link/n4051) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4266 Atributos de espacios de nombres y enumeradores](https://wg21.link/n4266) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4267 Literales de caracteres de u8](https://wg21.link/n4267) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4230 Definiciones de espacio de nombres anidadas](https://wg21.link/n4230) | VS 2015.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 static_assert breve](https://wg21.link/n3928) | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 Bucles for basados en intervalos generalizados](https://wg21.link/p0184r0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0188R1 \[\] Atributo](https://wg21.link/p0188r1)\[ fallthrough\] | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 Quitar la palabra clave register](https://wg21.link/p0001r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 Quitar operator++ para bool](https://wg21.link/p0002r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 Captura de *this por valor](https://wg21.link/p0018r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 Uso de espacios de nombres de atributo sin repetición](https://wg21.link/p0028r4) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0061R1 \_\_has_include](https://wg21.link/p0061r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 Inicialización de lista directa de enumeraciones fijas de enteros](https://wg21.link/p0138r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 Lambdas de constexpr](https://wg21.link/p0170r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0189R1 \[\] Atributo](https://wg21.link/p0189r1)\[ nodiscard\] | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0212R1 \[\] Atributo](https://wg21.link/p0212r1)\[ maybe_unused\] | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0217R3 Enlaces estructurados](https://wg21.link/p0217r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 Instrucciones if constexpr](https://wg21.link/p0292r2) | VS 2017 15.3 <sup>[D](#note_D)</sup> |
| &nbsp;&nbsp;[P0305R1 Instrucciones de selección con inicializadores](https://wg21.link/p0305r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 Literales Hexfloat](https://wg21.link/p0245r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268 Permitir más argumentos de plantilla sin tipo](https://wg21.link/n4268) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4295 Expresiones plegadas](https://wg21.link/n4295) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Quitar especificaciones de excepción dinámicas](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 Agregar noexcept al sistema de tipos](https://wg21.link/p0012r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 Asignación de memoria dinámica alineada en exceso](https://wg21.link/p0035r4) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0386R2 Variables insertadas](https://wg21.link/p0386r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 Coincidencia de parámetros de plantilla con argumentos compatibles](https://wg21.link/p0522r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 Quitar algunos pliegues unarios vacíos](https://wg21.link/p0036r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 Corregir conversiones de cualificación](https://wg21.link/n4261) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 Inicialización de agregados extendidos](https://wg21.link/p0017r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0091R3 Deducción de argumentos de plantilla para plantillas de clase](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;[P0512R0 Problemas de deducción de argumento para plantilla de clase](https://wg21.link/p0512r0) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 Declarar parámetros de plantilla sin tipo con auto](https://wg21.link/p0127r2) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 Elisión de copia garantizada](https://wg21.link/p0135r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0136R1 Nueva redacción de constructores de herencia](https://wg21.link/p0136r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std::launder](https://wg21.link/p0137r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0145R3 Refinar el orden de evaluación de expresiones](https://wg21.link/p0145r3)<br/>&nbsp;&nbsp;[P0400R0 Orden de evaluación de los argumentos de función](https://wg21.link/p0400r0) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0195R2 Expansiones del paquete en declaraciones using](https://wg21.link/p0195r2) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 Omitir atributos no reconocidos](https://wg21.link/p0283r2) | VS 2015 <sup>[14](#note_14)</sup> |
| __Características principales del lenguaje C++17 (informes de defectos)__ | __Compatible__ |
| &nbsp;&nbsp;[P0702R1 Corrección de deducción de argumento de plantilla para constructores initializer-list](https://wg21.link/p0702r1) | VS 2017 15.7 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1 Relajación de las reglas de búsqueda de punto de personalización de los enlaces estructurados](https://wg21.link/p0961r1) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0 Allowing structured bindings to accessible members](https://wg21.link/p0969r0) (Permitir enlaces estructurados para miembros accesibles) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1 Simplifying implicit lambda capture](https://wg21.link/p0588r1) (Simplificación de la captura de lambda implícita) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 \[\[nodiscard\]\] para constructores](https://wg21.link/p1771r1) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0 palabras combinadas para P0527R1 y P1155R3, más movimientos implícitos](https://wg21.link/p1825r0) | VS 2019 16.4 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2 Comprobación de tipos de clases abstractas](https://wg21.link/P0929R2) | No |
| &nbsp;&nbsp;[P0962R2 Relaxing the range-for loop customization point finding rules](https://wg21.link/p0962r1) (Relajación de las reglas de búsqueda de punto de personalización de los bucles range-for) | No |
| &nbsp;&nbsp;[P0859R0 CWG 1581: ¿Cuándo se definen las funciones miembro de las expresiones constantes?](https://wg21.link/p0859r0) | No |
| &nbsp;&nbsp;[P1009R2 Deducción del tamaño de la matriz en nuevas expresiones](https://wg21.link/P1009R2) | No |
| &nbsp;&nbsp;[P1286R2 Contra CWG DR1778](https://wg21.link/P1286R2) | No |
| __Características principales del lenguaje C++20__ | __Compatible__ |
| &nbsp;&nbsp;[P0704R1 Correción de los punteros const lvalue ref-qualified a los miembros](https://wg21.link/p0704r1) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4 Convertir los literales de cadena char16_t/char32_t en UTF-16/32](https://wg21.link/P1041R4) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0 Cambio del miembro activo dentro de una unión en constexpr](https://wg21.link/P1330R0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0 noexcept para \<chrono> zero(), min(), max()](https://wg21.link/P0972R0) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 Operador de comparación tridireccional (spaceship) <=>](https://wg21.link/P0515R3) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0941R2 Macros para la prueba de características](https://wg21.link/P0941R2) | VS 2019 16.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1 Prohibición de agregados con constructores declarados por el usuario](https://wg21.link/P1008R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0329R4 Inicialización designada](https://wg21.link/p0329r4) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0 Plantillas de ADL y funciones que no están visibles](https://wg21.link/P0846R0) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2 Permitir captura lambda \[=, this\]](https://wg21.link/p0409r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 Sintaxis de plantilla familiar para expresiones lambda genéricas](https://wg21.link/p0428r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2 Lambdas sin estado asignables y construibles predeterminadas](https://wg21.link/P0624R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2 Permitir la expansión de paquetes en lambda init-capture](https://wg21.link/P0780R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2 Dejar de usar la captura implícita de esto mediante \[=\]](https://wg21.link/P0806R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0 Mejoras de coherencia para <=> y otros operadores de comparación](https://wg21.link/P1120R0) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2 \<=\> != ==](https://wg21.link/P1185R2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0734R0 Conceptos](https://wg21.link/P0734R0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0 Corrección de lagunas de funcionalidad en las restricciones](https://wg21.link/P0857R0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2 Los requisitos de tipo de valor devuelto de hoy en día son insuficientes](https://wg21.link/P1084R2) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2 Condicional explícito](https://wg21.link/P0892R2) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3 Extensión de los enlaces estructurados para que se asemejen a las declaraciones de variables](https://wg21.link/P1091R3) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5 Uso de enumeración](https://wg21.link/P1099R5) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3 Cuándo se usa realmente \<=>](https://wg21.link/P1186R3) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1630R1 Spaceship necesita un ajuste](https://wg21.link/P1630R1) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 Incorporación de \_\_VA_OPT\_\_ para la omisión de comas y la eliminación de comas](https://wg21.link/P0306R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1 Bucles for basado en intervalo con inicializadores](https://wg21.link/P0614R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 Inicializadores de miembro predeterminado para los campos de bits](https://wg21.link/P0683R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1002R1 Bloques try-catch en funciones constexpr](https://wg21.link/P1002R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 Desuso del operador de coma en expresiones de subíndice](https://wg21.link/P1161R3) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[\[nodiscard("message")\]\]](https://wg21.link/P1301R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1 El reconocimiento de importaciones de unidades de encabezado requiere el preprocesamiento completo](https://wg21.link/P1703R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 Permitir comparaciones predeterminadas por valor](https://wg21.link/P1946R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0641R2 Coincidencia de const con el constructor de copia predeterminado](https://wg21.link/P0641R2) | Parcial |
| &nbsp;&nbsp;[P0912R5 Corrutinas](https://wg21.link/P0912R5) | Parcial |
| &nbsp;&nbsp;[P1103R3 Módulos](https://wg21.link/P1103R3) | Parcial |
| &nbsp;&nbsp;[P0315R4 Permitir lambdas en contextos no evaluados](https://wg21.link/P0315R4) | No |
| &nbsp;&nbsp;[P0388R4 Permitir conversiones en matrices con límites desconocidos](https://wg21.link/P0388R4) | No |
| &nbsp;&nbsp;[P0479R5 \[\] Atributos](https://wg21.link/P0479R5)\[likely\]\] y \[\[unlikely\] | No |
| &nbsp;&nbsp;[P0634R3 Eliminación de typename](https://wg21.link/P0634R3) | No |
| &nbsp;&nbsp;[P0692R1 Relación de la comprobación de acceso en las especializaciones](https://wg21.link/P0692R1) | No |
| &nbsp;&nbsp;[P0722R3 Eliminación dimensionada eficaz para clases dimensionadas de variables](https://wg21.link/P0722R3) | No |
| &nbsp;&nbsp;[P0732R2 Tipos de clases en parámetros de plantilla sin tipo](https://wg21.link/P0732R2) | No |
| &nbsp;&nbsp;[P0735R1 Interacción de memory_order_consume con secuencias de versión](https://wg21.link/P0735R1) | No |
| &nbsp;&nbsp;[P0784R7 Más contenedores constexpr](https://wg21.link/P0784R7) | No |
| &nbsp;&nbsp;[P0840R2 \[\]Atributo](https://wg21.link/P0840R2)\[no_unique_address\] | No |
| &nbsp;&nbsp;[P0848R3 Funciones miembro especiales triviales según determinadas condiciones](https://wg21.link/P0848R3) | No |
| &nbsp;&nbsp;[P0960R3 Permitir la inicialización de agregados desde una lista de valores entre paréntesis](https://wg21.link/P0960R3) | No |
| &nbsp;&nbsp;[P1064R0 Permitir las llamadas a funciones virtuales en expresiones constantes](https://wg21.link/P1064R0) | No |
| &nbsp;&nbsp;[P1073R3 Funciones inmediatas](https://wg21.link/P1073R3) | No |
| &nbsp;&nbsp;[P1094R2 Espacios de nombres insertados anidados](https://wg21.link/P1094R2) | No |
| &nbsp;&nbsp;[P1139R2 Solucionar problemas de redacción relacionados con la norma ISO 10646](https://wg21.link/P1139R2) | No |
| &nbsp;&nbsp;[P1141R2 Otro enfoque para las declaraciones restringidas](https://wg21.link/P1141R2) | No |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | No |
| &nbsp;&nbsp;[P1152R4 Desuso de elementos volátiles](https://wg21.link/P1152R4) | No |
| &nbsp;&nbsp;[P1236R1 Los enteros con signo son un complemento a dos](https://wg21.link/P1236R1) | No |
| &nbsp;&nbsp;[P1327R1 Permitir dynamic_cast y typeid polimórfico en expresiones constantes](https://wg21.link/P1327R1) | No |
| &nbsp;&nbsp;[P1331R2 Permitir la inicialización trivial predeterminada en contextos constexpr](https://wg21.link/P1331R2) | No |
| &nbsp;&nbsp;[P1353R0 Macros de prueba de características faltantes](https://wg21.link/P1353R0) | No |
| &nbsp;&nbsp;[P1381R1 Captura de referencia de enlaces estructurados](https://wg21.link/P1381R1) | No |
| &nbsp;&nbsp;[P1452R2 Semántica no uniforme de requisitos de tipo de valor devuelto](https://wg21.link/P1452R2) | No |
| &nbsp;&nbsp;[P1616R1 Uso de TTP sin restricciones con plantillas restringidas](https://wg21.link/P1616R1) | No |
| &nbsp;&nbsp;[P1668R1 Permitir el ensamblado alineado no evaluado en funciones constexpr](https://wg21.link/P1668R1) | No |
| &nbsp;&nbsp;[P1766R1 Mitigación de enfermedades de módulos menores](https://wg21.link/P1766R1) | No |
| &nbsp;&nbsp;[P1811R0 Relajación de la restricciones de redefinición para la solidez de la reexportación](https://wg21.link/P1811R0) | No |
| &nbsp;&nbsp;[P1814R0 CTAD para plantillas de alias](https://wg21.link/P1814R0) | No |
| &nbsp;&nbsp;[P1816R0 CTAD para agregados](https://wg21.link/P1816R0) | No |
| &nbsp;&nbsp;[P1874R1 Orden de inicialización dinámica de variables no locales en módulos](https://wg21.link/P1874R1) | No |
| &nbsp;&nbsp;[P1907R1 Incoherencias con parámetros de plantilla sin tipo](https://wg21.link/P1907R1) | No |
| &nbsp;&nbsp;[P1971R0 Cambios importantes en comentarios de NB en la reunión de noviembre de 2019 (Belfast)](https://wg21.link/P1971R0) | No |
| &nbsp;&nbsp;[P1972R0 US105 Comprobación de la satisfacción de las restricciones para recursos que no son plantillas al formar un puntero a una función](https://wg21.link/P1972R0) | No |
| &nbsp;&nbsp;[P1975R0 Corrección del texto de la inicialización entre paréntesis](https://wg21.link/P1975R0) | No |
| &nbsp;&nbsp;[P1979R0 Resolución de US086](https://wg21.link/P1979R0) | No |
| &nbsp;&nbsp;[P1980R0 CA096: la coincidencia de declaraciones para cláusulas "requires" no dependientes](https://wg21.link/P1980R0) | No |

## <a name="standard-library-features"></a>Características de la biblioteca estándar

|  |  |
|--|--|
| __Características de la biblioteca estándar de C++20__ | __Compatible__ |
| &nbsp;&nbsp;[P0809R0 Comparing Unordered Containers](https://wg21.link/p0809r0) (Comparación de contenedores sin ordenar) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0858R0 Constexpr Iterator Requirements](https://wg21.link/p0858r0) (Requisitos del iterador de expresiones constantes) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1 Evitar la decadencia innecesaria](https://wg21.link/p0777r1) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1 Convertir create_directory() e intuitivo](https://wg21.link/P1164R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0550R2 remove_cvref](https://wg21.link/p0550r2) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2 starts_with()/ends_with() para basic_string/basic_string_view](https://wg21.link/p0457r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 contains() para contenedores asociativos ordenados y desordenados](https://wg21.link/p0458r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1 Tipo de tamaño devuelto list/forward_list remove()/remove_if()/unique()](https://wg21.link/p0646r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2 shift_left(), shift_right()](https://wg21.link/p0769r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1 type_identity](https://wg21.link/p0887r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6 atomic\<float>, atomic\<double>, atomic\<long double>](https://wg21.link/p0020r6) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 endian](https://wg21.link/p0463r1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t: un tipo para los caracteres y las cadenas UTF-8](https://wg21.link/P0482R6) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1 \[\[nodiscard\]\] para STL, parte 1](https://wg21.link/p0600r1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2 \<version>](https://wg21.link/p0754r2) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1 noexcept para el constructor de movimiento de std::function](https://wg21.link/P0771R1) | VS 2019 16.2 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1 Corrección de operador>>(basic_istream&, CharT*)](https://wg21.link/P0487R1) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0 Uso de move() en \<numeric>](https://wg21.link/p0616r0) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0898R3 Conceptos de la biblioteca estándar](https://wg21.link/P0898R3) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3 Búsqueda heterogénea para contenedores desordenados](https://wg21.link/P0919R3) | VS 2019 16.3 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1 Cambio de nombre de los conceptos a standard_case](https://wg21.link/P1754R1) | VS 2019 16.4 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 to_array de LFTS con actualizaciones](https://wg21.link/P0325R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3 underlying_type compatible con SFINAE](https://wg21.link/P0340R3) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0439R0 Clase de enumeración memory_order](https://wg21.link/p0439r0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<bit> Funciones de rotación y recuento](https://wg21.link/P0553R4) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \<bit> ispow2(), ceil2(), floor2(), log2p1()](https://wg21.link/P0556R3) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0631R8 \<números> Constantes matemáticas](https://wg21.link/P0631R8) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2 Limpieza de istream_iterator](https://wg21.link/P0738R2) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1 Poner en desuso is_pod](https://wg21.link/P0767R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1 string::reserve() no debe reducirse](https://wg21.link/P0966R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0 erase_if(), erase()](https://wg21.link/P1209R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2 std::ssize() con signo y span::size() sin signo](https://wg21.link/P1227R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 Estrechamiento del contacto con ceil2()](https://wg21.link/P1355R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 Reubicación de endian en \<bit >](https://wg21.link/P1612R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front() No debe desencapsular reference_wrapper](https://wg21.link/P1651R0) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1 Refinamiento de la búsqueda heterogénea de contenedores desordenados](https://wg21.link/P1690R1) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 Macros de prueba de características faltantes 2017-2019](https://wg21.link/P1902R1) | VS 2019 16.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8) | No |
| &nbsp;&nbsp;[P0053R7 \<syncstream>](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[P0753R2 Manipuladores de osyncstream](https://wg21.link/p0753r2) | No |
| &nbsp;&nbsp;[P0122R7 \<span>](https://wg21.link/p0122r7) | No |
| &nbsp;&nbsp;[P0202R3 Expresión constante para \<algorithm> y exchange()](https://wg21.link/p0202r3) | No |
| &nbsp;&nbsp;[P0339R6 polymorphic_allocator<>](https://wg21.link/P0339R6) | No |
| &nbsp;&nbsp;[P0355R7 Calendarios y zonas horarias de \<chrono>](https://wg21.link/p0355r7) | No |
| &nbsp;&nbsp;[P0357R3 Tipos incompletos compatibles en reference_wrapper](https://wg21.link/P0357R3) | No |
| &nbsp;&nbsp;[P0415R1 Expresión constante para \<complex> (Again)](https://wg21.link/p0415r1) | No |
| &nbsp;&nbsp;[P0475R1 Omisión de copia garantizada para construcción de tramos](https://wg21.link/P0475R1) | No |
| &nbsp;&nbsp;[P0476R2 \<bit> bit_cast](https://wg21.link/P0476R2) | No |
| &nbsp;&nbsp;[P0528R3 Comparación e intercambio atómicos con bits de relleno](https://wg21.link/P0528R3) | No |
| &nbsp;&nbsp;[P0591R4 Funciones de utilidad para construcciones Uses-Allocator](https://wg21.link/P0591R4) | No |
| &nbsp;&nbsp;[P0608R3 Mejora de la asignación y el constructor de conversión de variantes](https://wg21.link/P0608R3) | No |
| &nbsp;&nbsp;[P0619R4 Quitar las características en desuso de C++17 en C++20](https://wg21.link/P0619R4) | No |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | No |
| &nbsp;&nbsp;[P0655R1 visit\<R>()](https://wg21.link/P0655R1) | No |
| &nbsp;&nbsp;[P0674R1 make_shared() para matrices](https://wg21.link/p0674r1) | No |
| &nbsp;&nbsp;[P0718R2 atomic\<shared_ptr\<T>>, atomic\<weak_ptr\<T>>](https://wg21.link/p0718r2) | No |
| &nbsp;&nbsp;[P0768R1 Compatibilidad con bibliotecas para el operador de comparación de nave espacial \<=>](https://wg21.link/p0768r1) | No |
| &nbsp;&nbsp;[P0811R3 midpoint(), lerp()](https://wg21.link/P0811R3) | No |
| &nbsp;&nbsp;[P0879R0 constexpr para funciones de intercambio](https://wg21.link/P0879R0) | No |
| &nbsp;&nbsp;[P0896R4 \<ranges\>](https://wg21.link/P0896R4) | No |
| &nbsp;&nbsp;[P0912R5 Compatibilidad de la biblioteca para corrutinas](https://wg21.link/P0912R5) | No |
| &nbsp;&nbsp;[P0920R2 Búsqueda de valores hash precalculados](https://wg21.link/P0920R2) | No |
| &nbsp;&nbsp;[P0935R0 Erradicación de constructores predeterminados explícitos innecesarios](https://wg21.link/P0935R0) | No |
| &nbsp;&nbsp;[P1001R2 execution::unseq](https://wg21.link/P1001R2) | No |
| &nbsp;&nbsp;[P1006R1 constexpr para pointer_traits<T*>::pointer_to()](https://wg21.link/P1006R1) | No |
| &nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3) | No |
| &nbsp;&nbsp;[P1020R1 Creación de puntero inteligente con inicialización predeterminada](https://wg21.link/P1020R1) | No |
| &nbsp;&nbsp;[P1023R0 constexpr para las comparaciones std::array](https://wg21.link/P1023R0) | No |
| &nbsp;&nbsp;[P1032R1 Varios elementos constexpr](https://wg21.link/P1032R1) | No |
| &nbsp;&nbsp;[P1165R1 Propagación coherente de asignadores sin estado en el operador +() basic_string](https://wg21.link/P1165R1) | No |
| &nbsp;&nbsp;[P1285R0 Mejora de los requisitos de integridad de los rasgos de tipo](https://wg21.link/P1285R0) | No |
| __Características de la biblioteca estándar de C++17__ | __Compatible__ |
| &nbsp;&nbsp;[LWG 2221 Operador de salida con formato para nullptr](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16.1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 Conversiones seguras en unique_ptr\<T[]>](https://wg21.link/n4089) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 invoke()](https://wg21.link/n4169) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 Quitar auto_ptr, random_shuffle() y elementos \<functional> antiguos](https://wg21.link/n4190) | VS 2015 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 Limpiezas de noexcept](https://wg21.link/n4258) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions()](https://wg21.link/n4259) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 reference_wrapper que se puede copiar de forma trivial](https://wg21.link/n4277) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() para map/unordered_map](https://wg21.link/n4279) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 size(), empty(), data()](https://wg21.link/n4280) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 Asignación unique_ptr con restricción precisa](https://wg21.link/n4366) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 Mejorar pair y tuple](https://wg21.link/n4387) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4389 bool_constant](https://wg21.link/n4389) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (no cronometrado)](https://wg21.link/n4508) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510 Admitir tipos incompletos en vector/list/forward_list](https://wg21.link/n4510) | VS 2013 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<algorithm> sample()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<any>](https://wg21.link/n4562#any) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<memory_resource>](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 Eliminar la asignación de polymorphic_allocator](https://wg21.link/p0337r0) | VS 2017 15.6 |
| &nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<optional>](https://wg21.link/n4562#optional) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<string_view>](https://wg21.link/n4562#string.view) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: \<tuple> apply()](https://wg21.link/n4562#tuple) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Elementos fundamentales de biblioteca: búsqueda Boyer-Moore()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Corregir tipos de valor devueltos de buscadores](https://wg21.link/p0253r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Quitar especificaciones de excepción dinámicas](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 Quitar alias Iostreams en desuso](https://wg21.link/p0004r1) | VS 2015.2 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 Correcciones para not_fn()](https://wg21.link/p0358r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0006R0 Plantillas de variables para rasgos de tipos (is_same_v, etc.)](https://wg21.link/p0006r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const()](https://wg21.link/p0007r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0013R1 Rasgos de tipos de operadores lógicos (conjunción, etc.)](https://wg21.link/p0013r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0024R2 Algoritmos paralelos](https://wg21.link/p0024r2)<br/>&nbsp;&nbsp;[P0336R1 Cambiar el nombre de directivas de ejecución en paralelo](https://wg21.link/p0336r1)<br/>&nbsp;&nbsp;[P0394R4 Los algoritmos paralelos deben invocar terminate() para las excepciones](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 Unificación de algoritmos paralelos \<numeric>](https://wg21.link/p0452r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0025R1 clamp()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot(x, y, z)](https://wg21.link/p0030r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0031R0 constexpr para \<array> (otra vez) e \<iterator>](https://wg21.link/p0031r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 Interfaz homogénea para variant/any/optional](https://wg21.link/p0032r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0033R1 Nueva redacción de enable_shared_from_this](https://wg21.link/p0033r1) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 Extender herramientas de administración de memoria](https://wg21.link/p0040r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0063R3 Biblioteca estándar de C11](https://wg21.link/p0063r3) | VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0067R5 Conversiones de cadenas elementales](https://wg21.link/p0067r5) | VS 2019 16.4 <sup>[charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0083R3 Insertar asignaciones y conjuntos](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 Aclarar insert_return_type](https://wg21.link/p0508r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0084R2 Tipo de valor devuelto emplace](https://wg21.link/p0084r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0088R3 \<variant>](https://wg21.link/p0088r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0092R1 \<chrono> floor(), ceil(), round(), abs()](https://wg21.link/p0092r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size, etc.](https://wg21.link/p0154r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 lock_guard variádico](https://wg21.link/p0156r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 Cambio de nombre de lock\_guard to scoped\_lock](https://wg21.link/p0156r2) variádico | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](https://wg21.link/p0163r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0174R2 Dejar en desuso vestigios de elementos de biblioteca](https://wg21.link/p0174r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple()](https://wg21.link/p0209r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0218R1 \<filesystem>](https://wg21.link/p0218r1)<br/>&nbsp;&nbsp;[P0219R1 Rutas de acceso relativas para el sistema de archivos](https://wg21.link/p0219r1)<br/>&nbsp;&nbsp;[P0317R1 Almacenamiento en caché de entrada de directorio para el sistema de archivos](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[P0392R0 Compatibilidad con string_view en las rutas de acceso del sistema de archivos](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2 Compatibilidad con sistemas de archivos no POSIX](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 Resolución de comentarios NB para el sistema de archivos](https://wg21.link/p0492r2) | VS 2017 15.7 <sup>[E](#note_E)</sup> |
| &nbsp;&nbsp;[P0220R1 Elementos fundamentales de biblioteca V1](https://wg21.link/p0220r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0226R1 Funciones matemáticas especiales](https://wg21.link/p0226r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0254R2 Integración de string_view y std::string](https://wg21.link/p0254r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0258R2 has_unique_object_representations](https://wg21.link/p0258r2) | VS 2017 15.3 <sup>[G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 basic_string::data() no constante](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 gcd(), lcm()](https://wg21.link/p0295r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std::byte](https://wg21.link/p0298r3) | VS 2017 15.3 <sup>[17](#note_17),&nbsp;[byte](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 Quitar la compatibilidad con el asignador en std::function](https://wg21.link/p0302r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2 Hacer que mayor igual sea opcional otra vez](https://wg21.link/p0307r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0393R3 Hacer que mayor igual sea variante](https://wg21.link/p0393r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0403R1 Archivos UDL para \<string_view> ("meow"sv, etc.)](https://wg21.link/p0403r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 Corregir shared_ptr para matrices](https://wg21.link/p0497r0) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0418R2 Requisitos atómicos de compare_exchange memory_order](https://wg21.link/p0418r2) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 constexpr para char_traits](https://wg21.link/p0426r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0433R2 Integración de deducción de plantilla para plantillas de clase en la biblioteca estándar](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 Mejora de la integración de deducción de argumento de plantilla de clase en la biblioteca estándar](https://wg21.link/p0739r0) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0435R1 Revisión de common_type](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1 Ajuste de common\_type y duration](https://wg21.link/p0548r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 Revisión de in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](https://wg21.link/p0504r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0505R0 constexpr para \<chrono> (otra vez)](https://wg21.link/p0505r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 Rechazar variantes de vacío, matrices, referencias y tipos incompletos](https://wg21.link/p0510r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0513R0 Hash de tipo "poisoning"](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 Hash noexcept](https://wg21.link/p0599r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0516R0 Marcar la copia de shared_future como noexcept](https://wg21.link/p0516r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 Construir future_error a partir de future_errc](https://wg21.link/p0517r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 Dejar en desuso shared_ptr::unique()](https://wg21.link/p0521r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1 Resolución de incoherencias de clase base con nombre atomic\<T>](https://wg21.link/p0558r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16.5 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4 Propagación de la trivialidad de copia y movimiento en variante/opcional](https://wg21.link/P0602R4) | VS 2017 15.3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 Cambio de\_callable/result\_of To invoke\_result, es\_invocable, es\_nothrow\_invocable](https://wg21.link/p0604r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0607R0 Variables insertadas para la biblioteca estándar](https://wg21.link/p0607r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0618R0 \<codecvt>](https://wg21.link/p0618r0) en desuso | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1 Reparación de conversiones de cadenas elementales](https://wg21.link/P0682R1) | VS 2015 15.7 <sup>[17](#note_17)</sup> |
| __Características de la biblioteca estándar de C++14__ | __Compatible__ |
| &nbsp;&nbsp;[N3462 result_of compatible con SFINAE](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 constexpr para \<complex>](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 constexpr para \<chrono>](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 constexpr para \<array>](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 constexpr para \<initializer_list>, \<tuple> y \<utility>](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant::operator()()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 Archivos UDL para \<chrono> y \<string> (1729ms, "meow"s, etc.)](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644 Iteradores hacia delante nulos](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 quoted()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 Búsqueda asociativa heterogénea](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex (cronometrado)](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 exchange()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 Corregir funciones miembro constexpr sin const](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670 get\<T>()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 equal(), is_permutation() y mismatch() de doble intervalo](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[N3778 Desasignación de tamaño](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 Archivos UDL para \<complex> (3.14i, etc.)](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 constexpr para \<functional>](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[N3887 tuple_element_t](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 Cambiar el nombre de shared_mutex (cronometrado) a shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[N3346 Requisitos mínimos de elemento contenedor](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 Objetos functor de operador transparentes (less\<>, etc.)](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[N3655 Plantillas de alias para \<type_traits> (decay_t, etc.)](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique()](https://wg21.link/n3656) | VS 2013 |

Un grupo de artículos enumerados juntos indica una característica estándar junto con una o varias mejoras o expansiones aprobadas. Estas características se implementan juntas.

### <a name="supported-values"></a>Valores admitidos

__No__ significa que aún no se ha implementado.\
__Parcial__ significa que la implementación está incompleta. Para más información, consulte la sección Notas.\
__VS 2010__ indica las características que se admiten en Visual Studio 2010.\
__VS 2013__ indica las características que se admiten en Visual Studio 2013.\
__VS 2015__ indica las características que se admiten en Visual Studio 2015 (RTW).\
__VS 2015.2__ y __VS 2015.3__ indican las características que se admiten en Visual Studio 2015 Update 2 y Visual Studio 2015 Update 3, respectivamente.\
__VS 2017 15.0__ indica las características que se admiten en Visual Studio 2017, versión 15.0 (RTW).\
__VS 2017 15.3__ indica las características que se admiten en Visual Studio 2017, versión 15.3.\
__VS 2017 15.5__ indica las características que se admiten en Visual Studio 2017, versión 15.5.\
__VS 2017 15.7__ indica las características que se admiten en Visual Studio 2017, versión 15.7.\
__VS 2019 16.0__ indica las características que se admiten en Visual Studio 2019, versión 16.0 (RTW).\
__VS 2019 16.1__ indica las características que se admiten en Visual Studio 2019, versión 16.1.\
__VS 2019 16.2__ indica las características que se admiten en Visual Studio 2019, versión 16.2.\
__VS 2019 16.3__ indica las características que se admiten en Visual Studio 2019, versión 16.3.\
__VS 2019 16.4__ indica las características que se admiten en Visual Studio 2019, versión 16.4.\
__VS 2019 16.5__ indica las características que se admiten en Visual Studio 2019, versión 16.5.

### <a name="notes"></a>Notas

<a name="note_A"></a> __A__ En el modo [/std:c++14](../build/reference/std-specify-language-standard-version.md), las especificaciones de excepción dinámicas permanecen sin implementar y `throw()` se sigue tratando como un sinónimo de `__declspec(nothrow)`. En C++ 17, las especificaciones de excepción dinámicas se quitaron principalmente por P0003R5, dejando un vestigio: `throw()` está en desuso y se debe comportar como un sinónimo de `noexcept`. En el modo [/std:c++17](../build/reference/std-specify-language-standard-version.md), MSVC ahora se ajusta al Estándar al otorgar a `throw()` el mismo comportamiento que `noexcept`, es decir, cumplimiento mediante la terminación.

La opción del compilador [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) solicita el comportamiento anterior de `__declspec(nothrow)`. Es probable que `throw()` se quite en C++20. Para ayudar a migrar el código en respuesta a estos cambios en el Estándar y la implementación, se agregaron advertencias del compilador nuevas para problemas de especificación de excepciones en [/std:c++17](../build/reference/std-specify-language-standard-version.md) y [/permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a> __B__ Se admite en el modo [/permissive-](../build/reference/permissive-standards-conformance.md) Visual Studio 2017, versión 15.7. Para más información, consulte [La compatibilidad con la búsqueda de nombres en dos fases llega a MSVC](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/).

<a name="note_C"></a> __C__ La compatibilidad del compilador con las reglas del preprocesador C99 es incompleta en Visual Studio 2017. Se va a revisar el preprocesador y hemos empezado a incluir esos cambios en Visual Studio 2017, versión 15.8 con el conmutador de compilador [/experimental:preprocessor](../build/reference/experimental-preprocessor.md).

<a name="note_D"></a> __D__ Compatible con [/std:c++14](../build/reference/std-specify-language-standard-version.md) con una advertencia que se puede suprimir, [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md).

<a name="note_E"></a> __E__ Esta es una implementación completamente nueva, incompatible con la versión anterior de `std::experimental`, necesaria por la compatibilidad con symlink, las correcciones de errores y los cambios en el comportamiento requerido estándar. Actualmente, la inclusión de \<filesystem> proporciona la versión nueva de `std::filesystem` y la versión anterior de `std::experimental::filesystem`, y la inclusión de \<experimental/filesystem> solo proporciona la implementación experimental anterior. La implementación experimental se QUITARÁ en la próxima versión sin ABI de las bibliotecas.

<a name="note_G"></a> __G__ Compatible con una función intrínseca de compilador.

<a name="note_14"></a> __14__ Estas características de C++17/20 siempre están habilitadas, incluso cuando se especifica [/std:c++14](../build/reference/std-specify-language-standard-version.md) (valor predeterminado). El motivo es que la característica se implementó antes de la introducción de las opciones **/std**, o porque la implementación condicional era compleja de una manera no deseable.

<a name="note_17"></a> __17__ Estas características se habilitan mediante la opción del compilador [/std:c++17](../build/reference/std-specify-language-standard-version.md) (o [/std:c++latest](../build/reference/std-specify-language-standard-version.md)).

<a name="note_20"></a> __20__ Estas características se habilitan mediante la opción del compilador [/std:c++latest](../build/reference/std-specify-language-standard-version.md). Si la implementación de C++20 es completa, se agregará una nueva opción del compilador **/std:c++20**, en la que estas características también estarán disponibles.

<a name="note_byte"></a> __byte__ `std::byte` se habilita mediante [/std:c++17](../build/reference/std-specify-language-standard-version.md) (o [/std:c++latest](../build/reference/std-specify-language-standard-version.md)), pero como en algunos casos puede entrar en conflicto con los encabezados de Windows SDK, tiene una macro de desactivación específica. Se puede deshabilitar si se define `_HAS_STD_BYTE` como `0`.

<a name="note_C11"></a> __C11__ Universal CRT implementó los elementos de la biblioteca estándar C11 que se requieren en C++17, a excepción de los especificadores de conversión alternativos de E/O `strftime()` de C99, el modo exclusivo de `fopen()` de C11 y `aligned_alloc()` de C11. Es poco probable implementar esta última opción, porque C11 especificó `aligned_alloc()` de una manera no compatible con la implementación de Microsoft de `free()`: es decir, que `free()` debe poder controlar asignaciones muy alineadas.

<a name="note_rem"></a> __rem__ Las características se quitan cuando se especifica la opción de compilador [/std:c++17](../build/reference/std-specify-language-standard-version.md) (o [/std:c++latest](../build/reference/std-specify-language-standard-version.md)). Estas características pueden habilitarse de nuevo para facilitar la transición a los modos de lenguaje más recientes mediante el uso de estas macros: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS` y `_HAS_UNEXPECTED`.

<a name="note_charconv"></a> __charconv__ `from_chars()` y `to_chars()` están disponibles para los enteros. La escala de tiempo de punto flotante `from_chars()` y de punto flotante `to_chars()` es la siguiente:

- VS 2017 15.7: Entero `from_chars()` y `to_chars()`.
- VS 2017 15.8: Punto flotante `from_chars()`.
- VS 2017 15.9: Sobrecargas de punto flotante `to_chars()` para decimales más cortos.
- VS 2019 16.0: Sobrecargas de punto flotante `to_chars()` para el hexadecimal más corto y el hexadecimal de precisión.
- VS 2019 16.2: Sobrecargas de punto flotante `to_chars()` para precisión fija y precisión científica.
- VS 2019 16.4: Sobrecarga de punto flotante `to_chars()` para precisión general.

<a name ="note_parallel"></a> __parallel__ La biblioteca de algoritmos paralelos de C++17 está completa. Que esté completa no significa que todos los algoritmos se paralelicen en todos los casos. Los algoritmos más importantes se han paralelizado, y se proporcionan firmas de la directiva de ejecución incluso cuando los algoritmos no están paralelizados. El encabezado interno central de nuestra implementación, yvals_core.h, contiene las siguientes "Notas de algoritmos paralelos": C++ permite que una implementación implemente algoritmos paralelos como llamadas a algoritmos en serie. Esta implementación paraleliza varias llamadas de algoritmo comunes, pero no todas.

Se paralelizan los algoritmos siguientes:

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Los siguientes algoritmos no están paralelizados en la actualidad:

- Ninguna mejora de rendimiento de paralelismo perceptible en el hardware de destino; todos los algoritmos que simplemente copian o permutan elementos sin ramas suelen tener ancho de banda de memoria limitado:
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Existe confusión sobre los requisitos de paralelismo de usuario; es probable que al menos en la categoría anterior:
  - `generate`, `generate_n`
- El paralelismo efectivo parece no ser viable:
  - `partial_sort`, `partial_sort_copy`
- Todavía sin evaluar; es posible que el paralelismo se implemente en una versión futura y se sospecha que sea beneficioso:
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)\
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)\
[Mejoras de conformidad de C++ en Visual Studio](cpp-conformance-improvements.md)\
[Novedades de Visual C++ en Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historial de cambios de Visual C++ de 2003 a 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Novedades de Visual C++ de 2003 a 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[Blog del equipo de C++](https://devblogs.microsoft.com/cppblog/)
