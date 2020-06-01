---
title: Novedades de C++ en Visual Studio
ms.date: 05/19/2020
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
ms.openlocfilehash: 7c36112f5d0f7f0475782eb40e31179e67ac4485
ms.sourcegitcommit: 3f91111c0350c0237fddb82766c290307f20e659
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2020
ms.locfileid: "83630486"
---
# <a name="whats-new-for-c-in-visual-studio"></a>Novedades de C++ en Visual Studio

::: moniker range=">=vs-2019"

Visual Studio 2019 incluye muchas actualizaciones y revisiones del entorno de Microsoft C++. Se han corregido muchos errores y problemas en el compilador y las herramientas. Muchos de estos problemas fueron enviados por los clientes mediante las opciones [Notificar un problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019) y [Aportar una sugerencia](https://developercommunity.visualstudio.com/spaces/62/index.html) en **Enviar comentarios**. ¡Muchas gracias por notificárnoslos! Para más información sobre todas las novedades de Visual Studio, visite [Novedades de Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019). Para información sobre las novedades de C++ en Visual Studio 2017, consulte [Novedades de C++ en Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017). Para información sobre las novedades de C++ en Visual Studio 2015 y versiones anteriores, consulte [Novedades de Visual C++ de 2003 a 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="c-compiler"></a>compilador C++

- Se proporciona compatibilidad mejorada con las características y las correcciones de exactitud de C++17, además de compatibilidad experimental con características de C++20, como módulos y corrutinas. Para obtener información detallada, vea [C++ Conformance Improvements in Visual Studio 2019](cpp-conformance-improvements.md) (Mejoras de conformidad de C++ en Visual Studio 2019).

- La opción `/std:c++latest` ahora incluye características de C++20 que no están necesariamente completas, como la compatibilidad inicial con el operador \<=> de C++20 ("nave espacial") para la comparación de tres vías.

- El modificador del compilador `/Gm` de C++ ahora está en desuso. Considere la posibilidad de deshabilitar el modificador `/Gm` en los scripts de compilación si se define explícitamente, aunque también puede ignorar de manera segura la advertencia de desuso de `/Gm`, ya que no se tratará como un error cuando use "Tratar advertencias como errores" (`/WX`).

- Cuando MSVC empiece a implementar las características del proyecto estándar de C++20 con la marca `/std:c++latest`, `/std:c++latest` ahora será incompatible con `/clr` (todas las versiones), `/ZW` y `/Gm`. En Visual Studio 2019, use los modos `/std:c++17` o `/std:c++14` al compilar con `/clr`, `/ZW` o `/Gm` (pero vea la viñeta anterior).

- Los encabezados precompilados ya no se generan de forma predeterminada para la consola de C++ y las aplicaciones de escritorio.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, seguridad, diagnóstico y control de versiones

Análisis mejorado con `/Qspectre` para proporcionar asistencia de mitigación en Spectre Variant 1 (CVE-2017-5753). Para obtener más información, vea [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/) (Mitigaciones de Spectre en MSVC).

## <a name="c-standard-library-improvements"></a>Mejoras de la biblioteca estándar de C++

- Implementación de características y correcciones de exactitud de la biblioteca de C++17 y C++20 adicionales. Para obtener información detallada, vea [C++ Conformance Improvements in Visual Studio 2019](cpp-conformance-improvements.md) (Mejoras de conformidad de C++ en Visual Studio 2019).

- Se ha aplicado el formato clang a los encabezados de la biblioteca estándar de C++ para mejorar la legibilidad.

- Dado que Visual Studio ahora admite Solo mi código de C++, la biblioteca estándar ya no necesita proporcionar maquinaria personalizada para que `std::function` y `std::visit` consigan el mismo efecto. Quitar esa maquinaria no tiene en gran medida ningún efecto visible para el usuario. Una excepción es que el compilador ya no producirá diagnósticos que indican problemas en la línea 15732480 o 16707566 de \<type_traits> o \<variant>.

## <a name="performancethroughput-improvements-in-the-compiler-and-standard-library"></a>Mejoras de rendimiento en el compilador y la biblioteca estándar

- Mejoras en el rendimiento de la compilación, incluida la manera en que el enlazador trata la E/S de archivos y el tiempo de vínculo en la creación y la combinación de tipos de PDB.

- Se ha agregado compatibilidad básica para la vectorización de OpenMP SIMD. Puede habilitarla con el nuevo modificador del compilador **`/openmp:experimental`** . Esta opción permite vectorizar potencialmente los bucles anotados con `#pragma omp simd`. No se garantiza la vectorización y se genera una advertencia para los bucles anotados sin vectorizar. No se admiten cláusulas SIMD; se omiten, y se notifica una advertencia.

- Se ha agregado un nuevo modificador de línea de comandos de inserción, **`/Ob3`** , que es una versión más agresiva de **`/Ob2`** . **`/O2`** (optimizar el binario para acelerar el proceso) todavía implica **`/Ob2`** de manera predeterminada. Si considera que el compilador no realiza las inserciones con la suficiente agresividad, considere la posibilidad de pasar **`/O2 -Ob3`** .

- Hemos agregado compatibilidad con las funciones intrínsecas de la biblioteca matemática de vectores cortos (SVML). Estas funciones calculan los equivalentes de vectores de 128 bits, 256 bits o 512 bits. Se han agregado para admitir la vectorización manual de bucles con llamadas a funciones de la biblioteca matemática y otras operaciones como la división de enteros. Vea la [Guía de funciones intrínsecas de Intel](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) para las definiciones de las funciones admitidas.

- Optimizaciones nuevas y mejoradas:

  - Simplificaciones aritméticas y plegado constante para las expresiones que usan intrínsecos de vector SIMD, para formatos de entero y float.

  - Un análisis más eficaz para extraer información de flujo de control (instrucciones if/else/switch) para quitar ramas que siempre se han demostrado true o false.

  - Despliegue mejorado de memset para usar instrucciones de vectores de SSE2.

  - Eliminación mejorada de copias de estructuras/clases inútiles, especialmente para los programas de C++ que pasan por valor.

  - Optimización mejorada del código que usa `memmove`, como la construcción `std::copy`, `std::vector` y `std::string`.

- Se ha optimizado el diseño físico de la biblioteca estándar para evitar compilar partes de la biblioteca estándar no incluidas directamente. Este cambio reduce el tiempo de compilación de un archivo vacío que incluya solamente \<vector> en la mitad. Como consecuencia, es posible que deba agregar directivas `#include` para los encabezados que se incluyeron indirectamente. Por ejemplo, el código que usa `std::out_of_range` puede que ahora deba agregar `#include <stdexcept>`. El código que usa un operador de inserción de flujos puede que ahora necesite agregar `#include <ostream>`. La ventaja es que solo las unidades de traducción que realmente usan los componentes \<stdexcept> o \<ostream> pagan el costo de rendimiento por compilarlos.

- `if constexpr` se aplicó en más lugares de la biblioteca estándar para mejorar el rendimiento y el tamaño del código reducido en las operaciones de copia, en permutaciones como invertir y girar y en la biblioteca de algoritmos paralelos.

- La biblioteca estándar ahora usa `if constexpr` internamente para reducir los tiempos de compilación, incluso en el modo C++14.

- La detección de vínculos dinámicos en tiempo de ejecución para la biblioteca de algoritmos paralelos ya no usa una página completa para almacenar la matriz de puntero de función. Marcar esta memoria como de solo lectura ya no se consideraba pertinente por motivos de seguridad.

- El constructor de `std::thread` ya no espera a que el subproceso se inicie y ya no inserta tantas capas de llamadas a función entre la biblioteca de C subyacente `_beginthreadex` y el objeto invocable proporcionado. Anteriormente `std::thread` coloca seis funciones entre `_beginthreadex` y el objeto al que se puede llamar. Esta cantidad se ha reducido a solo tres, dos de los cuales son simplemente `std::invoke`. Este cambio también resuelve un error de tiempo desconocido donde un constructor `std::thread` dejaría de responder si el reloj del sistema cambiara en el momento exacto en que se crea el elemento `std::thread`.

- Se ha corregido una regresión del rendimiento en `std::hash` que hemos introducido al implementar `std::hash<std::filesystem::path>`.

- En varios lugares, la biblioteca estándar ahora usa destructores en lugar de bloques catch para conseguir exactitud. Este cambio produce una mejor interacción del depurador: Las excepciones lanzadas mediante la biblioteca estándar en las ubicaciones afectadas ahora se muestran como procedentes del sitio de lanzamiento original, en lugar del sitio de reinicio. No se eliminaron todos los bloques catch de la biblioteca estándar. Esperamos que se reduzca el número de bloques catch en versiones posteriores de MSVC.

- La generación de código subóptima de `std::bitset` producida por un lanzamiento condicional dentro de una función noexcept se ha corregido mediante la deducción de la ruta de acceso de lanzamiento.

- La familia `std::list` y `std::unordered_*` usan iteradores no depuradores internamente en más lugares.

- Se han modificado varios miembros de `std::list` para reutilizar los nodos de lista cuando sea posible, en lugar de desasignarlos y reasignarlos. Por ejemplo, dado `list<int>` que ya tiene un tamaño de 3, una llamada a `assign(4, 1729)` ahora sobrescribe los valores de tipo int en los 3 primeros nodos de la lista y asigna un nuevo nodo de lista con el valor 1729.

- Todas las llamadas de la biblioteca estándar a `erase(begin(), end())` se cambiaron a `clear()`.

- `std::vector` ahora inicializa y borra los elementos con mayor eficacia en determinados casos.

- Mejoras en `std::variant` para que sea más adecuado para optimizadores, lo que conlleva un código mejor generado. La inserción de código ha mejorado mucho con `std::visit`.

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Compatibilidad de Live Share con C++

[Live Share](/visualstudio/liveshare/) ahora es compatible con C++, lo que permite a los desarrolladores que usan Visual Studio o Visual Studio Code colaborar en tiempo real. Para obtener más información, vea [Announcing Live Share for C++: Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/) (Presentación de Live Share para C++: colaboración y uso compartido en tiempo real).

### <a name="intellicode-for-c"></a>IntelliCode para C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019, versión 16.1

IntelliCode usa un amplio aprendizaje y su contexto de código para colocar lo que es más probable que use en la parte superior de la lista de finalización. A menudo puede eliminar la necesidad de desplazarse hacia abajo por la lista. Para C++, IntelliCode ofrece más ayuda al usar bibliotecas conocidas, como la biblioteca estándar. IntelliCode es una extensión opcional disponible como componente de carga de trabajo en el instalador. Para obtener más información, vea [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/) (Las sugerencias de finalización de código asistidas por inteligencia artificial se hacen realidad en C++ a través de IntelliCode).

### <a name="template-intellisense"></a>IntelliSense para plantilla

Ahora, la **barra de plantillas** usa la interfaz de usuario de **ventana de inspección** en lugar de una ventana modal, admite plantillas anidadas y rellena previamente los argumentos predeterminados en la **ventana de inspección**. Para obtener más información, vea [Template IntelliSense Improvements for Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/) (Mejoras de IntelliSense para plantilla para Visual Studio 2019, versión preliminar 2). La lista desplegable **Usados más recientemente** de la **barra de plantillas** permite cambiar rápidamente entre conjuntos anteriores de argumentos de ejemplo.

### <a name="new-start-window-experience"></a>Nueva experiencia de la ventana de inicio

Al iniciar el IDE, aparece una nueva ventana de inicio con opciones para abrir proyectos recientes, clonar código del control de código fuente, abrir código local como una solución o carpeta, o crear un proyecto. También se ha mejorado el cuadro de diálogo Nuevo proyecto con una experiencia inicial para búsqueda filtrable.

### <a name="new-names-for-some-project-templates"></a>Nuevos nombres para algunas plantillas de proyecto

Hemos modificado varios nombres y descripciones de plantilla de proyecto para que quepan en el cuadro de diálogo actualizado Nuevo proyecto.

### <a name="various-productivity-improvements"></a>Diversas mejoras de productividad

Visual Studio 2019 incluye las siguientes características que ayudarán a que el proceso de codificar sea más sencillo e intuitivo:

- Revisiones rápidas para:
  - Agregar las directivas #include que faltan
  - NULL para nullptr
  - Agregar punto y coma faltante
  - Resolver los espacios de nombres o ámbitos que faltan
  - Reemplazar los operandos de direccionamiento indirecto incorrectos (\* a & y & a \*)
- Información rápida para un bloque al mover el puntero sobre la llave de cierre
- Inspección del archivo de encabezado o código
- Ir a definición en #include abre el archivo

Para obtener más información, vea [C++ Productivity Improvements in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/) (Mejoras de productividad en Visual Studio 2019, versión preliminar 2).

### <a name="quickinfo-improvements"></a>Mejoras de Información rápida

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019, versión 16.1

La Información rápida ahora respeta los colores semánticos del editor. Tiene un nuevo vínculo **Buscar en línea** que buscará documentos en línea para obtener más información sobre la construcción de código activado. Si se trata de código subrayado en rojo, el vínculo proporcionado por Información rápida buscará el error en línea. De esta forma, no es necesario que vuelva a escribir el mensaje en el explorador. Para más información, vea [Quick Info Improvements in Visual Studio 2019: Colorization and Search Online](https://devblogs.microsoft.com/cppblog/quick-info-improvements-in-visual-studio-2019-colorization-and-search-online/) (Mejoras de Información rápida en Visual Studio 2019: colores y búsqueda en línea).

### <a name="intellicode-available-in-c-workload"></a>IntelliCode disponible en la carga de trabajo de C++

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019, versión 16.1

IntelliCode ahora se distribuye como un componente opcional en la carga de trabajo **Desarrollo para el escritorio con C++** . Para más información, vea [Improved C++ IntelliCode now Ships with Visual Studio 2019](https://devblogs.microsoft.com/cppblog/improved-c-intellicode-now-ships-with-visual-studio-2019/) (IntelliCode mejorado para C++ ahora se distribuye con Visual Studio 2019).

## <a name="cmake-support"></a>Compatibilidad con CMake

- Compatibilidad con CMake 3.14

- Visual Studio ahora puede abrir las memorias caché de CMake existentes generadas por herramientas externas, como CMakeGUI, por sistemas de compilación de metadatos personalizados o por scripts de compilación que invocan cmake.exe.

- Rendimiento de IntelliSense mejorado.

- Se ha introducido un nuevo editor de configuración que supone una alternativa a la edición manual del archivo CMakeSettings.json y comparte ciertas similitudes con CMakeGUI.

- Visual Studio impulsa el desarrollo en C++ mediante CMake en Linux, ya que detecta si tiene una versión compatible de CMake en su equipo Linux. Si no la tiene, ofrece la posibilidad de instalarla automáticamente.

- Las opciones de configuración que son incompatibles en CMakeSettings, como las arquitecturas no coincidentes o la configuración incompatible del generador de CMake, aparecen con subrayado ondulado en el editor de JSON y con errores en la lista de errores.

- La cadena de herramientas de vcpkg se detecta automáticamente y se habilita para los proyectos de CMake que se abren en el IDE una vez que `vcpkg integrate install` se ha ejecutado. Se puede desactivar este comportamiento si se especifica un archivo de cadena de herramientas vacío en CMakeSettings.

- Los proyectos de CMake ahora habilitan la depuración de Solo mi código de forma predeterminada.

- Las advertencias de análisis estático ahora se pueden procesar en segundo plano y mostrarse en el editor de proyectos de CMake.

- Mensajes más claros de inicio y final de la compilación y la configuración para los proyectos de CMake y compatibilidad con la interfaz de usuario de progreso de compilación de Visual Studio. Además, ahora hay una opción de configuración del nivel de detalle de CMake en **Herramientas > Opciones** para personalizar el nivel de detalle de los mensajes de compilación y configuración de CMake en la ventana de salida.

- Ahora se admite la opción `cmakeToolchain` en CMakeSettings.json para especificar cadenas de herramientas sin tener que modificar manualmente la línea de comandos de CMake.

- Nuevo acceso directo del menú para **Compilar todo**: **CTRL+Mayús+B**.

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019, versión 16.1

- Compatibilidad integrada para editar, compilar y depurar proyectos de CMake con Clang/LLVM. Para más información, vea [Clang/LLVM Support in Visual Studio](https://devblogs.microsoft.com/cppblog/clang-llvm-support-in-visual-studio/) (Compatibilidad con Clang/LLVM en Visual Studio).

## <a name="linux-and-the-windows-subsystem-for-linux"></a>Linux y el subsistema de Windows para Linux

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019, versión 16.1

- Compatibilidad con [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) en proyectos multiplataforma de Linux y CMake. Para más información, vea [AddressSanitizer (ASan) for the Linux Workload in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/addresssanitizer-asan-for-the-linux-workload-in-visual-studio-2019/) [AddressSanitizer (ASan) para la carga de trabajo de Linux en Visual Studio 2019].

- Compatibilidad integrada con Visual Studio para usar C++ con el subsistema de Windows para Linux (WSL). Para más información, vea [C++ with Visual Studio 2019 and Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/) [C++ con Visual Studio 2019 y el subsistema de Windows para Linux (WSL)].

## <a name="incredibuild-integration"></a>Integración de IncrediBuild

IncrediBuild se incluye como un componente opcional en la carga de trabajo **Desarrollo para el escritorio con C++** . El monitor de compilaciones de IncrediBuild está totalmente integrado en el IDE de Visual Studio. Para obtener más información, consulte [Visualización de la compilación con el monitor de compilaciones de IncrediBuild y Visual Studio 2019](https://devblogs.microsoft.com/cppblog/visualize-your-build-with-incredibuilds-build-monitor-and-visual-studio-2019/).

## <a name="debugging"></a>Depuración

- Para aplicaciones de C++ que se ejecutan en Windows, los archivos PDB ahora se cargan en un proceso independiente de 64 bits. Este cambio soluciona una variedad de bloqueos provocados por memoria insuficiente del depurador. Por ejemplo, al depurar aplicaciones que contienen un gran número de módulos y archivos PDB.

- La búsqueda está habilitada en las ventanas **Watch**, **Autos** y **Locals**.

## <a name="windows-desktop-development-with-c"></a>Desarrollo del escritorio de Windows con C++

- Los siguientes asistentes de ATL/MFC de C++ ya no están disponibles:

  - Asistente para componentes ATL COM+ 1.0
  - Asistente para componentes de páginas Active Server ATL
  - Asistente para proveedores OLE DB ATL
  - Asistente para páginas de propiedades ATL
  - Asistente para consumidores OLE DB ATL
  - Consumidor ODBC MFC
  - Clase MFC de un control ActiveX
  - Clase MFC de TypeLib

  El código de ejemplo para estas tecnologías se archiva en Microsoft Docs y el repositorio VCSamples de GitHub.

- El kit de desarrollo de software (SDK) de Windows 8.1 ya no está disponible en el instalador de Visual Studio. Recomendamos que actualice los proyectos de C++ al Windows 10 SDK más reciente. Si tiene una dependencia fuerte de 8.1, puede descargarlo desde el archivo de Windows SDK.

- Ya no estará disponible Windows XP como opción de destino para el conjunto de herramientas de C++ más actualizado. Se sigue admitiendo XP como destino con bibliotecas y el compilador de MSVC de nivel de VS 2017, y se puede instalar a través de "Componentes individuales".

- En nuestra documentación se desaconseja encarecidamente el uso de módulos de combinación para la implementación en tiempo de ejecución de Visual C++. En esta versión hemos dado un paso extra para marcar nuestros MSM como en desuso. Considere la posibilidad de migrar la implementación central VCRuntime de MSM al paquete redistribuible.

## <a name="mobile-development-with-c-android-and-ios"></a>Desarrollo móvil con C++ (Android y iOS)

La experiencia Android de C++ ahora toma como valor predeterminado el Android SDK 25 y el Android NDK 16b.

## <a name="clangc2-platform-toolset"></a>Conjunto de herramientas de la plataforma Clang/C2

Se ha eliminado el componente experimental Clang/C2. Use el conjunto de herramientas MSVC para un cumplimiento total de los estándares de C++ con `/permissive-` y `/std:c++17`, o bien la cadena de herramientas Clang/LLVM para Windows.

## <a name="code-analysis"></a>Análisis de código

- El análisis de código ahora se ejecuta automáticamente en segundo plano. Las advertencias se muestran como líneas verdes onduladas dentro del editor a medida que escribe. Para obtener más información, vea [In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/) (Análisis de código en el editor en Visual Studio 2019, versión preliminar 2).

- Nuevas reglas experimentales de ConcurrencyCheck para tipos conocidos de biblioteca estándar del encabezado \<mutex>. Para obtener más información, vea [Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/) (Análisis de código de simultaneidad en Visual Studio 2019).

- Implementación parcial actualizada del [Comprobador de perfil de duración](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), que detecta punteros y referencias pendientes. Para obtener más información, vea [Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/) (Actualización de perfiles de duración en Visual Studio 2019, versión preliminar 2).

- Más comprobaciones relacionadas con la corrutina, entre las que se incluyen C26138, C26810, C26811 y la regla experimental C26800. Para obtener más información, vea [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/) (Nuevas comprobaciones de análisis de código en Visual Studio 2019: uso después de mover y corrutina).

##### <a name="visual-studio-2019-version-161"></a>Visual Studio 2019, versión 16.1

- Nuevas correcciones rápidas de las comprobaciones de variables con la inicialización anulada. Para más información, vea [New code analysis quick fixes for uninitialized memory (C6001) and use before init (C26494) warnings](https://devblogs.microsoft.com/cppblog/new-code-analysis-quick-fixes-for-uninitialized-memory-c6001-and-use-before-init-c26494-warnings/) [Nuevas correcciones rápidas de análisis de código para memoria con inicialización anulada (C6001) y advertencias use before init (C26494)].

## <a name="unit-testing"></a>Pruebas unitarias

La plantilla de proyecto de prueba de C++ administrado ya no está disponible. Puede seguir usando el marco de pruebas de C++ administrado en los proyectos existentes. Para las pruebas unitarias nuevas, considere la opción de usar uno de los marcos de prueba nativos para los que Visual Studio proporciona plantillas (MSTest, Google Test) o la plantilla de proyecto de prueba de C# administrado.

::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 2017 incluye muchas actualizaciones y revisiones del entorno de C++. Hemos corregido más de 250 errores y se han comunicado problemas en el compilador y las herramientas. Muchos de estos problemas fueron enviados por los clientes mediante las opciones [Notificar un problema y Aportar una sugerencia](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2017) en **Enviar comentarios**. ¡Muchas gracias por notificárnoslos! Para más información sobre todas las novedades de Visual Studio, visite [Novedades de Visual Studio 2017](/visualstudio/ide/whats-new-visual-studio-2017?view=vs-2017). Para información sobre las novedades de C++ en Visual Studio 2019, consulte [Novedades de C++ en Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019). Para información sobre las novedades de C++ en Visual Studio 2015 y versiones anteriores, consulte [Novedades de Visual C++ de 2003 a 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="visual-studio-2017-c-compiler"></a>Compilador de C++ de Visual Studio 2017

### <a name="c-conformance-improvements"></a>Mejoras de conformidad de C++

En esta versión hemos actualizado el compilador de C++ y la biblioteca estándar mejorando la compatibilidad con las características de C++11 y C++14. También incluyen compatibilidad preliminar con ciertas características que se esperaba que estuvieran contenidas en el estándar C++17. Para obtener información detallada, vea [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

El compilador admite aproximadamente un 75 % de las características nuevas de C++17, incluidos los enlaces estructurados, las expresiones lambda `constexpr`, `if constexpr`, las variables alineadas, las expresiones fold y la adición de `noexcept` al sistema de tipos. Estas características están disponibles en la opción **`/std:c++17`** . Para obtener más información, consulte [Mejoras de conformidad de C++ en Visual Studio 2017](cpp-conformance-improvements.md).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

El conjunto de herramientas del compilador MSVC en Visual Studio versión 15.7 ahora cumple con el estándar de C++. Para obtener más información, vea [Announcing: MSVC Conforms to the C++ Standard](https://devblogs.microsoft.com/cppblog/announcing-msvc-conforms-to-the-c-standard/) (Anuncio: MSVC cumple con el estándar de C++) y [Conformidad del lenguaje Microsoft C++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-158"></a>Visual Studio 2017, versión 15.8

El modificador del compilador [`/experimental:preprocessor`](../build/reference/experimental-preprocessor.md) habilita el nuevo preprocesador MSVC experimental que finalmente será compatible con todos los estándares de C y C+ aplicables. Para obtener más información, consulte [Información general del preprocesador experimental MSVC](../preprocessor/preprocessor-experimental-overview.md).

### <a name="new-compiler-options"></a>Nuevas opciones del compilador

- [`/permissive-`](../build/reference/permissive-standards-conformance.md): habilita todas las opciones del compilador de cumplimiento de estándares estrictos y deshabilita la mayoría de las extensiones del compilador específicas de Microsoft, pero no `__declspec(dllimport)`, por ejemplo. Esta opción está activada de forma predeterminada en Visual Studio 2017 versión 15.5.  El modo de cumplimiento **`/permissive-`** incluye compatibilidad para la búsqueda de nombres en dos fases. Para obtener más información, vea [C++ Conformance Improvements in Visual Studio](cpp-conformance-improvements.md) (Mejoras de conformidad de C++ en Visual Studio).

- [`/diagnostics`](../build/reference/diagnostics-compiler-diagnostic-options.md): Permite mostrar la ubicación de la advertencia o del error de diagnóstico de tres maneras diferentes: solo el número de línea, el número de línea y columna, o el número de línea y columna con un símbolo de intercalación bajo la línea de código incorrecta.

- [`/debug:fastlink`](../build/reference/debug-generate-debug-info.md): permite tiempos de vínculo incremental hasta un 30 % más rápidos (frente a Visual Studio 2015), ya que no copia toda la información de depuración en el archivo PDB. En su lugar, el archivo PDB apunta a la información de depuración de los archivos de biblioteca y del objeto usados para crear el ejecutable. Consulte las páginas sobre el [ciclo de compilación en C++ más rápido en Visual Studio "15" con `/Debug:fastlink`](https://devblogs.microsoft.com/cppblog/faster-c-build-cycle-in-vs-15-with-debugfastlink/) y sobre las [recomendaciones para acelerar las compilaciones en C++ en Visual Studio](https://devblogs.microsoft.com/cppblog/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 permite usar [`/sdl`](../build/reference/sdl-enable-additional-security-checks.md) con [`/await`](../build/reference/await-enable-coroutine-support.md). Se ha eliminado la limitación [`/RTC`](../build/reference/rtc-run-time-error-checks.md) con corrutinas.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- [`/std:c++14` y `/std:c++latest`](../build/reference/std-specify-language-standard-version.md): estas opciones del compilador permiten participar en versiones específicas del lenguaje de programación ISO C++ en un proyecto. La mayoría de las nuevas características del borrador estándar están protegidas con la opción **`/std:c++latest`** .

- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) habilita el conjunto de características de C++17 implementadas por el compilador. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características posteriores a C++17 o que se han modificado en las versiones del borrador de trabajo y las actualizaciones de defectos de C++ Standard. Para habilitar esas características, utilice **`/std:c++latest`** .

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, seguridad, diagnóstico y control de versiones

Esta versión ofrece varias mejoras en la optimización, la generación de código, el control de versiones del conjunto de herramientas y el diagnóstico. Estas son algunas de las mejoras destacables incluidas:

- Generación de código de bucles mejorada: compatibilidad con vectorización automática de división de enteros constantes, mejor identificación de patrones de memset.
- Seguridad de código mejorada: emisión mejorada de diagnósticos de compilador de saturación del búfer; [`/guard:cf`](../build/reference/guard-enable-control-flow-guard.md) ahora protege instrucciones switch que generan tablas de saltos.
- Control de versiones: el valor de la macro de preprocesador integrada **\_MSC\_VER** se actualiza de forma continua en cada actualización del conjunto de herramientas de Visual C++. Para obtener más información, vea [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) (Versión del compilador de Visual C++).
- Nuevo diseño del conjunto de herramientas: el compilador y las herramientas de compilación relacionadas tienen una nueva ubicación y estructura de directorios en la máquina de desarrollo. El nuevo diseño permite instalaciones en paralelo de varias versiones del compilador. Para más información, consulte [Compiler Tools Layout in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/compiler-tools-layout-in-visual-studio-15/) (Diseño de las herramientas del compilador en Visual Studio 2017).
- Diagnóstico mejorado: en la ventana de salida ahora se muestra la columna en la que se produce un error. Para más información, vea [C++ improvisamente diagnostics improvements in VS "15" Preview 5](https://devblogs.microsoft.com/cppblog/c-compiler-diagnostics-improvements-in-vs-15-rc/) (Mejoras del diagnóstico del compilador C++ en VS "15" Preview 5).
- Se ha eliminado la palabra clave experimental **yield**, disponible en la opción **`/await`** , al usar las corrutinas. En su lugar, se debe actualizar el código para que use `co_yield`. Para más información, consulte el artículo sobre cómo la palabra clave [`yield` se convierte en `co_yield` en VS 2017](https://devblogs.microsoft.com/cppblog/yield-keyword-to-become-co_yield-in-vs-2017/).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

Se han implementado mejoras adicionales en los diagnósticos del compilador. Para más información, consulte el artículo sobre las [mejoras de diagnósticos en Visual Studio 2017 15.3.0](https://devblogs.microsoft.com/cppblog/diagnostic-improvements-in-vs2017-15-3-0/).

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

El rendimiento del entorno de ejecución Visual C++ sigue mejorando debido a que la calidad del código generado es mayor. Ahora puede volver a compilar simplemente el código, y la aplicación se ejecutará más rápido. Algunas de las optimizaciones del compilador son totalmente nuevas, como la vectorización de almacenes escalares condicionales, la combinación de llamadas `sin(x)` y `cos(x)` en una nueva llamada `sincos(x)`, y la eliminación de instrucciones redundantes del optimizador SSA. Otras optimizaciones del compilador son mejoras de funcionalidades existentes, como las heurísticas del vectorizador para expresiones condicionales, las optimizaciones de bucle mejoradas y la generación de código mín./máx. flotante. Ahora, el enlazador tiene una nueva implementación **`/OPT:ICF`** más rápida, con la que podrá agilizar el tiempo de vínculo hasta un 9 %. Asimismo, los vínculos incrementales también presentan otras mejoras de rendimiento. Para obtener más información, vea [/OPT (Optimizations)](../build/reference/opt-optimizations.md) (/OPT (optimizaciones)) e [/INCREMENTAL (Link Incrementally)](../build/reference/incremental-link-incrementally.md) (/INCREMENTAL (vincular de forma incremental)).

El compilador de Microsoft C++ es compatible con las instrucciones AVX-512 de Intel, así como con las instrucciones de longitud del vector que incorporan nuevas funciones de AVX-512 en registros con una amplitud de 128 y 256 bits.

La opción [/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) se puede usar para volver a la versión C++14 de `noexcept` al usar el modo C++17 de forma general. Esta opción le permite actualizar el código fuente para que guarde conformidad con C++17 sin tener que reescribir todo el código de `throw()` a la vez. Para obtener más información, vea [Eliminación de las especificaciones de excepción dinámica y noexcept](cpp-conformance-improvements.md#noexcept_removal).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

- Nuevo modificador de compilador [/Qspectre ](../build/reference/qspectre.md) para ayudar a mitigar el riesgo de ataques de canal lateral de ejecución especulativa. Para más información, consulte [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/) (Mitigaciones de Spectre en MSVC).
- Nueva advertencia de diagnóstico para la mitigación de Spectre. Para más información, consulte [Spectre diagnostic in Visual Studio 2017 Version 15.7 Preview 4](https://devblogs.microsoft.com/cppblog/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/) (Diagnóstico de Spectre en Visual Studio 2017 versión 15.7 [versión preliminar 4]).
- Un nuevo valor para /Zc, **`/Zc:__cplusplus`** , permite la generación de informes correctos de la compatibilidad del estándar de C++. Por ejemplo, cuando el modificador está establecido y el compilador está en modo **`/std:c++17`** , el valor se expande a **`201703L`** . Para más información, consulte [MSVC now correctly reports __cplusplus](https://devblogs.microsoft.com/cppblog/msvc-now-correctly-reports-__cplusplus/) (Ahora MSVC notifica __cplusplus correctamente).

## <a name="c-standard-library"></a>Biblioteca estándar de C++

### <a name="correctness-improvements"></a>Mejoras en la corrección

##### <a name="visual-studio-2017-rtm-version-150"></a>Visual Studio 2017 RTM (versión 15.0)

- Se han realizado mejoras secundaras en los diagnósticos (`basic_string``_ITERATOR_DEBUG_LEVEL != 0`). Al activar una comprobación de IDL en la maquinaria de cadenas, se indicará la conducta específica que provocó la activación. Por ejemplo, en lugar de recibir el mensaje "string iterator not dereferenceable" (El iterador de cadena no es desreferenciable), verá el mensaje "cannot dereference string iterator because it is out of range (e.g. an end iterator)" (No se puede desreferenciar el iterador de cadena porque está fuera del rango (por ejemplo, un iterador final).
- Se ha corregido el operador de asignación de movimiento `std::promise`, que anteriormente podía provocar que el código se bloqueara permanentemente.
- Se han corregido errores del compilador con la conversión implícita de `atomic<T*>` a `T*`.
- `pointer_traits<Ptr>` ahora detecta `Ptr::rebind<U>` correctamente.
- Se ha corregido la falta de un calificador `const` en el operador de resta `move_iterator`.
- Se ha corregido un elemento codegen silencioso incorrecto para asignadores con estado definido por el usuario al solicitar `propagate_on_container_copy_assignment` y `propagate_on_container_move_assignment`.
- `atomic<T>` ahora tolera la sobrecarga de `operator&()`.
- Se ha mejorado ligeramente el diagnóstico del compilador para llamadas `bind()`incorrectas.

Hay más mejoras de la biblioteca estándar en Visual Studio 2017 RTM. Para ver una lista completa, consulte la entrada sobre las [correcciones de la biblioteca estándar en Visual Studio 2017 RTM](https://devblogs.microsoft.com/cppblog/stl-fixes-in-vs-2017-rtm/) del blog del equipo de C++.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- Los contenedores de la biblioteca estándar ahora fijan su valor de `max_size()` en `numeric_limits<difference_type>::max()`, en lugar de `max()` en `size_type`. Este cambio garantiza que el resultado de `distance()` en los iteradores de dicho contenedor se pueda representar en el tipo de valor devuelto de `distance()`.
- Se ha corregido la falta de la especialización `auto_ptr<void>`.
- Los algoritmos `for_each_n()`, `generate_n()` y `search_n()` antes no se compilaban si el argumento de longitud no era un tipo entero. Ahora permiten convertir las longitudes no integrales al valor `difference_type` de los iteradores.
- `normal_distribution<float>` ya no emite advertencias dentro de la biblioteca estándar con respecto a la restricción de "double" a "float".
- Se han corregido algunas operaciones `basic_string` que usan `npos` en lugar de `max_size()` durante la comprobación del desbordamiento de tamaño máximo.
- `condition_variable::wait_for(lock, relative_time, predicate)` permitiría esperar durante todo el período de tiempo relativo en el caso de una reactivación falsa. Ahora solo espera un intervalo único del tiempo relativo.
- `future::get()` ahora permite invalidar `future`, tal como requiere el estándar.
- `iterator_traits<void *>` solía ser un error porque intentaba formar `void&`. Ahora se convierte limpiamente en una estructura vacía para permitir el uso de `iterator_traits` en condiciones SFINAE "is iterator".
- Se han corregido algunas advertencias que **-Wsystem-headers** ha notificado.
- También se ha corregido el mensaje "la especificación de la excepción en la declaración no coincide con la declaración anterior" que Clang **-Wmicrosoft-exception-spec** ha notificado.
- También se corrigió mem-initializer-list que ordena las advertencias informadas por Clang y C1XX.
- Los contenedores sin ordenar no intercambiaban sus funciones hash o predicados cuando se intercambiaban los propios contenedores. Ahora sí lo hacen.
- Muchas operaciones de intercambio de contenedores ahora están marcadas como `noexcept`, puesto que la biblioteca estándar nunca tiene la intención de generar una excepción al detectar una condición de comportamiento sin definir que no coincida con el asignador y que no sea del tipo `propagate_on_container_swap`.
- Muchas operaciones `vector<bool>` ahora aparecen marcadas como `noexcept`.
- La biblioteca estándar ahora aplica la coincidencia entre el asignador `value_type` (en modo C++17) con un sombreado de escape de rechazo.
- Se han corregido algunas condiciones en las que self-range-insert en `basic_string` resolvía el contenido de las cadenas. (Nota: la biblioteca estándar sigue prohibiendo self-range-insert en vectores).
- `basic_string::shrink_to_fit()` ya no se ve afectado por el valor `propagate_on_container_swap` del asignador.
- `std::decay` ahora controla los tipos de funciones abominables, es decir, los tipos de función cv-qualified, ref-qualified o ambos.
- Los cambios incluyen directivas para usar la distinción entre mayúsculas y minúsculas y barras diagonales para mejorar la portabilidad.
- Se ha corregido la advertencia C4061: el enumerador "*enumerator*" en la instrucción switch de la enumeración "*enumeration*" no está controlado de forma explícita por una etiqueta de caso. Esta advertencia está desactivada de manera predeterminada y se corrigió como una excepción de la directiva general de advertencias de la biblioteca estándar. La biblioteca estándar no tiene **`/W4`** , pero no tiene la intención de no tener **`/Wall`** . Muchas advertencias desactivadas de manera predeterminada son muy ruidosas y no están diseñadas para usarlas de manera regular.
- Se han mejorado las comprobaciones de depuración `std::list`. Los iteradores de lista ahora comprueban `operator->()`, y `list::unique()` ahora marca los iteradores como invalidados.
- Se ha corregido la metaprogramación uses-allocator en `tuple`.

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

- `std::partition` ahora llama al predicado `N` veces, en lugar de `N + 1`, tal y como requiere el estándar.
- Los intentos de evitar estáticas mágicas en la versión 15.3 se han reparado en la 15.5.
- `std::atomic<T>` ya no requiere que `T` sea construible de forma predeterminada.
- Cuando se habilita la depuración del iterador, los algoritmos de montón que necesiten un valor de tiempo logarítmico ya no realizan una aserción de tiempo lineal en la que la entrada es un montón.
- `__declspec(allocator)` ahora solo está protegido por C1XX para evitar advertencias de Clang que este elemento desclspec no entiende.
- `basic_string::npos` ahora está disponible como una constante de tiempo de compilación.
- `std::allocator` en C++17 ahora manipula adecuadamente la asignación de tipos sobrealineados, que son aquellos cuya alineación es superior a `max_align_t`, a menos que **`/Zc:alignedNew-`** lo deshabilite.  Por ejemplo, los vectores de objetos con una alineación de 16 o 32 bytes ahora se alinearán correctamente con instrucciones SSE y AVX.

### <a name="conformance-improvements"></a>Mejoras de conformidad

- Se ha agregado \<any\>, \<string_view\>, `apply()` y `make_from_tuple()`.
- Se ha agregado \<optional\>, \<variant\>, `shared_ptr::weak_type` y \<cstdalign\>.
- Se ha habilitado `constexpr` de C++14 en `min(initializer_list)`, `max(initializer_list)`, `minmax(initializer_list)`, `min_element()`, `max_element()` y `minmax_element()`.

Para más información, consulte [Tabla de conformidad del lenguaje Microsoft C++](../visual-cpp-language-conformance.md).

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- Se implementaron varias características adicionales de C++17. Para más información, consulte [Tabla de conformidad del lenguaje Microsoft C++](cpp-conformance-improvements.md#improvements_153).
- Se implementó P0602R0 "variante y opcional deben propagar la trivialidad de copia/movimiento".
- La biblioteca estándar ahora tolera de manera oficial que RTTI dinámico se deshabilite mediante la opción [/GR-](../build/reference/gr-enable-run-time-type-information.md). `dynamic_pointer_cast()` y `rethrow_if_nested()` requieren `dynamic_cast` de forma inherente, de modo que la biblioteca estándar ahora los marca como `=delete` en **`/GR-`** .
- Incluso si RTTI dinámico se ha deshabilitado mediante **`/GR-`** , "RTTI estático" (con el formato de `typeid(SomeType)`) sigue estando disponible y permite potenciar varios componentes de la biblioteca estándar. La biblioteca estándar ahora también admite la deshabilitación de esta característica mediante **`/D_HAS_STATIC_RTTI=0`** . Esta marca también deshabilita `std::any`, las funciones miembros `target()` y `target_type()` de `std::function` y la función de miembro friend `get_deleter()` de `std::shared_ptr` y `std::weak_ptr`.
- La biblioteca estándar ahora usa `constexpr` de C++14 sin condiciones, en lugar de macros definidas condicionalmente.
- La biblioteca estándar ahora usa plantillas de alias de forma interna.
- La biblioteca estándar ahora usa `nullptr` internamente, en lugar de `nullptr_t{}`. (Se eliminó el uso interno de NULL. El uso interno de 0-as-null se está limpiando de forma gradual).
- La biblioteca estándar ahora usa `std::move()` internamente, en lugar de hacer un mal uso de `std::forward()` de forma estilística.
- Se ha cambiado `static_assert(false, "message")` a `#error message`. Este cambio mejora los diagnósticos del compilador, porque `#error` detiene inmediatamente la compilación.
- La biblioteca estándar ya no marca las funciones como `__declspec(dllimport)`. La tecnología de enlazador moderna ya no lo requiere.
- Se extrajo SFINAE a argumentos de plantilla predeterminados, lo que reduce el desorden en comparación con los tipos de valor devuelto y los tipos de argumento de función.
- Las comprobaciones de depuración en \<random\> ahora usan la maquinaria habitual de la biblioteca estándar, en lugar de la función interna `_Rng_abort()` que llamaba `fputs()` a **stderr**. La implementación de esta función se ha mantenido para ofrecer compatibilidad binaria. La quitaremos en la siguiente versión sin compatibilidad binaria de la biblioteca estándar.

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

- Se han agregado, puesto en desuso o eliminado varias características de la biblioteca estándar según la versión estándar de C++17. Para más información, consulte [C++ conformance improvements in Visual Studio](cpp-conformance-improvements.md#improvements_155) (Mejoras de conformidad de C++ en Visual Studio).
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

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, versión 15.6

- \<memory_resource>
- Conceptos básicos de biblioteca V1
- Eliminación de la asignación `polymorphic_allocator`
- Mejora de la deducción de argumentos de plantilla de clase

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

- La compatibilidad con algoritmos paralelos ya no es experimental
- Una implementación nueva de \<filesystem>
- Conversiones de cadena elementales (parcial)
- `std::launder()`
- `std::byte`
- `hypot(x,y,z)`
- Evitación de la decadencia innecesaria
- Funciones matemáticas especiales
- `constexpr char_traits`
- Guías de deducción para la biblioteca estándar

Para más información, consulte [Tabla de conformidad del lenguaje Microsoft C++](../visual-cpp-language-conformance.md).

### <a name="performance-and-throughput-fixes"></a>Correcciones de rendimiento

- Las sobrecargas de `basic_string::find(char)` realizadas solo llaman a `traits::find` una vez. Anteriormente, esto se implementaba como una búsqueda general de una cadena de longitud 1.
- `basic_string::operator==` ahora comprueba el tamaño de la cadena antes de comparar su contenido.
- Se ha quitado el acoplamiento de control de `basic_string`, ya que era difícil de analizar para el optimizador de compilador. Para todas las cadenas cortas, las llamadas a `reserve` siguen teniendo un costo distinto de cero para no hacer nada.
- `std::vector` se ha mejorado para aumentar la precisión y el rendimiento: los alias durante las operaciones de inserción y emplazamiento ahora se controlan correctamente según lo requerido por el estándar, y la garantía de excepción sólida ahora se proporciona cuando el estándar lo solicita mediante `move_if_noexcept()` y otra lógica. Además, la inserción y el emplazamiento realizan menos operaciones de elementos.
- Ahora, la biblioteca estándar de C++ evita desreferenciar los punteros elaborados nulos.
- Se ha mejorado el rendimiento de `weak_ptr::lock()`.
- Para aumentar el rendimiento del compilador, los encabezados de la biblioteca estándar de C++ ahora evitan incluir declaraciones de intrínsecos del compilador innecesarios.
- Se ha triplicado la eficacia del rendimiento de los constructores de movimiento `std::string` y `std::wstring`.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- Se ha encontrado una solución alternativa para las interacciones con `noexcept` que impedían insertar la implementación de `std::atomic` en funciones que usan Control de excepciones estructurado (SEH).
- Se ha cambiado la función interna `_Deallocate()` de la biblioteca estándar para optimizarla en un código más pequeño, lo que permite insertarla en más lugares.
- Se ha cambiado `std::try_lock()` para usar la expansión del paquete en lugar de la recursividad.
- Se ha mejorado el algoritmo de prevención de interbloqueo `std::lock()` para usar operaciones `lock()` en lugar de dar giros en `try_lock()` en todos los bloqueos.
- Se ha habilitado la optimización del valor devuelto con nombre en `system_category::message()`.
- `conjunction` y `disjunction` ahora crean instancias de tipos `N + 1`, en lugar de tipos `2N + 2`.
- `std::function` ya no crea instancias de maquinaria de compatibilidad con el asignador para cada elemento invocable con tipo borrado, lo que mejora el rendimiento y disminuye el tamaño de .obj en programas que pasan muchas expresiones lambda distintas a `std::function`.
- `allocator_traits<std::allocator>` contiene las operaciones `std::allocator` insertadas manualmente, lo que permite reducir el tamaño del código que interactúa con `std::allocator` mediante `allocator_traits`, es decir, la mayoría del código.
- La biblioteca estándar ahora controla la interfaz de asignador mínimo de C++11 con una llamada directa a `allocator_traits`, en lugar de encapsular el asignador en una clase interna `_Wrap_alloc`. Este cambio disminuye el tamaño del código que se genera para la compatibilidad del asignador y mejora la experiencia de depuración y la capacidad del optimizador para razonar sobre los contenedores de la biblioteca estándar en ciertos casos, ya que en el depurador ahora puede ver el tipo de asignador, en lugar de `_Wrap_alloc<your_allocator_type>`.
- Se ha eliminado la metaprogramación para el elemento personalizado `allocator::reference`, un elemento que los asignadores no tienen permitido personalizar. (Los asignadores pueden hacer que los contenedores usen punteros sofisticados pero no referencias sofisticadas).
- El front-end del compilador se diseñó para desencapsular los iteradores de depuración en bucles "range-based for", lo que mejora el rendimiento de las compilaciones de depuración.
- La ruta de reducción interna `basic_string` para `shrink_to_fit()` y `reserve()` ya no está en la ruta de la reasignación de operaciones, lo que reduce el tamaño del código para todos los miembros de mutación.
- La ruta de crecimiento interna `basic_string` ya no está en la ruta de `shrink_to_fit()`.
- Las operaciones de mutación `basic_string` ahora se factorizan en funciones de ruta lenta de asignación y en funciones de ruta rápida de no asignación, lo que hace más probable que el caso no de reasignación se inserte en los llamadores.
- Las operaciones de mutación `basic_string` ahora construyen búferes reasignados con el estado preferido, en lugar de cambiar el tamaño en el mismo lugar. Por ejemplo, la inserción en el comienzo de una cadena ahora mueve el contenido después de la inserción exactamente una vez (ya sea hacia abajo o al búfer recién asignado) en lugar de dos veces en el caso de reasignación (al búfer recién asignado y luego abajo).
- Las operaciones que llaman a la biblioteca estándar C en \<string\> ahora almacenan en caché la dirección `errno` para quitar la interacción repetida con TLS.
- Se ha simplificado la implementación de `is_pointer`.
- Se ha completado el cambio de la expresión basada en funciones SFINAE para que, en su lugar, se base en `struct` y `void_t`.
- Los algoritmos de la biblioteca estándar ahora evitan el postincremento de los iteradores.
- Se corrigieron las advertencias de truncamiento cuando se usan asignadores de 32 bits en sistemas de 64 bits.
- La asignación de movimiento `std::vector` ahora es más eficaz en el caso de los asignadores que no coincidan y que no sean POCMA, ya que permite volver a usar el búfer cuando es posible.

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

- `basic_string<char16_t>` ahora interactúa en las mismas optimizaciones de `memcmp`, `memcpy` y similares que `basic_string<wchar_t>`.
- Una limitación del optimizador que impedía que los punteros de funciones se expusiesen insertados con el trabajo "evitar la copia de funciones" en Visual Studio 2015 Update 3, se ha corregido temporalmente mediante la restauración del rendimiento de `lower_bound(iter, iter, function pointer)`.
- La sobrecarga de la verificación del orden de depuración del iterador de entradas en `includes`, `set_difference`, `set_symmetric_difference` y `set_union` se ha reducido mediante el desempaquetado de iteradores antes de comprobar el orden.
- `std::inplace_merge` ahora omite elementos que ya están en posición.
- La construcción de `std::random_device` ya no construye y destruye `std::string`.
- `std::partition` y `std::equal` incluían un pase de optimización de procesamiento por saltos que ahorra una comparación del iterador.
- Ahora, cuando se pasan punteros a `std::reverse` para elementos `T` copiables de forma trivial, este realizará distribuciones a una implementación vectorizada escrita a mano.
- `std::fill`, `std::equal` y `std::lexicographical_compare` ahora permiten la distribución a `memset` y `memcmp` para `std::byte` y `gsl::byte`, así como en el caso de otras enumeraciones del tipo char y clases enum. Puesto que `std::copy` se envía mediante `is_trivially_copyable`, no necesita ningún cambio.
- La biblioteca estándar ya no contiene destructores de paréntesis vacíos, cuyo único comportamiento era hacer que los tipos no fueran destruibles de forma trivial.

## <a name="other-libraries"></a>Otras bibliotecas

### <a name="open-source-library-support"></a>Compatibilidad con bibliotecas de código abierto

**Vcpkg** es una herramienta de línea de comandos de código abierto que simplifica enormemente el proceso de adquirir y compilar bibliotecas estáticas de C++ de código abierto y archivos DLL en Visual Studio. Para obtener más información, vea [vcpkg: un administrador de paquetes de C++ para Windows, Linux y MacOS](../build/vcpkg.md).

### <a name="cpprest-sdk-290"></a>CppRestSDK 2.9.0

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

Se ha actualizado CppRestSDK (una API web multiplataforma para C++) a la versión 2.9.0. Para obtener más información, vea [CppRestSDK 2.9.0 is available on GitHub](https://devblogs.microsoft.com/cppblog/cpprestsdk-2-9-0-is-available-on-github/) (CppRestSDK 2.9.0 está disponible en GitHub).

### <a name="atl"></a>ATL

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

- Otro conjunto de correcciones de conformidad para la búsqueda de nombres.
- Los operadores de constructores de movimiento y de asignación de movimiento están ahora correctamente marcados como no productores de excepciones.
- Inclusión de la advertencia válida C4640 sobre la inicialización segura para subprocesos de elementos estáticos locales en atlstr.h.
- La inicialización segura para subprocesos de elementos estáticos locales se desactivó automáticamente en el conjunto de herramientas de XP al usar ATL para compilar un archivo DLL. Pero ahora no. Puede agregar **`/Zc:threadSafeInit-`** en la configuración del proyecto si no desea la inicialización segura para subprocesos.

### <a name="visual-c-runtime"></a>Runtime de Visual C++

- Nuevo encabezado "cfguard.h" para símbolos de protección de flujo de control.

## <a name="visual-studio-2017-c-ide"></a>C++ IDE de Visual Studio 2017

- El rendimiento del cambio de configuración ahora es mejor para proyectos nativos de C++ y mucho mejor para proyectos C++/CLI. Cuando se activa una configuración de solución por primera vez, ahora es más rápida y todas las activaciones posteriores de esta configuración de la solución serán casi instantáneas.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- Algunos asistentes de código y proyecto se han vuelto a escribir en el estilo del cuadro de diálogo de signatura.
- Ahora, al usar la opción **Agregar clase** se abre directamente el Asistente para agregar clases. Todos los demás elementos que estaban previamente aquí se encuentran disponibles ahora en **Agregar > Nuevo elemento**.
- Ahora los proyectos de Win32 están en la categoría **Escritorio de Windows** en el cuadro de diálogo **Nuevo proyecto**.
- Ahora las plantillas de la **consola de Windows** y de la **aplicación de escritorio** crean proyectos sin abrir un asistente. Hay un nuevo **Asistente de escritorio de Windows** en la misma categoría que muestra las mismas opciones que el asistente **Aplicación de consola Win32** anterior.

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

Ahora varias operaciones de C++ que usan el motor IntelliSense para la refactorización y la navegación de código se ejecutan mucho más rápido. Los siguientes números se basan en la solución de Chromium de Visual Studio con 3500 proyectos:

|||
|-|-|
|Característica|Mejora del rendimiento|
|Cambiar nombre|5,3x|
|Cambiar firma |4,5x|
|Buscar todas las referencias|4,7x|

Ahora C++ permite hacer clic presionando la tecla Control para **ir a la definición**, lo que hace más sencilla la navegación con el mouse a las definiciones. El Visualizador de estructuras del paquete Productivity Power Tools hora también se incluye en el producto de forma predeterminada.

## <a name="intellisense"></a>IntelliSense

- Ahora se está usando el nuevo motor de base de datos basado en SQLite de forma predeterminada. El nuevo motor acelera las operaciones de base de datos como **Ir a la definición** y **Buscar todas las referencias** y mejora considerablemente el tiempo de análisis de la solución inicial. La configuración se ha movido a **Herramientas > Opciones > Editor de texto > C/ C++ > Avanzado**. Anteriormente se encontraba en... C/ C++ > Experimental.

- Se ha mejorado el rendimiento de IntelliSense en proyectos y archivos que no usan encabezados precompilados; se creará un encabezado precompilado automático para los encabezados en el archivo actual.

- Se ha agregado el filtro de errores y la ayuda para errores de IntelliSense en la lista de errores. Ahora se puede filtrar al hacer clic en la columna de errores. Además, al hacer clic en los errores específicos o al presionar F1, se iniciará una búsqueda en línea del mensaje de error.

  ![Lista de errores](media/ErrorList1.png "Lista de errores")

  ![Lista de errores filtrados](media/ErrorList2.png "Lista de errores filtrados")

- Se agregó la capacidad de filtrar los elementos de la lista de miembros por tipo.

  ![Filtrado de la lista de miembros](media/mlfiltering.png "Filtrado de la lista de miembros")

- Se ha agregado una nueva característica de IntelliSense predictiva experimental que proporciona un filtrado de lo que aparece en la lista de miembros que tiene en cuenta el contexto. Para más información, consulte [C++ IntelliSense Improvements - Predictive IntelliSense & Filtering](https://devblogs.microsoft.com/cppblog/c-intellisense-improvements-predictive-intellisense-filtering/) (Mejoras de IntelliSense de C++: IntelliSense predictivo y filtrado).
- Ahora **Buscar todas las referencias** (Mayús+F12) permite desplazarse con facilidad, incluso en códigos base complejos. Proporciona agrupación avanzada, filtrado, ordenación, búsqueda en los resultados y (para algunos idiomas) uso de colores, para que pueda entender claramente las referencias. Para C++, la nueva interfaz de usuario incluye información sobre si se lee desde una variable o si se escribe en ella.
- La característica Punto a flecha de IntelliSense pasó de experimental a avanzada y ahora está habilitada de manera predeterminada. Las características del editor **Expandir ámbitos** y **Expandir precedencia** también han dejado de ser características experimentales y ahora son avanzadas.
- Las características experimentales de refactorización **Cambiar signatura** y **Extraer función** ahora están disponibles de manera predeterminada.
- Se ha agregado una característica experimental "Carga de proyecto más rápida" para proyectos de C++. La próxima vez que abra un proyecto de C++, se cargará más rápido y la siguiente todavía *más*.
- Algunas de estas características son comunes a otros lenguajes y otras son específicas de C++. Para más información sobre estas nuevas características, consulte [Announcing Visual Studio "15"](https://devblogs.microsoft.com/visualstudio/announcing-visual-studio-15-preview-5/) (Presentación de Visual Studio "15").

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

- se ha agregado compatibilidad para ClangFormat. Para obtener más información, vea [ClangFormat Support in Visual Studio 2017](https://devblogs.microsoft.com/cppblog/clangformat-support-in-visual-studio-2017-15-7-preview-1/) (Compatibilidad con ClangFormat en Visual Studio 2017).

## <a name="non-msbuild-projects-with-open-folder"></a>Proyectos que no son de MSBuild con Abrir carpeta

Visual Studio 2017 presenta la característica **Abrir carpeta**, que permite codificar, compilar y depurar elementos en una carpeta que contenga código fuente sin necesidad de crear soluciones o proyectos. Ahora es mucho más fácil empezar a trabajar con Visual Studio, incluso si el proyecto no es un proyecto basado en MSBuild. **Abrir carpeta** proporciona acceso a funcionalidades eficaces de reconocimiento, edición, compilación y depuración. Son las mismos que ya proporciona Visual Studio para los proyectos de MSBuild. Para más información, vea el artículo sobre los [proyectos Abrir carpeta para C++](../build/open-folder-projects-cpp.md).

- Mejoras en la experiencia de Abrir carpeta. Puede personalizar la experiencia con estos archivos .json:
  - CppProperties.json para personalizar la experiencia de IntelliSense y de exploración.
  - Tasks.json para personalizar los pasos de compilación.
  - Launch.json para personalizar la experiencia de depuración.

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- Se mejoró la compatibilidad con compiladores alternativos y entornos de compilación como MinGW y Cygwin. Para más información, consulte el artículo sobre el [uso de MinGW y Cygwin con Visual C++ y Abrir carpeta](https://devblogs.microsoft.com/cppblog/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Se ha agregado compatibilidad para definir variables de entorno globales y específicas de la configuración en CppProperties.json y CMakeSettings.json. Estas variables de entorno se pueden usar en las configuraciones de depuración definidas en launch.vs.json y en las tareas tasks.vs.json. Para obtener más información, vea [Customizing your Environment with Visual C++ and Open Folder](https://devblogs.microsoft.com/cppblog/customizing-your-environment-with-visual-c-and-open-folder/) (Personalización del entorno con Visual C++ y Abrir carpeta).
- Se mejoró la compatibilidad con el generador Ninja de CMake, incluida la capacidad de apuntar fácilmente a las plataformas de 64 bits.

## <a name="cmake-support-via-open-folder"></a>Compatibilidad con CMake mediante Abrir carpeta

Visual Studio 2017 incluye compatibilidad con el uso de proyectos CMake sin convertirlos en archivos de proyecto de MSBuild (.vcxproj). Para más información, vea el artículo sobre [proyectos de CMake en Visual Studio](../build/cmake-projects-in-visual-studio.md). Si abre proyectos CMake con **Abrir carpeta**, el entorno se configurará automáticamente para la edición, la compilación y la depuración de C++.

- IntelliSense de C++ funciona sin la necesidad de crear un archivo CppProperties.json en la carpeta raíz. También se ha agregado un nuevo menú desplegable que permite a los usuarios cambiar fácilmente entre las configuraciones que proporcionan los archivos CMake y CppProperties.json.

- Se admite una configuración adicional a través de un archivo CMakeSettings.json que reside en la misma carpeta que el archivo CMakeLists.txt.

  ![Abrir carpeta CMake](media/cmake-cpp.png "Abrir carpeta CMake")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- se ha agregado compatibilidad para el generador CMake Ninja.

##### <a name="visual-studio-2017-version-154"></a>Visual Studio 2017, versión 15.4

- se ha agregado compatibilidad para la importación de las memorias caché de CMake existentes.

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

- se ha agregado compatibilidad para CMake 3.11, el análisis de código en proyectos de CMake, la vista de destinos en el Explorador de soluciones, las opciones de generación de caché y la compilación de archivo único. Para obtener más información, vea [CMake Support in Visual Studio](https://devblogs.microsoft.com/cppblog/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) (Compatibilidad con CMake en Visual Studio) y [Proyectos de CMake en Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development"></a>Desarrollo de escritorio para Windows

Ahora se proporciona una experiencia de instalación más granular para la instalación de la carga de trabajo original de C++. Se han agregado componentes seleccionables que permiten instalar únicamente las herramientas que necesita. Los tamaños de instalación indicados para los componentes enumerados en la UI del instalador son incorrectos y subestiman el tamaño total.

Para crear correctamente proyectos de Win32 en la carga de trabajo de escritorio de C++, debe instalar un conjunto de herramientas y un SDK de Windows. Instale los componentes recomendados (seleccionados), que son el **conjunto de herramientas de VC++ 2017 v141 (x86, x64)** y **Windows 10 SDK (10.0.nnnnn)** para asegurarse de que funcionan. Si no se instalan las herramientas necesarias, los proyectos no se crearán correctamente y el asistente se bloqueará.

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

Visual C++ Build Tools (anteriormente disponible como un producto independiente) ahora se incluye como carga de trabajo en el instalador de Visual Studio. Esta carga de trabajo instala solo las herramientas necesarias para compilar proyectos de C++ sin tener que instalar el IDE de Visual Studio. Se incluyen los conjuntos de herramientas v140 y v141. El conjunto de herramientas v141 contiene las últimas mejoras de la versión 15.5 de Visual Studio 2017. Para obtener más información, vea [Visual Studio Build Tools now include the VS2017 and VS2015 MSVC Toolsets](https://devblogs.microsoft.com/cppblog/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/) (Visual Studio Build Tools ahora incluye los conjuntos de herramientas VS2017 y VS2015).

## <a name="linux-development-with-c"></a>Desarrollo para Linux con C++

La extensión popular [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) ya forma parte de Visual Studio. Esta instalación proporciona todo lo que necesita para desarrollar y depurar aplicaciones de C++ que se ejecutan en un entorno de Linux.

##### <a name="visual-studio-2017-version-152"></a>Visual Studio 2017, versión 15.2

Se han realizado mejoras para el uso compartido de código multiplataforma y visualización de tipos. Para más información, consulte las [mejoras en Linux C++ para el uso compartido de código multiplataforma y visualización de tipos](https://devblogs.microsoft.com/cppblog/linux-cross-platform-and-type-visualization/).

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

- La carga de trabajo de Linux presenta más opciones de compatibilidad con **rsync** como alternativa a **sftp** para sincronizar archivos en máquinas remotas Linux.
- Se ha agregado compatibilidad para compilación cruzada con destinos de microcontroladores ARM. Para habilitarla en la instalación, seleccione la carga de trabajo **Desarrollo de Linux con C++** y seleccione la opción **Desarrollo incrustado e IoT**. Esta opción agrega a su instalación las herramientas de compilación cruzada GCC de ARM y Make. Para obtener más información, vea [ARM GCC Cross Compilation in Visual Studio](https://devblogs.microsoft.com/cppblog/arm-gcc-cross-compilation-in-visual-studio/) (Compilación cruzada de GCC de ARM en Visual Studio).
- Se ha agregado compatibilidad para CMake. Ahora puede trabajar en su base de código CMake sin tener que convertirla a un proyecto de Visual Studio. Para obtener más información, vea [Configure a Linux CMake Project](../linux/cmake-linux-project.md) (Configuración de un proyecto CMake de Linux).
- Se ha agregado compatibilidad para la ejecución de tareas remotas. Esta capacidad le permite ejecutar cualquier comando en un sistema remoto que se defina en el Administrador de conexiones de Visual Studio. Las tareas remotas también proporcionan la capacidad de copia de archivos en el sistema remoto.
Para obtener más información, vea [Configure a Linux CMake Project](../linux/cmake-linux-project.md) (Configuración de un proyecto CMake de Linux).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

- Varias mejoras en escenarios de carga de trabajo de Linux. Para obtener más información, vea [Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://devblogs.microsoft.com/cppblog/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/) (Mejoras de carga de trabajo de C++ de Linux para el sistema de proyectos, la ventana de la consola de Linux, rsync y Asociar al proceso).
- IntelliSense para encabezados en conexiones remotas de Linux. Para obtener más información, vea [IntelliSense for Remote Linux Headers](https://devblogs.microsoft.com/cppblog/intellisense-for-remote-linux-headers/) (IntelliSense para encabezados remotos de Linux) y [Configuración de un proyecto de CMake de Linux](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Desarrollo de juegos con C++

Utilice toda la capacidad de C++ para crear juegos profesionales con tecnología de DirectX o Cocos2d.

## <a name="mobile-development-with-c-for-android-and-ios"></a>Desarrollo móvil con C++ (Android y iOS)

Ahora puede crear y depurar aplicaciones móviles con Visual Studio que pueden tener como destino iOS y Android.

## <a name="universal-windows-apps"></a>Aplicaciones Windows universales

C++ viene como un componente opcional de la carga de trabajo de la Aplicación Windows universal. Actualmente, debe actualizar los proyectos de C++ manualmente. Puede abrir un proyecto de la Plataforma universal de Windows destinado a v140 en Visual Studio 2017. Sin embargo, deberá seleccionar el conjunto de herramientas de la plataforma v141 en las páginas de propiedades del proyecto si no tiene instalado Visual Studio 2015.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nuevas opciones de C++ en la Plataforma universal de Windows (UWP)

Ahora tiene nuevas opciones para escribir y empaquetar aplicaciones C++ para la Plataforma universal de Windows y Microsoft Store: La infraestructura Puente de dispositivo de escritorio permite empaquetar el objeto COM o la aplicación de escritorio existentes para su implementación a través de la Tienda Windows, o mediante los canales existentes vía la instalación de prueba. Las nuevas capacidades de Windows 10 le permiten agregar funcionalidad de Plataforma universal de Windows a su aplicación de escritorio de varias maneras. Para obtener más información, vea [Puente de dispositivo de escritorio](/windows/uwp/porting/desktop-to-uwp-root).

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

Se ha agregado una plantilla de proyecto **Proyecto de paquete de aplicación de Windows**, lo que simplifica en gran medida la tarea de empaquetar aplicaciones de escritorio mediante el uso del Puente de dispositivo de escritorio. Está disponible en **Archivo | Nuevo | Proyecto | Instalado | Visual C++ | Plataforma universal de Windows**. Para obtener más información, consulte [Empaquetar una aplicación mediante Visual Studio (Puente de dispositivo de escritorio a UWP)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Al escribir código nuevo, ahora puede usar C++/WinRT, una proyección del lenguaje C++ estándar para Windows Runtime que se implementa solamente en los archivos de encabezado. Permite consumir y usar las API de Windows Runtime con cualquier compilador de C++ conforme a los estándares. C++/WinRT está diseñado para proporcionar a los desarrolladores de C++ acceso de primera a la API de Windows moderna. Para más información, consulte [C++/WinRT: Modern C++ for the Windows Runtime](https://moderncpp.com/) (C++ moderno para Windows Runtime).

A partir de la compilación 17025 de Windows SDK Insider Preview, C++/WinRT está incluido en Windows SDK. Para obtener más información, vea [C++/WinRT is now included the Windows SDK](https://devblogs.microsoft.com/cppblog/cppwinrt-is-now-included-the-windows-sdk/) (Ahora se incluyen C++/WinRT en Windows SDK).

## <a name="the-clangc2-platform-toolset"></a>Conjunto de herramientas de la plataforma Clang/C2

El conjunto de herramientas Clang/C2 que se incluye con Visual Studio 2017 ahora es compatible con el modificador **`/bigobj`** , que es fundamental para la creación de proyectos grandes. También incluye varias correcciones de errores importantes, tanto en el front-end y el back-end del compilador.

## <a name="c-code-analysis"></a>Análisis de código de C++

Ahora se distribuyen con Visual Studio los comprobadores principales de C++ para aplicar las [directrices principales de C++](https://github.com/isocpp/CppCoreGuidelines). Habilite los comprobadores en la página **Extensiones de análisis de código** en las páginas de propiedades del proyecto y las extensiones se incluirán al ejecutar análisis de código. Para más información, consulte [Usar los comprobadores de directrices principales de C++](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Página de propiedades de CppCoreCheck")

##### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 versión 15.3

- Se ha agregado compatibilidad con reglas relativas a la administración de recursos.

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

- Las nuevas comprobaciones de C++ Core Guidelines cubren la exactitud del puntero inteligente, el uso adecuado de inicializadores globales y la marca de usos de construcciones como `goto` y conversiones incorrectas.

- Algunos números de advertencias que puede encontrar en 15.3 ya no están disponibles en 15.5. Estas advertencias se han sustituido por comprobaciones más específicas.

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, versión 15.6

- Se ha agregado compatibilidad para el análisis de archivo único y mejoras en el rendimiento en tiempo de ejecución de los análisis. Para obtener más información, vea [C++ Static Analysis Improvements for Visual Studio 2017 15.6 Preview 2](https://devblogs.microsoft.com/cppblog/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/) (Mejoras de análisis estático de C++ para Visual Studio de 2017 15.6 [versión preliminar 2])

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

- Se ha agregado compatibilidad con [/analyze:ruleset](../build/reference/analyze-code-analysis.md), que permite especificar las reglas de análisis de código que se van a ejecutar.
- Se ha agregado compatibilidad para reglas de C++ Core Guidelines adicionales.  Para más información, consulte [Usar los comprobadores de directrices principales de C++](/cpp/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing-in-visual-studio-2017"></a>Pruebas unitarias en Visual Studio 2017

##### <a name="visual-studio-2017-version-155"></a>Versión 15.5 de Visual Studio 2017

Google Test Adapter y Boost.Test Adapter ahora están disponibles como componentes de la carga de trabajo **Desarrollo para el escritorio con C++** y se integran con el **Explorador de pruebas**. Se ha agregado compatibilidad con CTest para proyectos CMake (con Abrir carpeta), aunque todavía no está disponible la integración completa con el **Explorador de pruebas**. Para obtener más información, vea [Writing unit tests for C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp) (Escritura de pruebas unitarias para C/C++).

##### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017, versión 15.6

- Se ha agregado compatibilidad con `Boost.Test` para admitir la biblioteca dinámica de Boost.Test.
- Ahora en el IDE hay una plantilla de elemento `Boost.Test` disponible.

Para obtener más información, consulte [`Boost.Test` Unit Testing: Dynamic Library support and New Item Template](https://devblogs.microsoft.com/cppblog/boost-test-unit-testing-dynamic-library-support-and-new-item-template/) (Pruebas unitarias de Boost.Test: compatibilidad con bibliotecas dinámicas y nueva plantilla de elemento).

##### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 versión 15.7

Se ha agregado compatibilidad con [CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) para proyectos de pruebas unitarias de C++. Para obtener más información, vea [Announcing CodeLens for C++ Unit Testing](https://devblogs.microsoft.com/cppblog/announcing-codelens-for-c-unit-testing/) (Anuncio de CodeLens para pruebas unitarias de C++).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos de Visual Studio

Herramientas de Diagnóstico de gráficos de Visual Studio: puede usarlas para registrar y analizar problemas de representación y rendimiento en aplicaciones de Direct3D. Úselas en aplicaciones que se ejecutan localmente en su PC Windows, en un emulador de dispositivos de Windows o en un dispositivo o equipo remoto.

- **Entrada y salida para sombreadores de vértices y geometría**: la función para ver la entrada y la salida de los sombreadores de vértices y geometría ha sido una de las más solicitadas, y ahora se admite en las herramientas. Seleccione la fase VS (sombreadores de vértices) o GS (sombreadores de geometría) en la vista Etapas de canalización para empezar a inspeccionar su entrada y su salida en la tabla siguiente.

  ![Entrada y salida de los sombreadores](media/io-shaders.png)

- **Búsqueda y filtrado en la tabla de objetos**: proporciona un modo rápido y sencillo de encontrar los recursos que se buscan.

  ![Buscar](media/search.png)

- **Historial de recursos**: esta nueva vista proporciona una manera simplificada de ver el historial completo de modificaciones de un recurso tal como se usó durante el procesamiento de un fotograma capturado. Para invocar el historial de un recurso, haga clic en el icono de reloj que se encuentra junto a los hipervínculos de recursos.

  ![Historial de recursos](media/resource-history.png)

  De este modo, se mostrará la nueva ventana de herramientas **Historial de recursos**, rellenada con el historial de cambios del recurso.

  ![Historial de cambios del recurso](media/resource-history-change.png)

  Puede capturar fotogramas con la captura de pila de llamadas completa habilitada. De ese modo, se puede deducir rápidamente el contexto de cada evento de cambio e inspeccionarlo dentro del proyecto de Visual Studio. Establezca la opción captura de pila de llamadas completa en el cuadro de diálogo de Visual Studio **Herramientas > Opciones**, en **Diagnóstico de gráficos**.

- **Estadísticas de API**: vea un resumen de alto nivel del uso de la API en su fotograma. Puede ser útil para detectar llamadas que tal vez no sepa que realiza o para detectar llamadas que realiza demasiado a menudo. Esta ventana está disponible en **Vista > Estadísticas de API** en el Analizador de gráficos de Visual Studio.

  ![Estadísticas de API](media/api-stats.png)

- **Estadísticas de memoria**: vea cuánta memoria asigna el controlador a los recursos que crea en el fotograma. Esta ventana está disponible en **Vista > Estadísticas de memoria** en el **Analizador de gráficos de Visual Studio**. Para copiar datos en un archivo CSV para verlos en una hoja de cálculo, haga clic con el botón derecho y elija **Copiar todo**.

  ![Estadísticas de memoria](media/memory-stats.png)

- **Validación de fotogramas**: la nueva lista de errores y advertencias proporciona una manera fácil de navegar por la lista de eventos en función de los posibles problemas que haya detectado la capa de depuración de Direct3D. Haga clic en **Ver > Validación de fotogramas** en el Analizador de gráficos de Visual Studio para abrir la ventana. Después, haga clic en **Ejecutar validación** para comenzar el análisis. Puede tardar varios minutos en completarse, en función de la complejidad del fotograma.

  ![Validación de fotogramas](media/frame-validation.png)

- **Análisis de fotogramas para D3D12**: use el análisis de fotogramas para analizar el rendimiento de las llamadas a draw con experimentos "y si" dirigidos. Cambie a la pestaña Análisis de fotogramas y ejecute un análisis para ver el informe. Para obtener más información, vea el vídeo [GoingNative 25: Visual Studio Graphics Frame Analysis](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) (GoingNative 25: Análisis de fotogramas de gráficos de Visual Studio).

  ![Análisis de fotogramas](media/frame-analysis.png)

- **Mejoras de uso de GPU**: se pueden realizar seguimientos abiertos mediante el Generador de perfiles de uso de GPU de Visual Studio con la herramienta Vista de GPU o Windows Performance Analyzer (WPA) para un análisis más detallado. Si tiene instalado Windows Performance Toolkit, hay dos hipervínculos, uno para WPA y otro para Vista de GPU, en la parte inferior derecha de la información general de la sesión.

  ![Uso de GPU](media/gpu-usage.png)

  Los seguimientos abiertos en Vista de GPU a través de este vínculo admiten el zoom de escala de tiempo y el movimiento panorámico sincronizados entre Visual Studio y Vista de GPU. Una casilla de Visual Studio controla si la sincronización está habilitada o no.

  ![Vista de GPU](media/gpu-view.png)

::: moniker-end

::: moniker range="=vs-2015"

Para ver la lista completa de las novedades hasta Visual Studio 2015 Update 3, consulte [Novedades de Visual C++ de 2003 a 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

Para obtener más información sobre las novedades de Visual Studio 2015, consulte las notas de la versión vinculadas desde el [historial de notas de la versión de Visual Studio 2015](/visualstudio/releasenotes/vs2015-version-history).

Para información sobre las novedades de C++ en Visual Studio 2019, consulte [Novedades de C++ en Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2019).

Para información sobre las novedades de C++ en Visual Studio 2017, consulte [Novedades de C++ en Visual Studio 2017](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio?view=vs-2017).

::: moniker-end
