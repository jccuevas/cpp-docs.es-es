---
title: 'SDK de C++ Build Insights: tabla de eventos'
description: Referencia de eventos para el SDK de Visual Studio C++ Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 932b78347e05d313e7962da2fdff8c3454dec963
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324140"
---
# <a name="c-build-insights-sdk-event-table"></a>SDK de C++ Build Insights: tabla de eventos

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Eventos del compilador

[Compilador](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>Eventos front-end del compilador

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>Eventos back-end del compilador

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[Hilo](#thread)\
[Función](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Eventos de vinculador

[Vinculador](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>Tabla de eventos

| Evento | Propiedad | Descripción |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | Tipo | Actividad |
|  | Parents | [Compilador](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propiedades | - Ruta absoluta al archivo de origen de entrada<br/>- Ruta absoluta al archivo de objeto de salida |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | Descripción | Se produce al iniciar y detener el paso de back-end del compilador. Este pase es responsable de optimizar el código fuente C/C++ analizado y convertirlo en código de máquina. |
| <a name="bottom-up"></a>BOTTOM_UP | Tipo | Actividad |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | Descripción | Se produce al inicio y al detenerse de todo el paso de abajo hacia arriba del análisis del programa. |
| <a name="c1-dll"></a>C1_DLL | Tipo | Actividad |
|  | Parents | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Descripción | Se produce al iniciar y detener una invocación *c1.dll* o *c1xx.dll.* Estos archivos DLL son el front-end C y C++ del compilador. Se invocan únicamente por el controlador del compilador (*cl.exe*). |
| <a name="c2-dll"></a>C2_DLL | Tipo | Actividad |
|  | Parents | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Descripción | Se produce al iniciar y detener una invocación *c2.dll.* Este archivo DLL es el back-end del compilador. Lo llama el controlador del compilador (*cl.exe*). También lo invoca el vinculador (*link.exe*) cuando se usa la generación de código en tiempo de vínculo. |
| <a name="code-generation"></a>CODE_GENERATION | Tipo | Actividad |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [Función](#function)<br/>[Hilo](#thread) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | Descripción | Se produce al inicio y a la detención de la fase de generación de código del back-end. |
| <a name="command-line"></a>COMMAND_LINE | Tipo | Evento sencillo |
|  | Parents | [Compilador](#compiler)<br/>[Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | - La línea de comandos que se usó para invocar *cl.exe* o *link.exe* |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Commandline](cpp-event-data-types/command-line.md) |
|  | Descripción | Se produce cuando el compilador y el vinculador han terminado de evaluar la línea de comandos. La línea de comandos evaluada incluye todos los parámetros *cl.exe* y *link.exe* pasados a través de un archivo de respuesta. También incluye parámetros para *cl.exe* y *link.exe* pasados \_\_a través \_\_de variables de entorno como CL, CL, LINK y LINK . |
| <a name="compiler"></a>Compilador | Tipo | Actividad |
|  | Parents | None |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Propiedades | - Versión del compilador<br/>- Directorio de trabajo<br/>- Ruta absoluta al *cl.exe* invocado |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Invocación](cpp-event-data-types/invocation.md)<br/>[Compilador](cpp-event-data-types/compiler.md) |
|  | Descripción | Se produce al inicio y al parar de una invocación *cl.exe.* |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Tipo | Evento sencillo |
|  | Parents | [Compilador](#compiler)<br/>[Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | - El nombre de la variable de entorno<br/>- El valor de la variable de entorno. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Descripción | Se produce una vez por cada variable de entorno existente en el momento en que se invoca *cl.exe* o *link.exe.* |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | - La ruta absoluta a un archivo DLL o ejecutable. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Descripción | Se produce cuando una de las entradas del vinculador es un archivo DLL o un archivo de imagen ejecutable. |
| <a name="exp-output"></a>EXP_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | - La ruta absoluta a un archivo de salida *.exp.* |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | Descripción | Se produce cuando una de las salidas del vinculador es un archivo *.exp.* |
| <a name="file-input"></a>FILE_INPUT | Tipo | Evento sencillo |
|  | Parents | [Compilador](#compiler)<br/>[Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | - La ruta absoluta al archivo de entrada<br/>- El tipo de archivo de entrada |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | Descripción | Se produce para anunciar una entrada *cl.exe* o *link.exe.* |
| <a name="force-inlinee"></a>FORCE_INLINEE | Tipo | Evento sencillo |
|  | Parents | [Función](#function) |
|  | Children | None |
|  | Propiedades | - El nombre de la función de fuerza insertada.<br/>- El tamaño de la función de forzar insertada, representado como un recuento de instrucciones intermedio. |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Descripción | Se produce cuando una función se está insertando `__forceinline` por la fuerza en otra función mediante el uso de la palabra clave. |
| <a name="front-end-file"></a>FRONT_END_FILE | Tipo | Actividad |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propiedades | - Ruta absoluta al archivo. |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | Descripción | Se produce cuando el front-end del compilador se inicia y detiene el procesamiento de un archivo. Este evento es recursivo. La recursividad se produce cuando el front-end analiza los archivos incluidos. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Tipo | Actividad |
|  | Parents | [Compilador](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Propiedades | - Ruta absoluta al archivo de origen de entrada<br/>- Ruta absoluta al archivo de objeto de salida |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | Descripción | Se produce al iniciar y detener el paso de front-end del compilador. Este pase es responsable de analizar el código fuente de C/C++ y convertirlo en un lenguaje intermedio. |
| <a name="function"></a>Función | Tipo | Actividad |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[Hilo](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Propiedades | - Nombre de la función |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Función](cpp-event-data-types/function.md) |
|  | Descripción | Se produce al iniciar y finalizar la generación del código de una función. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | - La ruta absoluta a un archivo de salida de la biblioteca de importación. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | Descripción | Se produce cuando una de las salidas del vinculador es una biblioteca de importación. |
| <a name="lib-output"></a>LIB_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | - La ruta absoluta a un archivo de salida de biblioteca estática. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Descripción | Se produce cuando una de las salidas del vinculador es biblioteca estática. |
| <a name="linker"></a>Vinculador | Tipo | Actividad |
|  | Parents | None |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Propiedades | - Versión del vinculador<br/>- Directorio de trabajo<br/>- Ruta absoluta al *link.exe* invocado |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Invocación](cpp-event-data-types/invocation.md)<br/>[Enlazador](cpp-event-data-types/linker.md) |
|  | Descripción | Se produce al iniciar y detener una invocación *link.exe.* |
| <a name="ltcg"></a>LTCG | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Descripción | Se produce al iniciar y detener la generación de código en tiempo de vínculo. |
| <a name="obj-output"></a>OBJ_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [Compilador](#compiler) |
|  | Children | None |
|  | Propiedades | - La ruta absoluta al archivo de salida *.obj* |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | Descripción | Se produce una vez por cada salida *.obj* producida por *cl.exe*. |
| <a name="opt-icf"></a>OPT_ICF | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | Descripción | Se produce al inicio y detención de la optimización del vinculador COMDAT idéntico (/OPT:ICF). |
| <a name="opt-lbr"></a>OPT_LBR | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Descripción | Se produce al inicio y a la parada de la optimización del vinculador de la rama larga (/OPT:LBR). |
| <a name="opt-ref"></a>OPT_REF | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Descripción | Se produce al inicio y al detención de las funciones sin referencia y la optimización del vinculador de eliminación de datos (/OPT:REF). |
| <a name="pass1"></a>PASS1 | Tipo | Actividad |
|  | Parents | [Vinculador](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Descripción | Se produce al inicio y a la parada del pase 1 del vinculador. |
| <a name="pass2"></a>PASS2 | Tipo | Actividad |
|  | Parents | [Vinculador](#linker) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Descripción | Se produce al inicio y a la parada del pase 2 del vinculador. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Descripción | Se produce al iniciar y detener el paso de optimización del vinculador que elimina las funciones y los datos sin referencia (/OPT:REF). Se hace antes de la generación de código en tiempo de enlace. |
| <a name="symbol-name"></a>SYMBOL_NAME | Tipo | Evento sencillo |
|  | Parents | [C1_DLL](#c1-dll) |
|  | Children | None |
|  | Propiedades | - Una tecla de tipo<br/> - El nombre del tipo |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | Descripción | Se produce al final del paso de front-end: una vez por cada tipo implicado en las instancias de plantilla. La clave es un identificador numérico para el tipo, mientras que el nombre es su representación de texto. Las claves de tipo son únicas dentro del seguimiento que se está analizando. Sin embargo, diferentes claves procedentes de diferentes pasos de front-end del compilador pueden apuntar al mismo tipo. La comparación de tipos entre diferentes pasos de front-end del compilador requiere el uso de sus nombres. SYMBOL_NAME eventos se emiten al final de un paso de front-end del compilador, después de que se hayan realizado todas las instancias de plantilla. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Tipo | Actividad |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propiedades | - La clave para el tipo especializado<br/>- La clave para el tipo de plantilla principal<br/>- El tipo de plantilla que se crea una instancia |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Descripción | Se produce al principio y al final de una creación de instancias de plantilla. Se crea una instancia `vector`de un tipo de plantilla principal (como ) , lo que da como resultado un tipo especializado (como `std::vector<int>`). Se proporciona una clave para ambos tipos. Utilice el evento [SYMBOL_NAME](#symbol-name) para convertir una clave en el nombre del tipo. Las claves de tipo son únicas dentro del seguimiento que se está analizando. Sin embargo, diferentes claves procedentes de diferentes pasos de front-end del compilador pueden apuntar al mismo tipo. La comparación de tipos entre diferentes pasadas de front-end del compilador requiere el uso de nombres de símbolo. Este evento es recursivo. La recursividad se produce en algunos casos cuando el front-end está creando instancias de plantillas anidadas. |
| <a name="thread"></a>Hilo | Tipo | Actividad |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [Función](#function) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Hilo](cpp-event-data-types/thread.md) |
|  | Descripción | Se produce al principio y al final de la ejecución de un subproceso back-end del compilador. Un subproceso que se suspende se considera finalizado. Se considera iniciado un hilo que se está despertando. |
| <a name="top-down"></a>TOP_DOWN | Tipo | Actividad |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [Función](#function)<br/>[Hilo](#thread) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | Descripción | Se produce al inicio y al detenerse del paso descendente de todo el análisis del programa. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Tipo | Actividad |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Descripción | Se produce al inicio y al detenerse de la fase de análisis de todo el programa de la generación de código en tiempo de enlace. |

::: moniker-end
