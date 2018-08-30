---
title: Novedades de Visual C++ en Visual Studio | Microsoft Docs
ms.date: 11/15/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d3a3ec1fec213cc6fa1bb5dc0ebfdadbe7d22b2
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131725"
---
# <a name="whats-new-for-visual-c-in-visual-studio-2017"></a>Novedades de Visual C++ en Visual Studio 2017

Visual Studio 2017 incluye muchas actualizaciones y revisiones del entorno de Visual C++. Hemos corregido más de 250 errores y problemas en el compilador y en las herramientas. Muchos los han enviado los clientes a través de las opciones [Notificar un problema](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) y [Proporcionar una sugerencia](https://visualstudio.uservoice.com/) en **Enviar comentarios**. ¡Muchas gracias por notificárnoslos! Para obtener más información sobre todas las novedades de Visual Studio, visite [Novedades de Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=834481).

<!--The compiler and tools version number in Visual Studio 2017 is 14.10.24629. -->

## <a name="c-compiler"></a>compilador C++

### <a name="c-conformance-improvements"></a>Mejoras de conformidad de C++

En esta versión, hemos actualizado el compilador C++ y la biblioteca estándar con compatibilidad mejorada con características de C ++ 11 y C ++ 14, así como la compatibilidad preliminar para determinadas características que se esperan que estén en C ++ 17 estándar. Para obtener información detallada, vea [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements-2017.md).

**Versión 15.5 de Visual Studio 2017**: el compilador admite aproximadamente un 75 % de las características nuevas de C++17, incluidos los enlaces estructurados, las expresiones lambda `constexpr`, `if constexpr`, las variables alineadas, las expresiones fold y la adición de `noexcept` al sistema de tipos. Están disponibles en la opción **/std:c++17**. Para obtener más información, consulte [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements-2017.md).

**Versión 15.7 de Visual Studio 2017**: el conjunto de herramientas del compilador MSVC en Visual Studio, versión 15.7, ahora cumple con el estándar de C++. Para obtener más información, vea [Announcing: MSVC Conforms to the C++ Standard](https://blogs.msdn.microsoft.com/vcblog/2018/05/07/announcing-msvc-conforms-to-the-c-standard/) (Anuncio: MSVC cumple con el estándar de C++) y [Conformidad del lenguaje Visual C++](visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nuevas opciones del compilador

- [/permissive-](build/reference/permissive-standards-conformance.md): habilita todas las opciones del compilador de cumplimiento de estándares estrictos y deshabilita la mayoría de las extensiones del compilador específicas de Microsoft, pero no `__declspec(dllimport)`, por ejemplo. Esta opción está activada de forma predeterminada en Visual Studio 2017 versión 15.5.  El modo de cumplimiento **/permissive-** incluye compatibilidad para la búsqueda de nombres en dos fases. Para obtener más información, vea [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements-2017.md).

- [/diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md): permite mostrar el número de línea, el número de línea y columna, o el número de línea y columna y un símbolo de intercalación bajo la línea de código donde se ha encontrado el error de diagnóstico o la advertencia.

- [/debug:fastlink](build/reference/debug-generate-debug-info.md): permite tiempos de vínculo incremental hasta un 30 % más rápidos (frente a Visual Studio 2015), ya que no copia toda la información de depuración en el archivo PDB. En su lugar, el archivo PDB apunta a la información de depuración de los archivos de biblioteca y del objeto usados para crear el ejecutable. Consulte [Faster C++ build cycle in VS "15" with /Debug:fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) (Ciclo de compilación en C++ más rápido en VS "15" con /Debug:fastlink) y [Recommendations to speed C++ builds in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/) (Recomendaciones para acelerar las compilaciones en C++ en Visual Studio).

- Visual Studio 2017 permite usar [/sdl](build/reference/sdl-enable-additional-security-checks.md) con [/await](build/reference/await-enable-coroutine-support.md). Se ha eliminado la limitación de [/RTC](build/reference/rtc-run-time-error-checks.md) con corrutinas.

   **Visual Studio 2017 versión 15.3**:  
- [/std:c++14 y /std:c++latest](build/reference/std-specify-language-standard-version.md): estas opciones del compilador permiten participar en versiones específicas del lenguaje de programación ISO C++ en un proyecto. La mayoría de las nuevas características del borrador estándar están protegidas con la opción **/std:c++latest**.

- [/std:c++17](build/reference/std-specify-language-standard-version.md) habilita el conjunto de características de C++17 implementadas por el compilador. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características nuevas o que se han modificado en las versiones del borrador de trabajo y las actualizaciones de defectos de C++ Standard posteriores a C++17. Para habilitar estas características, use **/std:c++latest**.


### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, seguridad, diagnóstico y control de versiones

Esta versión ofrece varias mejoras en la optimización, la generación de código, el control de versiones del conjunto de herramientas y el diagnóstico. Estas son algunas de las mejoras destacables incluidas:

- Generación de código de bucles mejorada: compatibilidad con vectorización automática de división de enteros constantes, mejor identificación de patrones de memset.
- Seguridad de código mejorada: emisión mejorada de diagnósticos de compilador de desbordamiento del búfer. Asimismo, [/guard:cf](build/reference/guard-enable-control-flow-guard.md) ahora protege instrucciones switch que generan tablas de saltos.
- Control de versiones: el valor de la macro de preprocesador integrada **\_MSC\_VER** se actualiza de forma continua en cada actualización del conjunto de herramientas de Visual C++. Para obtener más información, vea [Visual C++ Compiler Version](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) (Versión del compilador de Visual C++).
- Nuevo diseño del conjunto de herramientas: el compilador y las herramientas de compilación relacionadas tienen una nueva ubicación y estructura de directorios en la máquina de desarrollo. El nuevo diseño permite instalaciones en paralelo de varias versiones del compilador. Para más información, vea [Compiler Tools Layout in Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/) (Diseño de las herramientas del compilador en Visual Studio "15").
- Diagnóstico mejorado: en la ventana de salida ahora se muestra la columna en la que se produce un error. Para más información, vea [C++ improvisamente diagnostics improvements in VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/) (Mejoras del diagnóstico del compilador C++ en VS "15" Preview 5).
- Se ha eliminado la palabra clave experimental **yield**, disponible en la opción **/await**, al usar las corrutinas. En su lugar, se debe actualizar el código para que use `co_yield`. Para más información, consulte el [blog del equipo de Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

**Visual Studio 2017 versión 15.3**:

Se han implementado mejoras adicionales en los diagnósticos del compilador. Para más información, consulte el artículo sobre las [mejoras de diagnósticos en Visual Studio 2017 15.3.0](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/).

**Versión 15.5 de Visual Studio 2017**:

El rendimiento del entorno de ejecución Visual C++ sigue mejorando debido a que la calidad del código generado es mayor. Esto significa que puede volver a compilar el código y la aplicación se ejecutará más rápido. Algunas de las optimizaciones del compilador son totalmente nuevas, como la vectorización de almacenes escalares condicionales, la combinación de llamadas `sin(x)` y `cos(x)` en una nueva llamada `sincos(x)`, y la eliminación de instrucciones redundantes del Optimizador SSA. Otras optimizaciones del compilador son mejoras de funcionalidades existentes, como las heurísticas del vectorizador para expresiones condicionales, las optimizaciones de bucle mejoradas y la generación de código min/max flotante. Ahora, el enlazador tiene una nueva implementación **/OPT:ICF** más rápida, con la que podrá agilizar el tiempo de vínculo hasta un 9 %. Asimismo, los vínculos incrementales también presentan otras mejoras de rendimiento. Para obtener más información, vea [/OPT (Optimizations)](https://docs.microsoft.com/en-us/cpp/build/reference/opt-optimizations) (/OPT (optimizaciones)) e [/INCREMENTAL (Link Incrementally)](https://docs.microsoft.com/en-us/cpp/build/reference/incremental-link-incrementally) (/INCREMENTAL (vincular de forma incremental)).

Visual C++ admite las instrucciones AVX-512 de Intel, incluidas las instrucciones vectoriales de longitud, que incorporan nuevas funciones en AVX-512 y amplios registros de 128 y 256 bits.

La opción [/Zc:noexceptTypes-](build/reference/zc-noexcepttypes.md) se puede usar para volver a la versión C++14 de `noexcept` al usar el modo C++17 de forma general. Esto le permite actualizar el código fuente para que sea conforme con C++17 sin tener que reescribir todo el código de `throw()` a la vez. Para obtener más información, vea [Eliminación de las especificaciones de excepción dinámica y noexcept](cpp-conformance-improvements-2017.md#noexcept_removal).

**Visual Studio 2017 versión 15.7**:

- Nuevo modificador de compilador [/Qspectre ](build/reference/qspectre.md) para ayudar a mitigar el riesgo de ataques de canal lateral de ejecución especulativa. Vea [Spectre mitigations in MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc/) (Mitigaciones de Spectre en MSVC) para obtener más información.
- Nueva advertencia de diagnóstico para la mitigación de Spectre. Vea [Spectre diagnostic in Visual Studio 2017 Version 15.7 Preview 4](https://blogs.msdn.microsoft.com/vcblog/2018/04/20/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/) (Diagnóstico de Spectre en Visual Studio 2017 versión 15.7 (versión preliminar 4)) para obtener más información.
- Un nuevo valor para /Zc, **/Zc:__cplusplus**, permite la generación de informes correctos de la compatibilidad del estándar de C++. Por ejemplo, cuando el modificador está establecido y el compilador está en modo /std:c++17, el valor se expande a **201703 L**. Vea [MSVC now correctly reports __cplusplus](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/msvc-now-correctly-reports-__cplusplus/) (Ahora MSVC notifica __cplusplus correctamente) para obtener más información.

## <a name="c-standard-library-improvements"></a>Mejoras de la biblioteca estándar de C++

- Se han realizado mejoras secundaras en los diagnósticos (`basic_string` `_ITERATOR_DEBUG_LEVEL != 0`). Activar una comprobación de IDL en la maquinaria de cadenas ahora indicará la conducta específica que provocó la activación. Por ejemplo, en lugar de recibir el mensaje "string iterator not dereferenceable" (El iterador de cadena no es desreferenciable), verá el mensaje "cannot dereference string iterator because it is out of range (e.g. an end iterator)" (No se puede desreferenciar el iterador de cadena porque está fuera del rango (por ejemplo, un iterador final).
- Mejora en el rendimiento: ahora las sobrecargas de `basic_string::find(char)` solo llaman a `traits::find` una vez. Anteriormente esto se implementó como buscar en las cadenas generales una cadena de longitud 1.
- Mejora en el rendimiento: `basic_string::operator==` ahora comprueba el tamaño de las cadenas antes de comparar el contenido de estas.
- Mejora en el rendimiento: se ha eliminado el acoplamiento de control en `basic_string`, ya que era difícil de analizar para el optimizador de compilador. Tenga en cuenta que, para todas las cadenas cortas, las llamadas a `reserve` siguen teniendo un costo distinto a cero para no hacer nada.
- Se ha agregado \<any\>, \<string_view\>, `apply()` y `make_from_tuple()`.
- Se ha mejorado `std::vector` para aumentar la precisión y el rendimiento: los alias durante la inserción y el emplazamiento ahora se controlan correctamente según lo requerido por el estándar, y la garantía de excepción sólida ahora se proporciona cuando el estándar lo solicita a través de `move_if_noexcept()` y otra lógica. Además, la inserción y el emplazamiento realizan menos operaciones de elementos.
- Ahora, la biblioteca estándar de C++ evita desreferenciar punteros elaborados nulos.
- Se ha agregado \<optional\>, \<variant\>, `shared_ptr::weak_type` y \<cstdalign\>.
- Se ha habilitado `constexpr` de C++14 en `min(initializer_list)`, `max(initializer_list)`, `minmax(initializer_list)`, `min_element()`, `max_element()` y `minmax_element()`.
- Se ha mejorado el rendimiento de `weak_ptr::lock()`.
- Se ha corregido el operador de asignación de movimiento `std::promise`, que anteriormente podía provocar que el código se bloqueara permanentemente.
- Se han corregido errores del compilador con la conversión implícita de `atomic<T*>` a `T*`.
- `pointer_traits<Ptr>` ahora detecta `Ptr::rebind<U>` correctamente.
- Se ha corregido la falta de un calificador `const` en el operador de resta `move_iterator`.
- Se ha corregido un elemento codegen silencioso incorrecto para asignadores con estado definido por el usuario al solicitar `propagate_on_container_copy_assignment` y `propagate_on_container_move_assignment`.
- `atomic<T>` ahora tolera la sobrecarga de `operator&()`.
- Para aumentar el rendimiento del compilador, los encabezados de la biblioteca estándar de C++ ahora evitan incluir declaraciones de intrínsecos del compilador innecesarios.
- Se ha mejorado ligeramente el diagnóstico del compilador para llamadas `bind()`incorrectas.
- Se ha triplicado la eficacia del rendimiento de los constructores de movimiento `std::string` y `std::wstring`.

Para una lista completa de las mejoras en la biblioteca estándar, consulte el artículo sobre las [correcciones de la biblioteca estándar en VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/).

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

#### <a name="c17-features"></a>Características de C++17

Se implementaron varias características adicionales de C++17. Para más información, consulte [Conformidad del lenguaje Visual C++](cpp-conformance-improvements-2017.md#improvements_153).

#### <a name="other-new-features"></a>Otras características nuevas

- Se implementó P0602R0 "variante y opcional deben propagar la trivialidad de copia/movimiento".
- La biblioteca estándar ahora tolera de manera oficial que RTTI dinámico se deshabilite mediante la opción [/GR-](build/reference/gr-enable-run-time-type-information.md). `dynamic_pointer_cast()` y `rethrow_if_nested()` requieren `dynamic_cast` de forma inherente, de modo que la biblioteca estándar ahora los marca como `=delete` en **/GR-**.
- Incluso si RTTI dinámico se ha deshabilitado mediante **/GR-**, "RTTI estático" (con el formato de `typeid(SomeType)`) sigue estando disponible y permite potenciar varios componentes de la biblioteca estándar. La biblioteca estándar ahora también admite deshabilitarlo con **/D\_HAS\_STATIC\_RTTI=0**. Tenga en cuenta que esto deshabilitará `std::any`, las funciones de miembros `target()` y `target_type()` de `std::function` y la función de miembro friend `get_deleter()` de `std::shared_ptr` y `std::weak_ptr`.

#### <a name="correctness-fixes-in-visual-studio-2017-version-153"></a>Mejoras de exactitud en la versión 15.3 de Visual Studio 2017

- Los contenedores de la biblioteca estándar ahora fijan sus `max_size()` en `numeric_limits<difference_type>::max()`, en lugar de sus `max()` en `size_type`. Esto garantiza que el resultado de `distance()` en los iteradores de dicho contenedor se pueda representar en el tipo de valor devuelto de `distance()`.
- Se ha corregido la falta de la especialización `auto_ptr<void>`.
- Anteriormente, los algoritmos `for_each_n()`, `generate_n()` y `search_n()` no se compilaban si el argumento de longitud no era un tipo de datos entero. Ahora permiten intentar convertir las longitudes no integrales al valor `difference_type` de los iteradores.
- `normal_distribution<float>` ya no emite advertencias dentro de la biblioteca estándar con respecto a la restricción de "double" a "float".
- Se han corregido algunas operaciones `basic_string` que se comparaban con `npos` en lugar de con `max_size()` al comprobar el desbordamiento de tamaño máximo.
- `condition_variable::wait_for(lock, relative_time, predicate)` permitiría esperar durante todo el período de tiempo relativo en el caso de una activación falsa. Ahora solo esperará un intervalo único del tiempo relativo.
- `future::get()` ahora permite invalidar `future`, tal como requiere el estándar.
- `iterator_traits<void *>` solía ser un error porque intentaba formar `void&`. Ahora se convierte limpiamente en una estructura vacía para permitir el uso de `iterator_traits` en condiciones SFINAE "is iterator".
- Se han corregido algunas advertencias que **-Wsystem-headers** ha notificado.
- También se ha corregido el mensaje "la especificación de la excepción en la declaración no coincide con la declaración anterior" que Clang **-Wmicrosoft-exception-spec** ha notificado.
- También se corrigió mem-initializer-list que ordena las advertencias informadas por Clang y C1XX.
- Los contenedores sin ordenar no intercambiaban sus hashers o predicados cuando se intercambiaban los contenedores mismos. Ahora sí lo hacen.
- Muchas operaciones de intercambio de contenedores ahora están marcadas como `noexcept`, puesto que la biblioteca estándar nunca tiene la intención de generar una excepción al detectar una condición de comportamiento sin definir que no coincida con el asignador y que no sea del tipo `propagate_on_container_swap`.
- Muchas operaciones `vector<bool>` ahora aparecen marcadas como `noexcept`.
- La biblioteca estándar ahora aplica la coincidencia entre el asignador `value_type` (en modo C++17) con un sombreado de escape de rechazo.
- Se han corregido algunas condiciones en las que self-range-insert en `basic_string` resolvía el contenido de las cadenas. (Nota: la biblioteca estándar sigue prohibiendo self-range-insert en vectores).
- `basic_string::shrink_to_fit()` ya no se ve afectado por el valor `propagate_on_container_swap` del asignador.
- `std::decay` ahora controla los tipos de funciones abominables, es decir, los tipos de función cv-qualified o ref-qualified.
- Los cambios incluyen directivas para usar la distinción entre mayúsculas y minúsculas y barras diagonales para mejorar la portabilidad.
- Se ha corregido la advertencia C4061: el enumerador "*enumerator*" en la instrucción switch de la enumeración "*enumeration*" no está controlado de forma explícita por una etiqueta de caso. Esta advertencia está desactivada de manera predeterminada y se corrigió como una excepción de la directiva general de advertencias de la biblioteca estándar. (La biblioteca estándar no tiene **/W4**, pero no tiene la intención de no tener **/Wall**. Muchas advertencias desactivadas de manera predeterminada son muy ruidosas y no están diseñadas para usarlas de manera regular).
- Se han mejorado las comprobaciones de depuración `std::list`. Los iteradores de lista ahora comprueban `operator->()`, y `list::unique()` ahora marca los iteradores como invalidados.
- Se ha corregido la metaprogramación uses-allocator en `tuple`.

#### <a name="performancethroughput-fixes"></a>Correcciones de rendimiento

- Se ha encontrado una solución alternativa para las interacciones con `noexcept` que impedían insertar la implementación de `std::atomic` en funciones que usan Control de excepciones estructurado (SEH).
- Se ha cambiado la función interna `_Deallocate()` de la biblioteca estándar para optimizarla en un código más pequeño, lo que permite insertarla en más lugares.
- Se ha cambiado `std::try_lock()` para usar la expansión del paquete en lugar de la recursividad.
- Se ha mejorado el algoritmo de prevención de interbloqueo `std::lock()` para usar operaciones `lock()` en lugar de dar giros en `try_lock()` en todos los bloqueos.
- Se ha habilitado la optimización del valor devuelto con nombre en `system_category::message()`.
- `conjunction` y `disjunction` ahora crean instancias de tipos N + 1, en lugar de tipos 2N + 2.
- `std::function` ya no crea instancias de maquinaria de compatibilidad con el asignador para cada elemento invocable con tipo borrado, lo que mejora el rendimiento y disminuye el tamaño de .obj en programas que pasan muchas expresiones lambda distintas a `std::function`.
- `allocator_traits<std::allocator>` contiene las operaciones `std::allocator` insertadas manualmente, lo que permite reducir el tamaño del código que interactúa con `std::allocator` mediante `allocator_traits`, es decir, la mayoría del código.
- La biblioteca estándar ahora controla la interfaz de asignador mínimo de C++11 con una llamada directa a `allocator_traits`, en lugar de encapsular el asignador en una clase interna `_Wrap_alloc`. Esto disminuye el tamaño del código que se genera para la compatibilidad del asignador y mejora la experiencia de depuración y la capacidad del optimizador para razonar sobre los contenedores de la biblioteca estándar en ciertos casos, ya que en el depurador ahora puede ver el tipo de asignador, en lugar de `_Wrap_alloc<your_allocator_type>`.
- Se ha eliminado la metaprogramación para el elemento personalizado `allocator::reference`, un elemento que, de hecho, los asignadores no tienen permitido personalizar. (Los asignadores pueden hacer que los contenedores usen punteros sofisticados pero no referencias sofisticadas).
- El front-end del compilador se diseñó para desencapsular los iteradores de depuración en Bucles for basados en intervalos, lo que mejora el rendimiento de las compilaciones de depuración.
- La ruta de reducción interna `basic_string` para `shrink_to_fit()` y `reserve()` ya no está en la ruta de la reasignación de operaciones, lo que reduce el tamaño del código para todos los miembros de mutación.
- La ruta de crecimiento interna `basic_string` ya no está en la ruta de `shrink_to_fit()`.
- Las operaciones de mutación `basic_string` ahora se factorizan en funciones de ruta lenta de asignación y en funciones de ruta rápida de no asignación, lo que hace más probable que el caso no de reasignación se inserte en los llamadores.
- Las operaciones de mutación `basic_string` ahora construyen búferes reasignados con el estado deseado, en lugar de cambiar el tamaño en el mismo lugar. Por ejemplo, la inserción en el comienzo de una cadena ahora mueve el contenido después de la inserción exactamente una vez (ya sea hacia abajo o al búfer recién asignado) en lugar de dos veces en el caso de reasignación (al búfer recién asignado y luego abajo).
- Las operaciones que llaman a la biblioteca estándar C en \<string\> ahora almacenan en caché la dirección `errno` para quitar la interacción repetida con TLS.
- Se ha simplificado la implementación de `is_pointer`.
- Se ha completado el cambio de la expresión basada en funciones SFINAE para que, en su lugar, se base en `struct` y `void_t`.
- Los algoritmos de la biblioteca estándar ahora evitan el postincremento de los iteradores.
- Se corrigieron las advertencias de truncamiento cuando se usan asignadores de 32 bits en sistemas de 64 bits.
- La asignación de movimiento `std::vector` ahora es más eficaz en el caso de los asignadores que no coincidan y que no sean POCMA, ya que permite volver a usar el búfer cuando es posible.

#### <a name="readability-and-other-improvements"></a>Legibilidad y otras mejoras

- La biblioteca estándar ahora usa `constexpr` de C++14 sin condiciones, en lugar de macros definidas condicionalmente.
- La biblioteca estándar ahora usa plantillas de alias de forma interna.
- La biblioteca estándar ahora usa `nullptr` internamente, en lugar de `nullptr_t{}`. (Se eliminó el uso interno de NULL. El uso interno de 0-as-null se está limpiando de forma gradual).
- La biblioteca estándar ahora usa `std::move()` internamente, en lugar de hacer un mal uso de `std::forward()` de forma estilística.
- Se ha cambiado `static_assert(false, "message")` a `#error message`. Con esto se mejoran los diagnósticos del compilador, porque `#error` detiene inmediatamente la compilación.
- La biblioteca estándar ya no marca las funciones como `__declspec(dllimport)`. La tecnología de enlazador moderna ya no lo requiere.
- Se extrajo SFINAE a argumentos de plantilla predeterminados, lo que reduce el desorden en comparación con los tipos de valor devuelto y los tipos de argumento de función.
- Las comprobaciones de depuración en \<random\> ahora usan la maquinaria usual de la biblioteca estándar, en lugar de la función interna `_Rng_abort()` que llamaba `fputs()` a **stderr**. La implementación de esta función se conserva por motivos de compatibilidad binaria, pero se quitó en la siguiente versión sin compatibilidad binaria de la biblioteca estándar.

### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

Se han agregado, puesto en desuso o eliminado varias características de la biblioteca estándar según la versión estándar de C++17. Para obtener información detallada, vea [Mejoras de conformidad de C++ en Visual Studio](cpp-conformance-improvements-2017.md#improvements_155).

#### <a name="new-experimental-features"></a>Nuevas características experimentales

- Compatibilidad experimental con los siguientes algoritmos:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Se han agregado las firmas para los siguientes algoritmos paralelos, pero por el momento no están paralelizados. En la generación de perfiles no se mostró ninguna ventaja en los algoritmos de paralelización que solo mueven o permutan elementos:
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

#### <a name="performance-fixes-and-improvements"></a>Mejoras y correcciones de rendimiento

- `basic_string<char16_t>` ahora interactúa en las mismas optimizaciones de `memcmp`, `memcpy` y similares que `basic_string<wchar_t>`.
- Una limitación del optimizador impedía que los punteros de funciones se expusiesen insertados con el trabajo "evitar la copia de funciones" en Visual Studio 2015 Update 3. Se ha aplicado una solución alternativa mediante la restauración del rendimiento de `lower_bound(iter, iter, function pointer)`.
- La sobrecarga de la verificación del orden de depuración del iterador de entradas en `includes`, `set_difference`, `set_symmetric_difference` y `set_union` se ha reducido mediante el desempaquetado de iteradores antes de comprobar el orden.
- `std::inplace_merge` ahora omite elementos que ya están en posición.
- La construcción de `std::random_device` ya no construye y destruye `std::string`.
- `std::equal` y `std::partition` incluían un pase de optimización de procesamiento por saltos que ahorra una comparación del iterador.
- Ahora, cuando se pasan punteros a `std::reverse` para elementos `T` copiables de forma trivial, este realizará distribuciones a una implementación vectorizada escrita a mano.
- `std::fill`, `std::equal` y `std::lexicographical_compare` ahora permiten la distribución a `memset` y `memcmp` para `std::byte` y `gsl::byte`, así como en el caso de otras enumeraciones del tipo char y clases enum. Tenga en cuenta que `std::copy` realiza la distribución mediante `is_trivially_copyable` y, por tanto, no requiere ningún cambio.
- La biblioteca estándar ya no contiene destructores de paréntesis vacíos, cuyo único comportamiento era hacer que los tipos no fueran destruibles de forma trivial.

#### <a name="correctness-fixes-in-visual-studio-2017-version-155"></a>Mejoras de exactitud en la versión 15.5 de Visual Studio 2017

- `std::partition` ahora llama al predicado N veces, en lugar de N+1, tal y como requiere el estándar.
- Los intentos de evitar estáticas mágicas en la versión 15.3 se han reparado en la 15.5.
- `std::atomic<T>` ya no requiere que `T` sea construible de forma predeterminada.
- Los algoritmos de montón que necesiten un valor de tiempo logarítmico ya no realizan una aserción de tiempo lineal en la que la entrada es un montón cuando se habilita la depuración del iterador.
- `__declspec(allocator)` ahora solo está protegido por C1XX para evitar advertencias de Clang que este elemento desclspec no entiende.
- `basic_string::npos` ahora está disponible como una constante de tiempo de compilación.
- En C++17, `std::allocator` ahora manipula adecuadamente la asignación de tipos sobrealineados, que son aquellos cuya alineación es superior a `max_align_t`, a menos que **/Zc:alignedNew-** lo deshabilite.  Por ejemplo, los vectores de objetos con una alineación de 16 o 32 bytes ahora se alinearán adecuadamente con instrucciones SSE y AVX.

### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, versión 15.6

- \<memory_resource>
- Conceptos básicos de biblioteca V1
- Eliminación de la asignación de polymorphic_allocator
- Mejora de la deducción de argumentos de plantilla de clase

### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

- La compatibilidad con algoritmos paralelos ya no es experimental
- Una implementación nueva de \<filesystem>
- Conversiones de cadena elementales (parcial)
- std::launder()
- std::byte
- hypot(x,y,z)
- Evitar la decadencia innecesaria
- Funciones matemáticas especiales
- Expresión constante char_traits
- Guías de deducción para STL

Vea [Conformidad del lenguaje Visual C++](visual-cpp-language-conformance.md) para obtener más información.

## <a name="other-libraries"></a>Otras bibliotecas

### <a name="open-source-library-support"></a>Compatibilidad con bibliotecas de código abierto

**Vcpkg** es una herramienta de línea de comandos de código abierto que simplifica enormemente el proceso de adquirir y compilar bibliotecas estáticas de C++ de código abierto y archivos DLL en Visual Studio. Para más información, vea [Vcpkg: Administrador de paquetes de C++ para Windows](vcpkg.md).

**Versión 15.5 de Visual Studio 2017**:

### <a name="cpprest-sdk-290"></a>CppRestSDK 2.9.0

Se ha actualizado CppRestSDK (una API web multiplataforma para C++) a la versión 2.9.0. Para obtener más información, vea [CppRestSDK 2.9.0 is available on GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/) (CppRestSDK 2.9.0 está disponible en GitHub).

### <a name="atl"></a>ATL

- Otro conjunto de correcciones de conformidad para la búsqueda de nombres.
- Los operadores de constructores de movimiento y de asignación de movimiento están ahora correctamente marcados como no productores de excepciones.
- Inclusión de la advertencia válida C4640 sobre la inicialización segura de subprocesos de elementos estáticos locales en atlstr.h.
- La inicialización segura de subprocesos de elementos estáticos locales estaba desactivada automáticamente en el conjunto de herramientas de XP al [usar ATL Y crear un archivo DLL]. Pero esto ya no es así. Puede agregar **/Zc:threadSafeInit-** en la configuración del proyecto si quiere tener desactivada la inicialización segura de subprocesos.

### <a name="visual-c-runtime"></a>Runtime de Visual C++

- Nuevo encabezado "cfguard.h" para símbolos de protección de flujo de control.

## <a name="c-ide"></a>C++ IDE

- El rendimiento del cambio de configuración ahora es mejor para proyectos nativos de C++ y mucho mejor para proyectos C++/CLI. Cuando se activa una configuración de solución por primera vez, ahora será más rápida y todas las activaciones posteriores de esta configuración de la solución serán casi instantáneas.

**Visual Studio 2017 versión 15.3**:

- Algunos asistentes de código y proyecto se han vuelto a escribir en el estilo del cuadro de diálogo de signatura.
- Ahora, al usar la opción **Agregar clase** se abre directamente el Asistente para agregar clases. Todos los demás elementos que estaban previamente aquí se encuentran disponibles ahora en **Agregar > Nuevo elemento**.
- Ahora los proyectos de Win32 están en la categoría **Escritorio de Windows** en el cuadro de diálogo **Nuevo proyecto**.
- Ahora las plantillas de la **consola de Windows** y de la **aplicación de escritorio** crean proyectos sin abrir un asistente. Hay un nuevo **Asistente de escritorio de Windows** en la misma categoría que muestra las mismas opciones que el asistente **Aplicación de consola Win32** anterior.

**Versión 15.5 de Visual Studio 2017**:

Ahora varias operaciones de C++ que usan el motor IntelliSense para la refactorización y la navegación de código se ejecutan mucho más rápido. Los siguientes números se basan en la solución de Chromium de Visual Studio con 3500 proyectos:

|||
|-|-|
|Característica|Mejora del rendimiento|
|Cambiar nombre|5,3x|
|Cambiar firma |4,5x|
|Buscar todas las referencias|4,7x|

Ahora C++ permite hacer clic presionando la tecla Control para **ir a la definición**, lo que hace más sencilla la navegación con el mouse a las definiciones. El Visualizador de estructuras del paquete Productivity Power Tools hora también se incluye en el producto de forma predeterminada.

## <a name="intellisense"></a>IntelliSense

- Ahora se está usando el nuevo motor de base de datos basado en SQLite de forma predeterminada. Esto acelerará las operaciones de base de datos como **Ir a definición** y **Buscar todas las referencias** y mejorará significativamente el tiempo de análisis inicial de la solución. La opción se ha movido a **Herramientas > Opciones > Editor de texto > C o C++ > Opciones avanzadas**. Anteriormente se encontraba en ...C/C++ > Experimental.

- Se ha mejorado el rendimiento de IntelliSense en proyectos y archivos que no usan encabezados precompilados; se creará un encabezado precompilado automático para los encabezados en el archivo actual.

- Se ha agregado el filtro de errores y la ayuda para errores de IntelliSense en la lista de errores. Ahora se puede filtrar al hacer clic en la columna de errores. Además, al hacer clic en los errores específicos o al presionar F1, se iniciará una búsqueda en línea del mensaje de error.

  ![Lista de errores](media/ErrorList1.png "Lista de errores")

  ![Lista de errores filtrados](media/ErrorList2.png "Lista de errores filtrados")

- Se agregó la capacidad de filtrar los elementos de la lista de miembros por tipo.

  ![Filtrado de la lista de miembros](media/mlfiltering.png "Filtrado de la lista de miembros")

- Se ha agregado una nueva característica de IntelliSense predictiva experimental que proporciona un filtrado de lo que aparece en la lista de miembros que tiene en cuenta el contexto. Vea [C++ IntelliSense Improvements – Predictive IntelliSense & Filtering](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/) (Mejoras de IntelliSense de C++: IntelliSense predictivo y filtrado).
- Ahora **Buscar todas las referencias** (Mayús+F12) permite desplazarse con facilidad, incluso en códigos base complejos. Proporciona agrupación avanzada, filtrado, ordenación, búsqueda en los resultados y (para algunos idiomas) uso de colores, para que pueda entender claramente las referencias. Para C++, la nueva interfaz de usuario incluye información sobre si se lee desde una variable o si se escribe en ella.
- La característica Punto a flecha de IntelliSense pasó de experimental a avanzada y ahora está habilitada de manera predeterminada. Las características del editor **Expandir ámbitos** y **Expandir precedencia** también han dejado de ser características experimentales y ahora son avanzadas.
- Las características experimentales de refactorización **Cambiar signatura** y **Extraer función** ahora están disponibles de manera predeterminada.
- La característica experimental "Carga de proyecto más rápida" está disponible para proyectos de C++. La próxima vez que abra un proyecto de C++, se cargará más rápido y la siguiente todavía más.
- Algunas de estas características son comunes a otros lenguajes y otras son específicas de C++. Para obtener más información sobre estas nuevas características, vea [Announcing Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/) (Presentación de Visual Studio "15").

**Visual Studio 1027 versión 15.7**: se ha agregado compatibilidad para ClangFormat. Para obtener más información, vea [ClangFormat Support in Visual Studio 2017](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/clangformat-support-in-visual-studio-2017-15-7-preview-1/) (Compatibilidad con ClangFormat en Visual Studio 2017).

## <a name="non-msbuild-projects-with-open-folder"></a>Proyectos que no son de MSBuild con Abrir carpeta

Visual Studio 2017 incluye la característica **Abrir carpeta**, que permite codificar, compilar y depurar elementos en un carpeta que contenga código fuente sin necesidad de crear soluciones o proyectos. Esto hace que sea mucho más fácil empezar a trabajar con Visual Studio, incluso si el proyecto no es un proyecto basado en MSBuild. Con**Abrir carpeta**, obtiene acceso a funciones útiles para entender, editar, compilar y depurar el código que Visual Studio proporciona para proyectos de MSBuild. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](ide/non-msbuild-projects.md).

- Mejoras en la experiencia de Abrir carpeta. Puede personalizar la experiencia con estos archivos .json:
  - CppProperties.json para personalizar la experiencia de IntelliSense y de exploración.
  - Tasks.json para personalizar los pasos de compilación.
  - Launch.json para personalizar la experiencia de depuración.

**Visual Studio 2017 versión 15.3**:

- Se mejoró la compatibilidad con compiladores alternativos y entornos de compilación como MinGW y Cygwin. Para más información, consulte el artículo sobre el [uso de MinGW y Cygwin con Visual C++ y Abrir carpeta](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Se ha agregado compatibilidad para definir variables de entorno globales y específicas de la configuración en CppProperties.json y CMakeSettings.json. Estas variables de entorno se pueden usar en las configuraciones de depuración definidas en launch.vs.json y en las tareas tasks.vs.json. Para obtener más información, vea [Customizing your Environment with Visual C++ and Open Folder](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/) (Personalización del entorno con Visual C++ y Abrir carpeta).
- Se mejoró la compatibilidad con el generador Ninja de CMake, incluida la capacidad de apuntar fácilmente a las plataformas de 64 bits.

## <a name="cmake-support-via-open-folder"></a>Compatibilidad con CMake mediante Abrir carpeta

Visual Studio 2017 incluye compatibilidad con el uso de proyectos CMake sin convertirlos en archivos de proyecto de MSBuild (.vcxproj). Para más información, consulte el artículo sobre [proyectos CMake en Visual C++](ide/cmake-tools-for-visual-cpp.md). Si abre proyectos CMake con **Abrir carpeta**, el entorno se configurará automáticamente para la edición, la compilación y la depuración de C++.

- IntelliSense de C++ funciona sin la necesidad de crear un archivo CppProperties.json en la carpeta raíz. Además, agregamos un nuevo menú desplegable que le permite a los usuarios cambiar fácilmente entre las configuraciones que proporcionan los archivos CMake y CppProperties.json.

- Se admite una configuración adicional a través de un archivo CMakeSettings.json que reside en la misma carpeta que el archivo CMakeLists.txt.

  ![Abrir carpeta Cmake](media/cmake_cpp.png "Abrir carpeta CMake")

**Visual Studio 2017 versión 15.3**: se agregó compatibilidad con el generador CMake Ninja. 

**Visual Studio 2017, versión 15.5**: se ha agregado compatibilidad para importar memorias caché de CMake existentes. 

**Visual Studio 2017 versión 15.7**: se ha agregado compatibilidad para CMake 3.11, análisis de código en proyectos de CMake, la vista de destinos en el Explorador de soluciones, opciones de generación de caché y la compilación de archivo único. Para obtener más información, vea [CMake Support in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) (Compatibilidad con CMake en Visual Studio) y [Proyectos de CMake en Visual C++](ide/cmake-tools-for-visual-cpp.md).

## <a name="windows-desktop-development-with-c"></a>Desarrollo del escritorio de Windows con C++

Ahora se proporciona una experiencia de instalación más granular para la instalación de la carga de trabajo original de C++. Se han agregado componentes seleccionables que permiten instalar únicamente las herramientas que necesita.  Tenga en cuenta que los tamaños de instalación indicados para los componentes enumerados en la IU del instalador no son precisos y subestiman el tamaño total.

Para crear correctamente proyectos de Win32 en la carga de trabajo de escritorio de C++, debe instalar un conjunto de herramientas y un SDK de Windows. La instalación de los componentes recomendados (seleccionados) **Conjunto de herramientas de VC ++ 2017 v141 (x86, x64)** y **Windows 10 SDK (10.0.nnnnn)** garantizará que esto funcione. Si no se instalan las herramientas necesarias, los proyectos no se crearán correctamente y el asistente se bloqueará.

**Versión 15.5 de Visual Studio 2017**:

Visual C++ Build Tools (anteriormente disponible como un producto independiente) ahora se incluye como carga de trabajo en el instalador de Visual Studio. Esta carga de trabajo instala solo las herramientas necesarias para compilar proyectos de C++ sin tener que instalar el IDE de Visual Studio. Se incluyen los conjuntos de herramientas v140 y v141. El conjunto de herramientas v141 contiene las últimas mejoras en la versión 15.5 de Visual Studio 2017. Para obtener más información, vea [Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/) (Visual Studio Build Tools ahora incluye los conjuntos de herramientas VS2017 y VS2015).

## <a name="linux-development-with-c"></a>Desarrollo para Linux con C++

La extensión popular [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) ya forma parte de Visual Studio. Esta instalación proporciona todo lo que necesita para desarrollar y depurar aplicaciones de C++ que se ejecutan en un entorno de Linux.

**Versión 15.2 de Visual Studio 2017**:

Se han realizado mejoras para el uso compartido de código multiplataforma y visualización de tipos. Para más información, consulte las [mejoras en Linux C++ para el uso compartido de código multiplataforma y visualización de tipos](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/).

**Versión 15.5 de Visual Studio 2017**:

- La carga de trabajo de Linux presenta más opciones de compatibilidad con **rsync** como alternativa a **sftp** para sincronizar archivos en máquinas remotas Linux.
- Se ha agregado compatibilidad para compilación cruzada con destinos de microcontroladores ARM. Para habilitarlo en la instalación, seleccione la carga de trabajo **Desarrollo para Linux con C++** y seleccione la opción para **Desarrollo incrustado e IoT**. Esto agrega las herramientas de compilación cruzada GCC de ARM y Make a su instalación. Para obtener más información, vea [ARM GCC Cross Compilation in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/) (Compilación cruzada de GCC de ARM en Visual Studio).
- Se ha agregado compatibilidad para CMake. Ahora puede trabajar en su base de código CMake sin tener que convertirla a un proyecto de Visual Studio. Para obtener más información, vea [Configure a Linux CMake Project](linux/cmake-linux-project.md) (Configuración de un proyecto CMake de Linux).
- Se ha agregado compatibilidad para la ejecución de tareas remotas. Esta capacidad le permite ejecutar cualquier comando en un sistema remoto que se defina en el Administrador de conexiones de Visual Studio. Las tareas remotas también proporcionan la capacidad de copia de archivos en el sistema remoto.
Para obtener más información, vea [Configure a Linux CMake Project](linux/cmake-linux-project.md) (Configuración de un proyecto CMake de Linux).

**Visual Studio 2017 versión 15.7**:

- Varias mejoras en escenarios de carga de trabajo de Linux. Para obtener más información, vea [Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/) (Mejoras de carga de trabajo de C++ de Linux para el sistema de proyectos, la ventana de la consola de Linux, rsync y Asociar al proceso).
- IntelliSense para encabezados en conexiones remotas de Linux. Para obtener más información, vea [IntelliSense for Remote Linux Headers](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/intellisense-for-remote-linux-headers/) (IntelliSense para encabezados remotos de Linux) y [Configuración de un proyecto de CMake de Linux](linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Desarrollo de juegos con C++

Utilice toda la capacidad de C++ para crear juegos profesionales con tecnología de DirectX o Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Desarrollo móvil con C++ (Android y iOS)

Ahora puede crear y depurar aplicaciones móviles con Visual Studio que pueden tener como destino iOS y Android.

## <a name="universal-windows-apps"></a>Aplicaciones Windows universales

C++ viene como un componente opcional de la carga de trabajo de la Aplicación Windows universal.  Actualmente, la actualización de proyectos de C++ se debe hacer de forma manual. Si abre un proyecto de UWP orientado a v140 en Visual Studio 2017, deberá seleccionar el conjunto de herramientas de la plataforma v141 en las páginas de propiedades del proyecto si no tiene instalado Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nuevas opciones de C++ en la Plataforma universal de Windows (UWP)
Ahora dispone de nuevas opciones para escribir y empaquetar aplicaciones de C++ para la Plataforma universal de Windows y la Tienda Windows: puede usar la infraestructura Puente de dispositivo de escritorio para empaquetar la aplicación de escritorio existente para su implementación a través de la Tienda Windows o a través de los canales existentes mediante la instalación de prueba. Las nuevas capacidades de Windows 10 le permiten agregar funcionalidad de Plataforma universal de Windows a su aplicación de escritorio de varias maneras. Para obtener más información, vea [Puente de dispositivo de escritorio](/windows/uwp/porting/desktop-to-uwp-root).

**Visual Studio 2017, versión 15.5**  
Se ha agregado una plantilla de proyecto **Proyecto de empaquetado de aplicaciones de Windows**, lo que simplifica en gran medida la tarea de empaquetar aplicaciones de escritorio mediante el uso del Puente de dispositivo de escritorio. Está disponible en **Archivo | Nuevo | Proyecto | Instalado | Visual C++ | Plataforma universal de Windows**. Para obtener más información, consulte [Empaquetar una aplicación mediante Visual Studio (Puente de dispositivo de escritorio a UWP)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Al escribir código nuevo, ahora puede usar C++/WinRT, una proyección del lenguaje C++ estándar para Windows Runtime que se implementa solamente en los archivos de encabezado. Permite crear y usar las API de Windows Runtime con cualquier compilador de C++ conforme a los estándares. C++/WinRT está diseñado para proporcionar a los desarrolladores de C++ acceso de primera a la API de Windows moderna. Para obtener más información, vea [C++/WinRT Available on GitHub](https://moderncpp.com/) (C++/WinRT está disponible en GitHub).

En la [compilación 17025 de la versión preliminar de Insider de Windows SDK](https://blogs.windows.com/buildingapps/2017/11/01/windows-10-sdk-preview-build-17025/#ryPH3zAy6yk2cIRX.97), C++/WinRT se incluyen en Windows SDK. Para obtener más información, vea [C++/WinRT is now included the Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/) (Ahora se incluyen C++/WinRT en Windows SDK).

## <a name="clangc2-platform-toolset"></a>Conjunto de herramientas de la plataforma Clang/C2

El conjunto de herramientas Clang/C2 que se incluye con Visual Studio 2017 ahora es compatible con el modificador **/bigobj**, que es fundamental para la creación de proyectos grandes. También incluye varias correcciones de errores importantes, tanto en el front-end y el back-end del compilador.

## <a name="c-code-analysis"></a>Análisis de código de C++

Ahora se distribuyen con Visual Studio los comprobadores principales de C++ para aplicar las [directrices principales de C++](https://github.com/isocpp/CppCoreGuidelines). Simplemente habilite los comprobadores en la página **Extensiones de análisis de código** en las páginas de propiedades del proyecto y las extensiones se incluirán al ejecutar análisis de código. Para más información, consulte [Usar los comprobadores de directrices principales de C++](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Página de propiedades de CppCoreCheck")

**Visual Studio 2017 versión 15.3**: se agregó compatibilidad con reglas relativas a la administración de recursos.

**Visual Studio 2017, versión 15.5**: las nuevas comprobaciones de C++ Core Guidelines cubren la corrección del puntero inteligente, el uso adecuado de inicializadores globales y la marca de usos de construcciones como `goto` y conversiones incorrectas.

Algunos números de advertencias que puede encontrar en 15.3 ya no están disponibles en 15.5. Estas advertencias se han sustituido por comprobaciones más específicas.

**Visual Studio 2017 versión 15.6**:  
Se ha agregado compatibilidad para el análisis de archivo único y mejoras en el rendimiento en tiempo de ejecución de los análisis. Para obtener más información, vea [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/) (Mejoras de análisis estático de C++ para Visual Studio de 2017 15.6 [versión preliminar 2])

**Visual Studio 2017 versión 15.7**:  

- Se ha agregado compatibilidad para [/analyze:ruleset](build/reference/analyze-code-analysis.md) que permite especificar las reglas de análisis de código que se van a ejecutar.
- Se ha agregado compatibilidad para reglas de C++ Core Guidelines adicionales.  Para más información, consulte [Usar los comprobadores de directrices principales de C++](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Pruebas unitarias

**Versión 15.5 de Visual Studio 2017**:

Google Test Adapter y Boost.Test Adapter ahora están disponibles como componentes de la carga de trabajo **Desarrollo para el escritorio con C++** y se integran con el **Explorador de pruebas**. Se ha agregado compatibilidad con CTest para proyecto CMake (con Abrir carpeta), aunque todavía no está disponible la integración completa con el **Explorador de pruebas**. Para obtener más información, vea [Writing unit tests for C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp) (Escritura de pruebas unitarias para C/C++).

**Visual Studio 2017 versión 15.6**:

- Se ha agregado compatibilidad para admitir la biblioteca dinámica de Boost.Test.
- Ahora en el IDE hay una plantilla de elemento Boost.Test disponible.

Para obtener más información, vea [Boost.Test Unit Testing: Dynamic Library support and New Item Template](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/boost-test-unit-testing-dynamic-library-support-and-new-item-template/) (Prueba unitaria Boost.Test: compatibilidad con las bibliotecas dinámicas y nueva plantilla de elemento). 

**Visual Studio 2017 versión 15.7**:

Se ha agregado compatibilidad con [CodeLens](https://docs.microsoft.com/en-us/visualstudio/ide/find-code-changes-and-other-history-with-codelens) para proyectos de pruebas unitarias de C++. Para obtener más información, vea [Announcing CodeLens for C++ Unit Testing](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/announcing-codelens-for-c-unit-testing/) (Anuncio de CodeLens para pruebas unitarias de C++).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos de Visual Studio

Diagnóstico de gráficos de Visual Studio es un conjunto de herramientas para grabar y analizar problemas de representación y rendimiento de las aplicaciones de Direct3D. Las características de Diagnóstico de gráficos pueden usarse con aplicaciones que se ejecutan localmente en su PC Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.

- **Entrada y salida para sombreadores de vértices y geometría:** la función para ver la entrada y la salida de los sombreadores de vértices y de geometría ha sido una de las más solicitadas, y ahora es compatible con las herramientas. Basta con que seleccione la fase VS (sombreadores de vértices) o GS (sombreadores de geometría) en la vista Etapas de canalización para empezar a inspeccionar su entrada y su salida en la tabla siguiente.

  ![Entrada y salida de los sombreadores](media/io-shaders.png)

- **Búsqueda y filtrado en la tabla de objetos:** proporciona un modo rápido y sencillo de encontrar los recursos que se buscan.

  ![Buscar](media/search.png)

- **Historial de recursos:** esta nueva vista proporciona una manera simplificada de ver el historial completo de modificaciones de un recurso tal como se usó durante el procesamiento de un fotograma capturado. Para invocar el historial de un recurso, haga clic en el icono de reloj que se encuentra junto a los hipervínculos de recursos.

  ![Historial de recursos](media/resource-history.png)

  De este modo se mostrará la nueva ventana de herramientas **Historial de recursos**, rellenada con el historial de cambios del recurso.

  ![Historial de cambios del recurso](media/resource-history-change.png)

  Tenga en cuenta que, si el fotograma se ha capturado con la captura de pila de llamadas completa habilitada (**Visual Studio > Herramientas > Opciones** en **Diagnóstico de gráficos**), el contexto de cada evento de cambio se puede deducir rápidamente e inspeccionar dentro del proyecto de Visual Studio.

- **Estadísticas de API:** vea un resumen de alto nivel del uso de la API en su fotograma. Esto puede ser útil para detectar llamadas que tal vez no sepa que realiza o para detectar llamadas que realiza demasiado. Esta ventana está disponible en **Vista > Estadísticas de API** en el Analizador de gráficos de Visual Studio.

  ![Estadísticas de API](media/api-stats.png)

- **Estadísticas de memoria:** vea cuánta memoria asigna el controlador a los recursos que crea en el fotograma. Esta ventana está disponible en **Vista > Estadísticas de memoria** en el **Analizador de gráficos de Visual Studio**. Es posible copiar los datos en un archivo .csv para verlos en una hoja de cálculo. Para ello, haga clic con el botón derecho y seleccione **Copiar todo**.

  ![Estadísticas de memoria](media/memory-stats.png)

- **Validación de fotogramas:** la nueva lista de errores y advertencias proporciona una manera fácil de navegar por la lista de eventos en función de los posibles problemas que haya detectado la capa de depuración de Direct3D. Haga clic en **Ver > Validación de fotogramas** en el Analizador de gráficos de Visual Studio para abrir la ventana. Después, haga clic en **Ejecutar validación** para comenzar el análisis. Puede tardar varios minutos en completarse, en función de la complejidad del fotograma.

  ![Validación de fotogramas](media/frame-validation.png)

- **Análisis de fotogramas para D3D12**: use el análisis de fotogramas para analizar el rendimiento de las llamadas a draw con experimentos "y si" dirigidos. Cambie a la pestaña Análisis de fotogramas y ejecute un análisis para ver el informe. Para obtener más información, vea el vídeo [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) (GoingNative 25: análisis de fotogramas de gráficos de Visual Studio).

  ![Análisis de fotogramas](media/frame-analysis.png)

- **Mejoras de uso de GPU:** abra los seguimientos realizados mediante el Generador de perfiles de uso de GPU de Visual Studio con la herramienta Vista de GPU o Windows Performance Analyzer (WPA) para obtener análisis más detallados. Si tiene instalado Windows Performance Toolkit, habrá dos hipervínculos (uno para WPA y otro para Vista de GPU) en la parte inferior derecha de la información general de la sesión.

  ![Uso de GPU](media/gpu-usage.png)

  Los seguimientos abiertos en Vista de GPU a través de este vínculo admiten el zoom y el movimiento panorámico sincronizados en la escala de tiempo entre VS y Vista de GPU. Se usa una casilla de VS para controlar si la sincronización está habilitada o no.

  ![Vista de GPU](media/gpu-view.png)
