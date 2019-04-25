---
title: Novedades de C++ en Visual Studio 2019
ms.date: 04/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 493b96a8ce3359cc18287adbae8cbd6c374671ec
ms.sourcegitcommit: b72a10a7b12e722fd91a17406b91b270026f763a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2019
ms.locfileid: "58899411"
---
<!--NOTE all https:// links to docs.microsoft.com need to be converted to site-relative links prior to publishing-->

# <a name="whats-new-for-c-in-visual-studio-2019"></a>Novedades de C++ en Visual Studio 2019

Visual Studio 2019 incluye muchas actualizaciones y revisiones del entorno de Microsoft C++. Hemos corregido numerosos errores y problemas en el compilador y en las herramientas. Muchos los han enviado los clientes a través de las opciones [Notificar un problema](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) y [Proporcionar una sugerencia](https://developercommunity.visualstudio.com/spaces/62/index.html), en **Enviar comentarios**. ¡Muchas gracias por notificárnoslos! Para obtener más información sobre todas las novedades de Visual Studio, visite [Novedades de Visual Studio](/visualstudio/ide/whats-new-visual-studio-2019).

## <a name="c-compiler"></a>compilador C++

- La opción `/std:c++latest` ahora incluye características de C++20 que no están necesariamente completas, como la compatibilidad inicial con el operador <=> de C++20 ("nave espacial") para la comparación de tres vías.

- La característica [Macros de prueba de características (P0941R2)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) está completa, con compatibilidad con `__has_cpp_attribute`. Ahora, las macros de prueba de características se admiten en todos los modos estándares.

- La característica [Prohibición de agregados con constructores declarados por el usuario (P1008R1) de C++20](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) también está completa.

- Se proporciona compatibilidad mejorada con características de C++17, además de compatibilidad experimental con características de C++20, como módulos y corrutinas. Para obtener información detallada, vea [C++ Conformance Improvements in Visual Studio 2019](../cpp-conformance-improvements.md) (Mejoras de conformidad de C++ en Visual Studio 2019).

- El modificador del compilador `/Gm` de C++ ahora está en desuso. Considere la posibilidad de deshabilitar el modificador `/Gm` en los scripts de compilación si se define explícitamente, aunque también puede ignorar de manera segura la advertencia de desuso de `/Gm`, ya que no se tratará como un error cuando use "Tratar advertencias como errores" (`/WX`).

- Los encabezados precompilados ya no se generan de forma predeterminada para la consola de C++ y las aplicaciones de escritorio.

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen, seguridad, diagnóstico y control de versiones

Análisis mejorado con `/Qspectre` para proporcionar asistencia de mitigación en Spectre Variant 1 (CVE-2017-5753). Para obtener más información, vea [Spectre Mitigations in MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/) (Mitigaciones de Spectre en MSVC).

## <a name="c-standard-library-improvements"></a>Mejoras de la biblioteca estándar de C++

- La característica [remove_cvref \(P0550R2) de C++20](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) está completada.

- Se ha mejorado \<charconv> floating-point to_chars() de C++17, ya que el parámetro chars_format::fixed más corto es un 60-80 % más rápido, y el parámetro chars_format::hex más corto o preciso está completado.

- Una mayor cantidad de algoritmos tiene implementaciones paralelizadas: is_sorted(), is_sorted_until(), is_partitioned(), set_difference(), set_intersection(), is_heap() y is_heap_until().

- Mejoras en `std::variant` para que sea más adecuado para optimizadores, lo que conlleva un código mejor generado. La inserción de código ha mejorado mucho con `std::visit`.

- Hemos aplicado formato clang a los encabezados de la biblioteca estándar de C++ para mejorar la legibilidad.

- Rendimiento mejorado al compilar con `if constexpr` varias características de la biblioteca estándar.

- Optimización del diseño físico de la biblioteca estándar para evitar la compilación de partes de la biblioteca estándar no especificadas con #include, lo que reduce a la mitad el tiempo de compilación de un archivo vacío que solo incluya \<vector>.

## <a name="performancethroughput-fixes"></a>Correcciones de rendimiento

- Mejoras en el rendimiento de la compilación, incluida la manera en que el enlazador trata la E/S de archivos y el tiempo de vínculo en la creación y la combinación de tipos de PDB.

- Se ha agregado compatibilidad básica para la vectorización de OpenMP SIMD. Puede habilitarla con el nuevo modificador de CL, `-openmp:experimental`. Esta opción permite vectorizar potencialmente los bucles anotados con `#pragma omp simd`. No se garantiza la vectorización y se genera una advertencia para los bucles anotados sin vectorizar. No se admiten las cláusulas SIMD, simplemente se omiten y se notifica una advertencia.

- Se ha agregado un nuevo modificador de línea de comandos de inserción, `-Ob3`, que es una versión más agresiva de `-Ob2`. `-O2` (optimizar el binario para acelerar el proceso) todavía implica `-Ob2` de manera predeterminada. Si considera que el compilador no realiza las inserciones con la suficiente agresividad, considere la posibilidad de pasar `-O2 -Ob3`.

- Para admitir la vectorización manual de bucles con llamadas a funciones de la biblioteca matemática y otras operaciones, como la división de enteros, hemos agregado compatibilidad con funciones intrínsecas de la biblioteca matemática de vectores cortos (SVML). Estas funciones calculan los equivalentes de vectores de 128 bits, 256 bits o 512 bits. Vea la [Guía de funciones intrínsecas de Intel](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML) para las definiciones de las funciones admitidas.

- Optimizaciones nuevas y mejoradas:

  - Simplificaciones aritméticas y plegado constante para las expresiones que usan intrínsecos de vector SIMD, para formatos de entero y float.

  - Un análisis más eficaz para extraer información de flujo de control (instrucciones if/else/switch) para quitar ramas que siempre se han demostrado true o false.

  - Despliegue mejorado de memset para usar instrucciones de vectores de SSE2.

  - Eliminación mejorada de copias de estructuras/clases inútiles, especialmente para los programas de C++ que pasan por valor.

  - Optimización mejorada del código que usa `memmove`, como la construcción `std::copy`, `std::vector` y `std::string`.

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Compatibilidad de Live Share con C++

[Live Share](/visualstudio/liveshare/) ahora es compatible con C++, lo que permite a los desarrolladores que usan Visual Studio o Visual Studio Code colaborar en tiempo real. Para obtener más información, vea [Announcing Live Share for C++: Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/) (Presentación de Live Share para C++: colaboración y uso compartido en tiempo real).

### <a name="intellicode-for-c"></a>IntelliCode para C++

IntelliCode es una extensión opcional que usa su amplio aprendizaje y su contexto de código para colocar lo que es más probable que use en la parte superior de la lista de finalización. A menudo puede eliminar la necesidad de desplazarse hacia abajo por la lista. Para C++, IntelliCode ofrece más ayuda al usar bibliotecas populares, como la biblioteca estándar. Para obtener más información, vea [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/) (Las sugerencias de finalización de código asistidas por inteligencia artificial se hacen realidad en C++ a través de IntelliCode).

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

## <a name="cmake-support"></a>Compatibilidad con CMake

- Visual Studio ahora puede abrir las memorias caché de CMake existentes generadas por herramientas externas, como CMakeGUI, por sistemas de compilación de metadatos personalizados o por scripts de compilación que invocan cmake.exe.

- Rendimiento de IntelliSense mejorado.

- Se ha introducido un nuevo editor de configuración que supone una alternativa a la edición manual del archivo CMakeSettings.json y comparte ciertas similitudes con CMakeGUI.

- Visual Studio impulsa el desarrollo en C++ mediante CMake en Linux, ya que detecta si tiene una versión compatible de CMake en su equipo Linux y, en caso de que no la tenga, se ofrece a instalarla.

- Las opciones de configuración que son incompatibles en CMakeSettings, como las arquitecturas no coincidentes o la configuración incompatible del generador de CMake, aparecen con subrayado ondulado en el editor de JSON y con errores en la lista de errores.

- La cadena de herramientas de vcpkg se detecta automáticamente y se habilita para los proyectos de CMake que se abren en el IDE una vez que `vcpkg integrate install` se ha ejecutado. Se puede desactivar este comportamiento si se especifica un archivo de cadena de herramientas vacío en CMakeSettings.

- Los proyectos de CMake ahora habilitan la depuración de Solo mi código de forma predeterminada.

- Las advertencias de análisis estático ahora se pueden procesar en segundo plano y mostrarse en el editor de proyectos de CMake.

- Mensajes más claros de inicio y final de la compilación y la configuración para los proyectos de CMake y compatibilidad con la interfaz de usuario de progreso de compilación de Visual Studio. Además, ahora hay una opción de configuración del nivel de detalle de CMake en **Herramientas > Opciones** para personalizar el nivel de detalle de los mensajes de compilación y configuración de CMake en la ventana de salida.

- Ahora se admite la opción `cmakeToolchain` en CMakeSettings.json para especificar cadenas de herramientas sin tener que modificar manualmente la línea de comandos de CMake.

- Nuevo acceso directo del menú para **Compilar todo**: **CTRL+Mayús+B**.

## <a name="debugging"></a>Depuración

- Para aplicaciones de C++ que se ejecutan en Windows, los archivos PDB ahora se cargan en un proceso independiente de 64 bits. Este cambio soluciona una variedad de bloqueos provocados por memoria insuficiente del depurador al depurar aplicaciones que contienen un gran número de módulos y archivos PDB.

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

- Windows 8.1 SDK ya no está disponible en el instalador de Visual Studio. Recomendamos que actualice los proyectos de C++ al Windows 10 SDK más reciente. Si tiene una dependencia fuerte de 8.1, puede descargarlo desde el archivo de Windows SDK.

- Ya no estará disponible Windows XP como opción de destino para el conjunto de herramientas de C++ más actualizado. Se sigue admitiendo XP como destino con bibliotecas y el compilador de MSVC de nivel de VS 2017, y se puede instalar a través de "Componentes individuales".

- En nuestra documentación se desaconseja encarecidamente el uso de módulos de combinación para la implementación en tiempo de ejecución de Visual C++. En esta versión hemos dado un paso extra para marcar nuestros MSM como en desuso. Considere la posibilidad de migrar la implementación central VCRuntime de MSM al paquete redistribuible.

## <a name="mobile-development-with-c-android-and-ios"></a>Desarrollo móvil con C++ (Android y iOS)

La experiencia Android de C++ ahora toma como valor predeterminado el Android SDK 25 y el Android NDK 16b.

## <a name="clangc2-platform-toolset"></a>Conjunto de herramientas de la plataforma Clang/C2

Se ha eliminado el componente experimental Clang/C2. Use el conjunto de herramientas MSVC para un cumplimiento total de los estándares de C++ con `/permissive-` y `/std:c++17`, o bien la cadena de herramientas Clang/LLVM para Windows.

## <a name="code-analysis"></a>Análisis de código

- El análisis de código ahora se ejecuta automáticamente en segundo plano. Las advertencias se muestran como líneas verdes onduladas dentro del editor a medida que escribe. Para obtener más información, vea [In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/) (Análisis de código en el editor en Visual Studio 2019, versión preliminar 2).

- Nuevas reglas ConcurrencyCheck experimentales para tipos conocidos de la biblioteca estándar del encabezado \<mutex>. Para obtener más información, vea [Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/) (Análisis de código de simultaneidad en Visual Studio 2019).

- Implementación parcial actualizada del [Comprobador de perfil de duración](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/), que detecta punteros y referencias pendientes. Para obtener más información, vea [Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/) (Actualización de perfiles de duración en Visual Studio 2019, versión preliminar 2).

- Más comprobaciones relacionadas con la corrutina, entre las que se incluyen C26138, C26810, C26811 y la regla experimental C26800. Para obtener más información, vea [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/) (Nuevas comprobaciones de análisis de código en Visual Studio 2019: uso después de mover y corrutina).

## <a name="unit-testing"></a>Pruebas unitarias

La plantilla de proyecto de prueba de C++ administrado ya no está disponible. Puede seguir usando el marco de pruebas de C++ administrado en los proyectos existentes. Para las pruebas unitarias nuevas, considere la opción de usar uno de los marcos de prueba nativos para los que Visual Studio proporciona plantillas (MSTest, Google Test) o la plantilla de proyecto de prueba de C# administrado.