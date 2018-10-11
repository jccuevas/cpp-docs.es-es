---
title: Historial de cambios en Visual C++ 2003-2015 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1f7d94dafa34c5ab01dfbcf28e2c429642dbf68
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397323"
---
# <a name="visual-c-change-history-2003---2015"></a>Historial de cambios en Visual C++ 2003-2015

En este artículo, se describen todos los cambios importantes de Visual Studio 2015 desde Visual Studio 2003 y, en este artículo, los términos “nuevo comportamiento” o “ahora” hacen referencia a Visual Studio 2015 y versiones posteriores. Los términos “comportamiento anterior” y “antes” hacen referencia a Visual Studio 2013 y versiones anteriores.

Para obtener más información sobre Visual Studio 2017, consulte [What's new for Visual C++ in Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) (Novedades de Visual C++ en Visual Studio 2017) y [Conformance Improvements in Visual C++ in Visual Studio 2017](../cpp-conformance-improvements-2017.md) (Mejoras de conformidad de Visual C++ en Visual Studio 2017).

> [!NOTE]
> No existen cambios principales binarios entre Visual Studio 2015 y Visual Studio 2017.

Al actualizar a una nueva versión de Visual Studio, se pueden producir errores de compilación o en tiempo de ejecución en código previamente compilado que se ejecutaba correctamente. Los cambios en la nueva versión que producen tales problemas se conocen como *cambios importantes*y normalmente son necesarios debido a las modificaciones en el estándar del lenguaje C++, las firmas de función o la disposición de los objetos en la memoria.

Para evitar errores en tiempo de ejecución que son difíciles de detectar y diagnosticar, recomendamos que nunca vincule estáticamente los binarios compilados con versiones diferentes del compilador. Además, cuando actualice un proyecto EXE o DLL, asegúrese de actualizar las bibliotecas a las que está vinculado. Si usa tipos CRT (Runtime de C) o de la biblioteca estándar de C++, no los pase entre los binarios (incluidos los archivos DLL) que se han compilado con versiones diferentes del compilador. Para obtener más información, consulte [Errores potenciales que pasan los objetos de CRT entre los límites de DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

También se recomienda que nunca escriba código que dependa de una disposición determinada de un objeto que no sea una interfaz COM o un objeto POD. Si escribe código de esta manera, debe asegurarse de que funciona después de la actualización. Para obtener más información, consulte [Portabilidad en los límites de ABI (C++ moderno)](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Además, las mejoras continuas en la conformidad del compilador a veces pueden cambiar cómo entiende el compilador el código fuente existente. Cuando esto sucede, pueden producirse errores nuevos o diferentes durante la compilación o puede haber incluso diferencias de comportamiento en el código previamente compilado que parecía ejecutarse correctamente. Aunque estos no son cambios importantes como los descritos en este documento, es posible que se necesiten cambios en el código fuente para resolver estos problemas:


- [Cambios importantes en la biblioteca en tiempo de ejecución de C (CRT)](#BK_CRT)

- [Cambios importantes de C++ estándar y la biblioteca estándar de C++](#BK_STL)

- [Cambios importantes en MFC y ATL](#BK_MFC)

- [Cambios importantes en el Runtime de simultaneidad](#BK_ConcRT)

## <a name="VC_2015"></a> Cambios de conformidad de Visual C++ 2015

###  <a name="BK_CRT"></a> Biblioteca en tiempo de ejecución de C (CRT)

#### <a name="general-changes"></a>Cambios generales

- **Binarios refactorizados**

   La biblioteca CRT se ha refactorizado en dos binarios distintos: un CRT universal (ucrtbase), que contiene la mayor parte de la funcionalidad estándar, y una biblioteca de VC Runtime (vcruntime), que contiene la funcionalidad relacionada con el compilador como el control de excepciones y funciones intrínsecas. Si usa la configuración predeterminada del proyecto, entonces este cambio no le afecta ya que el vinculador usará automáticamente las nuevas bibliotecas predeterminadas. Si ha configurado la propiedad del **Vinculador** del proyecto **Omitir todas las bibliotecas predeterminadas** en **Sí** o si usa la opción del vinculador `/NODEFAULTLIB` en la línea de comandos, debe actualizar la lista de bibliotecas (en la propiedad **Dependencias adicionales**) para incluir las nuevas bibliotecas refactorizadas. Reemplace la biblioteca CRT anterior (libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib) por las bibliotecas refactorizadas equivalentes. Para cada una de las dos bibliotecas refactorizadas hay versiones estáticas (.lib) y versiones dinámicas (.dll), así como versiones de lanzamiento (sin sufijo) y versiones de depuración (con el sufijo “d”). Las versiones dinámicas tienen una biblioteca de importación con la que se establece el vínculo. Las dos bibliotecas refactorizadas son CRT universal, concretamente ucrtbase.dll o .lib, ucrtbased.dll o .lib y la biblioteca de VC Runtime, libvcruntime.lib, vcruntime*versión*.dll, libvcruntimed.lib, and vcruntimed*versión*.dll. La *versión* en Visual Studio 2015 y Visual Studio 2017 es 140. Consulte [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).

#### <a name="localeh"></a>\<locale.h>

- **localeconv**

   La función [localeconv](../c-runtime-library/reference/localeconv.md) declarada en locale.h ahora funciona correctamente cuando la [configuración regional por subproceso](../parallel/multithreading-and-locales.md) está habilitada. En versiones anteriores de la biblioteca, esta función devolvía los datos de lconv de la configuración regional global, no de la configuración regional del subproceso.

   Si usa la configuración regional por subproceso, compruebe la utilización de localeconv para ver si el código asume que los datos de lconv devueltos corresponden a la configuración regional global y modifíquelo debidamente.

#### <a name="mathh"></a>\<math.h>

- **Sobrecargas de C++ de funciones de la biblioteca matemática**

   En versiones anteriores, \<math.h> definía algunas de las sobrecargas de C++ para las funciones de la biblioteca matemática, pero no todas. \<cmath> definía las sobrecargas restantes por lo que, para obtener todas las sobrecargas, era necesario incluir el encabezado \<cmath>. Esto causaba problemas con la resolución de sobrecargas de función en el código que solo incluía \<math.h>. Ahora, todas las sobrecargas de C++ se han quitado de \<math.h> y solo están presentes en \<cmath>.

   Para resolver errores, incluya \<cmath> para obtener las declaraciones de las funciones que se quitaron de \<math.h>. En la tabla siguiente se muestran las funciones que se han movido.

   Funciones movidas:

   - double abs(double) y float abs(float)

   - double pow(double, int), float pow(float, float), float pow(float, int), long double pow(long double, long double), long double pow(long double, int)

   - float y versiones long double de funciones de punto flotante acos, acosh, asin, asinh, atan, atanh, atan2, cbrt, ceil, copysign, cos, cosh, erf, erfc, exp, exp2, expm1, fabs, fdim, floor, fma, fmax, fmin, fmod, frexp, hypot, ilogb, ldexp, lgamma, llrint, llround, log, log10, log1p, log2, lrint, lround, modf, nearbyint, nextafter, nexttoward, remainder, remquo, rint, round, scalbln, scalbn, sin, sinh, sqrt, tan, tanh, tgamma, trunc

   Si tiene código que use abs con un tipo de punto flotante que solo incluya el encabezado math.h, las versiones de punto flotante ya no estarán disponibles, por lo que la llamada, incluso con un argumento de punto flotante, se resuelve ahora como abs(int). Esto produce el error:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

   La solución para esta advertencia es reemplazar la llamada a `abs` por una versión de punto flotante de `abs`, como `fabs` para un argumento de tipo double o `fabsf` para un argumento de tipo float, o incluir el encabezado cmath y seguir usando `abs`.

- **Conformidad de punto flotante**

   Se han introducido muchos cambios en la biblioteca matemática para mejorar la conformidad con las especificaciones IEEE-754 y el anexo F de C11 con respecto a entradas de casos especiales como infinitos y valores NaN. Por ejemplo, las entradas de valores NaN simples, que a menudo se trataban como errores en las versiones anteriores de la biblioteca, ya no se consideran como tales. Consulte el [estándar IEEE 754](http://grouper.ieee.org/groups/754) y el anexo F del [estándar C11](http://www.iso-9899.info/wiki/The_Standard).

   Estos cambios no provocarán errores en tiempo de compilación, pero pueden hacer que los programas se comporten de manera diferente y más correcta según el estándar.

- **FLT_ROUNDS**

   En Visual Studio 2013, la macro FLT_ROUNDS se expandía a una expresión constante, lo cual era incorrecto porque el modo de redondeo es configurable en tiempo de ejecución, por ejemplo, al llamar a fesetround. La macro FLT_ROUNDS ahora es dinámica y refleja correctamente el modo de redondeo actual.

#### <a name="new-and-newh"></a>\<new> y \<new.h>

- **new y delete**

   En versiones anteriores de la biblioteca, las funciones new y delete del operador definido por la implementación se exportaban desde la DLL de la biblioteca en tiempo de ejecución (por ejemplo, msvcr120.dll). Ahora, estas funciones de operador siempre se vinculan estáticamente en los archivos binarios, incluso cuando se usan las DLL de la biblioteca en tiempo de ejecución.

   Esto no supone un cambio importante del código nativo o mixto (`/clr`); en cambio, para código compilado como [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md), puede provocar que este no se compile. Si compila código como `/clr:pure`, quizá deba agregar `#include <new>` o `#include <new.h>` para evitar los errores de compilación debidos a este cambio. Tenga en cuenta que `/clr:pure` está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017. El código que tenga que ser puro se debe portar a C#.

#### <a name="processh"></a>\<process.h>

- **_beginthread y _beginthreadex**

   Las funciones [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) y [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) ahora contienen una referencia al módulo donde se define el procedimiento de subproceso para la duración del subproceso. Esto ayuda a garantizar que los módulos no se descargan hasta que un subproceso se ejecuta hasta su finalización.

#### <a name="stdargh"></a>\<stdarg.h>

- **va_start y tipos de referencia**

   Cuando se compila código C++, [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) ahora valida en tiempo de compilación que el argumento que se le pasa no es de tipo de referencia. Los argumentos de tipo de referencia están prohibidos por el estándar de C++.

#### <a name="stdioh-and-conioh"></a>\<stdio.h> y \<conio.h>

- **Las familias de funciones printf y scanf se definen ahora insertadas.**

   Las definiciones de todas las funciones printf y scanf se han insertado en \<stdio.h>, \<conio.h> y otros encabezados de CRT. Se trata de una novedad importante que lleva a un error del vinculador (LNK2019, símbolo externo sin resolver) en todos los programas que declaran localmente estas funciones sin incluir los encabezados de CRT apropiados. Si es posible, actualice el código para incluir los encabezados de CRT (es decir, agregue `#include <stdio.h>`) y las funciones insertadas. Si prefiere no modificar el código para incluir estos archivos de encabezado, una solución alternativa es agregar una biblioteca adicional a su entrada de enlazador, legacy_stdio_definitions.lib.

   Para agregar esta biblioteca a la entrada de vinculador en el IDE, abra el menú contextual del nodo de proyecto y elija **Propiedades**. A continuación, en el cuadro de diálogo **Propiedades del proyecto** , seleccione **Vinculador**, y edite **Entrada del vinculador** para agregar `legacy_stdio_definitions.lib` a la lista separada por signos de punto y coma.

   Si el proyecto está vinculado a bibliotecas estáticas compiladas con una versión de Visual Studio anterior a la 2015, el enlazador podría informar de un símbolo externo sin resolver. Estos errores pueden hacer referencia a las definiciones de stdio internas de _iob, _iob_func o a importaciones relacionadas para determinadas funciones de stdio en formato _imp\_*. Microsoft recomienda que, al actualizar un proyecto, recompile todas las bibliotecas estáticas con la versión más reciente del compilador y las bibliotecas de C++. Si se trata de una biblioteca de terceros cuyo origen no está disponible, solicite al autor un binario actualizado o encapsule su uso de la biblioteca en un archivo DLL independiente que luego pueda compilar con la versión anterior del compilador y las bibliotecas.

    > [!WARNING]
    > Si se vincula con el SDK de Windows 8.1 o con versiones anteriores, es posible encontrar estos errores de símbolo externo sin resolver. En ese caso, debe resolver el error agregando legacy_stdio_definitions.lib a la entrada de vinculador tal como se describió anteriormente.

   Para solucionar errores de símbolo sin resolver, puede probar a usar [dumpbin.exe](../build/reference/dumpbin-reference.md) para examinar los símbolos definidos en un archivo binario. Pruebe la siguiente línea de comandos para ver los símbolos definidos en una biblioteca.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **gets y _getws**

   Las funciones [gets](../c-runtime-library/gets-getws.md) y [_getws](../c-runtime-library/gets-getws.md) se han quitado. La función gets se quitó de la biblioteca estándar de C en C11 porque su uso no es seguro. La función _getws era una extensión de Microsoft que equivalía a gets, pero para cadenas de caracteres anchos. Como alternativa a estas funciones, puede usar [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md) y [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets y _cgetws**

   Las funciones [_cgets](../c-runtime-library/cgets-cgetws.md) y [_cgetws](../c-runtime-library/cgets-cgetws.md) se han quitado. Como alternativa a estas funciones, puede usar [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) y [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Formato de Infinity y NaN**

   En versiones anteriores, los valores infinitos y NaN adoptaban el formato mediante un conjunto de cadenas centinela específicas de MSVC.

   - Infinito: 1.#INF

   - NaN simple: 1. #QNAN

   - NaN de señalización: 1.#SNAN

   - NaN indefinido: 1.#IND

   Cualquiera de estas cadenas podía prefijarse con un signo y tener un formato ligeramente diferente según el ancho de campo y la precisión (a veces con efectos inusuales, p. ej., `printf("%.2f\n", INFINITY)` imprimía 1.#J porque #INF se "redondeaba" a una precisión de dos dígitos). C99 introdujo nuevos requisitos en el formato de los valores infinitos y NaN. La implementación de MSVC ahora cumple estos requisitos. Las nuevas cadenas son las siguientes:

   - Infinito: inf

   - NaN simple: nan

   - NaN de señalización: nan(snan)

   - NaN indefinido: nan(ind)

   Cualquiera de ellas puede ir precedida por un signo. Si se usa un especificador de formato en mayúscula (%F en lugar de %f), las cadenas se imprimen en mayúscula (INF en lugar de inf), según sea necesario.

   Las funciones [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) se han modificado para analizar estas nuevas cadenas de manera que harán un recorrido de ida y vuelta a través de printf y scanf.

- **Formato y análisis de punto flotante**

   Se han introducido nuevos algoritmos de análisis y formato de punto flotante para mejorar la corrección. Este cambio afecta a las familias de funciones [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) y [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), además de a otras funciones como [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Los algoritmos de formato anteriores generaban únicamente un número limitado de dígitos y rellenaban con cero el resto de posiciones decimales. Esto suele bastar para generar cadenas que hagan un recorrido de ida y vuelta hasta al valor de punto flotante original, pero no si se desea que el valor sea exacto (o la representación decimal más cercana al mismo). Los nuevos algoritmos de formato generan tantos dígitos como sea necesario para representar el valor (o para rellenar la precisión especificada). Como ejemplo de la mejora, considere los resultados cuando se imprime una gran potencia de dos:

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

    ```Output
        Old:  1208925819614629200000000    New:  1208925819614629174706176
    ```

   Los algoritmos de análisis antiguos solo tenían en cuenta un máximo de 17 dígitos significativos de la cadena de entrada y descartaban el resto de los dígitos. Esto es suficiente para generar una aproximación muy precisa del valor representado por la cadena y el resultado suele acercarse mucho al resultado redondeado correctamente. La nueva implementación tiene en cuenta todos los dígitos presentes y genera el resultado redondeado correctamente para todas las entradas (hasta 768 dígitos de longitud). Además, estas funciones ahora respetan el modo de redondeo (que se puede controlar a través de fesetround).  Este es un cambio de comportamiento potencialmente importante porque estas funciones pueden generar resultados diferentes. Los nuevos resultados siempre son más correctos que los resultados anteriores.

- **Análisis de punto flotante de hexadecimal e infinity/NaN**

   Los algoritmos de análisis de punto flotante ahora analizan cadenas hexadecimales de punto flotante (como las generadas por los especificadores de formato de printf %a y %A) y todas las cadenas infinity y NaN generadas por las funciones `printf`, como se describió anteriormente.

- **Relleno de ceros a la izquierda de %A y %a**

   Los especificadores de formato %a y %A dan formato a un número de punto flotante como mantisa hexadecimal y exponente binario. En versiones anteriores, las funciones de `printf` rellenaban con ceros las cadenas de manera incorrecta. Por ejemplo, `printf("%07.0a\n", 1.0)` imprimía 00x1p+0, cuando debería imprimir 0x01p+0. Esto se ha solucionado.

- **Precisión de %A y %a**

   La precisión predeterminada de los especificadores de formato %A y %a era de 6 en versiones anteriores de la biblioteca. La precisión predeterminada es ahora de 13, de conformidad con el estándar de C.

   Se trata de un cambio de comportamiento en tiempo de ejecución en la salida de cualquier función que usa una cadena de formato con %A o %a. En el comportamiento anterior, la salida que usaba el especificador %A podía ser “1.1A2B3Cp+111”. Ahora, la salida para el mismo valor es “1.1A2B3C4D5E6F7p+111”. Para obtener el comportamiento anterior, puede especificar la precisión, por ejemplo, %.6A. Consulte [Especificación de precisión](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **Especificador %F**

   Ahora se admite el especificador de formato/conversión %F. Es funcionalmente equivalente al especificador de formato %f, salvo que el formato de los valores infinitos y NaN es con letras mayúsculas.

   En versiones anteriores, la implementación solía analizar F y N como modificadores de longitud. Este comportamiento se remontaba a la época de los espacios de direcciones segmentados: estos modificadores de longitud se usaban para indicar punteros far y near, respectivamente, como en %Fp o %Ns. Este comportamiento se ha eliminado. Si se encuentra %F, ahora se trata como el especificador de formato %F; si se encuentra %N, ahora se trata como un parámetro no válido.

- **Formato de exponente**

   Los especificadores de formato %e y %E dan formato a un número de punto flotante como mantisa decimal y exponente. En algunos casos, los especificadores de formato %g y %G también dan este formato a los números. En versiones anteriores, CRT generaba siempre las cadenas con exponentes de tres dígitos. Por ejemplo, `printf("%e\n", 1.0)` imprimía 1.000000e+000. Ese comportamiento era incorrecto: C exige que si el exponente solo se puede representar mediante uno o dos dígitos, entonces solo se imprimirán dos dígitos.

   En Visual Studio 2005 se agregó un modificador de conformidad global: [_set_output_format](../c-runtime-library/set-output-format.md). Un programa podía llamar a esta función con el argumento _TWO_DIGIT_EXPONENT, para habilitar la impresión de exponentes conforme a los estándares. El comportamiento predeterminado se ha cambiado al modo de impresión de exponentes conforme a los estándares.

- **Validación de cadenas de formato**

   En versiones anteriores, las funciones printf y scanf aceptaban en modo silencioso muchas cadenas de formato no válido, a veces con efectos inesperados. Por ejemplo, %hlhlhld se trataba como %d. Ahora, todas las cadenas de formato no válido se tratan como parámetros no válidos.

- **Validación de cadenas de modo fopen**

   En versiones anteriores, la familia de funciones fopen aceptaba en modo silencioso algunas cadenas de modo no válido (por ejemplo, r+b+). Ahora, las cadenas de modo no válido se consideran como parámetros no válidos.

- **Modo _O_U8TEXT**

   La función [_setmode](../c-runtime-library/reference/setmode.md) ahora informa correctamente del modo de flujos abiertos en modo _O_U8TEXT. En versiones anteriores de la biblioteca, informaba de que dichos flujos se abrían en _O_WTEXT.

   Se trata de una novedad importante si su código interpreta el modo _O_WTEXT para los flujos en que la codificación es UTF-8. Si su aplicación no es compatible con UTF_8, considere la posibilidad de agregar compatibilidad con esta codificación cada vez más común.

- **snprintf y vsnprintf**

   Las funciones [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) y [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) están ahora implementadas. A menudo, el código anterior proporcionaba versiones de macro de definiciones de estas funciones porque la biblioteca CRT no las implementaba, pero ya no son necesarias en las versiones más recientes. Si [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) o [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) se definen como una macro antes de incluir \<stdio.h>, la compilación produce un error que indica dónde estaba definida la macro.

   Normalmente, la solución a este problema consiste en eliminar todas las declaraciones de `snprintf` o `vsnprintf` en el código de usuario.

- **tmpnam genera nombres de archivo utilizables**

   En versiones anteriores, las funciones `tmpnam` y `tmpnam_s` generaban nombres de archivo en la raíz de la unidad (por ejemplo, \sd3c.). Estas funciones generan ahora rutas de nombre de archivo utilizables en un directorio temporal.

- **Encapsulación FILE**

   En versiones anteriores, FILE estaba totalmente definido en \<stdio.h>, por lo que el código de usuario podía obtener acceso a FILE y modificar sus elementos internos. La biblioteca stdio se ha cambiado para ocultar los detalles de implementación. Como parte de esto, FILE tal como se define en \<stdio.h> es ahora un tipo opaco y sus miembros son inaccesibles desde fuera de la propia biblioteca CRT.

- **_outp e _inp**

   Las funciones [_outp](../c-runtime-library/outp-outpw-outpd.md), [_outpw](../c-runtime-library/outp-outpw-outpd.md), [_outpd](../c-runtime-library/outp-outpw-outpd.md), [_inp](../c-runtime-library/inp-inpw-inpd.md), [_inpw](../c-runtime-library/inp-inpw-inpd.md) e [_inpd](../c-runtime-library/inp-inpw-inpd.md) se han quitado.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>, \<malloc.h> y \<sys/stat.h>

- **strtof y wcstof**

   Las funciones `strtof` y `wcstof` no podían establecer errno en ERANGE si el valor no era representable como un float. Esto se ha solucionado. (Observe que este error era específico de estas dos funciones; las funciones `strtod`, `wcstod`, `strtold` y `wcstold` no se veían afectadas). Se trata de una novedad importante en tiempo de ejecución.

- **Funciones de asignación alineadas**

   En versiones anteriores, las funciones de asignación alineadas (`_aligned_malloc`, `_aligned_offset_malloc`, etc.) aceptaban de modo silencioso las solicitudes para un bloque de alineación 0. La alineación solicitada debe ser una potencia de dos, y cero no lo es. Esto se ha corregido. Ahora, una alineación solicitada de 0 se trata como un parámetro no válido. Se trata de una novedad importante en tiempo de ejecución.

- **Funciones de montón**

   Las funciones `_heapadd`, `_heapset` y `_heapused` se han quitado. Estas funciones dejaron de ser funcionales cuando el CRT se actualizó para usar el montón de Windows.

- **smallheap**

   La opción de vínculo `smalheap` se ha quitado. Consulte [Opciones de vínculo](../c-runtime-library/link-options.md).

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   La firma de la función `wcstok` se cambió para que coincida con los requisitos del estándar de C. En versiones anteriores de la biblioteca, la firma de esta función era:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Usaba un contexto interno por subproceso para realizar un seguimiento del estado a través de las llamadas, como se hace para `strtok`. La función ahora tiene la firma `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)` y requiere que el llamador pase el contexto como un tercer argumento a la función.

   Se ha agregado una nueva función `_wcstok` con la firma anterior para facilitar la portabilidad. Al compilar código de C++, también hay una sobrecarga en línea del `wcstok` que tiene la firma anterior. Esta sobrecarga se declara en desuso. En el código de C, puede definir _CRT_NON_CONFORMING_WCSTOK para que `_wcstok` se use en lugar de `wcstok`.

#### <a name="timeh"></a>\<time.h>

- **clock**

   En versiones anteriores, la función [clock](../c-runtime-library/reference/clock.md) se implementa mediante la API de Windows [GetSystemTimeAsFileTime](https://msdn.microsoft.com/library/windows/desktop/ms724397.aspx). Con esta implementación, la función clock era sensible a la hora del sistema y no era necesariamente monotónica. La función clock se ha implementado de nuevo en términos de [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) y ahora es monotónica.

- **fstat y _utime**

   En versiones anteriores, las funciones [_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) y [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) controlaban el horario de verano de manera incorrecta. Antes de Visual Studio 2013, todas estas funciones ajustaban incorrectamente las horas del horario estándar como si estuvieran en el horario de verano.

   En Visual Studio 2013, el problema se solucionó en la familia de funciones **_stat**, pero no se corrigieron los problemas similares en las familias de funciones **fstat** y **_utime**. Esto provoca problemas debido a la incoherencia entre las funciones. Las familias de funciones **fstat** y **_utime** ya se han corregido, por lo que todas estas funciones controlan ahora el horario de verano de manera correcta y coherente.

- **asctime**

   En versiones anteriores, la función [asctime](../c-runtime-library/reference/asctime-wasctime.md) rellenaba los días de un dígito con un cero inicial, por ejemplo: Vie Jun 06 08:00:00 2014. La especificación requiere que estos días se rellenen con un espacio inicial, por ejemplo: vie jun  6 08:00:00 2014. Esto se ha solucionado.

- **strftime y wcsftime**

   Ahora, las funciones `strftime` y `wcsftime` admiten los especificadores de formato %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u y %V. Además, los modificadores E y O se analizan, pero se ignoran.

   El especificador de formato %c se especifica como la producción de una “representación de fecha y hora adecuada” para la configuración regional actual. En la configuración regional de C, esta representación debe ser la misma que %a %b %e %T %Y. Se trata de la misma forma producida por asctime. En versiones anteriores, el especificador de formato %c representaba incorrectamente las horas con un formato MM/DD/YY HH:MM:SS. Esto se ha solucionado.

- **timespec y TIME_UTC**

   Ahora, el encabezado \<time.h> define el tipo `timespec` y la función `timespec_get` a partir del estándar de C11. Además, ahora está definida la macro TIME_UTC para su uso con la función `timespec_get`. Se trata de una novedad importante para el código que tiene una definición que está en conflicto con alguna de estas funciones.

- **CLOCKS_PER_SEC**

   La macro CLOCKS_PER_SEC ahora se expande a un entero de tipo `clock_t`, tal como exige el lenguaje C.

####  <a name="BK_STL"></a> Biblioteca estándar de C++
Para habilitar nuevas optimizaciones y comprobaciones de depuración, la implementación de Visual Studio de la Biblioteca estándar de C++ interrumpe deliberadamente la compatibilidad binaria de una versión a la siguiente. Por consiguiente, cuando se utiliza la Biblioteca estándar de C++, los archivos de objetos y las bibliotecas estáticas que se han compilado con versiones diferentes no se pueden combinar en un binario (EXE o DLL), y los objetos de la Biblioteca estándar de C++ no se pueden pasar entre los archivos binarios que se han compilado con versiones diferentes. Una combinación de este estilo emite errores del vinculador sobre discordancias _MSC_VER. (_MSC_VER es la macro que contiene la versión principal del compilador, por ejemplo, 1800 para Visual Studio 2013). Esta comprobación no detecta la combinación de archivos DLL ni otras que impliquen Visual Studio 2008 o versiones anteriores.

- **La biblioteca estándar de C++ incluye archivos**

   Algunos cambios se realizaron en la estructura include en los encabezados de la biblioteca estándar de C++. Los encabezados de la biblioteca estándar de C++ pueden incluirse entre sí de maneras no especificadas. En general, debe escribir el código para que incluya todos los encabezados necesarios según el estándar de C++ y que no se base en las inclusiones mutuas entre encabezados de bibliotecas estándar de C++. Con esto se logra que el código sea portable entre versiones y plataformas. Al menos dos de los cambios de encabezado en Visual Studio 2015 afectan al código de usuario. En primer lugar, \<string> ya no incluye \<iterator>. En segundo lugar, ahora \<tuple> declara `std::array` sin incluir todas las \<array>. Esto puede dañar el código a través de la siguiente combinación de construcciones de código: el código tiene una variable denominada “array” y tiene una directiva using “using namespace std;” y se incluye un encabezado de biblioteca estándar de C++ (por ejemplo, \<functional>) que incluye \<tuple>, que ahora declara `std::array`.

- **steady_clock**

   La implementación de \<chrono> de [steady_clock](../standard-library/steady-clock-struct.md) ha cambiado para cumplir los requisitos del estándar de C++ en cuanto a estabilidad y monotonía. `steady_clock` ahora se basa en [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) y `high_resolution_clock` ahora es un typedef para `steady_clock`. Como resultado, en Visual Studio `steady_clock::time_point` es ahora un typedef para `chrono::time_point<steady_clock>`; sin embargo, esto no es necesariamente así en otras implementaciones.

- **asignadores y const**

   Ahora es necesario que las comparaciones de igualdad y desigualdad de asignadores acepten argumentos const en ambos lados.  Si sus asignadores definen estos operadores del modo siguiente:

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   Debe actualizar estos elementos para declararlos como miembros const.

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **elementos const**

   El estándar de C++ siempre ha prohibido contenedores de elementos const (como vector\<const T> o set\<const T>). En Visual Studio 2013 y versiones anteriores sí se aceptaban dichos contenedores. En la versión actual, estos contenedores no se compilan.

- **std::allocator::deallocate**

   En Visual Studio 2013 y versiones anteriores, `std::allocator::deallocate(p, n)` ignoraba el argumento pasado para *n*.  El estándar de C++ siempre ha requerido que *n* sea igual que el valor pasado como primer argumento a la invocación de allocate que devuelve *p*. Sin embargo, en la versión actual, se inspecciona el valor de *n*. El código que pasa argumentos para *n* que difieren de lo que el estándar requiere puede bloquearse en tiempo de ejecución.

- **hash_map y hash_set**

   Los archivos de encabezado no estándar hash_map y hash_set han quedado en desuso en Visual Studio 2015 y se eliminarán en una versión futura. En su lugar, use unordered_map y unordered_set.

- **comparadores y operator()**

   Los contenedores asociativos (la familia \<map>) ahora exigen que sus comparadores tengan operadores de llamada de función invocables por constructores. Este código de declaración de clase de comparador ahora no se puede compilar:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Para resolver este error, cambie la declaración de función a:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **rasgos de tipos**

   Se han quitado los nombres anteriores de rasgos de tipos (type traits) de una versión anterior del proyecto de estándar de C++. Se cambiaron en C++11 y se han actualizado a los valores de C++11 en Visual Studio 2015. En la tabla siguiente se muestran los nombres anteriores y los nuevos.

   |Nombre anterior|Nuevo nombre|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **Directivas launch::any y launch::sync**

   Las directivas `launch::any` y `launch::sync` no estándar se han quitado. En su lugar, utilice `launch:async | launch:deferred` para `launch::any`. Para `launch::sync`, use `launch::deferred`. Consulte [Launch (enumeración)](../standard-library/future-enums.md#launch).

####  <a name="BK_MFC"></a> MFC y ATL

- **Microsoft Foundation Classes (MFC)**

   ya no se incluye en la instalación “típica” de Visual Studio por su gran tamaño. Para instalar MFC, elija la opción de instalación **personalizada** en el programa de instalación de Visual Studio 2015. Si ya tiene instalado Visual Studio 2015 y desea instalar MFC, vuelva a ejecutar el programa de instalación de **Visual Studio**, elija la opción de instalación **personalizada** y elija **Microsoft Foundation Classes**. Puede volver a ejecutar el programa de instalación de **Visual Studio** desde el **Panel de control**, **Programas y características**, o desde el medio de instalación.

   El paquete redistribuible de Visual C++ todavía incluye esta biblioteca.

####  <a name="BK_ConcRT"></a> Runtime de simultaneidad

- **Macro Yield de Windows.h en conflicto con concurrency::Context::Yield**

   El Runtime de simultaneidad usaba anteriormente `#undef` para anular las definiciones de la macro Yield a fin de evitar conflictos entre la macro Yield definida en Windows.hh y la función `concurrency::Context::Yield`. Se ha quitado `#undef` y se ha agregado una nueva llamada de API equivalente que no crea un conflicto: [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution). Para evitar conflictos con Yield, puede actualizar el código para llamar a la función `YieldExecution` o incluya el nombre de la función `Yield` entre paréntesis en los sitios de llamada, como en el ejemplo siguiente:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Mejoras de conformidad del compilador en Visual Studio 2015

Al actualizar código de versiones anteriores, es posible que también se produzcan errores del compilador causados por las mejoras de conformidad de Visual Studio 2015. Estas mejoras no anulan la compatibilidad binaria de versiones anteriores de Visual Studio, pero puede haber errores del compilador que antes no se producían. Para obtener más información, consulte [Visual C++ What's New 2003 through 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md) (Novedades de Visual C++ desde 2003 hasta 2015).

En Visual Studio 2015, las mejoras continuas en la conformidad del compilador a veces pueden cambiar cómo este entiende el código fuente existente. Cuando esto sucede, pueden producirse errores nuevos o diferentes durante la compilación o puede haber incluso diferencias de comportamiento en el código previamente compilado que parecía ejecutarse correctamente.

Afortunadamente, estas diferencias tienen poco o ningún efecto en la mayoría del código fuente y cuando se necesitan código fuente u otros cambios para resolver estas diferencias, las correcciones suelen ser pequeñas y sencillas. Hemos incluido muchos ejemplos de código fuente previamente aceptable que es posible que deba cambiarse *(antes)* y las revisiones para corregirlos *(después)*.

Aunque estas diferencias pueden afectar a su código fuente u otros artefactos de compilación, no afectan a la compatibilidad binaria entre actualizaciones de versiones de Visual Studio. Un tipo de cambio más drástico, el *cambio importante*, puede afectar a la compatibilidad binaria, pero este tipo de alteraciones de compatibilidad binaria solo se producen entre las versiones principales de Visual Studio. Por ejemplo, entre Visual Studio 2013 y Visual Studio 2015. Para obtener más información sobre los cambios importantes que se han producido entre Visual Studio 2013 y Visual Studio 2015, consulte [Cambios de conformidad de Visual Studio 2015](#VC_2015).

- [Mejoras de conformidad en Visual Studio 2015](#VS_RTM)

- [Mejoras de conformidad en Update 1](#VS_Update1)

- [Mejoras de conformidad en Update 2](#VS_Update2)

- [Mejoras de conformidad en Update 3](#VS_Update3)

###  <a name="VS_RTM"></a> Mejoras de conformidad en Visual Studio 2015

- /Zc:forScope- (opción)

   La opción del compilador `/Zc:forScope-` está en desuso y se quitará en una próxima versión.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Esta opción solía usarse para que el código no estándar que usa las variables de bucle se pudiese usar después del punto donde, según el estándar, debería quedar fuera del ámbito. Solo era necesario al compilar con la opción `/Za`, ya que sin `/Za`, siempre se permite usar una variable de bucle for tras el final del bucle. Si no le interesa el cumplimiento de los estándares (por ejemplo, si su código no está destinado a otros compiladores), puede desactivar la opción `/Za` (o establecer la propiedad **Deshabilitar extensiones de lenguaje** en **No**). Si le interesa escribir código portable y compatible con los estándares, debe volver a escribir el código de modo que se ajuste a la norma. Para ello, mueva la declaración de dichas variables a un punto fuera del bucle.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- Opción del compilador `/Zg`

   La opción de compilador `/Zg` (Generar prototipos de función) ya no está disponible. Esta opción del compilador quedó en desuso anteriormente.

- Ya no se pueden ejecutar pruebas unitarias con C++/CLI desde la línea de comandos con mstest.exe. En su lugar, use vstest.console.exe. Consulte [Opciones de la línea de comandos para VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options).

- **Palabra clave mutable**

   El especificador de clase de almacenamiento **mutable** ya no se permite en lugares donde anteriormente se compilaba sin errores. Ahora, el compilador produce el error C2071 (clase de almacenamiento no válida). Según el estándar, el especificador **mutable** solo puede aplicarse a los nombres de miembros de datos de clase; no puede aplicarse a los nombres declarados como const o static y tampoco para hacer referencia a los miembros.

   Por ejemplo, considere el siguiente código:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Las versiones anteriores del compilador aceptaban esto, pero ahora el compilador produce el siguiente error:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Para corregir el error, basta con quitar la palabra clave **mutable** redundante.

- **char_16_t y char32_t**

   Ya no puede usar `char16_t` o `char32_t` como alias en una definición de tipo (**typedef**), ya que estos tipos ahora se consideran integrados. Era habitual que los usuarios y creadores de bibliotecas definieran `char16_t` y `char32_t` como alias de `uint16_t` y `uint32_t`, respectivamente.

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   Para actualizar el código, quite las declaraciones **typedef** y cambie el nombre de todos los identificadores que estén en conflicto con estos nombres.

- **Parámetros de plantilla sin tipo**

   Hay determinado código que implica parámetros de plantilla sin tipo en el que ahora se comprueba la compatibilidad de tipos cuando se proporcionan argumentos de plantilla explícitos. Por ejemplo, el código siguiente se compilaba sin errores en las versiones anteriores de Visual Studio.

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   El compilador actual produce correctamente un error, porque el tipo de parámetro de plantilla no coincide con el argumento de plantilla (el parámetro es un puntero a miembro const, pero la función f no es const):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Para solucionar este error en el código, asegúrese de que el tipo del argumento de la plantilla que está usando coincide con el tipo declarado del parámetro de plantilla.

- **__declspec(align)**

   El compilador ya no acepta `__declspec(align)` en las funciones. Esto siempre se ignoraba, pero ahora produce un error del compilador.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Para solucionar este problema, quite `__declspec(align)` de la declaración de función. Puesto que no tenía ningún efecto, el hecho de quitarlo no cambia nada.

- **Control de excepciones**

   Hay un par de cambios en el control de excepciones. En primer lugar, los objetos de excepción deben poderse copiar o mover. El siguiente código se compila en Visual Studio 2013, pero no en Visual Studio 2015:

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   El problema es que el constructor de copias es privado, por lo que el objeto no se puede copiar como cuando se controla una excepción de la manera habitual. Lo mismo sucede cuando el constructor de copias se declara **explicit**.

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Para actualizar el código, asegúrese de que el constructor de copias correspondiente al objeto de excepción es **público** y no esté marcado como **explicit**.

   Para detectar una excepción por valor, también es necesario que el objeto de excepción se pueda copiar. El siguiente código se compila en Visual Studio 2013, pero no en Visual Studio 2015:

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   Para solucionar este problema, cambie el tipo de parámetro de **catch** a una referencia.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Literales de cadena seguidos de macros**

   El compilador ahora admite literales definidos por el usuario. En consecuencia, los literales de cadena seguidos de macros sin ningún espacio en blanco intermedio se interpretan como literales definidos por el usuario, lo que puede dar lugar a errores o resultados inesperados. Por ejemplo, en los compiladores anteriores el código siguiente se compilaba perfectamente:

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   El compilador interpretaba esto como un literal de cadena “hello” seguido de una macro, expandida en “there” y, a continuación, los dos literales de cadena se concatenaban en uno solo. En Visual Studio 2015, el compilador interpreta esto como un literal definido por el usuario, pero dado que no hay ningún literal coincidente _x definido por el usuario, produce un error.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Para solucionar este problema, agregue un espacio entre el literal de cadena y la macro.

- **Literales de cadena adyacentes**

   Como en el caso anterior, en versiones anteriores de Visual C++ y debido a los cambios relacionados con el análisis de cadenas, los literales de cadena adyacentes (ya fueran literales de cadena de caracteres anchos o estrechos) sin ningún espacio en blanco se interpretaban como una sola cadena concatenada. En Visual Studio 2015, ahora debe agregarse un espacio en blanco entre las dos cadenas. Por ejemplo, el código siguiente debe modificarse:

    ```cpp
    char * str = "abc""def";
    ```

   Simplemente agregue un espacio entre las dos cadenas.

    ```cpp
    char * str = "abc" "def";
    ```

- **Placement new y delete**

   Se ha realizado un cambio en el operador **delete** a fin de adaptarlo al estándar de C++14. Detalles del cambio de los estándares se pueden encontrar en la página de [desasignación de ajuste de tamaño de C++](http://isocpp.org/files/papers/n3778.html). Los cambios agregan un formulario del operador **delete** global que toma un parámetro de tamaño. La novedad es que si antes usaba un operador **delete** con la misma firma (para que se correspondiese con un operador **placement new**), ahora recibirá un error del compilador (C2956, que se produce en el punto donde se usa placement new, ya que es la posición en el código en la que el compilador intenta identificar un operador **delete** coincidente adecuado).

   La función `void operator delete(void *, size_t)` era un operador **placement delete** correspondiente a la función **placement new**  `void * operator new(size_t, size_t)` en C++11. Con la desasignación con tamaño de C ++ 14, esta función delete es ahora una *función de desasignación habitual* (operador **delete** global). Según el estándar, si el uso de placement new busca una función de eliminación correspondiente y encuentra una función de desasignación habitual, el programa tiene un formato incorrecto.

   Supongamos, por ejemplo, que el código define tanto **placement new** como **placement delete**:

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   El problema se produce debido a la coincidencia de las firmas de función entre un operador **placement delete** definido y el nuevo operador global **delete** con tamaño. Analice si puede usar un tipo que no sea `size_t` para los operadores **placement new** y **delete**.  Tenga en cuenta que **typedef** de `size_t` depende del compilador; es un **typedef** para **int sin signo** en Visual C++. Una buena solución es que use un tipo enumerado como el siguiente:

    ```cpp
    enum class my_type : size_t {};
    ```

   A continuación, cambie la definición de **placement new** y **delete** para usar este tipo como el segundo argumento en lugar de `size_t`. También es necesario que actualice las llamadas a placement new para pasar el nuevo tipo (por ejemplo, con `static_cast<my_type>` para convertir a partir del valor entero) y que actualice la definición de **new** y **delete** para realizar la conversión al tipo entero. No es necesario usar **enum** para esto; un tipo de clase con un miembro `size_t` también funcionaría.

   Una solución alternativa es que pueda eliminar por completo **placement new**. Si el código usa **placement new** para implementar un bloque de memoria donde el argumento placement sea el tamaño del objeto que se va a asignar o eliminar, entonces podría usarse la característica de desasignación con tamaño para reemplazar su propio código de bloque de memoria personalizado, y así deshacerse de las funciones placement y usar simplemente su propio operador **delete** de dos argumentos en lugar de las funciones placement.

   Si no quiere actualizar su código de forma inmediata, puede recuperar el comportamiento anterior mediante la opción de compilador `/Zc:sizedDealloc-`. Si usa esta opción, las funciones delete de dos argumentos no existen y no se provocará un conflicto con el operador **placement delete**.

- **Miembros de datos de uniones**

   Los miembros de datos de uniones ya no pueden tener tipos de referencia. El siguiente código se compila en Visual Studio 2013, pero genera un error en Visual Studio 2015.

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   El código anterior produce los errores siguientes:

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   Para solucionar este problema, cambie los tipos de referencia a un puntero o a un valor. Para poder cambiar el tipo a un puntero, hay que hacer cambios en el código que usa el campo union. Si se cambia el código a un valor, también cambian los datos almacenados en la unión, lo que afecta a otros campos, ya que los campos de tipos union comparten la misma memoria. En función del tamaño del valor, también podrá cambiar el tamaño de la unión.

- Ahora, las uniones anónimas se ajustan mejor al estándar. Las versiones anteriores del compilador generaban un constructor y destructor explícitos para uniones anónimas. Estos se eliminan en Visual Studio 2015.

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   El código anterior genera el error siguiente en Visual Studio 2015:

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   Para resolver este problema, proporcione sus propias definiciones del constructor o del destructor.

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **Uniones con estructuras anónimas**

   Para cumplir con el estándar, el comportamiento de runtime ha cambiado para los miembros de estructuras anónimas en uniones. El constructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando se crea este tipo de unión. Además, el destructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando la unión sale del ámbito. Analice el siguiente código, en el que una unión U contiene una estructura anónima que a su vez contiene a un miembro que es una estructura con nombre S que tiene un destructor.

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   En Visual Studio 2013, se llama al constructor de S cuando se crea la unión, y se llama al destructor de S cuando se limpia la pila de la función f. Pero en Visual Studio 2015, no se llama al constructor ni al destructor. El compilador emite una advertencia sobre este cambio de comportamiento.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Para restaurar el comportamiento original, asigne un nombre a la estructura anónima. El comportamiento en tiempo de ejecución de las estructuras no anónima es el mismo, independientemente de la versión del compilador.

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Por otro lado, intente mover el código del constructor y el destructor a funciones nuevas y agregue llamadas a estas funciones desde el constructor y el destructor de la unión.

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **Resolución de plantilla**

   Se han hecho cambios en la resolución de nombres de plantillas. En C++, al pensar en candidatos para la resolución de un nombre, puede darse el caso de que uno o más de los nombres considerados como coincidencias posibles produzcan una creación de instancias de plantilla no válida. Normalmente, estas instancias no válidas no provocan errores del compilador; este principio se conoce como SFINAE (Substitution Failure Is Not An Error).

   Ahora, si SFINAE requiere que el compilador cree una instancia de la especialización de una plantilla de clase, los errores que se producen durante este proceso son errores del compilador. En versiones anteriores, el compilador omitiría esos errores. Por ejemplo, considere el siguiente código:

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   Si usa el compilador actual, obtendrá el siguiente error:

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   Esto se debe a que el punto de la primera invocación de is_base_of de la clase `D` aún no se ha definido.

   En este caso, la solución es no usar los rasgos de tipos (type traits) mientras no se defina la clase. Si mueve las definiciones de `B` y `D` al principio del archivo de código, el error se soluciona. Si las definiciones están en archivos de encabezado, compruebe el orden de las instrucciones include para los archivos de encabezado a fin de asegurarse de que las definiciones de clase se compilan antes de que se usen las plantillas problemáticas.

- **Constructores de copias**

   Tanto en Visual Studio 2013 como en Visual Studio 2015, el compilador genera un constructor de copias para una clase si esa clase tiene un constructor de movimiento definido por el usuario, pero ningún constructor de copias definido por el usuario. En Dev14, este constructor de copias generado implícitamente también se marca como "= delete".

<!--From here to VS_Update1 added 04/21/2017-->

- **main declarado como "C" externo requiere un tipo de valor devuelto.**

   El código siguiente genera ahora C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Para corregir el error, agregue el tipo de valor devuelto:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **typename no se permite en un inicializador de miembro**

   El código siguiente genera ahora C2059.

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   Para corregir el error, quite `typename` del inicializador:

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **La clase de almacenamiento en especializaciones explícitas se omite.**

   En el siguiente código, se omite el especificador de clase de almacenamiento estático.

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **Una constante usada en un elemento static_assert dentro de un aplantilla de clase siempre dará error.**

   El código siguiente provoca que `static_assert` siempre genere error:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Para solucionar este problema, ajuste el valor en un **struct**:

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **Reglas aplicadas para declaraciones adelantadas. (Solo se aplica a C.)**

   El código siguiente produce ahora C2065:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Para corregir el problema, agregue las declaraciones adelantadas adecuadas:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Cumplimiento más coherente de tipos de puntero de función**

   El código siguiente produce ahora C2197:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Llamadas ambiguas a funciones sobrecarfadas**

   El código siguiente produce ahora C266: 'N::bind': llamada ambigua a una función sobrecargada

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   Para corregir el error, puede calificar completamente la llamada a `bind: N::bind(...)`. Sin embargo, si este cambio se manifiesta mediante un identificador sin declarar (C2065), puede ser adecuado corregirlo con una declaración **using** en su lugar.

   Este patrón se produce con frecuencia con ComPtr y otros tipos en el espacio de nombres `Microsoft::WRL`.

- **Corrija la dirección incorrecta de**

   El código siguiente produce ahora C2440:  "=": no se puede convertir de "type *" a "type". Para corregir el error, cambie &(type) por (type) y (&f()) por (f()).

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **El literal de cadena es una matriz constante**

   El código siguiente produce ahora C2664: "void f(void *)": el argumento 1 no se puede convertir de "const char (*)[2]" a "void *".

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Para corregir el error, cambie el tipo de parámetro de función a `const void*`, o bien cambie el cuerpo de `h` para que tenga este aspecto:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **Cadenas UDL C++11**

   El código siguiente produce ahora el error C3688: sufijo literal no válido "L"; no se encontró el operador literal o la plantilla de operador literal ""L'.

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Para corregir el error, cambie el código por esto:

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they are not needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   En el ejemplo anterior, `MACRO` ya no se analiza como dos tokens (una cadena seguida de una macro).  Ahora se analiza como un UDL de token único.  Lo mismo se aplica a L""L"", que se analizó anteriormente como L"" y L"", y que ahora se analiza como L""L y "".

   Las reglas de concatenación de cadenas también se formularon con el estándar, lo que significa que L"a" "b" es equivalente a L"ab". En las ediciones anteriores de Visual Studio no se aceptaba la concatenación de cadenas con un ancho de carácter diferente.

- **Carácter vacío quitado de C++11**

   El código siguiente produce ahora el error C2137: constante de carácter vacío

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Para corregir el error, cambie el código por esto:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **El valor no puede capturar excepciones de MFC porque no se pueden copiar**

   El siguiente código en una aplicación de MFC produce ahora el error C2316: 'D': no se puede capturar porque el destructor o el constructor de copia son inaccesibles o se han eliminado.

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   Para corregir el código, puede cambiar el bloque catch a `catch (const D &)` pero la mejor solución suele ser usar las macros TRY/CATCH de MFC.

- **alignof es ahora una palabra clave**

   El siguiente código produce ahora el error C2332: "clase": falta nombre de etiqueta. Para corregir el código, debe cambiar el nombre de la clase o, si la clase realiza el mismo trabajo que alignof, simplemente sustituya la clase por la nueva palabra clave.

    ```cpp
    class alignof{}
    ```

- **constexpr ahora es una palabra clave**

   El código siguiente produce ahora el error C2059: error de sintaxis: ')'. Para corregir el código, debe cambiar el nombre de las funciones o las variables que se llamen "constexpr".

    ```cpp
    int constexpr() {return 1;}
    ```

- **Los tipos que se pueden mover no pueden ser const**

   Cuando una función devuelve un tipo destinado a moverse, su tipo de valor devuelto no debe ser **const**.

- **Constructores de copia eliminados**

   El código siguiente genera ahora el error C2280 'S::S(S &&)': se está intentando hacer referencia a una función eliminada:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Para corregir el error, use la inicialización directa para `S2`:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Conversión a puntero de función solo generada cuando no hay captura lambda**

   El código siguiente produce el error C2664 en Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Para corregir el error, quite `=` de la lista de captura.

- **Llamadas ambiguas que afectan a operadores de conversión**

   El código siguiente produce ahora el error C2440: "conversión de tipo": no se puede convertir de "S2" a "S1":

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   Para corregir el error, debe llamar explícitamente al operador de conversión:

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   El código siguiente produce ahora el error C2593: "operador =" es ambiguo:

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   Para corregir el error, debe llamar explícitamente al operador de conversión:

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Corregir inicialización de copia no válida en inicialización de miembro no estático (NSDMI)**

   El código siguiente genera ahora el error C2664: "S1::S1(S1 &&)": no se puede convertir el argumento 1 de "bool" a "const S1 &":

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Para corregir el error, use la inicialización directa:

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Acceso a constructores dentro de instrucciones decltype**

   El código siguiente genera ahora el error C2248: "S::S": no se puede acceder al miembro privado declarado en la clase "S":

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   Para corregir el error, agregue una declaración friend para `S2` en `S`:

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **El constructor predeterminado de lambda se ha eliminado implícitamente**

   El código siguiente produce ahora el error C3497: no puede construir una instancia de una expresión lambda:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Para corregir el error, elimine la necesidad de llamar al constructor predeterminado. Si la expresión lambda no captura nada, se puede convertir en un puntero de función.

- **Expresiones lambda con un operador de asignación eliminado**

   El código siguiente produce ahora el error C2280:

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   Para corregir el error, reemplace la expresión lambda por una clase functor o elimine la necesidad de usar el operador de asignación.

- **Se está intentando mover un objeto con constructor de copia eliminado**

   El código siguiente produce ahora el error C2280: "'moveable::moveable(const moveable &)":  se está intentando hacer referencia a una función eliminada

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   Para resolver el error, use `std::move` en su lugar:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **La clase local no puede hacer referencia a otra clase local definida posteriormente en la misma función**

   El código siguiente produce ahora el error C2079: "s" usa struct "main::S2" sin definir.

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   Para corregir el error, mueva arriba la definición de `S2`:

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **No se puede llamar a un ctor base protegido en el cuerpo de ctor derivado.**

   El código siguiente produce ahora el error C2248: "S1::S1": no se puede acceder al miembro protegido declarado en la clase "S1"

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   Para corregir el error, en `S2`, quite la llamada a `S1()` desde el constructor y, si es necesario, colóquela en otra función.

- **{} impide la conversión a puntero**

   El código siguiente produce ahora el error C2439 "S::p": no se pudo inicializar el miembro

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Para corregir el error, quite las llaves de alrededor de `0`, o bien use en su lugar **nullptr**, como se muestra en este ejemplo:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Definición incorrecta de macro y uso con paréntesis**

   El código siguiente produce ahora el error C2008: ";": no se esperaba en la definición de macro

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Para corregir el problema, cambie la línea superior a `#define A();`.

   El código siguiente produce el error C2059: error de sintaxis: ")"

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Para corregir el código, quite el espacio entre A y ().

   El código siguiente genera el error C2091: la función devuelve una función:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Para corregir el error, quite los paréntesis después DECLARE en S: `DECLARE;`.

   El código siguiente produce el error C2062: tipo "int" inesperado

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Para corregir el problema, defina `A` de la siguiente manera:

    ```cpp
    #define A int
    ```

- **Paréntesis adicionales en las declaraciones**

   El código siguiente produce el error C2062: tipo "int" inesperado

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Para corregir el error, quite los paréntesis de `j`. Si los paréntesis son necesarios por motivos de claridad, use entonces **typedef**.

- **Constructores generados por el compilador y __declspec(novtable)**

   En Visual Studio 2015, existe una mayor probabilidad de que los constructores generados por el compilador insertados de clases abstractas con clases base virtuales puedan exponer el uso inadecuado de `__declspec(novtable)` cuando se emplea en combinación con `__declspec(dllimport)`.

- **auto requiere una sola expresión en direct-list-initialization**

   El código siguiente produce ahora el error C3518: "testPositions": en un contexto de inicialización de lista directa, el tipo para "auto" solo se puede deducir a partir de una sola expresión de inicializador

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Para corregir el error, una posibilidad es inicializar `testPositions` de la manera siguiente:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Comprobación de tipos frente a punteros a tipos de is_convertible**

   El código siguiente provoca ahora que la aserción estática produzca error.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Para corregir el error cambie `static_assert` para que compare los punteros a `D` y `B2`:

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **las declaraciones declspec(novtable) deben ser coherentes**

   Las declaraciones **declspec** deben ser coherentes en todas las bibliotecas. El siguiente código producirá ahora una infracción de regla ahora producirá una infracción de una regla de definición (ODR):

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

###  <a name="VS_Update1"></a> Mejoras de conformidad en Update 1

- **Clases base virtuales privadas y herencia indirecta**

   Las versiones anteriores del compilador permiten una clase derivada para llamar a funciones de miembro de sus clases base *derivadas indirectamente*`private virtual` . Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2280 como resultado.

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   Ejemplo (antes)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   Ejemplo (después)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   O bien

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Operador new y operador delete sobrecargados**

   Las versiones anteriores del compilador permitieron que **operator new** no miembro y **operator delete** no miembro se declarasen como static y que se declararan en espacios de nombres distintos del espacio de nombres global.  Este comportamiento anterior provocó el riesgo de que el programa no llamaba a la implementación del operador **new** o **delete** tal y como estaba diseñada por el programador, lo que daba lugar a un comportamiento en tiempo de ejecución incorrecto silencioso. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2323 en su lugar.

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   Ejemplo (antes)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   Ejemplo (después)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   Además, aunque el compilador no ofrece un diagnóstico específico, se considera que el operador en línea **nuevo** está mal formado.

- **Llamada a "operator *type*()" (conversión definida por el usuario) en tipos que no son de clase**

   Las versiones anteriores del compilador permitieron que se llamara 'operator *type*()' en tipos que no son de clase mientras que se les ignora en modo silencioso. Este comportamiento anterior creó un riesgo de generación de código incorrecto silencioso, lo que produjo un comportamiento impredecible en tiempo de ejecución. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2228 en su lugar.

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   Ejemplo (antes)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   Ejemplo (después)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **Typename redundante en los especificadores de tipos elaborados**

   Las versiones anteriores del compilador permitieron **typename** en especificadores de tipo elaborados; el código escrito de este modo es incorrecto semánticamente. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C3406 en su lugar.

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   Ejemplo (antes)

    ```cpp
    template <typename class T>
    class container;
    ```

   Ejemplo (después)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **Deducción de tipos de matrices de una lista de inicializadores**

   Las versiones anteriores del compilador no admitían la deducción de tipos de matrices de una lista de inicializadores. El compilador admite ahora esta forma de deducción de tipos y, como resultado, las llamadas a las plantillas de función mediante listas de inicializadores podrían ser ahora ambiguas o se podría elegir una sobrecarga diferente de la de versiones anteriores del compilador. Para resolver estos problemas, el programa debe especificar ahora explícitamente la sobrecarga que el programador tiene como objetivo.

   Cuando este comportamiento nuevo haga que la resolución de sobrecarga considere que un candidato adicional sea igual de bueno que el candidato histórico, la llamada pasará a ser ambigua y el compilador emitirá el error del compilador C2668 como resultado.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   Ejemplo 1: llamada ambigua a una función sobrecargada (antes)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   Ejemplo 1: llamada ambigua a una función sobrecargada (después)

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   Cuando este comportamiento nuevo provoque que la resolución de sobrecarga considere que un candidato adicional es una coincidencia mejor que el candidato histórico, la llamada resuelve sin ambigüedades al nuevo candidato, provocando un cambio en el comportamiento del programa que probablemente sea diferente de lo que el programador pensaba.

   Ejemplo 2: cambio en la resolución de sobrecarga (antes)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   Ejemplo 2: cambio en la resolución de sobrecarga (después)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **Restauración de las advertencias de la instrucción switch**

   Una versión anterior del compilador quitó advertencias existentes anteriormente relacionadas con instrucciones **switch**; estas advertencias se han restaurado ahora. El compilador emite ahora las advertencias restauradas y se emiten ahora advertencias relacionadas con los casos específicos (incluido el caso predeterminado) en la línea que contiene el caso que genera el error, en lugar de en la última línea de la instrucción switch. Como resultado de emitir ahora esas advertencias en líneas diferentes a como se hacía en el pasado, ya no se podrán suprimir según lo previsto las advertencias suprimidas anteriormente mediante `#pragma warning(disable:####)` . Para suprimir estas advertencias según lo previsto, es posible que sea necesario mover la directiva `#pragma warning(disable:####)` a una línea por encima del primer caso que genera potencialmente el error. Las siguientes son las advertencias restauradas.

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   Ejemplo de C4063: (antes)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   Ejemplo de C4063: (después)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   En su documentación se ofrecen ejemplos de las otras advertencias restauradas.

- **#include: uso del especificador de principal-directorio '..' en pathname** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador no detectaron el uso del especificador de principal-directorio '..' en el nombre de la ruta de acceso de las directivas  `#include` . El código escrito de este modo normalmente está pensado para incluir encabezados que existen fuera del proyecto usando incorrectamente rutas de acceso relativas del proyecto. Este comportamiento antiguo crea un riesgo de que el programa se pueda compilar incluyendo un archivo de origen diferente del que pensaba el programador, o que esas rutas de acceso relativas no son portables a otros entornos de compilación. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C4464 de compilador opcional, si se habilita.

    ```Output
    warning C4464: relative include path contains '..'
    ```

   Ejemplo (antes)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   Ejemplo (después)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   Además, aunque el compilador no ofrece un diagnóstico específico, se recomienda no usar el especificador de directorio principal “..” para especificar los directorios de inclusión del proyecto.

- **optimize() #pragma se extiende más allá del final del archivo de encabezado** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador no detectaban cambios en la configuración de la marca de optimización que eluden un archivo de encabezado incluido dentro de una unidad de traducción. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C4426 de compilador opcional en la ubicación de `#include`que genera el problema, si se habilita. Esta advertencia solo se emite si el cambio entra en conflicto con las marcas de optimización establecidas por los argumentos de la línea de comandos para el compilador.

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   Ejemplo (antes)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   Ejemplo (después)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **Error de coincidencia de #pragma warning(push)** y **#pragma warning(pop)** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador no detectaban que los cambios de estado `#pragma warning(push)` se emparejaban con cambios de estado `#pragma warning(pop)` en un archivo de código fuente diferente, lo que rara vez es lo previsto. Este comportamiento antiguo creaba un riesgo de que el programa se compilara con un conjunto de advertencias habilitadas diferentes de lo que el programador había pensado, lo cual puede provocar un comportamiento en tiempo de ejecución incorrecto silencioso. Ahora el compilador detecta el código escrito de esta manera, lo notifica al programador y emite una advertencia del compilador opcional C5031 en la ubicación de `#pragma warning(pop)` coincidente, si se habilita. Esta advertencia incluye una nota que hace referencia a la ubicación de #pragma warning(push) correspondiente.

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   Ejemplo (antes)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   Ejemplo (después)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   Aunque es poco frecuente, a veces el código escrito de este modo es intencionado. El código escrito de este modo es sensible a los cambios en el orden de `#include`. Cuando sea posible, se recomienda que los archivos de código fuente administren el estado de advertencia de forma independiente.

- **#pragma warning(push) sin coincidencia** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador no detectaron cambios de estado `#pragma warning(push)` sin coincidencia al final de una unidad de traducción. Ahora el compilador detecta el código escrito de esta manera, lo notifica al programador y emite una advertencia del compilador opcional C5032 en la ubicación de `#pragma warning(push)` no coincidente, si se habilita. Esta advertencia solo se emite si no hay ningún error de compilación en la unidad de traducción.

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   Ejemplo (antes)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   Ejemplo (después)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **Se pueden emitir advertencias adicionales como resultado del seguimiento del estado de advertencia #pragma mejorado**

   Las versiones anteriores del compilador no realizaron un seguimiento de los cambios de estados de advertencia #pragma lo suficientemente bueno como para emitir todas las advertencias que se pretendían. Este comportamiento provocó un riesgo de que se suprimirían algunas advertencias de manera eficaz en circunstancias diferentes de las que tenía previstas el programador. El compilador realiza ahora el seguimiento del estado `#pragma warning` con mayor eficacia, especialmente en relación con los cambios de estado `#pragma warning` dentro de las plantillas y, opcionalmente, emite nuevas advertencias C5031 y C5032 que están pensadas para ayudar al programador a localizar usos imprevistos de `#pragma warning(push)` y `#pragma warning(pop)`.

   Como resultado del seguimiento del cambio de estado de `#pragma warning` mejorado, es posible emitir ahora las advertencias anteriormente suprimidas de manera incorrecta o las advertencias relacionadas con problemas que anteriormente tenían un mal diagnóstico.

- **Mejora de la identificación del código inaccesible**

   Los cambios en la biblioteca estándar de C++ y la mejora en la capacidad para llamadas a funciones insertadas respecto a versiones anteriores del compilador pueden permitirle a este demostrar que determinado código ahora es inaccesible. Este nuevo comportamiento puede producir nuevas instancias de advertencia C4720 emitidas con mayor frecuencia.

    ```Output
    warning C4720: unreachable code
    ```

   En muchos casos, esta advertencia solo se puede emitir al compilar con las optimizaciones habilitadas, puesto que las optimizaciones pueden insertar más llamadas a funciones, eliminar código redundante o hacer posible de otra manera que se determine cierto código que no sea accesible. Hemos observado que las instancias nuevas de la advertencia C4720 han aparecido con frecuencia en bloques **try/catch**, especialmente en relación con el uso de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

   Ejemplo (antes)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   Ejemplo (después)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

###  <a name="VS_Update2"></a> Mejoras de conformidad en Update 2

- **Puede que se generen errores y advertencias adicionales como resultado de la compatibilidad parcial con la expresión SFINAE**

   Las versiones anteriores del compilador no analizaban determinados tipos de expresiones dentro de especificadores **decltype** debido a la falta de compatibilidad con la expresión SFINAE. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. Ahora, el compilador analiza estas expresiones y tiene compatibilidad parcial para la expresión SFINAE gracias a las mejoras de cumplimiento continuas. Como resultado, ahora, el compilador genera advertencias y errores detectados en las expresiones que las versiones anteriores del compilador no analizaban.

   Cuando este comportamiento nuevo analiza una expresión **decltype** que incluye un tipo que aún no se ha declarado, el compilador genera el error del compilador C2039 como resultado.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Ejemplo 1: uso de un tipo no declarado (antes)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   Ejemplo 1 (después)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   Cuando este comportamiento nuevo analiza una expresión **decltype** en la que falta el uso necesario de la palabra clave **typename** para especificar que un nombre dependiente es un tipo, el compilador emite la advertencia del compilador C4346, junto con el error del compilador C2923.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Ejemplo 2: un nombre dependiente no es un tipo (antes)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   Ejemplo 2 (después)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- **Las variables de miembro `volatile` impiden los operadores de asignación y constructores definidos implícitamente**

   Las versiones anteriores del compilador permitían que se generaran automáticamente constructores para copiar o mover predeterminados y operadores de asignación para copiar o mover predeterminados para una clase con variables de miembro **volátiles**. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. Ahora, el compilador considera que una clase que tiene variables de miembro **volátiles** tiene operadores de asignación y construcción no triviales, lo que impide que se generen implementaciones predeterminadas de estos operadores automáticamente. Cuando esta clase es miembro de una unión (o una unión anónima dentro de una clase), los constructores para copiar o mover y los operadores de asignación de copiar o mover de la unión (o la clase que contiene la unión anónima) se definirán implícitamente como eliminados. Intentar crear o copiar la unión (o la clase que contiene la unión anónima) sin definirlas explícitamente es un error y, en tal caso, el compilador genera el error de compilador C2280 como resultado.

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   Ejemplo (antes)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   Ejemplo (después)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **Las funciones miembro estáticas no admiten calificadores cv.**

   Las versiones anteriores de Visual Studio 2015 permitían que las funciones miembro estáticas tuvieran calificadores cv. Este comportamiento se debe a una regresión en Visual Studio 2015 y Visual Studio 2015 Update 1, ya que Visual Studio 2013 y las versiones anteriores del compilador rechazan el código escrito de este modo. El comportamiento de Visual Studio 2015 y Visual Studio 2015 Update 1 no es correcto ni conforme con el estándar de C++.  Visual Studio 2015 Update 2 rechaza el código escrito de este modo y genera el error de compilador C2511 en su lugar.

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   Ejemplo (antes)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   Ejemplo (después)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **No se permite la declaración adelantada de la enumeración en el código de WinRT** (solo afecta a `/ZW`)

   El código compilado para Windows Runtime (WinRT) no permite que los tipos **enum** se declaren por adelantado, del mismo modo que cuando el código C++ administrado se compila para .NET Framework mediante el modificador de compilador `/clr`. Este comportamiento garantiza que siempre se conozca el tamaño de una enumeración y que se pueda proyectar correctamente al sistema de tipos de WinRT. El compilador rechaza el código escrito de este modo y genera los errores de compilador C2599 y C3197.

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   Ejemplo (antes)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   Ejemplo (después)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **El operador no miembro sobrecargado new y el operador delete no se pueden declarar como inline** (nivel 1 (`/W1`), activo de manera predeterminada)

   Las versiones anteriores del compilador no generan ninguna advertencia cuando las funciones de operador no miembro new y de operador delete se declaraban como inline. El código escrito de este modo tiene un formato incorrecto (no se requiere ningún diagnóstico) y puede provocar problemas de memoria derivados de operadores new y delete no coincidentes (especialmente si se usan junto con una desasignación dimensionada) que puede resultar difícil de diagnosticar. Ahora, el compilador emite la advertencia C4595 para ayudarle a identificar el código escrito de este modo.

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   Ejemplo (antes)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   Ejemplo (después)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   Corregir el código escrito de este modo puede requerir el traslado de las definiciones de operador fuera de un archivo de encabezado y al archivo de origen correspondiente.

###  <a name="VS_Update3"></a> Mejoras de conformidad en Update 3

- **std::is_convertable ahora detecta la asignación automática** (biblioteca estándar)

   Las versiones anteriores del rasgo de tipo `std::is_convertable` no detectaban correctamente la asignación automática de un tipo de clase cuando el constructor de copias se había eliminado o era privado. Ahora, `std::is_convertable<>::value` está establecido de forma correcta en **false** cuando se aplica a un tipo de clase con un constructor de copias eliminado o privado.

   No hay ningún diagnóstico del compilador asociado con este cambio.

   Ejemplo

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   En versiones anteriores del compilador, las aserciones estáticas de la parte inferior de este ejemplo se aceptaban porque `std::is_convertable<>::value` estaba establecido de forma incorrecta en **true**. Ahora, `std::is_convertable<>::value` se ha establecido de forma correcta en **false**, lo que hace que se produzcan errores en las aserciones estáticas.

- **Los constructores de copias y movimiento triviales establecidos como valor predeterminado o eliminados respetan los especificadores de acceso**

   Las versiones anteriores del compilador no comprobaban el especificador de acceso de los constructores de copias y movimiento triviales establecidos como valor predeterminado o eliminados antes de permitir llamarlos. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. En algunos casos, este comportamiento anterior ha creado un riesgo de generación de código no válido silencioso, lo que ha producido un comportamiento impredecible en tiempo de ejecución. Ahora, el compilador comprueba el especificador de acceso de los constructores de copias y movimiento triviales establecidos como valor predeterminado o eliminados para determinar si se pueden llamar y, en caso contrario, emite como resultado una advertencia del compilador C2248.

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   Ejemplo (antes)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   Ejemplo (después)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- **Compatibilidad en desuso con código ATL con atributos**  (nivel 1 (`/W1`), activo de manera predeterminada)

   Las versiones anteriores del compilador admitían código ATL con atributos. Como parte de la fase siguiente para quitar la compatibilidad con código ATL con atributos que [comenzó en Visual Studio 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), el código ATL con atributos está en desuso. Ahora, el compilador emite la advertencia del compilador C4467 para ayudarle a identificar este tipo de código en desuso.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Si quiere seguir usando código ATL con atributos hasta que se quite la compatibilidad del compilador, puede deshabilitar esta advertencia. Para ello, pase los argumentos de la línea de comandos `/Wv:18` o `/wd:4467` al compilador o agregue `#pragma warning(disable:4467)` en el código fuente.

   Ejemplo 1 (antes)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Ejemplo 1 (después)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   A veces, necesitará o querrá crear un archivo IDL para evitar el uso de atributos ATL en desuso, como se muestra en el ejemplo de código siguiente

   Ejemplo 2 (antes)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   Primero, cree el archivo *.idl. Puede usar el archivo vc140.idl generado para obtener un archivo \*.idl que contenga las interfaces y las anotaciones.

   Después, agregue un paso MIDL a la compilación para asegurarse de que se generan las definiciones de interfaz de C++.

   Ejemplo 2 de IDL (después)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   Luego, use ATL directamente en el archivo de implementación, como se muestra en el ejemplo de código siguiente.

   Ejemplo 2 de implementación (después)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **Archivos de encabezado precompilado (PCH) y directivas #include no coincidentes** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador aceptaban directivas `#include` no coincidentes en archivos de código fuente entre compilaciones `-Yc` y `-Yu` cuando se usaban archivos de encabezado precompilado (PCH). El compilador ya no admite código escrito de este modo.   Ahora, el compilador emite la advertencia del compilador CC4598 para ayudar a identificar las directivas `#include` no coincidentes cuando se usan archivos PCH.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   Ejemplo (antes):

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   Ejemplo (después)

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **Archivos de encabezado precompilado (PCH) y directivas #include no coincidentes** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador aceptaban argumentos de la línea de comandos de directorios de inclusión no coincidentes (`-I`) en el compilador entre compilaciones `-Yc` y `-Yu` cuando se usaban archivos de encabezado precompilado (PCH). El compilador ya no admite código escrito de este modo.   Ahora, el compilador emite la advertencia del compilador CC4599 para ayudar a identificar los argumentos de la línea de comandos de directorios de inclusión no coincidentes (`-I`) cuando se usan archivos PCH.

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   Ejemplo (antes)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   Ejemplo (después)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Cambios de conformidad de Visual Studio 2013

### <a name="compiler"></a>Compilador

- La palabra clave **final** genera ahora un error de símbolo sin resolver donde previamente se habría compilado:

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   En versiones anteriores, el error no se producía porque la llamada era **virtual**, aunque el programa sufriría un bloqueo en tiempo de ejecución. Ahora, se produce un error del vinculador porque se sabe que se trata de la clase final. En este ejemplo, para corregir el error, tendría que establecer vínculos con el objeto que contiene la definición de `S2::f`.

- Si usa funciones friend en espacios de nombres, debe volver a declarar la función friend antes de hacer referencia a ella o se producirá un error, ya que ahora el compilador se ajusta al estándar ISO C++. Por ejemplo, este código ya no se compila:

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   Para corregir este código, declare la función **friend**:

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- El estándar de C++ no permite la especialización explícita de una clase. Aunque el Compilador de Microsoft Visual C++ lo permite en ciertos casos, en otros como el del ejemplo siguiente se genera un error porque el compilador no considera que la segunda función sea una especialización de la primera.

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   Para corregir este código, modifique la segunda función:

    ```cpp
    template <> void f(char& val);
    ```

- En el ejemplo siguiente, el compilador ya no intenta eliminar la ambigüedad de las dos funciones y ahora notifica un error:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   Para corregir este código, clarifique la llamada:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- Antes de que el compilador siguiera el estándar ISO C++11, el siguiente código se habría compilado y habría provocado que `x` se resolviera en el tipo **int**:

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Ahora, este código resuelve `x` en un tipo de `std::initializer_list<int>` y produce un error en la siguiente línea que intenta asignar `x` al tipo **int**. (No hay ninguna conversión predeterminada). Para corregir este código, use **int** para reemplazar **auto**:

    ```cpp
    int x = {0};
    int y = x;
    ```

- Ya no se permite la inicialización de agregado cuando el tipo del valor derecho no coincide con el tipo del valor izquierdo que se está inicializando, y se produce un error porque el estándar ISO C++11 requiere que funcione la inicialización uniforme sin conversiones de restricción. Anteriormente, si había una conversión de restricción disponible, se emitía una [advertencia del compilador (nivel 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) en lugar de un error.

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   Para corregir este código, agregue una conversión de restricción explícita:

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- La inicialización siguiente ya no se permite:

    ```cpp
    void *p = {{0}};
    ```

   Para corregir este código, use cualquiera de estas formas:

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- La búsqueda de nombres ha cambiado. El código siguiente se resuelve de forma diferente en el Compilador de Microsoft Visual C++ de Visual Studio 2012 y Visual Studio 2013:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   En Visual Studio 2012, `E1` en la expresión `E1::b` se resuelve como `::E1` en el ámbito global. En Visual Studio 2013, `E1` en la expresión `E1::b` se resuelve como la definición `typedef E2` de `main()` y tiene el tipo `::E2`.

- La disposición de los objetos ha cambiado. En x64, la disposición de los objetos de una clase puede cambiar con respecto a versiones anteriores. Si tiene una función **virtual** pero no tiene una clase base que tenga una función **virtual**, el modelo de objetos del compilador inserta un puntero a una tabla de función **virtual** después de la disposición de los miembros de datos. Esto significa que la disposición tal vez no sea óptima en todos los casos. En versiones anteriores, se ha intentado mejorar la disposición con una optimización de x64, pero como no ha funcionado correctamente en situaciones de código complejas, se ha eliminado en Visual Studio 2013. Por ejemplo, considere este código:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- En Visual Studio 2013, el resultado de `sizeof(S2)` en x64 es 48, pero en versiones anteriores se evalúa como 32. Para que se evalúe como 32 en el Compilador de Microsoft Visual C++ en Visual Studio 2013 (x64), agregue una clase base ficticia que tenga una función **virtual**:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Para buscar ubicaciones en el código que en una versión anterior se habrían intentado optimizar, use un compilador de esa versión junto con la opción del compilador `/W3` y active la advertencia 4370. Por ejemplo:

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   En versiones anteriores a Visual Studio 2013, este código genera este mensaje: "Advertencia C4370: "S2": el diseño de clase cambió desde una versión anterior del compilador debido a una mejora del empaquetado".

   El compilador de x86 presenta el mismo problema de disposición en todas las versiones. Por ejemplo, si este código se compila para x86:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   El resultado de `sizeof(S)` es 24. Sin embargo, se puede reducir a 16 si se emplea la solución alternativa mencionada para x64:

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>biblioteca estándar

El Compilador de Microsoft Visual C++ de Visual Studio 2013 detecta las discordancias en _ITERATOR_DEBUG_LEVEL, función que se implementó en Visual Studio 2010, y las discordancias de la biblioteca en tiempo de ejecución. Estas se producen cuando se mezclan las opciones del compilador `/MT` (versión estática), `/MTd` (depuración estática), `/MD` (versión dinámica) y `/MDd` (depuración dinámica).

- Si el código usa las plantillas de alias simuladas de la versión anterior, tiene que cambiarlo. Por ejemplo, en lugar de `allocator_traits<A>::rebind_alloc<U>::other`, tiene que especificar `allocator_traits<A>::rebind_alloc<U>`. Aunque `ratio_add<R1, R2>::type` ya no es necesario y ahora se recomienda `ratio_add<R1, R2>`, el primero seguirá compilándose porque `ratio<N, D>` es necesario para tener una definición de tipos “tipo” para una ratio reducida, que será el mismo tipo si ya se ha reducido.

- Debe utilizar `#include <algorithm>` cuando llame a `std::min()` o `std::max()`.

- Si el código existente usa las enumeraciones con ámbito simuladas de la versión anterior (enumeraciones sin ámbito tradicionales incluidas en espacios de nombres), tendrá que cambiarlo. Por ejemplo, si incluía una referencia al tipo `std::future_status::future_status`, ahora tiene que especificar `std::future_status`. Sin embargo, la mayor parte del código no se ve afectado; por ejemplo, `std::future_status::ready` todavía se compila.

- `explicit operator bool()` es más estricto que el operador unspecified-bool-type(). `explicit operator bool()` permite conversiones explícitas a bool (por ejemplo, para `shared_ptr<X> sp`, tanto `static_cast<bool>(sp)` como `bool b(sp)` son válidos) y "conversiones contextuales" de pruebas booleanas a bool (por ejemplo, cualquiera de `if (sp)`,`!sp` y `sp &&`). Sin embargo, `explicit operator bool()` impide conversiones implícitas en bool, por lo que no puede especificar `bool b = sp;`; y para un tipo de valor devuelto bool, no puede especificar `return sp`.

- Ahora que se han implementado plantillas variádicas reales, _VARIADIC_MAX y las macros relacionadas no tienen ningún efecto. Si aún se mantiene la definición de _VARIADIC_MAX, sencillamente se omite. Si utilizó nuestra maquinaria de macros diseñada para admitir plantillas variádicas simuladas de cualquier otra forma, tendrá que cambiar el código.

- Además de las palabras clave normales, los encabezados de biblioteca estándar de C++ prohíben ahora el uso de macros en las palabras clave contextuales **override** y **final**.

- reference_wrapper/ref()/cref() ahora no permite el enlace a objetos temporales.

- \<random> ahora aplica estrictamente sus condiciones previas de tiempo de compilación.

- Varios rasgos de tipo de biblioteca estándar de C++ tienen la condición previa "T debe ser un tipo completo". Aunque el compilador aplique ahora esto de forma más estricta, no puede aplicarlo en todas las situaciones. (Dado que las infracciones de las condiciones previas de biblioteca estándar de C++ desencadenan un comportamiento no definido, la biblioteca de plantillas estándar no garantiza su cumplimiento).

- La biblioteca estándar de C++ no admite `/clr:oldSyntax`.

- La especificación de C++11 para common_type<> tenía consecuencias inesperadas y no deseadas; en concreto, hacía que common_type\<int, int>::type devolviera int&&. Por tanto, el Compilador de Microsoft Visual C++ implementa la resolución propuesta para el problema 2141 del grupo de trabajo de biblioteca, que hace que common_type\<int, int="">::type devuelva int.

   Un efecto secundario de este cambio es que ya no funciona el caso de identidad (common_type\<T> no siempre devuelve un tipo T). Este comportamiento se ajusta a la resolución propuesta, pero interrumpe cualquier código que dependiera del comportamiento anterior.

   Si necesita un tipo de rasgo de identidad, no use el elemento `std::identity` no estándar que se define en \<type_traits> porque no funcionará para \<void>. En su lugar, implemente un rasgo de tipo de identidad propio que se ajuste a sus necesidades. Por ejemplo:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC y ATL

- **Solo Visual Studio 2013**: La biblioteca MFC MBCS no se incluye en Visual Studio debido a la popularidad de Unicode y a que el uso de MBCS se ha reducido significativamente. Este cambio también hace que MFC se adapte más al propio Windows SDK, ya que muchos de los nuevos controles y mensajes son solo Unicode. En cambio, si necesita seguir usando la biblioteca MFC MBCS, puede descargarla del Centro de descarga de MSDN en [Multibyte MFC Library para Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770). El paquete redistribuible de Visual C++ todavía incluye esta biblioteca.  Nota: El archivo DLL de MBCS se incluye en los componentes de instalación de Visual Studio 2015 y versiones posteriores.

- Se ha modificado la accesibilidad de la barra de herramientas de MFC.  En lugar de una arquitectura de una capa, ahora hay una arquitectura jerárquica. Puede seguir utilizando el comportamiento antiguo llamando a `CRibbonBar::EnableSingleLevelAccessibilityMode()`.

- Se elimina el método `CDatabase::GetConnect`. Para mejorar la seguridad, ahora la cadena de conexión solo se almacena cifrada y se descifra solo si es necesario; no puede devolverse como texto sin formato.  La cadena puede obtenerse al usar el método `CDatabase::Dump`.

- La firma de `CWnd::OnPowerBroadcast` ha cambiado. La signatura de este controlador de mensajes se ha modificado para tomar LPARAM como segundo parámetro.

- Las signaturas se han modificado para alojar controladores de mensajes. Las listas de parámetros de las funciones siguientes se han modificado para utilizar los controladores de mensajes ON_WM_* que se han agregado:

   - `CWnd::OnDisplayChange` ha cambiado a (UINT, int, int) en lugar de (WPARAM, LPARAM) para que la nueva macro ON_WM_DISPLAYCHANGE pueda usarse en el mapa de mensajes.

   - `CFrameWnd::OnDDEInitiate` ha cambiado a (CWnd*, UINT, UNIT) en lugar de (WPARAM, LPARAM) para que la nueva macro ON_WM_DDE_INITIATE pueda usarse en el mapa de mensajes.

   - `CFrameWnd::OnDDEExecute` ha cambiado a (CWnd*, HANDLE) en lugar de (WPARAM, LPARAM) para que la nueva macro ON_WM_DDE_EXECUTE pueda usarse en el mapa de mensajes.

   - `CFrameWnd::OnDDETerminate` ha cambiado a (CWnd*) como parámetro en lugar de (WPARAM, LPARAM) para que la nueva macro ON_WM_DDE_TERMINATE pueda usarse en el mapa de mensajes.

   - `CMFCMaskedEdit::OnCut` ha cambiado a sin parámetros en lugar de (WPARAM, LPARAM) para que la nueva macro ON_WM_CUT pueda usarse en el mapa de mensajes.

   - `CMFCMaskedEdit::OnClear` ha cambiado a sin parámetros en lugar de (WPARAM, LPARAM) para que la nueva macro ON_WM_CLEAR pueda usarse en el mapa de mensajes.

   - `CMFCMaskedEdit::OnPaste` ha cambiado a sin parámetros en lugar de (WPARAM, LPARAM) para que la nueva macro ON_WM_PASTE pueda usarse en el mapa de mensajes.

- Se han quitado los \#ifdefs de los archivos de encabezado de MFC. Se han quitado varios #ifdefs de los archivos de encabezado de MFC relacionados con las versiones de Windows no compatibles (WINVER &lt; 0x0501).

- Se ha quitado ATL DLL (atl120.dll). ATL ahora se proporciona en forma de encabezados y como biblioteca estática (atls.lib).

- Se ha quitado atlsd.lib, atlsn.lib y atlsnd.lib. Atls.lib ya no tiene código ni dependencias de juego de caracteres específicos para la depuración y el lanzamiento. Como funciona igual para Unicode y ANSI y para depuración y lanzamiento, solo se necesita una versión de la biblioteca.

- Se ha quitado la herramienta de seguimiento ATL/MFC junto con ATL DLL y se ha simplificado el mecanismo de seguimiento. Ahora, el constructor `CTraceCategory` toma un parámetro (el nombre de categoría) y las macros TRACE llaman a las funciones de creación de informes de depuración de CRT.

## <a name="visual-c-2012-breaking-changes"></a>Cambios importantes en Visual C++ 2012

### <a name="compiler"></a>Compilador

- La opción del compilador `/Yl` ha cambiado. De manera predeterminada, el compilador usa esta opción, que puede conducir a errores LNK2011 en determinadas condiciones. Para obtener más información, consulte [/Yl (Insertar referencia PCH para biblioteca de depuración)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- En el código que se compila con `/clr`, la palabra clave de clase de **enumeración** define una enumeración de C++11, no una enumeración de Common Language Runtime (CLR). Para definir una enumeración de CLR, debe ser explícito sobre su accesibilidad.

- Use la palabra clave template para eliminar la ambigüedad explícitamente de un nombre dependiente (compatibilidad con estándar de lenguaje C++). En el ejemplo siguiente, la palabra clave template resaltada es obligatoria para resolver la ambigüedad. Para obtener más información, consulte [Resolución de nombres para tipos dependientes](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Ya no se permite una expresión constante de tipo flotante como argumento de plantilla, como se muestra en el ejemplo siguiente.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- El código que se compila con la opción de línea de comandos `/GS` y que tiene una vulnerabilidad con error por un paso puede provocar que el proceso termine en tiempo de ejecución, tal como se muestra en el siguiente ejemplo de pseudocódigo.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- La arquitectura predeterminada para compilaciones x86 se cambia a SSE2; por tanto, el compilador puede emitir instrucciones SSE y usará los registros XMM para realizar cálculos de punto flotante. Si quiere revertir al comportamiento anterior, use la marca de compilador `/arch:IA32` para especificar la arquitectura como IA32.

- El compilador puede emitir las advertencias [del compilador (nivel 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) y C4701 donde anteriormente no lo hacía. El compilador aplica comprobaciones más fuertes para el uso de variables locales sin inicializar de tipo de puntero.

- Cuando se especifica la nueva marca de enlazador `/HIGHENTROPYVA`, normalmente, Windows 8 hace que las asignaciones de memoria devuelvan una dirección de 64 bits. (Antes de Windows 8, estas asignaciones devolvían más a menudo direcciones de menos de 2 GB). Esto puede exponer errores de truncamiento de puntero en el código existente. De manera predeterminada, este modificador está activado. Para deshabilitar este comportamiento, especifique `/HIGHENTROPYVA:NO`.

- El compilador administrado (Visual Basic o C#) también es compatible con `/HIGHENTROPYVA` para las compilaciones administradas.  En cambio, en este caso, el modificador `/HIGHENTROPYVAswitch` está desactivado de manera predeterminada.

### <a name="ide"></a>IDE

- Aunque se recomienda que no cree aplicaciones de Windows Forms en C++/CLI, el mantenimiento de aplicaciones de interfaz de usuario de C++/CLI es compatible. Si tiene que crear una aplicación de Windows Forms o cualquier otra aplicación de interfaz de usuario .NET, use C# o Visual Basic. Use C++/CLI solo con fines de interoperabilidad.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Biblioteca de modelos de procesamiento paralelo y biblioteca de Runtime de simultaneidad

La enumeración `SchedulerType` de `UmsThreadDefault` está en desuso. La especificación de `UmsThreadDefault` genera una advertencia en desuso y se asigna internamente a `ThreadScheduler`.

### <a name="standard-library"></a>biblioteca estándar

- Después de un cambio importante entre C++98/03 y estándares C++11, con argumentos de plantilla explícitos para llamar a `make_pair()` (como en `make_pair<int, int>(x, y)`), normalmente no se compila en Visual C++ en Visual Studio 2012. La solución consiste en llamar siempre a `make_pair() ` sin argumentos de plantilla explícitos, como en `make_pair(x, y)`. Proporcionar argumentos de plantilla explícitos acaba con el propósito de la función. Si necesita un control preciso sobre el tipo resultante, use `pair` en lugar de `make_pair` (como en `pair<short, short>(int1, int2)`).

- Otro cambio importante entre C++98/03 y estándares C++11: si A es implícitamente convertible a B y B es implícitamente convertible a C, pero A no es implícitamente convertible a C, C++98/03 y Visual C++2010 permitían que `pair<A, X>` se convirtiera (implícita o explícitamente) en `pair<C, X>`. (El otro tipo, X, no es de interés aquí y no es específico al tipo primero en el par). Puesto que C++11 y el Compilador de Microsoft Visual C++ de Visual Studio 2012 detectan que A no es implícitamente convertible a C, eliminan la conversión de par de la resolución de sobrecarga. Se trata de un cambio positivo para muchos escenarios. Por ejemplo, si sobrecarga `func(const pair<int, int>&)` y `func(const pair<string, string>&)`, y si llama a `func()` con `pair<const char *, const char *>`, se compilará con este cambio. En cambio, este cambio interrumpe el código que dependía de conversiones de par agresivas. Normalmente, este código se puede solucionar al realizar una parte de la conversión de forma explícita; por ejemplo, al pasar `make_pair(static_cast<B>(a), x)` a una función que espere `pair<C, X>`.

- Visual C++ 2010 simulaba plantillas variádicas, por ejemplo, `make_shared<T>(arg1, arg2, argN)`, hasta un límite de 10 argumentos, al eliminar sobrecargas y especializaciones con maquinaria de preprocesador. En Visual Studio 2012, este límite se reduce a 5 argumentos para mejorar los tiempos de compilación y el consumo de memoria del compilador para la mayoría de los usuarios. En cambio, puede establecer el límite anterior al definir de forma explícita _VARIADIC_MAX como 10, en todo el proyecto.

- C++11 17.6.4.3.1 [macro.names]/2 prohíbe palabras clave de uso de macros cuando se incluyen encabezados de la biblioteca estándar de C++. Los encabezados emiten ahora errores del compilador si detectan palabras clave de uso de macros. (Al definir _ALLOW_KEYWORD_MACROS, se permite compilar este código, pero se desaconseja encarecidamente este uso). Como excepción, el uso de la macro new se permite de manera predeterminada, porque los encabezados se defienden de manera integral al usar #pragma push_macro("new")/#undef new/#pragma pop_macro("new"). Al definir _ENFORCE_BAN_OF_MACRO_NEW, se hace exactamente lo que implica su nombre.

- Para implementar varias optimizaciones y comprobaciones de depuración, la implementación de la biblioteca estándar de C++ interrumpe deliberadamente la compatibilidad binaria entre versiones de Visual Studio (2005, 2008, 2010, 2012). Cuando se usa la biblioteca estándar de C++, esto impide que se combinen archivos objeto y bibliotecas estáticas que se han compilado con versiones diferentes en un binario (EXE o DLL), e impide que se pasen objetos de la biblioteca estándar de C++ entre los archivos binarios que se han compilado con versiones diferentes. El hecho de combinar archivos objeto y bibliotecas estáticas (mediante la biblioteca estándar de C++) compilados usando Visual C++ 2010 con los compilados usando el compilador de C++ en Visual Studio 2012 emite errores del enlazador relativos a un error de coincidencia _MSC_VER, donde _MSC_VER es la macro que contiene la versión principal del compilador (1700 para Visual C++ en Visual Studio 2012). Esta comprobación no detecta la combinación de archivos DLL ni detecta combinaciones que impliquen Visual C++ 2008 o versiones anteriores.

- Además de detectar discordancias de _ITERATOR_DEBUG_LEVEL, que se ha implementado en Visual C++ 2010, el Compilador de Microsoft Visual C++ de Visual Studio 2012 detecta discordancias de la biblioteca en tiempo de ejecución. Estas se producen cuando se mezclan las opciones del compilador `/MT` (versión estática), `/MTd` (depuración estática), `/MD` (versión dinámica) y `/MDd` (depuración dinámica).

- `operator<()`, `operator>()`, `operator<=()` y `operator>=()` estaban disponibles para las familias de contenedores `std::unordered_map` y `stdext::hash_map`, aunque sus implementaciones no eran realmente útiles. Se han quitado estos operadores no estándares en Visual C++ en Visual Studio 2012. Además, la implementación de `operator==()` y `operator!=()` para la familia `std::unordered_map` se ha ampliado para abarcar la familia `stdext::hash_map`. (Se recomienda evitar el uso de la familia `stdext::hash_map` en el nuevo código).

- C++11 22.4.1.4 [locale.codecvt] especifica que `codecvt::length()` y `codecvt::do_length()` deben tomar parámetros `stateT&` modificables, pero Visual C++ 2010 tomaba `const stateT&`. El Compilador de Microsoft Visual C++ de Visual Studio 2012 toma `stateT&` como valor obligatorio de acuerdo con el estándar. Esta diferencia es importante para cualquier usuario que esté intentando reemplazar la función `do_length()`.

### <a name="crt"></a>CRT

- El montón en tiempo de ejecución de C (CRT), que se usa para new y malloc(), ya no es privado. CRT ahora usa el montón del proceso. Esto significa que el montón no se destruye cuando se descarga un archivo DLL, por lo que los archivos DLL vinculados de forma estática a CRT deben asegurar que la memoria asignada por el código del archivo DLL se limpia antes de que se cargue.

- La función `iscsymf()` se valida con valores negativos.

- La estructura `threadlocaleinfostruct` ha cambiado para adaptarse a los cambios en las funciones de configuración regional.

- Se han quitado de intrin.h las funciones de CRT que tienen intrínsecos correspondientes como `memxxx()`, `strxxx()`. Si incluye intrin.h solo para estas funciones, ahora debe incluir los encabezados de CRT correspondientes.

### <a name="mfc-and-atl"></a>MFC y ATL

- Se ha eliminado la compatibilidad de Fusion (afxcomctl32.h); por tanto, se han quitado todos los métodos que se definen en afxcomctl32.h. Se han eliminado los archivos de encabezado afxcomctl32.inl y afxcomctl32.h.

- Se ha cambiado el nombre de `CDockablePane::RemoveFromDefaultPaneDividier` a `CDockablePane::RemoveFromDefaultPaneDivider`.

- Se ha cambiado la firma de `CFileDialog::SetDefExt` para usar LPCTSTR; por tanto, se ven afectadas las compilaciones de Unicode.

- Se han quitado categorías de seguimiento de ATL obsoletas.

- Se ha cambiado la firma de `CBasePane::MoveWindow` para tomar un `const CRect`.

- Se ha cambiado la firma de `CMFCEditBrowseCtrl::EnableBrowseButton`.

- Se ha quitado `m_fntTabs` y `m_fntTabsBold` de `CMFCBaseTabCtrl`.

- Se ha agregado un parámetro a los constructores `CMFCRibbonStatusBarPane`. (Es un parámetro predeterminado y por tanto no requiere cambios en el código fuente).

- Se ha agregado un parámetro al constructor `CMFCRibbonCommandsListBox`. (Es un parámetro predeterminado y por tanto no requiere cambios en el código fuente).

- Se ha quitado la API `AFXTrackMouse` (y procesadores de temporizador relacionados). Use la API de Win32 `TrackMouseEvent` en su lugar.

- Se ha agregado un parámetro al constructor `CFolderPickerDialog`. (Es un parámetro predeterminado y por tanto no requiere cambios en el código fuente).

- Se ha cambiado el tamaño de la estructura de `CFileStatus`: el miembro `m_attribute` ha cambiado de BYTE a DWORD (para que coincida con el valor que ha devuelto `GetFileAttributes`).

- `CRichEditCtrl` y `CRichEditView` usan MSFTEDIT_CLASS (control RichEdit 4.1) en lugar de RICHEDIT_CLASS (control RichEdit 3.0) en las compilaciones de Unicode.

- Se ha eliminado `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` porque siempre es TRUE en Windows Vista, Windows 7 y Windows 8.

- Se ha eliminado `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` porque siempre es TRUE en Windows Vista, Windows 7 y Windows 8.

- Se ha eliminado `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`. Llame a la API de Windows directamente en Windows Vista, Windows 7 y Windows 8.

- Se ha eliminado `AFX_GLOBAL_DATA::DwmDefWindowProc`. Llame a la API de Windows directamente en Windows Vista, Windows 7 y Windows 8.

- Se ha cambiado el nombre de `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` a `IsDwmCompositionEnabled` para eliminar el conflicto de nombres.

- Se han cambiado los identificadores de varios temporizadores internos de MFC y se han movido las definiciones a afxres.h (AFX_TIMER_ID_ *).

- Se ha cambiado la firma del método `OnExitSizeMove` para que coincida con la macro ON_WM_EXITSIZEMOVE:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Se han cambiado el nombre y la firma de `OnDWMCompositionChanged` para que coincidan con la macro ON_WM_DWMCOMPOSITIONCHANGED:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Se ha cambiado la firma del método `OnMouseLeave` para que coincida con la macro ON_WM_MOUSELEAVE:

   - `CMFCCaptionBar`

   - `CMFCColorBar`

   - `CMFCHeaderCtrl`

   - `CMFCProperySheetListBox`

   - `CMFCRibbonBar`

   - `CMFCRibbonPanelMenuBar`

   - `CMFCRibbonRichEditCtrl`

   - `CMFCSpinButtonCtrl`

   - `CMFCToolBar` Reemplazar este texto

   - `CMFCToolBarComboBoxEdit`

   - `CMFCToolBarEditCtrl`

   - `CMFCAutoHideBar`

- Se ha cambiado la firma de `OnPowerBroadcast` para que coincida con la macro ON_WM_POWERBROADCAST:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

- Se ha cambiado la firma de `OnStyleChanged` para que coincida con la macro ON_WM_POWERBROADCAST:

   - `CMFCListCtrl`

   - `CMFCStatusBar`

- Se ha cambiado el nombre del método interno `FontFamalyProcFonts` a `FontFamilyProcFonts`.

- Se han quitado varios objetos de `CString` estáticos globales para eliminar las pérdidas de memoria en algunas situaciones (reemplazado por #defines), y las siguientes variables de miembro de clase:

   - `CKeyBoardManager::m_strDelimiter`

   - `CMFCPropertyGridProperty::m_strFormatChar`

   - `CMFCPropertyGridProperty::m_strFormatShort`

   - `CMFCPropertyGridProperty::m_strFormatLong`

   - `CMFCPropertyGridProperty::m_strFormatUShort`

   - `CMFCPropertyGridProperty::m_strFormatULong`

   - `CMFCPropertyGridProperty::m_strFormatFloat`

   - `CMFCPropertyGridProperty::m_strFormatDouble`

   - `CMFCToolBarImages::m_strPngResType`

   - `CMFCPropertyGridProperty::m_strFormat`

- Se ha cambiado la firma de `CKeyboardManager::ShowAllAccelerators` y se ha quitado el parámetro de delimitador del acelerador.

- Se ha agregado `CPropertyPage::GetParentSheet` y en la clase `CPropertyPage`, llámelo en lugar de `GetParent` para obtener la ventana de hoja principal correcta, que puede ser el elemento primario o una ventana principal de `CPropertyPage`. Es posible que tenga que cambiar el código para llamar a `GetParentSheet` en lugar de `GetParent`.

- Se ha corregido #pragma warning(push) desequilibrado en ATLBASE.H, lo que ha provocado que las advertencias se deshabiliten de forma incorrecta. Esas advertencias están habilitadas correctamente después de que ATLBASE.H se haya analizado.

- Se han movido métodos relacionados con D2D de AFX_GLOBAL_DATA a _AFX_D2D_STATE:

   - `GetDirectD2dFactory`

   - `GetWriteFactory`

   - `GetWICFactory`

   - `InitD2D`

   - `ReleaseD2DRefs`

   - `IsD2DInitialized`

   - `D2D1MakeRotateMatrix`

   - Por ejemplo, en lugar de llamar a `afxGlobalData.IsD2DInitialized`, llame a `AfxGetD2DState->IsD2DInitialized`.

- Se han quitado archivos de ATL*.CPP obsoletos de la carpeta \atlmfc\include\.

- Se ha movido la inicialización `afxGlobalData` a petición en lugar de en tiempo de inicialización de CRT para satisfacer los requisitos de `DLLMain`.

- Agrega el método `RemoveButtonByIndex` a la clase `CMFCOutlookBarPane`.

- Se ha corregido `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` a `IsFrequentlyUsedCmd`.

- Se han corregido varias instancias de `RestoreOriginalstate` a `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`.

- Se han quitado métodos no usados de `CDockablePane`: `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, `GetRecentSiblingPaneInfo` y `CanAdjustLayout`.

- Se han quitado las variables de miembro estático de `CDockablePane` `m_bCaptionText` y `m_bHideDisabledButtons`.

- Agrega una invalidación del método `DeleteString` a `CMFCFontComboBox`.

- Se han quitado métodos no usados de `CPane`: `GetMinLength` y `IsLastPaneOnLastRow`.

- Se cambia el nombre de `CPane::GetDockSiteRow(CDockingPanesRow *)` a `CPane::SetDockSiteRow`.

## <a name="visual-c-2010-breaking-changes"></a>Cambios importantes en Visual C++ 2010

### <a name="compiler"></a>Compilador

- La palabra clave **auto** tiene un nuevo significado predeterminado. Dado que el uso del significado antiguo es poco frecuente, la mayoría de las aplicaciones no se verán afectadas por este cambio.

- Se introduce la nueva palabra clave **static_assert**, lo que provocará un conflicto de nombres si ya existe un identificador con ese nombre en el código.

- La compatibilidad con la nueva notación lambda excluye la compatibilidad para codificar un GUID sin comillas en un atributo IDL uuid.

- .NET Framework 4 introduce el concepto de excepciones de estado dañado, que son excepciones que dejan un proceso en un estado dañado e irrecuperable. De manera predeterminada, no se detecta una excepción de estado dañado, incluso con la opción del compilador /EHa que detecta todas las demás excepciones.                 Para detectar de forma explícita una excepción de estado dañado, use instrucciones de __try -\__except. O bien, aplique el atributo [HandledProcessCorruptedStateExceptions] para habilitar una función para detectar excepciones de estado dañado.  Este cambio afecta principalmente a los programadores de sistemas que podrían tener que detectar una excepción de estado dañado. Las ocho excepciones son STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ACCESS_VIOLATION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, STATUS_UNWIND_CONSOLIDATE.                 Para obtener más información sobre estas excepciones, consulte la macro [GetExceptionCode](/windows/desktop/Debug/getexceptioncode).

- La opción del compilador `/GS` revisada protege frente a saturaciones del búfer de forma más exhaustiva que en versiones anteriores. Esta versión podría insertar comprobaciones de seguridad adicionales en la pila que podría disminuir el rendimiento. Use la nueva palabra clave **__declspec(safebuffers)** para indicar al compilador que no inserte comprobaciones de seguridad para una función determinada.

- Si compila con las opciones del compilador `/GL` (Whole Program Optimization) y `/clr` (compilación de Common Language Runtime), se omite la opción `/GL`. Este cambio se ha realizado porque la combinación de opciones del compilador resultaba poco ventajosa. Como resultado de este cambio, se mejora el rendimiento de la compilación.

- De manera predeterminada, la compatibilidad con trígrafos está deshabilitada en Visual C++ 2010. Use la opción del compilador `/Zc:trigraphs` para habilitar la compatibilidad con trígrafos. Un trígrafo se compone de dos signos de interrogación consecutivos ("??") seguidos de un tercer carácter único. El compilador reemplaza un trígrafo por un carácter de puntuación correspondiente. Por ejemplo, el compilador reemplaza el trígrafo "? ?=" por el carácter "#". Use trígrafos en archivos de código fuente C que usen un juego de caracteres que no contenga representaciones gráficas adecuadas para algunos caracteres de puntuación.

- El enlazador ya no admite la optimización para Windows 98. La opción `/OPT` (optimizaciones) produce un error en tiempo de compilación si especifica `/OPT:WIN98` o `/OPT:NOWIN98`.

- Las opciones predeterminadas del compilador que se especifican mediante las propiedades de sistema de compilación RuntimeLibrary y DebugInformationFormat han cambiado. De manera predeterminada, estas propiedades de compilación se especifican en proyectos creados con las versiones de Visual C++ de 7.0 a 10.0. Si migra un proyecto creado por Visual C++ 6.0, considere la posibilidad de especificar un valor para estas propiedades.

- En Visual C++ 2010, RuntimeLibrary = MultiThreaded (`/MD`) y DebugInformationFormat = ProgramDatabase (`/Zi`). En Visual C++ 9.0, RuntimeLibrary = MultiThreaded (`/MT`) y DebugInformationFormat = Disabled.

### <a name="clr"></a>CLR

- Los compiladores de Microsoft C# y Visual Basic ahora pueden generar un ensamblado de interoperabilidad no primario (no-PIA). Un ensamblado no-PIA puede usar los tipos COM sin la implementación del ensamblado de interoperabilidad primario (PIA) correspondiente. Al usar ensamblados no-PIA generados por Visual C# o Visual Basic, debe hacer referencia el ensamblado PIA en el comando de compilación antes de hacer referencia a cualquier ensamblado no-PIA que use la biblioteca.

### <a name="visual-c-projects-and-msbuild"></a>Proyectos de Visual C++ y MSBuild

- Los proyectos de Visual C++ se basan ahora en la herramienta MSBuild. Por tanto, los archivos de proyecto usan un nuevo formato de archivo XML y un sufijo de archivo .vcxproj. Visual C++ 2010 convierte de forma automática los archivos de proyecto de versiones anteriores de Visual Studio al nuevo formato de archivo. Un proyecto existente se ve afectado si depende de la herramienta de compilación anterior, VCBUILD.exe, o del sufijo de archivo de proyecto .vcproj.

- En versiones anteriores, Visual C++ admitía la evaluación en tiempo de ejecución de hojas de propiedades. Por ejemplo, una hoja de propiedades primaria podría importar una hoja de propiedades secundaria y el elemento primario podría usar una variable definida en el elemento secundario para definir otras variables. La evaluación en tiempo de ejecución ha habilitado al elemento primario para que use la variable secundaria incluso antes de importar la hoja de propiedades secundarias. En Visual C++ 2010, una variable de hoja de proyecto no se puede usar antes de definirse porque MSBuild solo admite la evaluación temprana.

### <a name="ide"></a>IDE

- El cuadro de diálogo de finalización de aplicación ya no finaliza una aplicación. En versiones anteriores, cuando la función `abort()` o `terminate()` cierra la versión comercial de una aplicación, la biblioteca en tiempo de ejecución de C mostraba un mensaje de finalización de aplicación en un cuadro de diálogo o ventana de consola. Este mensaje decía, en parte: “Esta aplicación solicitó la finalización del tiempo de ejecución de modo no habitual. Póngase en contacto con el equipo de asistencia técnica de la aplicación para obtener más información”. El mensaje de finalización de aplicación era redundante porque Windows mostraba posteriormente el controlador de finalización actual, que normalmente era el cuadro de diálogo del informe de errores de Windows (Dr. Watson) o el depurador de Visual Studio. A partir de Visual Studio 2010, la biblioteca en tiempo de ejecución de C no muestra el mensaje. Además, el tiempo de ejecución impide que la aplicación finalice antes de iniciar un depurador. Se trata de un cambio importante solo si depende del comportamiento anterior del mensaje de finalización de la aplicación.

- Específicamente para Visual Studio 2010, IntelliSense no funciona para código o atributos de C++/CLI, **Buscar todas las referencias** no funciona para las variables locales y el modelo de código no recupera nombres de tipo de ensamblados importados ni resuelve tipos para sus nombres completos.

### <a name="libraries"></a>Bibliotecas

- La clase SafeInt se incluye en Visual C++ y ya no es una descarga independiente. Se trata de un cambio importante solo si ha desarrollado una clase también denominada "SafeInt".

- El modelo de implementación de bibliotecas ya no usa manifiestos para encontrar una versión concreta de una biblioteca de vínculos dinámicos. En su lugar, el nombre de cada biblioteca de vínculos dinámicos contiene su número de versión y tiene que usar ese nombre para buscar la biblioteca.

- En versiones anteriores de Visual Studio, podía volver a compilar las bibliotecas en tiempo de ejecución. Visual C++ 2010 ya no admite la compilación de sus propias copias de los archivos de la biblioteca en tiempo de ejecución de C.

### <a name="standard-library"></a>biblioteca estándar

- El encabezado \<iterator> ya no lo incluyen de forma automática muchos otros archivos de encabezado. En su lugar, incluya ese encabezado de forma explícita si necesita compatibilidad con los iteradores independientes definidos en el encabezado .vcproj.interator> "Un proyecto existente se ve afectado si depende de la herramienta de compilación anterior, VCBUILD.exe, o del sufijo de archivo de proyecto .vcproj".

- En el encabezado \<algorithm>, se han quitado las funciones checked_ * y unchecked_\*. Y en el encabezado \<iterator>>, se ha quitado la clase `checked_iterator` y se ha agregado la clase `unchecked_array_iterator`.

- El constructor `CComPtr::CComPtr(int)` se ha quitado. Este constructor permitía que un objeto `CComPtr` se construyera a partir de la macro NULL, pero no era necesario y permitía construcciones sin sentido de enteros distintos de cero.

   Aún se puede construir un `CComPtr` de NULL, que se define como 0, pero se producirá un error si se construye a partir de un entero distinto de 0 literal. Use **nullptr** en su lugar.

- Se han quitado las siguientes funciones miembro de `ctype`: `ctype::_Do_narrow_s`, `ctype::_Do_widen_s`, `ctype::_narrow_s`, `ctype::_widen_s`. Si una aplicación usa una de estas funciones miembro, debe reemplazarla con la versión no segura correspondiente: `ctype::do_narrow`, `ctype::do_widen`, `ctype::narrow`, `ctype::widen`.

### <a name="crt-mfc-and-atl-libraries"></a>Bibliotecas ATL, MFC y CRT

- Se ha quitado la compatibilidad para que los usuarios compilen las bibliotecas CRT, MFC y ATL. Por ejemplo, no se proporciona un archivo nmake adecuado. En cambio, los usuarios aún tienen acceso al código fuente de estas bibliotecas. Probablemente se publicará un documento que describe las opciones de MSBuild que usa Microsoft para compilar estas bibliotecas en un blog del equipo de Visual C++.

- Se ha quitado la compatibilidad de MFC con IA64. En cambio, aún se proporciona compatibilidad con CRT y ATL en IA64.

- Los ordinales ya no se vuelven a usar en archivos de definición de módulos (.def) de MFC. Este cambio significa que los ordinales no serán distintos entre las versiones secundarias y se mejorará la compatibilidad binaria de los service packs y versiones de ingeniería de corrección rápida.

- Se ha agregado una nueva función virtual a la clase `CDocTemplate`. Esta nueva función virtual es [CDocTemplate (clase)](../mfc/reference/cdoctemplate-class.md). La versión anterior de `OpenDocumentFile` tenía dos parámetros. La nueva versión tiene tres parámetros. Para admitir al administrador de reinicio, cualquier clase derivada de `CDocTemplate` debe implementar la versión que tiene tres parámetros. El nuevo parámetro es `bAddToMRU`.

### <a name="macros-and-environment-variables"></a>Variables de entorno y macros

- Ya no se admite la variable de entorno __MSVCRT_HEAP_SELECT. Se ha quitado esta variable de entorno y no hay ningún reemplazo.

### <a name="microsoft-macro-assembler-reference"></a>Referencia de Microsoft Macro Assembler

- Se han quitado varias directivas del compilador de referencia de Microsoft Macro Assembler. Las directivas que se han quitado son .186, .286, .286P, .287,.8086, .8087, y .NO87.

## <a name="visual-c-2008-breaking-changes"></a>Cambios importantes en Visual C++ 2008

### <a name="compiler"></a>Compilador

- Ya no se admiten las plataformas Windows 95, Windows 98, Windows Millennium Edition y Windows NT. Estos sistemas operativos se han quitado de la lista de plataformas de destino.

- El compilador ya no admite varios atributos que estaban directamente asociados con el servidor ATL. Ya no se admiten los siguientes atributos:

   - perf_counter

   - perf_object

   - perfmon

   - request_handler

   - soap_handler

   - soap_header

   - soap_method

   - tag_name

### <a name="visual-c-projects"></a>Proyectos de Visual C++

- Al actualizar proyectos desde versiones anteriores de Visual Studio, es posible que tenga que modificar las macros WINVER y _WIN32_WINNT para que sean mayores o iguales a 0x0500.

- A partir de Visual Studio 2008, el Asistente para nuevos proyectos no tiene una opción para crear un proyecto de C++ SQL Server. Los proyectos de SQL Server creados con una versión anterior de Visual Studio seguirán compilándose y funcionarán correctamente.

- Se ha quitado el archivo de encabezado de la API de Windows Winable.h. Incluya Winuser.h en su lugar.

- Se ha quitado la biblioteca de la API de Windows Rpcndr.lib. Vincule con rpcrt4.lib en su lugar.

### <a name="crt"></a>CRT

- Se ha quitado la compatibilidad con Windows 95, Windows 98, Windows Millennium Edition y Windows NT 4.0.

- Se han quitado las siguientes variables globales:

   - _osplatform

   - _osver

   - _winmajor

   - _winminor

   - _winver

- Se han quitado las siguientes funciones. En su lugar, utilice las funciones de API de Windows `GetVersion` o `GetVersionEx`:

   - _get_osplatform

   - _get_osver

   - _get_winmajor

   - _get_winminor

   - _get_winver

- Se ha cambiado la sintaxis de anotaciones de SAL. Para obtener más información, consulte [Anotaciones de SAL](../c-runtime-library/sal-annotations.md).

- El filtro IEEE ahora admite el conjunto de instrucciones de SSE 4.1. Para obtener más información, consulte [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Las bibliotecas en tiempo de ejecución de C que se suministran con Visual Studio ya no dependen del archivo DLL de sistema msvcrt.dll.

### <a name="standard-library"></a>biblioteca estándar

- Se ha quitado la compatibilidad con Windows 95, Windows 98, Windows Millennium Edition y Windows NT 4.0.

- Al compilar en modo de depuración con _HAS_ITERATOR_DEBUGGING definido (reemplazado por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) después de Visual Studio 2010), una aplicación impondrá ahora cuando un iterador intente incrementar o disminuir más allá de los límites del contenedor subyacente.

- La variable miembro c de la clase Stack está declarada como protegida. Anteriormente, esta variable miembro estaba declarada como pública.

- El comportamiento de `money_get::do_get` ha cambiado. Anteriormente, al analizar un importe monetario con más dígitos de fracción a los que llamaba `frac_digits`, `do_get` los consumía todos. Ahora, `do_get` detiene el análisis después de consumir caracteres de `frac_digits`.

### <a name="atl"></a>ATL

- No se puede compilar ATL sin una dependencia en CRT. En versiones anteriores de Visual Studio, podía usar #define ATL_MIN_CRT para hacer que un proyecto de ATL dependa mínimamente de CRT. En Visual C++ 2008, todos los proyectos de ATL dependen mínimamente de CRT, independientemente de si se ha definido ATL_MIN_CRT.

- La base de código del servidor ATL se ha publicado como un proyecto de origen compartido en CodePlex y no se instala como parte de Visual Studio. Se han mantenido las clases de codificación y descodificación de datos de atlenc.h y las clases y funciones de utilidad de atlutil.h y atlpath.h y ahora forman parte de la biblioteca ATL. Varios archivos asociados con el servidor ATL ya no forman parte de Visual Studio.

- Algunas funciones ya no están incluidas en el archivo DLL. Todavía se encuentran en la biblioteca de importación. Esto no afectará al código que usa las funciones de forma estática. Afectará solo al código que usa estas funciones de forma dinámica.

- Las macros PROP_ENTRY y PROP_ENTRY_EX están en desuso y se han reemplazado por las macros PROP_ENTRY_TYPE y PROP_ENTRY_TYPE_EX por motivos de seguridad.

### <a name="atlmfc-shared-classes"></a>Clases compartidas de ATL y MFC

- No se puede compilar ATL sin una dependencia en CRT. En versiones anteriores de Visual Studio, podía usar `#define ATL_MIN_CRT` para hacer que un proyecto de ATL dependa mínimamente de CRT. En Visual C++ 2008, todos los proyectos de ATL dependen mínimamente de CRT, independientemente de si se ha definido ATL_MIN_CRT.

- La base de código del servidor ATL se ha publicado como un proyecto de origen compartido en CodePlex y no se instala como parte de Visual Studio. Se han mantenido las clases de codificación y descodificación de datos de atlenc.h y las clases y funciones de utilidad de atlutil.h y atlpath.h y ahora forman parte de la biblioteca ATL. Varios archivos asociados con el servidor ATL ya no forman parte de Visual Studio.

- Algunas funciones ya no están incluidas en el archivo DLL. Todavía se encuentran en la biblioteca de importación. Esto no afectará al código que usa las funciones de forma estática. Afectará solo al código que usa estas funciones de forma dinámica.

### <a name="mfc"></a>MFC

- Clase `CTime`: la clase `CTime` acepta ahora fechas a partir del 1/1/1900 de la era común en lugar de 1/1/1970 de la era común.

- Orden de tabulación de controles en cuadros de diálogo de MFC: el orden de tabulación correcto de varios controles en un cuadro de diálogo de MFC se ve afectado si se inserta un control ActiveX de MFC en el orden de tabulación. Este cambio corrige el problema.

   Por ejemplo, cree una aplicación de cuadro de diálogo de MFC que tenga un control ActiveX y varios controles de edición. Coloque el control ActiveX en el medio de la orden de tabulación de los controles de edición. Inicie la aplicación, haga clic en un control de edición cuyo orden de tabulación esté después del control ActiveX y pulse TAB. Antes de realizar este cambio, el foco pasaba al control de edición siguiendo el control ActiveX en lugar del control de edición siguiente en el orden de tabulación.

- Clase `CFileDialog`: las plantillas personalizadas para la clase `CFileDialog` no se pueden migrar a Windows Vista de forma automática. Aún se pueden usar, pero no tendrán la funcionalidad adicional o el aspecto de los cuadros de diálogo de estilo de Windows Vista.

- Clase `CWnd` y clase `CFrameWnd`: se ha quitado el método `CWnd::GetMenuBarInfo`.

   El método `CFrameWnd::GetMenuBarInfo` ahora es un método no virtual. Para obtener más información, consulte la función **GetMenuBarInfo** en el SDK de Windows.

- Compatibilidad con ISAPI de MFC: MFC ya no admite la compilación de aplicaciones con la interfaz de programación de aplicaciones para servidores de Internet (ISAPI). Si quiere compilar una aplicación de ISAPI, llame directamente a las extensiones de ISAPI.

- API de ANSI en desuso: las versiones ANSI de varios métodos de MFC están en desuso. Use las versiones Unicode de esos métodos en sus aplicaciones futuras. Para obtener más información, consulte **Requisitos de compilación para los controles comunes de Windows Vista**.

## <a name="visual-c-2005-breaking-changes"></a>Cambios importantes en Visual C++ 2005

### <a name="crt"></a>CRT

- Algunas funciones han quedado desusadas. Consulte las **funciones de CRT en desuso**.

- Ahora, muchas funciones validan sus parámetros y detienen la ejecución si hay parámetros no válidos. Esto puede interrumpir el código que pasa parámetros no válidos y se basa en la función al omitirlos o simplemente al devolver un código de error. Consulte la **validación de parámetros**.

- El valor de descriptor de archivo -2 ahora se usa para indicar que stdout y stderr no están disponibles para la salida, por ejemplo, en una aplicación Windows que no tiene ninguna ventana de consola. El valor anterior que se usaba era -1. Para obtener más información, consulte [_fileno](../c-runtime-library/reference/fileno.md).

- Se han quitado las bibliotecas de CRT de un solo subproceso libc.lib y libcd.lib. Use las bibliotecas de CRT multiproceso. Ya no se admite la marca de compilador `/ML`. Se han agregado versiones de no bloqueo de algunas funciones en casos en que es importante la diferencia de rendimiento entre el código multiproceso y el código de un solo subproceso.

- Se ha quitado la sobrecarga de pow, double pow(int, int), para cumplir mejor con el estándar.

- El especificador de formato %n ya no se admite de manera predeterminada en ninguna de las familias de funciones printf porque es inherentemente inseguro. El comportamiento predeterminado si se encuentra %n es invocar al controlador de parámetros no válidos. Para habilitar la compatibilidad de %n, use _set_printf_count_output (también see_get_printf_count_output).

- `sprintf` ahora imprime el signo negativo de un cero firmado.

- `swprintf` ha cambiado para cumplir con el estándar; ahora requiere un parámetro de tamaño. La forma de `swprintf` sin un parámetro de tamaño está desusada.

- Se ha quitado `_set_security_error_handler`. Quite todas las llamadas a esa función; el controlador predeterminado es una forma mucho más segura de tratar los errores de seguridad.

- `time_t` ahora es un valor de 64 bits (a menos que se defina _USE_32BIT_TIME_T).

- Las funciones `_spawn`, `_wspawn` ahora no modifican errno correctamente, tal y como especifica el estándar de C.

- RTC usa ahora caracteres anchos de manera predeterminada.

- Las funciones de compatibilidad de control de punto flotante han quedado en desuso para aplicaciones compiladas con /CLR o/CLR:PURE. Las funciones afectadas son `_clear87`, `_clearfp`, `_control87`, `_controlfp`, `_fpreset`, `_status87`, `_statusfp`. Puede deshabilitar la advertencia de desuso al definir _CRT_MANAGED_FP_NO_DEPRECATE, pero el uso de estas funciones en código administrado es imprevisible y no se admite.

- Algunas funciones devuelven ahora punteros const. El comportamiento anterior no const puede reanudarse al definir _CONST_RETURN. Las funciones afectadas son

   - memchr, wmemchr

   - strchr, wcschr, _mbschr, _mbschr_l

   - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

   - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

   - strstr, wcsstr, _mbsstr, _mbsstr_l

- Al vincular con Setargv.obj o Wsetargv.obj, ya no es posible suprimir la expansión de un carácter comodín en la línea de comandos al escribirlo entre comillas dobles. Para obtener más información, consulte [Expandir argumentos de caracteres comodín](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Biblioteca estándar (2005)

- La clase de excepción (ubicada en el encabezado \<exception>) se ha movido al espacio de nombres `std`. En versiones anteriores, esta clase estaba en el espacio de nombres global. Para resolver cualquier error que indique que no se encuentra la clase de excepción, agregue la siguiente instrucción using al código:                 `using namespace std;`

- Al llamar a `valarray::resize()`, el contenido de `valarray` se perderá y se reemplazará por los valores predeterminados. El método `resize()` está pensado para reinicializar `valarray` en lugar de hacer que crezca de manera dinámica como un vector.

- Iteradores de depuración: las aplicaciones compiladas con una versión de depuración de la biblioteca en tiempo de ejecución de C y que usan iteradores de forma incorrecta pueden empezar a ver aserciones en tiempo de ejecución. Para deshabilitar estas aserciones, debe definir _HAS_ITERATOR_DEBUGGING (reemplazado por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) a partir de Visual Studio 2010) en 0. Para obtener más información, consulte [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)

## <a name="visual-c-net-2003-breaking-changes"></a>Cambios importantes en Visual C++ .NET 2003

### <a name="compiler"></a>Compilador

- Ahora se requieren paréntesis de cierre para la directiva de preprocesador definida (C2004).

- Las especializaciones explícitas ya no buscan parámetros de plantilla desde la plantilla principal ([error del compilador C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Un miembro protegido (n) solo puede obtenerse a través de una función miembro de una clase (B) que hereda de la clase (A) de la que (n) es miembro ([error del compilador C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Las comprobaciones de accesibilidad mejoradas en el compilador detectan ahora clases base inaccesibles ([error del compilador C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- No se puede detectar una excepción si el destructor o constructor de copia es inaccesible (C2316).

- Ya no se admiten los argumentos predeterminados de punteros a funciones ([error de compilador C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- No se puede inicializar un miembro de datos estático mediante una clase derivada ([error del compilador C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- La inicialización de un **typedef** no está permitida por el estándar y genera ahora un error del compilador ([error del compilador C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- Ahora, **bool** es un tipo adecuado ([error del compilador C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- Una UDC puede crear ahora ambigüedad con operadores sobrecargados ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Ahora hay más expresiones que se consideran constantes válidas de puntero nulo ([error del compilador C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- template<> se requiere ahora en lugares en que el compilador previamente la implicaría ([error del compilador C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- La especialización explícita de una función miembro fuera de la clase no es válida si la función ya se ha especializado explícitamente a través de una especialización de la clase de plantilla ([error del compilador C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Ya no se admiten parámetros de plantilla sin tipo de punto flotante ([error del compilador C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- No se admiten las plantillas de clase como argumentos de tipo de plantilla (C3206).

- Ya no se introducen los nombres de función friend en el espacio de nombres contenedor ([error del compilador C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- El compilador ya no aceptará comas adicionales en una macro (C4002).

- Un objeto de tipo POD construido con un inicializador del formulario () será inicializado de forma predeterminada (C4345).

- TypeName es necesario ahora si un nombre dependiente tiene que tratarse como un tipo ([advertencia del compilador (nivel 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Ya no se consideran especializaciones de plantilla las funciones que se consideraban así incorrectamente (C4347).

- No se pueden inicializar miembros de datos estáticos mediante una clase derivada (C4356).

- Una especialización de plantilla de clase debe definirse antes de que se haya usado en un tipo devuelto ([advertencia del compilador (nivel 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Ahora, el compilador genera código inalcanzable (C4702).

## <a name="see-also"></a>Vea también

[Novedades de Visual C++ en Visual Studio](../what-s-new-for-visual-cpp-in-visual-studio.md)