---
title: /MP (Compilar con varios procesos)
ms.date: 02/22/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MultiProcessorCompilation
helpviewer_keywords:
- -MP compiler option (C++)
- /MP compiler option (C++)
- MP compiler option (C++)
- cl.exe compiler, multi-process build
ms.openlocfilehash: d0a3e50ca75535d505e46c0e454a8e0902b1ffb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562089"
---
# <a name="mp-build-with-multiple-processes"></a>/MP (Compilar con varios procesos)

La opción **/MP** puede reducir el tiempo total de compilación de los archivos de origen en la línea de comandos. La opción **/MP** hace que el compilador cree una o varias copias de sí mismo, cada una en un proceso independiente. Después, estas copias compilan simultáneamente los archivos de origen. Por consiguiente, se puede reducir considerablemente el tiempo total necesario para compilar los archivos de origen.

## <a name="syntax"></a>Sintaxis

> **/MP**[*processMax*]

## <a name="arguments"></a>Argumentos

*processMax*<br/>
(Opcional) Número máximo de procesos que puede crear el compilador.

El *processMax* argumento debe estar comprendido entre 1 y 65536. En caso contrario, el compilador emite el mensaje de advertencia **D9014**, omite la *processMax* argumento y supone que el número máximo de procesos es 1.

Si se omite el *processMax* argumento, el compilador recupera el número de [procesadores efectivos](#effective_processors) en el equipo desde el sistema operativo y crea un proceso para cada procesador.

## <a name="remarks"></a>Comentarios

La opción del compilador **/MP** puede reducir considerablemente el tiempo de compilación al compilar varios archivos. Para mejorar el tiempo de compilación, el compilador crea hasta *processMax* copias de sí mismo y, a continuación, usa para compilar los archivos de origen al mismo tiempo. La opción **/MP** se aplica a las compilaciones, no a la generación de código de vinculación ni a la generación de código en tiempo de vínculo. De forma predeterminada, la opción **/MP** está desactivada.

La mejora en el tiempo de compilación depende del número de procesadores que hay en un equipo, del número de archivos que se van a compilar y de la disponibilidad de los recursos del sistema, como la capacidad de E/S. Experimente con la opción **/MP** para determinar la mejor configuración para compilar un proyecto en concreto. Para obtener consejos que le ayuden a tomar esa decisión, consulte [Instrucciones](#guidelines).

## <a name="incompatible-options-and-language-features"></a>Opciones y características de lenguaje incompatibles

La opción **/MP** es incompatible con algunas opciones del compilador y algunas características de lenguaje. Si usa una opción del compilador incompatible con la **/MP** opción, el compilador emite la advertencia **D9030** y omite la **/MP** opción. Si usa una característica de lenguaje incompatible, el compilador emite el error [C2813](../../error-messages/compiler-errors-2/compiler-error-c2813.md) y termina o continúa, según el compilador actual de la opción de nivel de advertencia.

> [!NOTE]
> La mayoría de las opciones son incompatibles porque, de lo contrario, los compiladores que se ejecutan a la vez escribirían sus resultados al mismo tiempo en la consola o en un archivo determinado. Por consiguiente, el resultado podría combinarse y resultar confuso. En algunos casos, la combinación de opciones podría empeorar el rendimiento.

En la siguiente tabla aparecen las opciones del compilador y las características de lenguaje que no son compatibles con la opción **/MP** :

|Opción o característica de lenguaje|Descripción|
|--------------------------------|-----------------|
|Directiva de preprocesador[#import](../../preprocessor/hash-import-directive-cpp.md) |Convierte los tipos en una biblioteca de tipos en clases de C++ y las escribe en un archivo de encabezado.|
|[/E](../../build/reference/e-preprocess-to-stdout.md), [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Copia los resultados del preprocesador en los resultados estándar (**stdout**).|
|[/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|Permite una reconstrucción incremental.|
|[/showIncludes](../../build/reference/showincludes-list-include-files.md)|Escribe una lista de archivos de inclusión en el error estándar (**stderr**).|
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Escribe un archivo de encabezado precompilado.|

## <a name="diagnostic-messages"></a>Mensajes de diagnóstico

Si especifica una opción o una característica de lenguaje que no es compatible con la opción **/MP** , recibirá un mensaje de diagnóstico. En la siguiente tabla aparecen los mensajes y el comportamiento del compilador:

|Mensaje de diagnóstico|Descripción|Comportamiento del compilador|
|------------------------|-----------------|-----------------------|
|**C2813**|La directiva **#import** no es compatible con la opción **/MP** .|La compilación finaliza a menos que una opción de [nivel de advertencia del compilador](../../build/reference/compiler-option-warning-level.md) especifique lo contrario.|
|**D9014**|Se especificó un valor no válido para el *processMax* argumento.|El compilador omite el valor no válido y presupone el valor 1.|
|**D9030**|La opción especificada no es compatible con **/MP**.|El compilador omite la opción **/MP** .|

## <a name="guidelines"></a> Instrucciones

### <a name="measure-performance"></a>Medir el rendimiento

Use el tiempo de compilación total para medir el rendimiento. Puede medir el tiempo de compilación con un reloj físico o con un software que calcule la diferencia entre el inicio y el final de la compilación. Si su equipo tiene varios procesadores, un reloj físico podría aportar unos resultados más precisos que una medición de tiempo de un software.

### <a name="effective_processors"></a> Effective Processors

Un equipo puede tener uno o más procesadores virtuales, también conocidos como *procesadores efectivos*, para cada uno de los procesadores físicos. Cada procesador físico puede tener uno o varios núcleos y, si el sistema operativo permite la tecnología hyperthreading para un núcleo, cada uno de ellos actúa como dos procesadores virtuales.

Por ejemplo, un equipo tiene un procesador efectivo si tiene un procesador físico que tiene un núcleo y la tecnología hyperthreading está deshabilitada. En cambio, un equipo tiene ocho procesadores efectivos si tiene dos procesadores físicos, cada uno de los cuales tiene dos núcleos y todos los núcleos tienen habilitada la tecnología hyperthreading. Es decir, (8 procesadores efectivos) = (2 procesadores físicos) x (2 núcleos por procesador físico) x (2 procesadores efectivos por núcleo debido al hyperthreading).

Si se omite el *processMax* argumento en el **/MP** opción, el compilador obtiene el número de procesadores efectivos desde el sistema operativo y, a continuación, crea un proceso por cada procesador efectivo. Hay que tener en cuenta que el compilador no puede garantizar qué proceso se ejecuta en un procesador en concreto: el encargado de tomar esa decisión es el sistema operativo.

### <a name="number-of-processes"></a>Número de procesos

El compilador calcula el número de procesos que va a usar para compilar los archivos de origen. Ese valor es el número más bajo del número de archivos de origen que especifica en la línea de comandos y el número de procesos que especifica explícita o implícitamente con la opción **/MP** . Puede establecer explícitamente el número máximo de procesos si proporciona el *processMax* argumento de la **/MP** opción. O bien puede usar el valor predeterminado, que es igual al número de procesadores efectivos en un equipo, si se omite el *processMax* argumento.

Por ejemplo, imagínese que especifica la siguiente línea de comandos:

`cl /MP7 a.cpp b.cpp c.cpp d.cpp e.cpp`

En este caso, el compilador usa cinco procesos, ya que es el número más bajo de cinco archivos de origen y un máximo de siete procesos. También puede imaginarse que su equipo tiene dos procesadores efectivos y especifica la siguiente línea de comandos:

`cl /MP a.cpp b.cpp c.cpp`

En este caso, el sistema operativo detecta dos procesadores; por lo tanto, el compilador usará dos procesos en sus cálculos. Como resultado, el compilador ejecutará la compilación con dos procesos, ya que ese es el número más bajo de dos procesos y tres archivos de origen.

### <a name="source-files-and-build-order"></a>Archivos de origen y orden de compilación

Es posible que los archivos de origen no se compilen en el mismo orden en el que aparecen en la línea de comandos. Aunque el compilador crea un conjunto de procesos que contienen copias del compilador, el sistema operativo programa el momento en el que se ejecuta cada proceso. Por consiguiente, no se puede garantizar que los archivos de origen se compilen en un orden determinado.

Un archivo de origen se compila cuando un proceso está disponible para la compilación. Si hay más archivos que procesos, los procesos disponibles compilan el primer conjunto de archivos. Los archivos restantes se procesan cuando un proceso acaba de tratar un archivo anterior y está disponible para trabajar en uno de los archivos restantes.

No especifique el mismo archivo de origen varias veces en una línea de comandos. Esto puede ocurrir, por ejemplo, si una herramienta crea automáticamente un [archivo Make](../../build/contents-of-a-makefile.md) que se basa en la información de dependencia de un proyecto. Si no especifica la opción **/MP** , el compilador procesa secuencialmente la lista de archivos y vuelve a compilar todas las apariciones del archivo. Pero si la especifica **/MP** , es posible que diferentes compiladores compilen el mismo archivo a la vez. Por consiguiente, los distintos compiladores intentarán escribir en el mismo archivo de salida a la vez. Un compilador obtendrá correctamente acceso exclusivo de escritura en el archivo de salida, mientras que en el resto de los compiladores se producirá un error de acceso al archivo.

### <a name="using-type-libraries-import"></a>Usar bibliotecas de tipos (#import)

El compilador no admite el uso de la directiva [#import](../../preprocessor/hash-import-directive-cpp.md) con el modificador **/MP** . Si es posible, siga estos pasos para solucionar este problema:

- Mueva todas las directivas `#import` de los distintos archivos de origen a uno o varios archivos y compílelos sin la opción **/MP** . El resultado será un conjunto de archivos de encabezado generados.

- En los otros archivos de origen, inserte directivas [#include](../../preprocessor/hash-include-directive-c-cpp.md) que especifiquen los encabezados generados y compile los archivos de origen restantes con la opción **/MP** .

### <a name="visual-studio-project-settings"></a>Configuración de un proyecto de Visual Studio

#### <a name="the-msbuildexe-tool"></a>Herramienta MSBUILD.exe

Visual Studio usa el [MSBuild.exe](/visualstudio/msbuild/msbuild-reference) herramienta para crear soluciones y proyectos. El **/maxcpucount:**_número_ (o **/m:**_número_) opción de línea de comandos de la herramienta MSBuild.exe puede crear varios proyectos en la mismo tiempo. mientras que la opción del compilador **/MP** puede crear varias unidades de compilación al mismo tiempo. Si es adecuado para su aplicación, mejore el tiempo de compilación de la solución usando **/MP** , **/maxcpucount**o ambas opciones.

El tiempo de compilación de la solución depende en parte del número de procesos que llevan a cabo la compilación. El *número* argumento de la [/maxcpucount](/visualstudio/msbuild/msbuild-command-line-reference) MSBuild opción especifica el número máximo de proyectos para compilar al mismo tiempo. De forma similar, el *processMax* argumento de la **/MP** opción del compilador especifica el número máximo de unidades de compilación para compilar al mismo tiempo. Si el **/maxcpucount** especifica la opción *P* proyectos y la **/MP** especifica la opción *C* procesa un máximo de *P*  x *C* procesos se ejecutan al mismo tiempo.

El criterio para decidir si se debe usar MSBuild o **/MP** tecnología es como sigue:

- Si hay muchos proyectos con pocos archivos en cada proyecto, use la herramienta MSBuild.

- Si hay pocos proyectos con muchos archivos en cada proyecto, use la opción **/MP** .

- Si el número de proyectos y archivos por proyecto está equilibrado, use ambos MSBuild y **/MP**. Para comenzar, establezca la opción **maxcpucount** en el número de proyectos que se van a crear y la opción **/MP** en el número de procesadores que hay en su equipo. Mida el rendimiento y, luego, ajuste la configuración para conseguir los mejores resultados. Repita este ciclo hasta que esté satisfecho con el tiempo de compilación total.

#### <a name="the-gm-compiler-option"></a>Opción del compilador /Gm

De forma predeterminada, la compilación de un proyecto permite la opción del compilador **/Gm** (compilaciones incrementales) para las compilaciones de depuración y la deshabilita para las compilaciones de versión. Por lo tanto, la opción del compilador **/MP** se deshabilita automáticamente en las compilaciones de depuración, puesto que entra en conflicto con la opción del compilador **/Gm** predeterminada.

## <a name="see-also"></a>Vea también

[directiva #import](../../preprocessor/hash-import-directive-cpp.md)<br/>
[Referencia de la línea de comandos](/visualstudio/msbuild/msbuild-command-line-reference)<br/>
[/Zf (generación de PDB más rápida)](zf.md)<br/>
