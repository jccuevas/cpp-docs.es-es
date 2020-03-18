---
title: Características de la biblioteca CRT
ms.date: 08/20/2018
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
ms.openlocfilehash: a350e2c45d9ccf83fb09a76f43b63a6b17273cff
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438539"
---
# <a name="crt-library-features"></a>Características de la biblioteca CRT

En este tema se describen los distintos archivos .lib que forman las bibliotecas en tiempo de ejecución de C, así como las opciones de compilador y las directivas de preprocesador asociadas.

## <a name="c-run-time-libraries-crt"></a>Bibliotecas en tiempo de ejecución de C (CRT)

La biblioteca de tiempo de ejecución de C (CRT) es la parte de la biblioteca estándar de C++ que incorpora la biblioteca del estándar ISO C99. Las bibliotecas de Visual C++ que implementan CRT admiten el desarrollo de código nativo, así como código mixto (nativo y administrado) y código administrado. Todas las versiones de CRT admiten el desarrollo multiproceso. La mayoría de las bibliotecas admite la vinculación estática, para vincular la biblioteca directamente en el código, o la vinculación dinámica para permitir que el código use archivos DLL comunes.

A partir de Visual Studio 2015, el CRT se ha refactorizado en nuevos binarios. CRT Universal (UCRT) contiene las funciones y variables globales exportadas por la biblioteca CRT del estándar C99. El UCRT ahora es un componente de Windows y se incluye en Windows 10. La biblioteca estática, la biblioteca de importación de DLL y los archivos de encabezado para el UCRT ahora se encuentran en el SDK de Windows 10. Cuando se instala Visual C++, el programa de instalación de Visual Studio instala el subconjunto del SDK de Windows 10 necesario para usar el UCRT. Se puede usar el UCRT en cualquier versión de Windows compatible con Visual Studio 2015 y versiones posteriores. También se puede redistribuir mediante vcredist para las versiones compatibles de Windows que no sean Windows 10. Para obtener más información, vea [Redistributing Visual C++ Files](../windows/redistributing-visual-cpp-files.md).

En la tabla siguiente se muestran las bibliotecas que implementan el UCRT.

|Biblioteca|DLL asociado|Características|Opción|Directivas de preprocesador|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt.lib|None|Vincula estáticamente el UCRT en el código.|**/MT**|_MT|
|libucrtd.lib|None|Versión de depuración del UCRT para la vinculación estática. No redistribuible.|**/MTd**|_DEBUG, _MT|
|ucrt.lib|ucrtbase.dll|Biblioteca de importación de DLL para el UCRT.|**/MD**|_MT, _DLL|
|ucrtd.lib|ucrtbased.dll|Biblioteca de importación de DLL para la versión de depuración del UCRT. No redistribuible.|**/MDd**|_DEBUG, _MT, _DLL|

La biblioteca de vcruntime contiene código específico de la implementación de CRT en Visual C++ como, por ejemplo, compatibilidad con la depuración y el control de excepciones, comprobaciones en tiempo de ejecución e información de tipos, detalles de la implementación y determinadas funciones de biblioteca ampliada. Esta biblioteca es específica de la versión del compilador que se use.

En la siguiente tabla se muestran las bibliotecas que implementan la biblioteca vcruntime.

|Biblioteca|DLL asociado|Características|Opción|Directivas de preprocesador|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime.lib|None|Se vincula estáticamente en el código.|**/MT**|_MT|
|libvcruntimed.lib|None|Versión de depuración para la vinculación estática. No redistribuible.|**/MTd**|_MT, _DEBUG|
|vcruntime.lib|vcruntime\<versión>.dll|Biblioteca de importación de DLL para vcruntime.|**/MD**|_MT, _DLL|
|vcruntimed.lib|vcruntime\<versión>d.dll|Biblioteca de importación de DLL para vcruntime de depuración. No redistribuible.|**/MDd**|_DEBUG, _MT, _DLL|

> [!NOTE]
> Cuando se produjo la refactorización de UCRT, las funciones de Runtime de simultaneidad se movieron a concrt140.dll, que se agregó al paquete redistribuible de C++. Esta DLL es necesaria para los algoritmos y los contenedores paralelos de C++, como `concurrency::parallel_for`. Además, la biblioteca estándar de C++ requiere que esta DLL en Windows XP admita primitivas de sincronización, dado que Windows XP no tiene variables de condición.

El código que inicializa el CRT está en una de varias bibliotecas, en función de si la biblioteca CRT está vinculada estática o dinámicamente o es código nativo, administrado o mixto. Este código controla el inicio de CRT, la inicialización de datos internos por subproceso y la terminación. Es específico de la versión del compilador que se use. Esta biblioteca siempre se vincula estáticamente, incluso cuando se usa un UCRT vinculado dinámicamente.

En la siguiente tabla se muestran las bibliotecas que implementan la inicialización y la terminación de CRT.

|Biblioteca|Características|Opción|Directivas de preprocesador|
|-------------|---------------------|------------|-----------------------------|
|libcmt.lib|Vincula estáticamente el inicio de CRT nativo en el código.|**/MT**|_MT|
|libcmtd.lib|Vincula estáticamente la versión de depuración del inicio de CRT nativo. No redistribuible.|**/MTd**|_DEBUG, _MT|
|msvcrt.lib|Biblioteca estática para el inicio de CRT nativo para su uso con UCRT y vcruntime de DLL.|**/MD**|_MT, _DLL|
|msvcrtd.lib|Biblioteca estática para la versión de depuración de inicio de CRT nativo para su uso con UCRT y vcruntime de DLL. No redistribuible.|**/MDd**|_DEBUG, _MT, _DLL|
|msvcmrt.lib|Biblioteca estática para el inicio de CRT mixto (nativo y administrado) para su uso con UCRT y vcruntime de DLL.|**/clr**||
|msvcmrtd.lib|Biblioteca estática para la versión de depuración del inicio de CRT mixto (nativo y administrado) para su uso con UCRT y vcruntime de DLL. No redistribuible.|**/clr**||
|msvcurt.lib|**En desuso** Biblioteca estática para CRT administrado puro.|**/clr:pure**||
|msvcurtd.lib|**En desuso** Biblioteca estática para la versión de depuración de CRT administrado puro. No redistribuible.|**/clr:pure**||

Si vincula el programa desde la línea de comandos sin una opción de compilador que especifique una biblioteca en tiempo de ejecución de C, el enlazador usará las bibliotecas de CRT vinculadas estáticamente: libcmt.lib, libvcruntime.lib y libucrt.lib.

El uso de CRT vinculado estáticamente implica que toda información de estado que guarde la biblioteca en tiempo de ejecución de C será local en esa instancia de CRT. Por ejemplo, si usa [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) al usar CRT vinculado estáticamente, la posición del analizador `strtok` no guarda relación con el estado `strtok` que se usa en el código en el mismo proceso (pero en otro archivo DLL o EXE) vinculado a otra instancia del CRT estático. Por el contrario, CRT vinculado dinámicamente tiene el mismo estado para todo el código de un proceso que se vincule dinámicamente a CRT. Este problema no se da si usa las nuevas versiones más seguras de estas funciones. Por ejemplo, `strtok_s` no presenta este problema.

Dado que un archivo DLL compilado mediante la vinculación a CRT estático tendrá su propio estado de CRT, no se recomienda para vincular estáticamente a CRT en un archivo DLL, a menos que las consecuencias de hacerlo se entiendan y se deseen obtener. Por ejemplo, si llama a [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) en un archivo ejecutable que cargue el DLL vinculado a su propio CRT estático, el traductor no detectará ninguna excepción de hardware que genere el código del archivo DLL, pero se detectarán las excepciones de hardware que genere el código del archivo ejecutable principal.

Si usa el modificador de compilador **/clr** , el código se vinculará a una biblioteca estática, msvcmrt.lib. La biblioteca estática proporciona un proxy entre el código administrado y CRT nativo. CRT vinculado estáticamente (opciones **/MT** o **/MTd** ) no se puede usar con **/clr**. En su lugar, use las bibliotecas vinculadas dinámicamente ( **/MD** o **/MDd**). Las bibliotecas de CRT administradas puras están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

Para obtener más información sobre cómo usar CRT con **/clr**, vea [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md).

Para compilar una versión de depuración de la aplicación, debe estar definida la marca [_DEBUG](../c-runtime-library/debug.md) y la aplicación se debe vincular a una versión de depuración de una de estas bibliotecas. Para obtener más información sobre cómo usar las versiones de depuración de los archivos de biblioteca, vea [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

Esta versión de CRT no es totalmente compatible con el estándar C99. En concreto, no se admiten el encabezado \<tgmath.h> ni las macros pragma CX_LIMITED_RANGE/FP_CONTRACT. Determinados elementos como el significado de los especificadores de parámetros en las funciones estándar de E/S usan interpretaciones heredadas de forma predeterminada. Se pueden usar opciones de conformidad del compilador /Zc y se pueden especificar las opciones del enlazador para controlar algunos aspectos de cumplimiento de la biblioteca.

## <a name="c-standard-library"></a>Biblioteca estándar de C++

|Biblioteca estándar de C++|Características|Opción|Directivas de preprocesador|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|Vínculo multiproceso, estático|**/MT**|_MT|
|msvcprt.lib|Vínculo multiproceso dinámico (biblioteca de importación para MSVCP*versión*.dll)|**/MD**|_MT, _DLL|
|libcpmtd.lib|Vínculo multiproceso, estático|**/MTd**|_DEBUG, _MT|
|msvcprtd.lib|Vínculo multiproceso dinámico (biblioteca de importación para MSVCP*versión*d.dll)|**/MDd**|_DEBUG, _MT, _DLL|

Cuando compile una versión de lanzamiento del proyecto, una de las bibliotecas en tiempo de ejecución básicas de C (libcmt.lib, msvcmrt.lib, msvcrt.lib) se vinculará de forma predeterminada, según la opción de compilador que elija (multiproceso, .dll, /clr). Si incluye uno de los [Archivos de encabezado de la biblioteca estándar de C++](../standard-library/cpp-standard-library-header-files.md) en el código, Visual C++ vinculará automáticamente una biblioteca estándar de C++ en tiempo de compilación. Por ejemplo:

```cpp
#include <ios>
```

Para la compatibilidad binaria, es posible que sea necesario especificar más de un archivo .dll mediante una única biblioteca de importación. Asimismo, las actualizaciones de versión pueden introducir *bibliotecas DOT*, es decir, .dll independientes con nuevas funcionalidades de biblioteca. Por ejemplo, la versión 15.6 de Visual Studio 2017 introdujo msvcp140_1.dll para admitir más funcionalidades de la biblioteca estándar sin eliminar la compatibilidad con ABI de msvcp140.dll. La biblioteca de importación msvcprt.lib incluida en el conjunto de herramientas para la versión 15.6 de Visual Studio 2017 admite ambos .dll, y el elemento vcredist de esta versión los instala ambos. Una vez enviada, una biblioteca DOT tendrá un ABI fijo, y nunca presentará ninguna dependencia con una biblioteca DOT posterior.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>¿Qué problemas existen si una aplicación usa más de una versión de CRT?

Cada imagen ejecutable (EXE o DLL) puede tener su propio CRT vinculado estáticamente, o puede vincularse dinámicamente a CRT. La versión de CRT incluida estáticamente o cargada dinámicamente mediante una imagen determinada depende de la versión de las herramientas y bibliotecas con que se haya compilado. Un solo proceso puede cargar varias imágenes EXE y DLL, cada una con su propio CRT. Cada uno de los CRT puede usar un asignador diferente, puede tener diferentes diseños estructura interna y puede usar diferentes disposiciones de almacenamiento. Esto significa que la memoria asignada, los recursos de CRT o las clases que se pasan a través de un límite DLL pueden causar problemas en la administración de memoria, el uso estático interno o la interpretación de diseño. Por ejemplo, si se asigna una clase en un archivo DLL, pero se pasa y se elimina por otro, ¿qué desasignador de CRT se usa? Los errores causados pueden oscilar entre algo sutil o inmediatamente crítico; por eso, se desaconseja la transferencia directa de estos recursos.

Puede evitar muchos de estos problemas empleando las tecnologías de la interfaz binaria de aplicaciones, ya que están diseñadas para ser estables y versionables. Diseñe las interfaces de exportación de DLL para pasar información por valor, o para trabajar en la memoria que se pasa por el autor de llamada en lugar de la asignada localmente que se devuelve al autor de llamada. Use técnicas de cálculo de referencias para copiar los datos estructurados entre imágenes ejecutables. Encapsule recursos localmente y permita solo la manipulación a través de identificadores o funciones que exponga a los clientes.

También es posible evitar algunos de estos problemas si todas las imágenes del proceso usan la misma versión cargada dinámicamente de CRT. Para asegurarse de que todos los componentes utilizan la misma versión DLL de CRT, compílelos mediante la opción **/MD** y use el mismo conjunto de herramientas y configuración de propiedades del compilador.

Es necesario prestar atención si el programa pasa ciertos recursos de CRT (por ejemplo, identificadores de archivo, configuraciones regionales y variables de entorno) a través de los límites de los archivos DLL, incluso si se utiliza la misma versión de CRT. Para obtener más información sobre los posibles problemas y cómo resolverlos, consulte [Potential Errors Passing CRT Objects Across DLL Boundaries](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

## <a name="see-also"></a>Consulte también

- [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)
