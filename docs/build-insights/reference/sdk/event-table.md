---
title: 'C++SDK de Build Insights: tabla de eventos'
description: Referencia de eventos para el SDK C++ de Visual Studio Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ccc8a4ef707942963b85edc6db9e21e05610b54
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422965"
---
# <a name="c-build-insights-sdk-event-table"></a>C++SDK de Build Insights: tabla de eventos

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>Eventos del compilador

\ [del compilador](#compiler)
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

## <a name="compiler-back-end-events"></a>Eventos de back-end del compilador

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[Subproceso](#thread)\
\ de [función](#function)
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>Eventos del enlazador

\ [del vinculador](#linker)
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
\ [PASS1](#pass1)
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
|  | Parents | [COMPILACIÓN](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propiedades | -Ruta de acceso absoluta al archivo de origen de entrada<br/>-Ruta de acceso absoluta al archivo de objeto de salida |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | Descripción | Se produce al iniciar y detener el paso de back-end del compilador. Este paso es responsable de optimizar el código de C/C++ Source analizado y convertirlo en código máquina. |
| <a name="bottom-up"></a>BOTTOM_UP | Tipo | Actividad |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | Descripción | Se produce al iniciar y detener todo el análisis de todo el programa. |
| <a name="c1-dll"></a>C1_DLL | Tipo | Actividad |
|  | Parents | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Descripción | Se produce al iniciar y detener una invocación de *C1. dll* o *C1XX. dll* . Estos archivos dll son el C C++ y el front-end del compilador. Se invocan únicamente mediante el controlador del compilador (*cl. exe*). |
| <a name="c2-dll"></a>C2_DLL | Tipo | Actividad |
|  | Parents | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Descripción | Se produce al iniciar y detener una invocación de *C2. dll* . Este archivo DLL es el back-end del compilador. Lo llama el controlador del compilador (*cl. exe*). También lo invoca el enlazador (*Link. exe*) cuando se usa la generación de código en tiempo de vínculo. |
| <a name="code-generation"></a>CODE_GENERATION | Tipo | Actividad |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [FUNCTION](#function)<br/>[CONVERSACIONES](#thread) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | Descripción | Se produce al inicio y al final de la fase de generación de código del back-end. |
| <a name="command-line"></a>COMMAND_LINE | Tipo | Evento sencillo |
|  | Parents | [COMPILACIÓN](#compiler)<br/>[DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | -La línea de comandos que se usó para invocar *cl. exe* o *Link. exe* |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[CommandLine](cpp-event-data-types/command-line.md) |
|  | Descripción | Se produce cuando el compilador y el vinculador finalizan la evaluación de la línea de comandos. La línea de comandos evaluada incluye todos los parámetros *cl. exe* y *Link. exe* pasados a través de un archivo de respuesta. También incluye parámetros para *cl. exe* y *Link. exe* pasados a través de variables de entorno como cl, \_cl\_, link y \_Link\_. |
| <a name="compiler"></a>COMPILACIÓN | Tipo | Actividad |
|  | Parents | None |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Propiedades | -Versión del compilador<br/>-Directorio de trabajo<br/>-Ruta de acceso absoluta al *cl. exe* invocado |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Invocación](cpp-event-data-types/invocation.md)<br/>[Compilación](cpp-event-data-types/compiler.md) |
|  | Descripción | Se produce al iniciar y detener una invocación de *cl. exe* . |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | Tipo | Evento sencillo |
|  | Parents | [COMPILACIÓN](#compiler)<br/>[DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | : El nombre de la variable de entorno.<br/>: El valor de la variable de entorno. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Descripción | Se produce una vez para cada variable de entorno existente en el momento en que se invoca *cl. exe* o *Link. exe* . |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | : La ruta de acceso absoluta a un archivo DLL o un archivo de salida ejecutable. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Descripción | Se produce cuando una de las entradas del enlazador es una DLL o un archivo de imagen ejecutable. |
| <a name="exp-output"></a>EXP_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | : La ruta de acceso absoluta a un archivo de salida *. exp* . |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | Descripción | Se produce cuando una de las salidas del enlazador es un archivo *. exp* . |
| <a name="file-input"></a>FILE_INPUT | Tipo | Evento sencillo |
|  | Parents | [COMPILACIÓN](#compiler)<br/>[DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | -La ruta de acceso absoluta al archivo de entrada<br/>-El tipo de archivo de entrada |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | Descripción | Se produce para anunciar una entrada de *cl. exe* o *Link. exe* . |
| <a name="force-inlinee"></a>FORCE_INLINEE | Tipo | Evento sencillo |
|  | Parents | [FUNCTION](#function) |
|  | Children | None |
|  | Propiedades | : El nombre de la función insertada en el forzado.<br/>: El tamaño de la función insertada por fuerza, representada como un recuento de instrucciones intermedias. |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Descripción | Se produce cuando una función se inserta obligatoriamente en otra función mediante el uso de la palabra clave `__forceinline`. |
| <a name="front-end-file"></a>FRONT_END_FILE | Tipo | Actividad |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propiedades | : Ruta de acceso absoluta al archivo. |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | Descripción | Se produce cuando el front-end del compilador inicia y detiene el procesamiento de un archivo. Este evento es recursivo. La recursividad se produce cuando el front-end está analizando los archivos incluidos. |
| <a name="front-end-pass"></a>FRONT_END_PASS | Tipo | Actividad |
|  | Parents | [COMPILACIÓN](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Propiedades | -Ruta de acceso absoluta al archivo de origen de entrada<br/>-Ruta de acceso absoluta al archivo de objeto de salida |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | Descripción | Se produce al iniciar y detener el paso de front-end del compilador. Este paso es responsable de analizar el códigoC++ de C/source y convertirlo en lenguaje intermedio. |
| <a name="function"></a>FUNCIONALIDAD | Tipo | Actividad |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[CONVERSACIONES](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Propiedades | : Nombre de la función |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Function](cpp-event-data-types/function.md) |
|  | Descripción | Se produce al iniciar y finalizar la generación del código para una función. |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | : La ruta de acceso absoluta a un archivo de salida de la biblioteca de importación. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | Descripción | Se produce cuando una de las salidas del enlazador es una biblioteca de importación. |
| <a name="lib-output"></a>LIB_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | : La ruta de acceso absoluta a un archivo de salida de biblioteca estática. |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Descripción | Se produce cuando uno de los resultados del enlazador es una biblioteca estática. |
| <a name="linker"></a>DEL VINCULADOR | Tipo | Actividad |
|  | Parents | None |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Propiedades | -Versión del vinculador<br/>-Directorio de trabajo<br/>-Ruta de acceso absoluta al *archivo Link. exe* invocado |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Invocación](cpp-event-data-types/invocation.md)<br/>[Linker](cpp-event-data-types/linker.md) |
|  | Descripción | Se produce al iniciar y detener una invocación de *Link. exe* . |
| <a name="ltcg"></a>LTCG | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Descripción | Se produce al iniciar y detener la generación de código en tiempo de vínculo. |
| <a name="obj-output"></a>OBJ_OUTPUT | Tipo | Evento sencillo |
|  | Parents | [COMPILACIÓN](#compiler) |
|  | Children | None |
|  | Propiedades | -La ruta de acceso absoluta al archivo de salida *. obj* |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | Descripción | Se produce una vez para cada salida *. obj* generada por *cl. exe*. |
| <a name="opt-icf"></a>OPT_ICF | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | Descripción | Se produce al iniciar y detener la optimización del enlazador de plegamientos de COMDAT idénticos (/OPT: ICF). |
| <a name="opt-lbr"></a>OPT_LBR | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Descripción | Se produce al iniciar y detener la optimización del enlazador de rama larga (/OPT: LBR). |
| <a name="opt-ref"></a>OPT_REF | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Descripción | Se produce al iniciar y detener las funciones sin referencia y la optimización del enlazador de la eliminación de datos (/OPT: REF). |
| <a name="pass1"></a>PASS1 | Tipo | Actividad |
|  | Parents | [DEL VINCULADOR](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Descripción | Se produce al iniciar y detener el paso 1 del vinculador. |
| <a name="pass2"></a>PASS2 | Tipo | Actividad |
|  | Parents | [DEL VINCULADOR](#linker) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Descripción | Se produce al iniciar y detener el paso 2 del vinculador. |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | Tipo | Actividad |
|  | Parents | [PASS1](#pass1) |
|  | Children | None |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Descripción | Se produce al iniciar y detener el paso de optimización del enlazador que elimina las funciones y los datos sin referencia (/OPT: REF). Se realiza antes de la generación de código en tiempo de vínculo. |
| <a name="symbol-name"></a>SYMBOL_NAME | Tipo | Evento sencillo |
|  | Parents | [C1_DLL](#c1-dll) |
|  | Children | None |
|  | Propiedades | -Una clave de tipo<br/> -El nombre del tipo |
|  | Clases de captura | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | Descripción | Se produce al final de la fase de front-end: una vez por cada tipo implicado en las instancias de plantilla. La clave es un identificador numérico para el tipo, mientras que el nombre es su representación de texto. Las claves de tipo son únicas en el seguimiento que se está analizando. Sin embargo, las distintas claves que provienen de diferentes fases de front-end del compilador pueden apuntar al mismo tipo. La comparación de tipos entre diferentes pasos de front-end del compilador requiere el uso de sus nombres. SYMBOL_NAME eventos se emiten al final de una fase de front-end del compilador, después de que se hayan realizado todas las creaciones de instancias de la plantilla. |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | Tipo | Actividad |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Propiedades | -La clave para el tipo especializado<br/>: La clave del tipo de la plantilla principal<br/>-El tipo de plantilla de la que se ha creado una instancia |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | Descripción | Se produce al principio y al final de una instancia de la plantilla. Se crea una instancia de un tipo de plantilla principal (como `vector`), lo que da como resultado un tipo especializado (como `std::vector<int>`). Se proporciona una clave para ambos tipos. Utilice el evento [SYMBOL_NAME](#symbol-name) para convertir una clave en el nombre del tipo. Las claves de tipo son únicas en el seguimiento que se está analizando. Sin embargo, las distintas claves que provienen de diferentes fases de front-end del compilador pueden apuntar al mismo tipo. La comparación de tipos entre diferentes pasos de front-end del compilador requiere el uso de nombres de símbolos. Este evento es recursivo. En algunos casos, la recursividad se produce cuando el front-end crea instancias de plantillas anidadas. |
| <a name="thread"></a>CONVERSACIONES | Tipo | Actividad |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FUNCTION](#function) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Subproceso](cpp-event-data-types/thread.md) |
|  | Descripción | Se produce al principio y al final de la ejecución de un subproceso de back-end del compilador. Un subproceso que se está suspendiendo se considera finalizado. Un subproceso que se está reactivarán se considera iniciado. |
| <a name="top-down"></a>TOP_DOWN | Tipo | Actividad |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [FUNCTION](#function)<br/>[CONVERSACIONES](#thread) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[Desactivación](cpp-event-data-types/top-down.md) |
|  | Descripción | Se produce al iniciar y detener todo el análisis de todo el programa. |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | Tipo | Actividad |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Propiedades | None |
|  | Clases de captura | [Actividad](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Descripción | Se produce al iniciar y detener la fase de análisis de todo el programa de generación de código en tiempo de vínculo. |

::: moniker-end
