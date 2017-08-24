---
title: Novedades de Visual C++ en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 8/2/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: b90891be2ca726bb6cdd28d024cda68494e69af4
ms.openlocfilehash: 9103da7fb4e10553d2558b15a24bc6a894dd1eff
ms.contentlocale: es-es
ms.lasthandoff: 08/15/2017

---

# <a name="whats-new-for-visual-c-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>Novedades de Visual C++ en [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] incluye muchas actualizaciones y correcciones del entorno de Visual C++. Hemos corregido más de 250 errores y problemas notificados en el compilador y las herramientas, muchos enviados por los usuarios a través de [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect"). ¡Muchas gracias por notificárnoslos!  Para más información sobre todas las novedades de Visual Studio, visite [Novedades de [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]](https://go.microsoft.com/fwlink/?linkid=834481).

<!--The compiler and tools version number in [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] is 14.10.24629. -->


## <a name="c-compiler"></a>Compilador C++

### <a name="c-conformance-improvements"></a>Mejoras de conformidad de C++
En esta versión, hemos actualizado el compilador C++ y la biblioteca estándar con compatibilidad mejorada con características de C ++ 11 y C ++ 14, así como la compatibilidad preliminar para determinadas características que se esperan que estén en C ++ 17 estándar. Para obtener información detallada, vea [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements-2017.md).

### <a name="new-compiler-switches"></a>Nuevos modificadores del compilador  

 -**/std:c++14** y **/std:c++latest**: estos modificadores de compilador le permiten participar en versiones específicas del lenguaje de programación ISO C++ en un proyecto. Para más información, consulte [-std (Especificar la versión estándar del lenguaje)](build/reference/std-specify-language-standard-version.md). La mayoría de las nuevas características del proyecto estándar están protegidas por el modificador /std:c++latest. 

**Visual Studio 2017 versión 15.3**: la opción **/std:c++17** habilita el conjunto de características de C++17 que implementa el compilador de Visual C++. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características que se modificaron o que son nuevas en las versiones más recientes del borrador de trabajo y las actualizaciones de defectos de C++ Standard.

-[/permissive-](build/reference/permissive-standards-conformance.md): habilita todas las opciones del compilador de cumplimiento de estándares estrictos y deshabilita la mayoría de las extensiones del compilador específicas de Microsoft (pero no __declspec(dllimport), por ejemplo). (Desactivado de forma predeterminada, pero estará activado de forma predeterminada en algún momento en el futuro).

-[/diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md): permite mostrar el número de línea, el número de línea y columna, o el número de línea y columna y un símbolo de intercalación bajo la línea de código donde se encontró el error de diagnóstico o la advertencia.

-[/debug:fastlink](build/reference/debug-generate-debug-info.md):  
permite tiempos de vínculo incremental hasta un 30 % más rápidos (frente a Visual Studio 2015), ya que no copia toda la información de depuración en el archivo PDB. En su lugar, el archivo PDB apunta a la información de depuración de los archivos de biblioteca y del objeto usados para crear el ejecutable. Vea [Faster C++ build cycle in VS "15" with /Debug:fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) (Ciclo de compilación en C++ más rápido en VS "15" con /Debug:fastlink) y [Recommendations to speed C++ builds in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/) (Recomendaciones para acelerar las compilaciones en C++ en Visual Studio).

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] permite usar /sdl con /await. Hemos quitado la limitación de /RTC con corrutinas. 

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, seguridad, diagnóstico y control de versiones
Esta versión ofrece varias mejoras en la optimización, la generación de código, el control de versiones del conjunto de herramientas y el diagnóstico. Estas son algunas de las mejoras destacables incluidas:  

- Generación de código de bucles mejorada: compatibilidad con vectorización automática de división de enteros constantes, mejor identificación de patrones de memset.
- Seguridad de código mejorada: emisión mejorada de diagnósticos de compilador de saturación del búfer y /guard:cf ahora protege instrucciones switch que generan tablas de saltos.
- Control de versiones: el valor de la macro de preprocesador integrada _MSC_VER se está actualizando de forma continua en cada actualización del conjunto de herramientas de Visual C++. Para obtener más información, vea [Visual C++ Compiler Version](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) (Versión del compilador de Visual C++).
- Nuevo diseño del conjunto de herramientas: el compilador y las herramientas de compilación relacionadas tienen una nueva ubicación y estructura de directorios en la máquina de desarrollo. El nuevo diseño permite instalaciones en paralelo de varias versiones del compilador. Para más información, vea [Compiler Tools Layout in Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/) (Diseño de las herramientas del compilador en Visual Studio "15").
- Diagnóstico mejorado: en la ventana de salida ahora se muestra la columna en la que se produce un error. Para más información, vea [C++ improvisamente diagnostics improvements in VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/) (Mejoras del diagnóstico del compilador C++ en VS "15" Preview 5).
- Se quitó la palabra clave experimental "yield" (disponible en el modificador /await) cuando se usan las corrutinas. En su lugar, se debe actualizar el código para que use `co_yield`. Para más información, consulte el [blog del equipo de Visual C++](https://blogs.msdn.microsoft.com/vcblog/). 

**Visual Studio 2017 versión 15.3**: mejoras adicionales en los diagnósticos del compilador. Para más información, consulte el artículo sobre las [mejoras de diagnósticos en Visual Studio 2017 15.3.0](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/).

## <a name="c-libraries"></a>Bibliotecas de C++

### <a name="standard-library-improvements"></a>Mejoras de la biblioteca estándar:

* Mejoras menores en los diagnósticos basic_string _ITERATOR_DEBUG_LEVEL != 0. Activar una comprobación de IDL en la maquinaria de cadenas ahora indicará la conducta específica que provocó la activación. Por ejemplo, en lugar de recibir el mensaje "string iterator not dereferenceable" (El iterador de cadena no es desreferenciable), verá el mensaje "cannot dereference string iterator because it is out of range (e.g. an end iterator)" (No se puede desreferenciar el iterador de cadena porque está fuera del rango (por ejemplo, un iterador final).
* Mejoras del rendimiento: se hizo que las sobrecargas de basic_string::find(char) solo llamen una vez a traits::find. Anteriormente esto se implementó como buscar en las cadenas generales una cadena de longitud 1.
* Mejora en el rendimiento: basic_string::operator== ahora comprueba el tamaño de las cadenas antes de comparar el contenido de las mismas.
* Mejora en el rendimiento: se quitó el acoplamiento de control en basic_string, que era difícil de analizar para el optimizador de compilador. Resuelve VSO# 262848 "\<string\>: reserve() trabaja demasiado". Tenga en cuenta que, para todas las cadenas cortas, la reserva de llamadas sigue teniendo un costo distinto de cero para no hacer nada.
* Agregamos \<any\>, \<string_view\>, apply(), make_from_tuple().
* Se mejoró std::vector para aumentar la precisión y el rendimiento: los alias durante la inserción/emplazamiento se controlan correctamente según lo requerido por el estándar, la garantía de excepción sólida ahora se proporciona cuando el estándar lo solicita a través de move_if_noexcept() y otra lógica; además, la inserción o el emplazamiento realiza menos operaciones de elementos.
* Ahora, la biblioteca estándar de C++ evita desreferenciar punteros elaborados nulos.
* Se ha agregado \<optional\>, \<variant\>, shared_ptr::weak_type y \<cstdalign\>.
* Se ha habilitado C++14 constexpr in min/max/minmax(initializer_list) y min_element/max_element/minmax_element().
* Se ha mejorado el rendimiento de weak_ptr::lock().
* Se ha corregido el operador de asignación de movimiento de std::promise, que anteriormente podía provocar que el código se bloqueara permanentemente.
* Se han corregido errores del compilador con la conversión implícita de atomic\<T \*\> a T \*.
* pointer_traits\<Ptr\> ahora detecta correctamente Ptr::rebind\<U\>.
* Se ha corregido un calificador const en el operador de resta de move_iterator.
* Se ha corregido un codegen incorrecto silencioso para asignadores definidos por el usuario con estado que solicitan propagate_on_container_copy_assignment y propagate_on_container_move_assignment.
* atomic\<T\> ahora admite operator&() sobrecargado.
* Para aumentar el rendimiento del compilador, los encabezados de la biblioteca estándar de C++ ahora evitan incluir declaraciones de intrínsecos del compilador innecesarios.
* Diagnóstico de compilador mejorado ligeramente para llamadas bind() incorrectas.
* Se mejora el rendimiento de los constructores de movimiento de std::string o std::wstring al multiplicarse por más de tres.
* Para una lista completa de las mejoras en la biblioteca estándar, consulte el artículo sobre las [correcciones de la biblioteca estándar en VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/).

#### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

##### <a name="c17-features"></a>Características de C++17 
Se implementaron varias características adicionales de C++17. Para más información, consulte [Conformidad del lenguaje Visual C++](visual-cpp-language-conformance.md).

##### <a name="other-new-features"></a>Otras características nuevas
* Se implementó P0602R0 "variante y opcional deben propagar la trivialidad de copia/movimiento".
* La biblioteca estándar ahora tolera de manera oficial que RTTI dinámico se deshabilite mediante /GR-. dynamic_pointer_cast() y rethrow_if_nested() requieren de manera inherente dynamic_cast, por lo que la biblioteca estándar ahora los marca como =delete en /GR-.
* Incluso si RTTI dinámico se deshabilita mediante /GR-, "RTTI estático" (con formato typeid(SomeType)) sigue disponible y potencia a varios componentes de la biblioteca estándar. La biblioteca estándar ahora también admite deshabilitarlo, con /D_HAS_STATIC_RTTI=0. *Tenga en cuenta que con esto se deshabilitará std::any, std::function's target() y target_type(), y get_deleter() de shared_ptr.*

##### <a name="correctness-fixes"></a>Correcciones de exactitud
* La biblioteca estándar ahora fija su max_size() en numeric_limits\<difference_type\>::max() en lugar del máximo de size_type. Esto asegura que el resultado de distance() en los iteradores de ese contenedor se representa en el tipo de valor devuelto de distance().
* Se corrigió la omisión de la especialización auto_ptr\<void\>.
* Anteriormente, los algoritmos meow_n() no se compilaban si el argumento de longitud no era un tipo de datos entero. Ahora intentan convertir las longitudes no integrales en el difference_type de los iteradores.
* normal_distribution\<float\> ya no emite advertencias dentro de la biblioteca estándar con respecto a la restricción de double a float.
* Se corrigieron algunas operaciones basic_string que se comparaban con npos en lugar de max_size() cuando se comprobaba el desbordamiento de tamaño máximo.
* condition_variable::wait_for(lock, relative_time, predicate) podía esperar todo el tiempo relativo ante la eventualidad de una reactivación en falso. Ahora, solo esperará un intervalo único del tiempo relativo.
* future::get() ahora invalida el futuro, tal como requiere el estándard.
* iterator_traits\<void \*\> solía ser un error porque intentaba formar&; ahora se convierte limpiamente en una estructura vacía para permitir el uso de iterator_traits en condiciones SFINAE "is iterator".
* Se corrigieron algunas advertencias informadas por Clang -Wsystem-headers.
* También se corrigió "la especificación de excepción en la declaración no coincide con la declaración anterior" que informó Clang -Wmicrosoft-exception-spec.
* También se corrigió mem-initializer-list que ordena las advertencias informadas por Clang y C1XX.
* Los contenedores sin ordenar no intercambiaban sus hashers o predicados cuando se intercambiaban los contenedores mismos. Ahora sí lo hacen.
* Muchas operaciones de intercambio de contenedores ahora están marcados como noexcept (puesto que la biblioteca estándar nunca tiene la intención de generar una excepción al detectar la condición de comportamiento no definido non-propagate_on_container_swap non-equal-allocator).
* Muchas operaciones vector\<bool\> ahora están marcadas como noexcept.
* La biblioteca estándar ahora aplicará la coincidencia entre el asignador value_types (en modo C++17) con un sombreado de escape de rechazo.
* Se corrigieron algunas condiciones en las que self-range-insert en basic_strings podría revolver el contenido de las cadenas. (Nota: la biblioteca estándar sigue prohibiendo self-range-insert en vectores).
* basic_string::shrink_to_fit() ya no se ve afectado por propagate_on_container_swap del asignador.
* std::decay ahora controla los tipos de funciones abominables (es decir, los tipos de función cv-qualified o ref-qualified).
* Los cambios incluyen directivas para usar la distinción entre mayúsculas y minúsculas y barras diagonales para mejorar la portabilidad.
* Se corrigió la advertencia C4061 "el enumerador 'Meow' en la instrucción switch de la enumeración 'Kitten' no está controlado de forma explícita por una etiqueta de caso". Esta advertencia está desactivada de manera predeterminada y se corrigió como una excepción de la directiva general de advertencias de la biblioteca estándar. (La biblioteca estándar no tiene /W4, pero no tiene la intención de no tener /Wall. Muchas advertencias desactivadas de manera predeterminada son muy ruidosas y no están diseñadas para usarlas de manera regular).
* Se mejoraron las comprobaciones de depuración de std::list. Los iteradores de lista ahora comprueban operator->() y list::unique() ahora marca los iteradores como invalidados.
* Se corrigió la metaprogramación uses-allocator en la tupla.

##### <a name="performancethroughput-fixes"></a>Correcciones de rendimiento
* Se solucionaron las interacciones con noexcept que impedían insertar la implementación de std::atomic en funciones que usan Control de excepciones estructurado (SEH).
* Se cambió la función internal _Deallocate() de la biblioteca estándar para optimizarla en un código más pequeño, lo que permitirá insertarla en más lugares.
* Se cambió std::try_lock() para usar la expansión del paquete en lugar de la recursividad.
* Se mejoró el algoritmo de prevención de interbloqueo de std::lock() para usar operaciones lock() en lugar de dar giros en todos los try_lock() de los bloqueos.
* Se habilitó la optimización del valor devuelto con nombre en system_category::message().
* Conjunción y disyunción ahora crean instancias de tipos N + 1, en lugar de tipos 2N + 2.
* std::function ya no crea instancias de maquinaria de compatibilidad con el asignador para cada invocable con tipo borrado, lo que mejora el rendimiento y disminuye el tamaño de .obj en programas que pasan muchas expresiones lambda distintas a std::function.
* allocator_traits\<std::allocator\> contiene operaciones std::allocator insertadas manualmente, lo que disminuye el tamaño del código que interactúa con std::allocator solo a través de allocator_traits (es decir, la mayoría del código).
* La biblioteca estándar ahora controla la interfaz de controlador mínimo de C++11 mediante una llamada directa a allocator_traits en lugar de encapsular el asignador en una clase interna _Wrap_alloc. Con esto se disminuye el tamaño del código que se genera para la compatibilidad del asignador, se mejora la capacidad del optimizador para razonar sobre los contenedores de la biblioteca estándar en algunos casos y brinda una mejor experiencia de depuración (porque ahora puede ver el tipo de asignador en lugar de _Wrap_alloc\<su tipo de asignador\> en el depurador).
* Se quitó la metaprogramación para allocator::reference personalizada, que los asignadores en realidad no tienen permitido personalizar. (Los asignadores pueden hacer que los contenedores usen punteros sofisticados pero no referencias sofisticadas).
* El front-end del compilador se diseñó para desencapsular los iteradores de depuración en Bucles for basados en intervalos, lo que mejora el rendimiento de las compilaciones de depuración.
* La ruta de reducción interna de basic_string para shrink_to_fit() y reserve() ya no está en la ruta de reasignar operaciones, lo que reduce el tamaño del código para todos los miembros de mutación.
* La ruta de crecimiento interna de basic_stringya no está en la ruta de shrink_to_fit().
* Las operaciones de mutación de basic_string ahora se factorizan en funciones de ruta rápida no de asignación y de ruta lenta de asignación, lo que hace más probable que el caso no de reasignación se inserte en los llamadores.
* Las operaciones de mutuación de basic_string ahora construyen búferes reasignado con el estado deseado en lugar de cambiar el tamaño en el mismo lugar. Por ejemplo, la inserción en el comienzo de una cadena ahora mueve el contenido después de la inserción exactamente una vez (ya sea hacia abajo o al búfer recién asignado) en lugar de dos veces en el caso de reasignación (al búfer recién asignado y luego abajo).
* Las operaciones que llaman a la biblioteca estándar C en \<string\> ahora almacenan en caché la dirección errno para quitar la interacción repetida con TLS.
* Se simplificó la implementación de is_pointer.
* Se completó el cambio de la expresión SFINAE basada en función a basada en struct/void_t.
* Los algoritmos de la biblioteca estándar ahora evitan el postincremento de los iteradores.
* Se corrigieron las advertencias de truncamiento cuando se usan asignadores de 32 bits en sistemas de 64 bits.
* La asignación de movimiento de std::vector move ahora es más eficaz en el caso non-equal-allocator a través de volver a usar el búfer cuando sea posible.

##### <a name="readability-and-other-improvements"></a>Legibilidad y otras mejoras
* La biblioteca estándar ahora usa constexpr de C++14 sin condiciones, en lugar de macros definidas condicionalmente.
* La biblioteca estándar ahora usa plantillas de alias de forma interna.
* La biblioteca estándar ahora usa nullprt de forma interna, en lugar de nullptr_t{}. (Se eliminó el uso interno de NULL. El uso interno de 0-as-null se está limpiando de forma gradual).
* La biblioteca estándar ahora usa std::move() de forma interna en lugar de hacer mal uso de std::forward() estilísticamente.
* Se modificó el formato de static_assert(false, "mensaje") al de mensaje #error. Con esto se mejoran los diagnósticos del compilador, porque #error detiene inmediatamente la compilación.
* La biblioteca estándar ya no marca las funciones como __declspec(dllimport). La tecnología de enlazador moderna ya no lo requiere.
* Se extrajo SFINAE a argumentos de plantilla predeterminados, lo que reduce el desorden en comparación con los tipos de valor devuelto y los tipos de argumento de función.
* Las comprobaciones de depuración en \<random\> ahora usan la maquinaria usual de la biblioteca estándar en lugar de la función interna _Rng_abort() que llamaba fputs() a stderr. La implementación de esta función se conserva por motivos de compatibilidad binaria, pero se quitó en la siguiente versión sin compatibilidad binaria de la biblioteca estándar. 

### <a name="open-source-library-support"></a>Compatibilidad con bibliotecas de código abierto  
Vcpkg es una herramienta de línea de comandos de código abierto que simplifica enormemente el proceso de adquirir y compilar bibliotecas estáticas de C++ de código abierto y archivos DLL en Visual Studio. Para más información, vea [Vcpkg: Administrador de paquetes de C++ para Windows](vcpkg.md).

### <a name="cpprest-sdk-290"></a>CppRestSDK 2.9.0  
Se ha actualizado CppRestSDK (una API web multiplataforma para C++) a la versión 2.9.0. Para obtener más información, vea [CppRestSDK 2.9.0 is available on GitHub](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/) (CppRestSDK 2.9.0 está disponible en GitHub).

### <a name="atl"></a>ATL
* Otro conjunto de correcciones de conformidad para la búsqueda de nombres.
* Los operadores de constructores de movimiento y de asignación de movimiento están ahora correctamente marcados como no productores de excepciones.
* Inclusión de la advertencia válida C4640 sobre la inicialización segura de subprocesos de elementos estáticos locales en atlstr.h.
* La inicialización segura de subprocesos de elementos estáticos locales estaba desactivada automáticamente en el conjunto de herramientas de XP al [usar ATL Y crear un archivo DLL]. Pero esto ya no es así. Puede agregar /Zc:threadSafeInit- en la configuración del proyecto si se desea tener desactivada la inicialización segura de subprocesos. 

### <a name="visual-c-runtime"></a>Runtime de Visual C++
* Nuevo encabezado "cfguard.h" para símbolos de protección de flujo de control. 

## <a name="c-ide"></a>C++ IDE

* El rendimiento del cambio de configuración ahora es mejor para proyectos nativos de C++ y mucho mejor para proyectos C++/CLI. Cuando se activa una configuración de solución por primera vez, ahora será más rápida y todas las activaciones posteriores de esta configuración de la solución serán casi instantáneas.

**Visual Studio 2017 versión 15.3**:
* Algunos asistentes de código y proyecto se han vuelto a escribir en el estilo del cuadro de diálogo de signatura.
* Ahora, al usar la opción **Agregar clase** se abre directamente el Asistente para agregar clases. Todos los demás elementos que estaban previamente aquí se encuentran disponibles ahora en **Agregar > Nuevo elemento**.
* Ahora, los proyectos de Win32 están en la categoría Escritorio de Windows en el cuadro de diálogo **Nuevo proyecto**.
* Ahora, las plantillas de la consola de Windows y de la aplicación de escritorio crean proyectos sin abrir un asistente. Ahora hay un nuevo Asistente de escritorio de Windows en la misma categoría que muestra las mismas opciones que antes.

### <a name="intellisense"></a>Intellisense  
* Ahora se está usando el nuevo motor de base de datos basado en SQLite de forma predeterminada. Esto acelerará las operaciones de base de datos como Definiciones de ir y Buscar todas las referencias y mejorará significativamente el tiempo de análisis de la solución inicial. La configuración se ha movido a Herramientas > Opciones > Editor de texto > C o C++ > Opciones avanzadas (se encontraba anteriormente en... C/C++ > Experimental).

* Se ha mejorado el rendimiento de IntelliSense en proyectos y archivos que no usan encabezados precompilados; se creará un encabezado precompilado automático para los encabezados en el archivo actual.

* Se ha agregado el filtro de errores y la ayuda para errores de IntelliSense en la lista de errores. Ahora se puede filtrar al hacer clic en la columna de errores. Además, al hacer clic en los errores específicos o al presionar F1, se iniciará una búsqueda en línea del mensaje de error.

  ![Lista de errores](media/ErrorList1.png "Lista de errores")

  ![Lista de errores filtrados](media/ErrorList2.png "Lista de errores filtrados")

* Se agregó la capacidad de filtrar los elementos de la lista de miembros por tipo.

  ![Filtrado de la lista de miembros](media/mlfiltering.png "Filtrado de la lista de miembros")

* Se ha agregado una nueva característica de IntelliSense predictiva experimental que proporciona un filtrado de lo que aparece en la lista de miembros que tiene en cuenta el contexto. Vea [C++ IntelliSense Improvements – Predictive IntelliSense & Filtering](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/) (Mejoras de IntelliSense de C++: IntelliSense predictivo y filtrado).

* Ahora, Buscar todas las referencias (Mayús+F12) le ayuda a moverse con facilidad, incluso en códigos base complejos. Proporciona agrupación avanzada, filtrado, ordenación, búsqueda en los resultados y (para algunos idiomas) uso de colores, para que pueda entender claramente las referencias. Para C++, la nueva interfaz de usuario incluye información sobre si se lee desde una variable o si se escribe en ella.

* La característica Punto a flecha de IntelliSense pasó de experimental a avanzada y ahora está habilitada de manera predeterminada. Las características del editor Expandir ámbitos y Expandir precedencia también pasaron de ser una característica experimental a una característica avanzada.

* Las características experimentales de refacturación Cambiar signatura y Extraer función ahora están disponibles de manera predeterminada.

* La característica experimental para proyectos de C++ "Carga de proyecto más rápida". La próxima vez que abra un proyecto de C++, se cargará más rápido y la siguiente todavía más.

Algunas de estas características son comunes a otros lenguajes y otras son específicas de C++. Para obtener más información sobre estas nuevas características, vea [Announcing Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/) (Presentación de Visual Studio "15"). 


### <a name="support-for-non-msbuild-projects-with-open-folder"></a>Compatibilidad con proyectos que no son de MSBuild con Abrir carpeta
Visual Studio 2017 incluye la característica "Abrir carpeta", que permite codificar, compilar y depurar en un carpeta que contenga código fuente sin necesidad de crear soluciones o proyectos. Esto hace que sea mucho más fácil empezar a trabajar con Visual Studio, incluso si el proyecto no es un proyecto basado en MSBuild. Con "Abrir carpeta", obtiene acceso a las potentes funciones para entender, editar, compilar y depurar el código que Visual Studio proporciona para proyectos de MSBuild. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](ide/non-msbuild-projects.md).

* Mejoras en la experiencia de Abrir carpeta. Puede personalizar la experiencia con estos archivos .json:
  - CppProperties.json para personalizar la experiencia de IntelliSense y de exploración.
  - Tasks.json para personalizar los pasos de compilación. 
  - Launch.json para personalizar la experiencia de depuración.

**Visual Studio 2017 versión 15.3**: 
* Se mejoró la compatibilidad con compiladores alternativos y entornos de compilación como MinGW y Cygwin. Para más información, consulte el artículo sobre el [uso de MinGW y Cygwin con Visual C++ y Abrir carpeta](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
* Se ha agregado compatibilidad para definir variables de entorno globales y específicas de la configuración en "CppProperties.json" y "CMakeSettings.json". Estas variables de entorno se pueden usar en las configuraciones de depuración definidas en "launch.vs.json" y en las tareas de "tasks.vs.json".
* Se mejoró la compatibilidad con el generador Ninja de CMake, incluida la capacidad de apuntar fácilmente a las plataformas de 64 bits.

### <a name="cmake-support-via-open-folder"></a>Compatibilidad con CMake mediante Abrir carpeta
Visual Studio 2017 incluye compatibilidad con el uso de proyectos CMake sin convertirlos en archivos de proyecto de MSBuild (.vcxproj). Para más información, consulte el artículo sobre [proyectos CMake en Visual C++](ide/cmake-tools-for-visual-cpp.md). Si abre proyectos CMake con "Abrir carpeta", el entorno se configurará automáticamente para la edición, la compilación y la depuración de C++.

* IntelliSense de C++ trabajará sin la necesidad de crear un archivo CppProperties.json en la carpeta raíz. Además, agregamos un nuevo menú desplegable que le permite a los usuarios cambiar fácilmente entre las configuraciones que proporcionan los archivos CMake y CppProperties.json.

* Se admite una configuración adicional a través de un archivo CMakeSettings.json que reside en la misma carpeta que el archivo CMakeLists.txt.

  ![Abrir carpeta Cmake](media/cmake_cpp.png "Abrir carpeta CMake")

**Visual Studio 2017 versión 15.3**: se agregó compatibilidad con el generador CMake Ninja. Para más información, consulte el artículo sobre [compatibilidad con CMake en Visual Studio: novedades en 2017 15.3 versión preliminar 2](https://blogs.msdn.microsoft.com/vcblog/2017/06/14/cmake-support-in-visual-studio-whats-new-in-2017-15-3-preview-2/). 

## <a name="c-installation-workloads"></a>Cargas de trabajo de instalación de C++ 

### <a name="windows-desktop-development-with-c"></a>Desarrollo del escritorio de Windows con C++:  
Ahora se proporciona una experiencia de instalación más granular para la instalación de la carga de trabajo original de C++. Se han agregado componentes seleccionables que permiten instalar únicamente las herramientas que necesita.  Tenga en cuenta que los tamaños de instalación indicados para los componentes enumerados en la IU del instalador no son precisos y subestiman el tamaño total.

Para crear correctamente proyectos de Win32 en la carga de trabajo de escritorio de C++, debe instalar un conjunto de herramientas y un SDK de Windows. La instalación de los componentes recomendados (seleccionados) "Conjunto de herramientas de VC ++ 2017 v141 (x86, x64)" y "Windows 10 SDK (10.0.14393)" garantizará que esto funciona. Si no se instalan las herramientas necesarias, los proyectos no se crearán correctamente y el asistente se bloqueará.

### <a name="linux-development-with-c"></a>Desarrollo para Linux con C++:  
La extensión popular [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) ya forma parte de Visual Studio. Esta instalación proporciona todo lo que necesita para desarrollar y depurar aplicaciones de C++ que se ejecutan en un entorno de Linux.  

**Visual Studio 2017 versión 15.2**: mejoras para el uso compartido de código multiplataforma y visualización de tipos. Para más información, consulte las [mejoras en Linux C++ para el uso compartido de código multiplataforma y visualización de tipos](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/).

### <a name="game-development-with-c"></a>Desarrollo de juegos con C++:  
Utilice toda la capacidad de C++ para crear juegos profesionales con tecnología de DirectX o Cocos2d.  

### <a name="mobile-development-with-c-android-and-ios"></a>Desarrollo móvil con C++ (Android y iOS):  
Ahora puede crear y depurar aplicaciones móviles con Visual Studio que pueden tener como destino iOS y Android.  

### <a name="universal-windows-apps"></a>Aplicaciones Windows universales:  
C++ viene como un componente opcional de la carga de trabajo de la Aplicación Windows universal.  Actualmente, la actualización de proyectos de C++ se debe hacer de forma manual. Si abre un proyecto de UWP orientado a v140 en Visual Studio 2017, deberá seleccionar el conjunto de herramientas de la plataforma v141 en las páginas de propiedades del proyecto si no tiene instalado Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform"></a>Nuevas opciones de C++ en la Plataforma universal de Windows
Ahora dispone de nuevas opciones para escribir y empaquetar aplicaciones de C++ para la Plataforma universal de Windows y la Tienda Windows. Puede usar Desktop App Converter para empaquetar la aplicación de escritorio existente para su implementación a través de la Tienda Windows. Para obtener más información, vea [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/) (Usar el tiempo de ejecución de Visual C++ en el proyecto Centennial) y [Convertir la aplicación de escritorio en una aplicación para Plataforma universal de Windows (UWP) con el puente de escritorio](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).

Al escribir código nuevo, ahora puede usar C++/WinRT, una proyección del lenguaje C++ estándar para Windows Runtime que se implementa solamente en los archivos de encabezado. Permite crear y usar las API de Windows Runtime con cualquier compilador de C++ conforme a los estándares. C++/WinRT está diseñado para proporcionar a los desarrolladores de C++ acceso de primera a la API de Windows moderna. Para obtener más información, vea [C++/WinRT Available on GitHub](https://moderncpp.com/) (C++/WinRT está disponible en GitHub).


## <a name="clangc2-platform-toolset"></a>Conjunto de herramientas de la plataforma Clang/C2
El conjunto de herramientas Clang/C2 que se incluye con [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] ahora es compatible con el modificador /bigobj, que es fundamental para la compilación de proyectos grandes. También incluye varias correcciones de errores importantes, tanto en el front-end y el back-end del compilador.

## <a name="c-code-analysis"></a>Análisis de código de C++

Ahora se distribuyen con Visual Studio los comprobadores principales de C++ para aplicar las [directrices principales de C++](https://github.com/isocpp/CppCoreGuidelines). Simplemente habilite los comprobadores en el cuadro de diálogo Extensiones de análisis de código en las páginas de propiedades del proyecto y las extensiones se incluirán al ejecutar análisis de código. 

![CppCoreCheck](media/CppCoreCheck.png "Página de propiedades de CppCoreCheck") 

**Visual Studio 2017 versión 15.3**: se agregó compatibilidad con reglas relativas a la administración de recursos. Para más información, consulte [Usar los comprobadores de directrices principales de C++](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Pruebas unitarias

Las nuevas extensiones de Visual Studio le permiten ejecutar las pruebas unitarias según Google Test y Boost.Test directamente en Visual Studio. Para más información, consulte el artículo sobre las [actualizaciones de pruebas unitarias de C++: anuncio del adaptador Boost.Test y mejor compatibilidad con Google Test](https://blogs.msdn.microsoft.com/vcblog/2017/08/04/c-unit-testing-updates-announcing-boost-test-adapter-and-improved-google-test-support/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos de Visual Studio

Diagnóstico de gráficos de Visual Studio es un conjunto de herramientas para grabar y analizar problemas de representación y rendimiento de las aplicaciones de Direct3D. Las características de Diagnóstico de gráficos pueden usarse con aplicaciones que se ejecutan localmente en su PC Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.

* **Entrada y salida para sombreadores de vértices y geometría:** la función para ver la entrada y la salida de los sombreadores de vértices y de geometría ha sido una de las más solicitadas, y ahora es compatible con las herramientas. Basta con que seleccione la fase VS (sombreadores de vértices) o GS (sombreadores de geometría) en la vista Etapas de canalización para empezar a inspeccionar su entrada y su salida en la tabla siguiente.

  ![Entrada y salida de los sombreadores](media/io-shaders.png)

* **Búsqueda y filtrado en la tabla de objetos:** proporciona un modo rápido y sencillo de encontrar los recursos que se buscan.

  ![Buscar](media/search.png)
   
* **Historial de recursos:** esta nueva vista proporciona una manera simplificada de ver el historial completo de modificaciones de un recurso tal como se usó durante el procesamiento de un fotograma capturado. Para invocar el historial de un recurso, haga clic en el icono de reloj que se encuentra junto a los hipervínculos de recursos.

  ![Historial de recursos](media/resource-history.png)

  De este modo se mostrará la nueva ventana de herramientas del historial de recursos, rellenada con el historial de cambios del recurso.

  ![Historial de cambios del recurso](media/resource-history-change.png)

  Tenga en cuenta que, si el fotograma se capturó con la captura de pila de llamadas completa habilitada (**Visual Studio > Herramientas > Opciones > Diagnóstico de gráficos**), el contexto de cada evento de cambio se puede deducir rápidamente e inspeccionar dentro del proyecto de Visual Studio.  

* **Estadísticas de API:** vea un resumen de alto nivel del uso de la API en su fotograma. Esto puede ser útil para detectar llamadas que tal vez no sepa que realiza o para detectar llamadas que realiza demasiado. Esta ventana está disponible en **Vista > Estadísticas de API** en el Analizador de gráficos de Visual Studio.

  ![Estadísticas de API](media/api-stats.png)

* **Estadísticas de memoria:** vea cuánta memoria asigna el controlador a los recursos que crea en el fotograma. Esta ventana está disponible en Vista->Estadísticas de memoria en el Analizador de gráficos de Visual Studio. Es posible copiar los datos en un archivo CSV para verlos en una hoja de cálculo. Para ello, haga clic con el botón derecho y seleccione Copiar todo.

  ![Estadísticas de memoria](media/memory-stats.png)
 
* **Validación de fotogramas:** la nueva lista de errores y advertencias proporciona una manera fácil de navegar por la lista de eventos en función de los posibles problemas que haya detectado la capa de depuración de Direct3D. Haga clic en Ver->Validación de fotogramas en el Analizador de gráficos de Visual Studio para abrir la ventana. Después, haga clic en Ejecutar validación para comenzar el análisis. Puede tardar varios minutos en completarse, en función de la complejidad del fotograma.

  ![Validación de fotogramas](media/frame-validation.png)
 
* **Análisis de fotogramas para D3D12:** use el análisis de fotogramas para analizar el rendimiento de las llamadas a draw con experimentos "y si" dirigidos. Cambie a la pestaña Análisis de fotogramas y ejecute un análisis para ver el informe. Para obtener más información, vea el vídeo [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) (GoingNative 25: análisis de fotogramas de gráficos de Visual Studio).

  ![Análisis de fotogramas](media/frame-analysis.png)

* **Mejoras de uso de GPU:** abra los seguimientos realizados mediante el Generador de perfiles de uso de GPU de Visual Studio con la herramienta Vista de GPU o Windows Performance Analyzer (WPA) para obtener análisis más detallados. Si tiene instalado Windows Performance Toolkit, habrá dos hipervínculos (uno para WPA y otro para Vista de GPU) en la parte inferior derecha de la información general de la sesión.

  ![Uso de GPU](media/gpu-usage.png)
 
  Los seguimientos abiertos en Vista de GPU a través de este vínculo admiten el zoom y el movimiento panorámico sincronizados en la escala de tiempo entre VS y Vista de GPU. Se usa una casilla de VS para controlar si la sincronización está habilitada o no. 

  ![Vista de GPU](media/gpu-view.png) 


 

