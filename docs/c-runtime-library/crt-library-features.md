---
title: "Características de la biblioteca CRT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
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
caps.latest.revision: 32
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 22da7776e46171467a37d46c3de3227f060eaf77
ms.openlocfilehash: 0ae005c2367f891e0b7a91e3f7e45d42d852fb78
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="crt-library-features"></a>Características de la biblioteca CRT
En este tema se describen los distintos archivos .lib que forman las bibliotecas en tiempo de ejecución de C, así como las opciones de compilador y las directivas de preprocesador asociadas.  
  
## <a name="c-run-time-libraries-crt"></a>Bibliotecas en tiempo de ejecución de C (CRT)  
 La biblioteca de tiempo de ejecución de C (CRT) es la parte de la biblioteca estándar de C++ que incorpora la biblioteca del estándar ISO C99. Las bibliotecas de Visual C++ que implementan el CRT admiten el desarrollo de código nativo, así como código mixto (nativo y administrado) y código administrado puro para el desarrollo de .NET. Todas las versiones de CRT admiten el desarrollo multiproceso. La mayoría de las bibliotecas admite la vinculación estática, para vincular la biblioteca directamente en el código, o la vinculación dinámica para permitir que el código use archivos DLL comunes.  
  
 A partir de Visual Studio 2015, el CRT se ha refactorizado en nuevos binarios. CRT Universal (UCRT) contiene las funciones y variables globales exportadas por la biblioteca CRT del estándar C99. El UCRT ahora es un componente de Windows y se incluye en Windows 10. La biblioteca estática, la biblioteca de importación de DLL y los archivos de encabezado para el UCRT ahora se encuentran en el SDK de Windows 10. Cuando se instala Visual C++, el programa de instalación de Visual Studio instala el subconjunto del SDK de Windows 10 necesario para usar el UCRT. Se puede usar el UCRT en cualquier versión de Windows compatible con Visual Studio 2015 y versiones posteriores. También se puede redistribuir mediante vcredist para las versiones compatibles de Windows que no sean Windows 10. Para obtener más información, vea [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md).  
  
 En la tabla siguiente se muestran las bibliotecas que implementan el UCRT.  
  
|Biblioteca|DLL asociado|Características|Opción|Directivas de preprocesador|  
|-------------|--------------------|---------------------|------------|-----------------------------|  
|libucrt.lib|Ninguna|Vincula estáticamente el UCRT en el código.|**/MT**|_MT|  
|libucrtd.lib|Ninguna|Versión de depuración del UCRT para la vinculación estática. No redistribuible.|**/MTd**|_DEBUG, _MT|  
|ucrt.lib|ucrtbase.dll|Biblioteca de importación de DLL para el UCRT.|**/MD**|_MT, _DLL|  
|ucrtd.lib|ucrtbased.dll|Biblioteca de importación de DLL para la versión de depuración del UCRT. No redistribuible.|**/MDd**|_DEBUG, _MT, _DLL|  
  
 La biblioteca de vcruntime contiene código específico de la implementación de CRT en Visual C++ como, por ejemplo, compatibilidad con la depuración y el control de excepciones, comprobaciones en tiempo de ejecución e información de tipos, detalles de la implementación y determinadas funciones de biblioteca ampliada. Esta biblioteca es específica de la versión del compilador que se use.  
  
 En la siguiente tabla se muestran las bibliotecas que implementan la biblioteca vcruntime.  
  
|Biblioteca|DLL asociado|Características|Opción|Directivas de preprocesador|  
|-------------|--------------------|---------------------|------------|-----------------------------|  
|libvcruntime.lib|Ninguna|Se vincula estáticamente en el código.|**/MT**|_MT|  
|libvcruntimed.lib|Ninguna|Versión de depuración para la vinculación estática. No redistribuible.|**/MTd**|_MT, _DEBUG|  
|vcruntime.lib|vcruntime\<versión>.dll|Biblioteca de importación de DLL para vcruntime.|**/MD**|_MT, _DLL|  
|vcruntimed.lib|vcruntime\<versión>d.dll|Biblioteca de importación de DLL para vcruntime de depuración. No redistribuible.|**/MDd**|_DEBUG, _MT, _DLL|  
  
 El código que inicializa el CRT está en una de varias bibliotecas, en función de si la biblioteca CRT está vinculada estática o dinámicamente o es código nativo, administrado o mixto. Este código controla el inicio de CRT, la inicialización de datos internos por subproceso y la terminación. Es específico de la versión del compilador que se use. Esta biblioteca siempre se vincula estáticamente, incluso cuando se usa un UCRT vinculado dinámicamente.  
  
 En la siguiente tabla se muestran las bibliotecas que implementan la inicialización y la terminación de CRT.  
  
|Biblioteca|Características|Opción|Directivas de preprocesador|  
|-------------|---------------------|------------|-----------------------------|  
|LIBCMT.lib|Vincula estáticamente el inicio de CRT nativo en el código.|**/MT**|_MT|  
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
  
 Si usa el modificador de compilador **/clr** , el código se vinculará a una biblioteca estática, msvcmrt.lib. La biblioteca estática proporciona un proxy entre el código administrado y CRT nativo. CRT vinculado estáticamente (opciones **/MT** o **/MTd** ) no se puede usar con **/clr**. En su lugar, use las bibliotecas vinculadas dinámicamente (**/MD** o **/MDd**).  
  
 Si usa el modificador de compilador **/clr:pure** , el código se vinculará a la biblioteca estática msvcurt.lib. Lo mismo que con **/clr**, no se puede vincular a la biblioteca estática vinculada. Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso a partir de Visual Studio 2015.  
  
 Para obtener más información sobre cómo usar CRT con **/clr**, consulte [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md); para **/clr:pure**, consulte [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Para compilar una versión de depuración de la aplicación, debe estar definida la marca [_DEBUG](../c-runtime-library/debug.md) y la aplicación se debe vincular a una versión de depuración de una de estas bibliotecas. Para obtener más información sobre cómo usar las versiones de depuración de los archivos de biblioteca, vea [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
 Esta versión de CRT no es totalmente compatible con el estándar C99. En concreto, no se admiten el encabezado \<tgmath.h> ni las macros pragma CX_LIMITED_RANGE/FP_CONTRACT. Determinados elementos como el significado de los especificadores de parámetros en las funciones estándar de E/S usan interpretaciones heredadas de forma predeterminada. Se pueden usar opciones de conformidad del compilador /Zc y se pueden especificar las opciones del enlazador para controlar algunos aspectos de cumplimiento de la biblioteca.  
  
## <a name="c-standard-library"></a>Biblioteca estándar de C++  
  
|Biblioteca estándar de C++|Características|Opción|Directivas de preprocesador|  
|----------------------------|---------------------|------------|-----------------------------|  
|LIBCPMT.lib|Vínculo multiproceso, estático|**/MT**|_MT|  
|MSVCPRT.LIB|Vínculo multiproceso, dinámico (biblioteca de importación para MSVCP\<versión>.dll)|**/MD**|_MT, _DLL|  
|LIBCPMTD.LIB|Vínculo multiproceso, estático|**/MTd**|_DEBUG, _MT|  
|MSVCPRTD.LIB|Vínculo multiproceso, dinámico (biblioteca de importación para MSVCP\<versión>.D.DLL)|**/MDd**|_DEBUG, _MT, _DLL|  
  
 Cuando compile una versión de lanzamiento del proyecto, una de las bibliotecas en tiempo de ejecución básicas de C (LIBCMT.LIB, MSVCMRT.LIB, MSVCRT.LIB) se vinculará de forma predeterminada, según la opción de compilador que elija (multiproceso, DLL, /clr). Si incluye uno de los [Archivos de encabezado de la biblioteca estándar de C++](../standard-library/cpp-standard-library-header-files.md) en el código, Visual C++ vinculará automáticamente una biblioteca estándar de C++ en tiempo de compilación. Por ejemplo:  
  
```  
#include <ios>   
```  
  
## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>¿Qué problemas existen si una aplicación usa más de una versión de CRT?  
 Si tiene más de un archivo DLL o EXE, puede tener varios CRT, independientemente de que use distintas versiones de Visual C++. Por ejemplo, la vinculación estática de CRT a varios archivos DLL puede presentar el mismo problema. Se ha indicado a los desarrolladores que tienen este problema con CRT estáticos que compilen con **/MD** para usar el archivo DLL de CRT. Si los archivos DLL pasan recursos de CRT a través del límite de DLL, se producirán problemas de CRT dispares y habrá que volver a compilar el proyecto con Visual C++.  
  
 Si el programa usa más de una versión de CRT, es necesario prestar atención al pasar ciertos objetos de CRT (por ejemplo identificadores de archivo, configuraciones regionales y variables de entorno) a través de los límites de los archivos DLL. Para obtener más información sobre los posibles problemas y cómo resolverlos, consulte [Errores potenciales que pasan los objetos de CRT entre los límites de DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)
