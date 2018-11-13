---
title: Información general sobre posibles problemas de actualización (Visual C++)
ms.date: 11/04/2016
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: e4a1f4ecb6492bf74fca46df6f096ca79c71da18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504265"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Información general sobre posibles problemas de actualización (Visual C++)

A lo largo de los años, el Compilador de Microsoft Visual C++ ha experimentado numerosos cambios, como los introducidos en el propio lenguaje C++, la biblioteca estándar de C++, el entorno de ejecución de C (CRT) y otras bibliotecas como MFC y ATL. Como resultado, al actualizar una aplicación desde una versión anterior de Visual Studio, es posible que se produzcan errores del compilador y el enlazador y se generen advertencias relativas a código que antes se compilaba correctamente. Cuanto más antiguo sea el código base original, más probable es que se produzcan dichos errores. En este artículo se resumen las clases de problemas más comunes que pueden aparecer y se proporcionan vínculos a información detallada.

> [!NOTE]
> Antes recomendábamos que las actualizaciones que abarcaban varias versiones de Visual Studio se realizasen de forma incremental de una en una. pero ya no se recomienda este método. Hemos descubierto que casi siempre es más fácil actualizar a la versión más reciente de Visual Studio, independientemente de la antigüedad del código base.

Si tiene preguntas o comentarios sobre el proceso de actualización, puede enviarlos a vcupgrade@microsoft.com.

## <a name="library-and-toolset-dependencies"></a>Dependencias de biblioteca y conjunto de herramientas

Al actualizar una aplicación a una nueva versión de Visual Studio, es muy recomendable, y en muchos casos necesario, actualizar también todas las bibliotecas y archivos DLL a los que esté vinculada la aplicación. Esto requiere tener acceso al código fuente o que el proveedor de bibliotecas pueda proporcionar nuevos archivos binarios compilados con la misma versión principal del compilador. Si se cumple alguna de estas condiciones, puede omitir esta sección, que trata sobre los detalles de la compatibilidad binaria. Si no se cumple ninguna, es posible que no puedan usar las bibliotecas en la aplicación actualizada. La información incluida en esta sección le ayudará a comprender si puede continuar con la actualización.

### <a name="toolset"></a>Conjunto de herramientas

Los formatos de archivo .obj y .lib están bien definidos y no cambian casi nunca. A veces se realizan adiciones a estos formatos de archivo, pero no suelen afectar a la capacidad de los conjuntos de herramientas más recientes de consumir los archivos objeto y las bibliotecas que los conjuntos de herramientas anteriores producen. La única excepción significativa es si se efectúa la compilación con [/GL (Optimización de todo el programa)](../build/reference/gl-whole-program-optimization.md). Si realiza la compilación con `/GL`, el archivo objeto resultante solo se podrá vincular con el mismo conjunto de herramientas que se haya usado para crearlo. Por lo tanto, si produce un archivo objeto con `/GL` y usa el compilador de Visual Studio 2017 (v141), deberá vincularlo con el enlazador de Visual Studio 2017 (v141). Esto se debe a que las estructuras de datos internas de los archivos objeto no son estables en las versiones principales del conjunto de herramientas y a que los conjuntos de herramientas más recientes no entienden los formatos de datos más antiguos.

C++ no tiene una interfaz binaria de aplicaciones (ABI) estable. Visual Studio mantiene una ABI de C++ estable para todas las versiones secundarias de una versión. Por ejemplo, Visual Studio 2017 y todas sus actualizaciones son compatibles a nivel binario. Pero la ABI no es necesariamente compatible con las versiones principales de Visual Studio (excepto 2015 y 2017, que _son_ compatibles con los binarios). Es decir, podemos hacer cambios importantes en el diseño de tipo de C++, la decoración de nombres, el control de excepciones y otros elementos de la ABI de C++. Por lo tanto, si dispone de un archivo objeto con símbolos externos y vinculación de C++, dicho archivo objeto podría no estar vinculado correctamente a los archivos objeto generados mediante otra versión principal del conjunto de herramientas. Tenga en cuenta que, en este caso, cuando decimos que podría no funcionar, contemplamos muchas posibilidades: el vínculo puede producir un error (por ejemplo, si la decoración de nombres ha cambiado), el vínculo podría ser correcto, pero las cosas podrían no funcionar en el entorno de ejecución (por ejemplo, si el diseño de tipo ha cambiado) o, en muchos casos, es posible que todo funcione bien. Además, tenga en cuenta que, aunque la ABI de C++ no es estable, la ABI de C y el subconjunto de la ABI de C++ requeridos para COM son estables.

Si establece un vínculo con una biblioteca de importación, las versiones posteriores de las bibliotecas redistribuibles de Visual Studio que conserven la compatibilidad con ABI se podrán usar en el entorno de ejecución. Por ejemplo, si la aplicación se compila y vincula con el conjunto de herramientas de Visual Studio 2015 Update 3, podrá utilizar cualquier biblioteca redistribuible de Visual Studio 2017, puesto que las bibliotecas de las versiones 2015 y 2017 conservan la compatibilidad binaria con versiones anteriores. El caso contrario no es aplicable, ya que no puede usar una biblioteca redistribuible para una versión anterior del conjunto de herramientas a la que haya utilizado para compilar el código, incluso en el caso de que ABI sea compatible.

### <a name="libraries"></a>Bibliotecas

Si compila un archivo de código fuente con una versión determinada de los archivos de encabezado de las bibliotecas de Visual Studio C++ (mediante la inclusión de los encabezados), el archivo objeto resultante debe vincularse con la misma versión de las bibliotecas. Por ejemplo, si el archivo de origen se compila con \<immintrin.h> de Visual Studio 2015 Update 3, debe vincularlo con la biblioteca vcruntime de Visual Studio 2015 Update 3. Del mismo modo, si el archivo de origen se compila con \<iostream> de la versión 15.5 de Visual Studio 2017, debe vincularlo con msvcprt, la biblioteca estándar de C++ de la versión 15.5 de Visual Studio 2017. No se permite mezclar y combinar.

En el caso de la biblioteca estándar de C++, se ha deshabilitado explícitamente la opción de mezclar y combinar mediante el uso de `#pragma detect_mismatch` en los encabezados estándar a partir de Visual Studio 2010. Si intenta vincular archivos objeto incompatibles, o si intenta vincular con una biblioteca estándar incorrecta, se producirá un error en el vínculo.

En el caso de CRT, nunca se ha admitido la opción de mezclar y combinar, pero a menudo funcionaba, al menos hasta Visual Studio 2015 y CRT universal, ya que la superficie de API no ha cambiado mucho a lo largo del tiempo. CRT universal interrumpió la compatibilidad con versiones anteriores para que en el futuro podamos mantener la compatibilidad con versiones anteriores. En otras palabras, no tenemos pensado introducir en el futuro archivos binarios nuevos de CRT universal con versiones. En su lugar, hemos actualizado en contexto CRT universal.

Para proporcionar compatibilidad de vínculo parcial con archivos objeto (y bibliotecas) compilados con versiones anteriores de los encabezados de tiempo de ejecución de Microsoft C, proporcionamos una biblioteca (legacy_stdio_definitions.lib) con Visual Studio 2015 y versiones posteriores. Esta biblioteca proporciona símbolos de compatibilidad para la mayoría de las funciones y exportaciones de datos que se quitaron de CRT universal. El conjunto de símbolos de compatibilidad proporcionado por legacy_stdio_definitions.lib es suficiente para satisfacer la mayoría de las dependencias, incluidas todas las dependencias de las bibliotecas incluidas en Windows SDK. Pero hay algunos símbolos que se quitaron de CRT universal para los que no se pueden proporcionar símbolos de compatibilidad. Estos símbolos incluyen algunas funciones (por ejemplo, \_\_iob\_func) y las exportaciones de datos (por ejemplo, \_\_imp\_\_\_iob, \_\_imp\_\_\_pctype, \_\_imp\_\_\_mb\_cur\_max).

Si tiene una biblioteca estática que se ha compilado con una versión anterior de los encabezados de tiempo de ejecución de C, recomendamos las acciones siguientes (en este orden):

1. Recompile la biblioteca estática con Visual Studio 2017 y los encabezados de CRT universal para admitir la vinculación con CRT universal. Esta es una opción totalmente compatible (y, por tanto, la mejor).

1. Si no puede (o no quiere) recompilar la biblioteca estática, puede intentar vincularla con legacy\_stdio\_definitions.lib. Si satisface las dependencias en tiempo de vínculo de la biblioteca estática, puede que le interese probar exhaustivamente la biblioteca estática como se usa en el binario, para asegurarse de que no se ve afectada negativamente por alguno de los [cambios de comportamiento que se realizaron en CRT universal](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Si legacy\_stdio\_definitions.lib no cumple las dependencias de la biblioteca estática o si esta no funciona con CRT universal debido a los cambios de comportamiento mencionados anteriormente, recomendamos encapsular la biblioteca estática en un archivo DLL y vincularlo con la versión correcta del entorno de ejecución de Microsoft C. Por ejemplo, si la biblioteca estática se compiló con Visual Studio 2013, es posible que quiera compilar dicho DLL, así como las bibliotecas de C++ de Visual Studio 2013, con Visual Studio 2013. Al compilar la biblioteca en una DLL, encapsula el detalle de implementación que es su dependencia en una versión determinada del tiempo de ejecución de Microsoft C. (Tenga en cuenta que deberá procurar que no se produzca una pérdida por parte de la interfaz DLL de los detalles del tiempo de ejecución de C que usa, por ejemplo, al devolver un archivo* a través del límite de DLL o al devolver un puntero asignado por malloc y esperar a que el autor de la llamada lo libere).

El uso de varios CRT en un mismo proceso no es en sí mismo problemático (de hecho, la mayoría de los procesos acaban cargando varias DLL de CRT; por ejemplo, los componentes del sistema operativo Windows dependen de msvcrt.dll y CLR depende de su propio CRT privado). Los problemas se producen cuando se mezcla el estado de diferentes CRT. Por ejemplo, no debe asignar memoria mediante msvcr110.dll!malloc e intentar desasignarla mediante msvcr120.dll!free, y no debe intentar abrir un archivo con msvcr110!fopen e intentar leer desde ese archivo mediante msvcr120!fread. Mientras no mezcle el estado de diferentes CRT, no hay problema en que se carguen varios CRT en un mismo proceso.

Para obtener más información, vea [Upgrade your code to the Universal CRT](upgrade-your-code-to-the-universal-crt.md) (Actualizar código a CRT universal).

## <a name="errors-due-to-project-settings"></a>Errores debidos a la configuración del proyecto

Para comenzar el proceso de actualización, basta con que abra un proyecto, solución o área de trabajo antiguos en la versión más reciente de Visual Studio. Visual Studio creará un proyecto nuevo basado en la configuración del proyecto antiguo. Si el proyecto antiguo tiene una biblioteca o incluye rutas de acceso codificadas de forma rígida en ubicaciones no estándar, es posible que los archivos situados en esas rutas de acceso no estén visibles para el compilador cuando el proyecto usa la configuración predeterminada. Para obtener más información, vea [Configuración de OutputFile del vinculador](porting-guide-spy-increment.md#linker_output_settings).

En general, ahora es un buen momento para organizar correctamente el código del proyecto a fin de simplificar el mantenimiento del proyecto y ayudar a compilar el código actualizado de la manera más rápida posible. Si el código fuente ya está bien organizado y el proyecto antiguo está compilado con Visual Studio 2010 o versiones posteriores, puede editar manualmente el archivo de proyecto nuevo para admitir la compilación en el compilador antiguo y en el nuevo. En el ejemplo siguiente se muestra cómo se compila para Visual Studio 2015 y Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: externo sin resolver

En el caso de los símbolos sin resolver, es posible que tenga que corregir la configuración del proyecto.

- Si el archivo de código fuente se encuentra en una ubicación no predeterminada, ¿ha agregado la ruta de acceso a los directorios de inclusión del proyecto?

- Si el externo está definido en un archivo .lib, ¿ha especificado la ruta de acceso de lib en las propiedades del proyecto y se encuentra realmente allí la versión correcta del archivo .lib?

- ¿Está intentando vincular un archivo .lib compilado con una versión diferente de Visual Studio? Si es así, consulte la sección anterior sobre las dependencias de biblioteca y de conjunto de herramientas.

- ¿Coinciden realmente los tipos de los argumentos en el sitio de llamada con una sobrecarga existente de la función? Compruebe que los tipos subyacentes de las definiciones de tipo de la firma de la función y del código que llama a la función son los esperados.

Para solucionar errores de símbolo sin resolver, puede probar a usar dumpbin.exe para examinar los símbolos definidos en un archivo binario. Pruebe la siguiente línea de comandos para ver los símbolos definidos en una biblioteca:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t es un tipo nativo)

(En Microsoft Visual C++ 6.0 y versiones anteriores, **wchar_t** no se implementaba como tipo integrado, sino que se declaraba en wchar.h como definición de tipo para un entero corto sin signo). El estándar de C++ requiere que **wchar_t** sea un tipo integrado. Si usa la versión de definición de tipo, pueden producirse problemas de portabilidad. Si actualiza desde versiones anteriores de Visual Studio y encuentra un error del compilador C2664 porque el código intenta convertir implícitamente **wchar_t** en un **entero corto sin signo**, es recomendable cambiar el código para corregir el error, en lugar de establecer `/Zc:wchar_t-`. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Actualizar con las opciones del enlazador /NODEFAULTLIB, /ENTRY y /NOENTRY

La opción `/NODEFAULTLIB` del enlazador (o la propiedad del enlazador Omitir todas las bibliotecas predeterminadas) indica al enlazador que no vincule automáticamente las bibliotecas predeterminadas como CRT. Esto significa que cada biblioteca tiene que aparecer como entrada individual. Esta lista de bibliotecas se proporciona en la propiedad **Dependencias adicionales** en la sección **Enlazador** del cuadro de diálogo **Propiedades del proyecto**.

Los proyectos que usan esta opción presentan un problema al actualizar, ya que los nombres de algunas de las bibliotecas predeterminadas han cambiado. Dado que cada biblioteca tiene que aparecer en la propiedad **Dependencias adicionales** o en la línea de comandos del enlazador, deberá actualizar la lista de bibliotecas para que use los nombres actuales.

En la tabla siguiente se muestran las bibliotecas cuyos nombres han cambiado a partir de Visual Studio 2015. Para actualizar, debe reemplazar los nombres de la primera columna por los nombres de la segunda columna. Algunas de las bibliotecas son bibliotecas de importación, pero esto no importa.

|||
|-|-|
|Si usaba:|Debe reemplazarlo por:|
|libcmt.lib|libucrt.lib, libvcruntime.lib|
|libcmtd.lib|libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|ucrt.lib, vcruntime.lib|
|msvcrtd.lib|ucrtd.lib, vcruntimed.lib|

El mismo problema se aplica si usa la opción `/ENTRY` o la opción `/NOENTRY`, que también permiten omitir las bibliotecas predeterminadas.

## <a name="errors-due-to-improved-language-conformance"></a>Errores debidos a la conformidad de lenguaje mejorada

El Compilador de Microsoft Visual C++ ha mejorado continuamente su conformidad con el estándar de C++ a lo largo de los años. El código compilado en versiones anteriores podría no compilarse en Visual Studio 2017 porque el compilador marca correctamente un error que antes omitía o permitía explícitamente.

Por ejemplo, el modificador `/Zc:forScope` se introdujo en las primeras versiones de MSVC. Permite un comportamiento no conforme para las variables de bucle. Este modificador ahora está en desuso y podría quitarse en versiones futuras. Se recomienda encarecidamente no usar este modificador al actualizar el código. Para obtener más información, vea [/Zc:forScope- está en desuso](porting-guide-spy-increment.md#deprecated_forscope).

Por ejemplo, es habitual que aparezca un error del compilador al actualizar cuando se pasa un argumento que no es const a un parámetro const. Las versiones antiguas del compilador no siempre lo marcaban como error. Para obtener más información, vea [Las conversiones más estrictas del compilador](porting-guide-spy-increment.md#stricter_conversions).

Para obtener más información sobre mejoras de conformidad específicas, vea [Historial de cambios en Visual C++ 2003-2015](visual-cpp-change-history-2003-2015.md) y [Mejoras de conformidad de C++ en Visual Studio 2017](../cpp-conformance-improvements-2017.md).

## <a name="errors-involving-stdinth-integral-types"></a>Errores relacionados con tipos enteros \<stdint.h>

El encabezado \<stdint.h> define definiciones de tipos y macros que, a diferencia de los tipos enteros integrados, tienen una longitud específica garantizada en todas las plataformas. Algunos ejemplos son `uint32_t` y `int64_t`. El encabezado \<stdint.h> se agregó en Visual Studio 2010. El código escrito antes de 2010 podría haber proporcionado definiciones privadas para esos tipos y esas definiciones podrían no ser siempre coherentes con las definiciones \<stdint.h>.

Si el error es C2371 y está implicado un tipo `stdint`, probablemente significa que el tipo está definido en un encabezado, ya sea en el código o en un archivo lib de terceros. Al actualizar, debe eliminar todas las definiciones personalizadas de tipos \<stdint.h>, pero primero compare las definiciones personalizadas con las definiciones estándar actuales para asegurarse de que no incorpora nuevos problemas.

Puede pulsar **F12** (**Ir a definición**) para ver dónde está definido el tipo en cuestión.

La opción del compilador [/showIncludes](../build/reference/showincludes-list-include-files.md) puede resultar útil en este caso. En el cuadro de diálogo **Páginas de propiedades** del proyecto, abra la página **C/C++** > **Avanzadas** y establezca **Mostrar inclusiones** en **Sí**. Después, recompile el proyecto y vea la lista de `#include` en la ventana de salida. Se aplica sangría a cada encabezado bajo el encabezado que lo incluye.

## <a name="errors-involving-crt-functions"></a>Errores relacionados con funciones de CRT

A lo largo de los años, se han realizado muchos cambios en el tiempo de ejecución de C. Se han agregado muchas versiones seguras de funciones y algunas se han quitado. Además, como se describe anteriormente en este artículo, la implementación de CRT por parte de Microsoft se ha refactorizado en Visual Studio 2015 en nuevos binarios y archivos .lib asociados.

Si un error está relacionado con una función de CRT, consulte [Historial de cambios en Visual C++ 2003-2015](visual-cpp-change-history-2003-2015.md) o [Mejoras de conformidad de C++ en Visual Studio 2017](../cpp-conformance-improvements-2017.md) para ver si los temas contienen información adicional. Si el error es LNK2019: externo sin resolver, asegúrese de que no se ha quitado la función. Si está seguro de que la función todavía existe y el código de llamada es correcto, compruebe si el proyecto usa `/NODEFAULTLIB`. Si es así, debe actualizar la lista de bibliotecas para que el proyecto use las nuevas bibliotecas universales (UCRT). Vea la sección anterior sobre la biblioteca y las dependencias para obtener más información.

Si el error está relacionado con `printf` o `scanf`, asegúrese de que no esté definiendo de manera privada alguna función sin incluir stdio.h. Si es así, quite las definiciones privadas o vincúlelas a legacy\_stdio\_definitions.lib. Puede configurar esta opción en el cuadro de diálogo **Páginas de propiedades**, en **Propiedades de configuración** > **Enlazador** > **Entrada**, en la propiedad **Dependencias adicionales**. Si está realizando la vinculación con Windows SDK 8.1 o versiones anteriores, agregue legacy\_stdio\_definitions.lib.

Si el error está relacionado con argumentos de cadena de formato, se trata probablemente de que el compilador es más estricto a la hora de aplicar el estándar. Vea el historial de cambios para obtener más información. Preste mucha atención a los errores que se produzcan, ya que pueden representar un riesgo de seguridad.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Errores debidos a cambios en el estándar de C++

El estándar de C++ ha evolucionado de maneras que no siempre son compatibles con versiones anteriores. La introducción en C++11 de semántica de transferencia de recursos, nuevas palabras clave y otras características de lenguaje y biblioteca estándar puede provocar errores del compilador e incluso un comportamiento diferente en tiempo de ejecución.

Por ejemplo, un programa de C++ antiguo puede incluir el encabezado iostream.h. Este encabezado quedó en desuso en las primeras versiones de C++ y, finalmente, se eliminó por completo de Visual Studio. En este caso, deberá usar \<iostream> y volver a escribir el código. Para obtener más información, vea [Actualizar el código antiguo de iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: advertencia de conversión de restricción

El estándar de C++ ahora especifica que las conversiones de valores enteros sin signo a con signo se consideran conversiones de restricción. El compilador no emitía esta advertencia en versiones anteriores a Visual Studio 2015. Debe inspeccionar cada aparición para asegurarse de que la restricción no afecta a la corrección del código.

## <a name="warnings-to-use-secure-crt-functions"></a>Advertencias para usar funciones de CRT seguras

A lo largo de los años, se han introducido versiones seguras de funciones de tiempo de ejecución de C. Aunque las versiones no seguras antiguas siguen estando disponibles, se recomienda que cambie el código para usar las versiones seguras. El compilador emitirá una advertencia del uso de versiones no seguras. Puede decidir deshabilitar u omitir estas advertencias. Para deshabilitar la advertencia en todos los proyectos de la solución, abra **Ver** > **Administrador de propiedades**, seleccione los proyectos, haga clic con el botón derecho en los elementos seleccionados y elija **Propiedades**. En el cuadro de diálogo **Páginas de propiedades**, en **Propiedades de configuración** > **C/C++** > **Avanzadas**, seleccione **Deshabilitar advertencias específicas**. Haga clic en la flecha desplegable y, después, en **Editar**. Escriba 4996 en el cuadro de texto. (No incluya el prefijo "C"). Para obtener más información, vea [Migrar para usar las funciones seguras de CRT](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Errores debidos a cambios en las API de Windows o SDK obsoletos

A lo largo de los años, se han agregado API de Windows y tipos de datos y, a veces, se han cambiado o eliminado. Además, han aparecido y desaparecido otros SDK que no pertenecían al sistema operativo principal. Por lo tanto, algunos programas antiguos pueden contener llamadas a API que ya no existen. También pueden contener llamadas a API de otros SDK de Microsoft que ya no son compatibles. Si ve un error relacionado con una API de Windows o una API de un SDK de Microsoft antiguo, es posible que se haya quitado la API o que se haya reemplazado por una función más reciente y más segura.

Para obtener más información sobre el conjunto de API actual y los sistemas operativos mínimos compatibles con una API específica de Windows, consulte el [Catálogo de referencia y API de Microsoft](https://msdn.microsoft.com/library) y vaya a la API en cuestión.

### <a name="windows-version"></a>Versión de Windows

Al actualizar un programa que usa la API de Windows directa o indirectamente, debe decidir la versión mínima de Windows con la que es compatible. En la mayoría de los casos, Windows 7 es una buena elección. Para obtener más información, vea [Problemas de archivos de encabezado](porting-guide-spy-increment.md#header_file_problems). La macro `WINVER` define la versión de Windows más antigua en la que puede ejecutarse el programa. Si el programa MFC establece WINVER en 0x0501 (Windows XP), obtendrá una advertencia porque MFC ya no es compatible con XP, aunque el compilador tenga un modo XP.

Para obtener más información, vea [Actualizar la versión de Windows de destino](porting-guide-spy-increment.md#updating_winver) y [Más archivos de encabezado obsoletos](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL/MFC

ATL y MFC son API relativamente estables, pero en ocasiones se realizan cambios. Para obtener más información, vea [Historial de cambios en Visual C++ 2003-2015](visual-cpp-change-history-2003-2015.md), [Novedades de Visual C++ en Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) y [Mejoras de conformidad de C++ en Visual Studio 2017](../cpp-conformance-improvements-2017.md).

### <a name="lnk-2005-dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 ya definido en MSVCRTD.lib

Este error puede producirse en las aplicaciones MFC. Indica un problema de ordenación entre la biblioteca CRT y la biblioteca MFC. Es necesario vincular MFC primero para que proporcione operadores new y delete. Para solucionar el error, use el modificador `/NODEFAULTLIB` para omitir estas bibliotecas predeterminadas: MSVCRTD.lib y mfcs140d.lib. Después, agregue estas mismas bibliotecas como dependencias adicionales.

## <a name="32-vs-64-bit"></a>32 bits frente a 64 bits

Si el código original está compilado para sistemas de 32 bits, tiene la opción de crear una versión de 64 bits en lugar de una aplicación nueva de 32 bits o además de ella. En general, debe hacer que el programa compile primero en modo de 32 bits y, después, intentarlo en 64 bits. La compilación para 64 bits es sencilla, pero en algunos casos puede revelar errores que estaban ocultos en las compilaciones de 32 bits.

Además, debe ser consciente de los posibles problemas en tiempo de compilación y en tiempo de ejecución relacionados con el tamaño del puntero, los valores de tiempo y tamaño, y los especificadores de formato en funciones printf y scanf. Para obtener más información, vea [Configurar Visual C++ en destinos de 64 bits, x64](../build/configuring-programs-for-64-bit-visual-cpp.md) y [Problemas comunes de migración a 64 bits en Visual C++](../build/common-visual-cpp-64-bit-migration-issues.md). Para obtener sugerencias adicionales de migración, vea [Programming Guide for 64-bit Windows](/windows/desktop/WinProg64/programming-guide-for-64-bit-windows) (Guía de programación de Windows de 64 bits).

## <a name="unicode-vs-mbcsascii"></a>Unicode frente a MBCS/ASCII

Antes de que se estandarizase Unicode, muchos programas usaban el juego de caracteres multibyte (MBCS) para representar los caracteres que no estaban incluidos en el juego de caracteres ASCII. En proyectos de MFC antiguos, MBCS era la configuración predeterminada y, al actualizar el programa, verá advertencias que aconsejan que use Unicode en su lugar. Puede deshabilitar o ignorar la advertencia si decide que la conversión a Unicode es un costo de desarrollo que no merece la pena. Para deshabilitarla en todos los proyectos de la solución, abra **Ver** > **Administrador de propiedades**, seleccione todos los proyectos, haga clic con el botón derecho en los elementos seleccionados y elija **Propiedades**. En el cuadro de diálogo **Páginas de propiedades**, seleccione **Propiedades de configuración** > **C/C++** > **Avanzadas**. En la propiedad **Deshabilitar advertencias específicas**, abra la flecha desplegable y elija **Editar**. Escriba 4996 en el cuadro de texto. (No incluya el prefijo "C"). Elija **Aceptar** para guardar la propiedad y de nuevo **Aceptar** para guardar los cambios.

Para obtener más información, vea [Migrar de MBCS a Unicode](porting-guide-spy-increment.md#porting_to_unicode). Para obtener información general sobre MBCS frente a Unicode, vea [Texto y cadenas en Visual C++](../text/text-and-strings-in-visual-cpp.md) e [Internacionalización](../c-runtime-library/internationalization.md).

## <a name="see-also"></a>Vea también

[Actualizar proyectos desde versiones anteriores de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Mejoras de conformidad de C++ en Visual Studio 2017](../cpp-conformance-improvements-2017.md)