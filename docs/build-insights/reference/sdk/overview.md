---
title: C++ Build Insights SDK
description: Descripción general del SDK de Visual Studio C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 126abb0d039227eb269500966d46ef0a729763ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323259"
---
# <a name="c-build-insights-sdk"></a>C++ Build Insights SDK

::: moniker range="<=vs-2015"

El SDK de C++ Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range=">=vs-2017"

El SDK de C++ Build Insights es una colección de API que le permiten crear herramientas personalizadas encima de la plataforma C++ Build Insights. Esta página proporciona una visión general de alto nivel para ayudarle a empezar.

## <a name="obtaining-the-sdk"></a>Obtención del SDK

Puede descargar el SDK de C++ Build Insights como un paquete NuGet siguiendo estos pasos:

1. Desde Visual Studio 2017 y versiones posteriores, cree un nuevo proyecto de C++.
1. En el **panel Explorador** de soluciones, haga clic con el botón secundario en el proyecto.
1. Seleccione **Administrar paquetes NuGet** en el menú contextual.
1. En la parte superior derecha, seleccione el origen del paquete **nuget.org.**
1. Busque la versión más reciente del paquete Microsoft.Cpp.BuildInsights.
1. Elija **Instalar**.
1. Acepte la licencia.

Siga leyendo para obtener información sobre los conceptos generales que rodean el SDK. También puede acceder al repositorio oficial de GitHub de ejemplos de [C++ Build Insights](https://github.com/microsoft/cpp-build-insights-samples) para ver ejemplos de aplicaciones C++ reales que usan el SDK.

## <a name="collecting-a-trace"></a>Recopilación de un rastro

El uso del SDK de C++ Build Insights para analizar los eventos que salen de la cadena de herramientas MSVC requiere que primero recopile un seguimiento. El SDK hace uso de Seguimiento de eventos para Windows (ETW) como la tecnología de seguimiento subyacente. La recopilación de un seguimiento se puede hacer de dos maneras:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Método 1: uso de vcperf en Visual Studio 2019 y versiones posteriores

1. Abra un símbolo del sistema con privilegios elevados x64 Native Tools para VS 2019.
1. Ejecute el comando siguiente: `vcperf /start MySessionName`.
1. Compile el proyecto.
1. Ejecute el comando siguiente: `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`.

   > [!IMPORTANT]
   > Utilice `/stopnoanalyze` el comando al detener el seguimiento con vcperf. No puede usar el SDK de C++ Build Insights `/stop` para analizar los seguimientos detenidos por el comando normal.

### <a name="method-2-programmatically"></a>Método 2: mediante programación

Use cualquiera de estas funciones de recopilación de seguimiento del SDK de C++ Build Insights para iniciar y detener los seguimientos mediante programación. **El programa que ejecuta estas llamadas de función debe tener privilegios administrativos.** Solo las funciones de seguimiento de inicio y detención requieren privilegios administrativos. Todas las demás funciones del SDK de C++ Build Insights se pueden ejecutar sin ellas.

### <a name="sdk-functions-related-to-trace-collection"></a>Funciones del SDK relacionadas con la colección de seguimientos

| Funcionalidad | API de C++ | API de C |
|--|--|--|
| Inicio de un seguimiento | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Detener un rastro | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Detener un rastro y<br />inmediatamente analizando el resultado | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessiona](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Detener un rastro y<br />inmediatamente relogging el resultado | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

Las secciones siguientes muestran cómo configurar un análisis o una sesión de reregistro. Es necesario para las funciones de funcionalidad combinadas, como [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Consumir un seguimiento

Una vez que tenga un seguimiento ETW, use el SDK de C++ Build Insights para desempaquetarlo. El SDK le proporciona los eventos en un formato que le permite desarrollar sus herramientas rápidamente. No se recomienda consumir el seguimiento ETW sin procesar sin usar el SDK. El formato de evento utilizado por MSVC es indocumentado, optimizado para escalar a grandes compilaciones, y difícil de entender. Además, la API del SDK de C++ Build Insights es estable, mientras que el formato de seguimiento ETW sin procesar está sujeto a cambios sin previo aviso.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Tipos y funciones de SDK relacionados con el consumo de seguimiento

| Funcionalidad | API de C++ | API de C | Notas |
|--|--|--|--|
| Configuración de devoluciones de llamada de eventos | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | El SDK de C++ Build Insights proporciona eventos a través de funciones de devolución de llamada. En C++, implemente las funciones de devolución de llamada creando una clase analyzer o relogger que herede la interfaz IAnalyzer o IRelogger. En C, implemente las devoluciones de llamada en funciones globales y proporcione punteros a ellas en la estructura ANALYSIS_CALLBACKS o RELOG_CALLBACKS. |
| Grupos de construcción | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | La API de C++ proporciona funciones y tipos auxiliares para agrupar varios objetos de analizador y reregistrador. Los grupos son una manera ordenada de dividir un análisis complejo en pasos más simples. [vcperf](https://github.com/microsoft/vcperf) se organiza de esta manera. |
| Analizar o volver a registrar | [Analizar](functions/analyze.md)<br />[Relog](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Análisis y relogging

El consumo de un seguimiento se realiza a través de una sesión de análisis o una sesión de reslogging.

El uso de un análisis regular es adecuado para la mayoría de los escenarios. Este método le ofrece la flexibilidad de `printf` elegir el formato de salida: text, xml, JSON, database, llamadas REST, etc.

El reregistro es para análisis de propósito especial que necesitan producir un archivo de salida ETW. Mediante el reregistro, puede traducir los eventos de C++ Build Insights a su propio formato de evento ETW. Un uso adecuado del reregistro sería enlazar los datos de C++ Build Insights a sus herramientas e infraestructura ETW existentes. Por ejemplo, [vcperf](https://github.com/microsoft/vcperf) hace uso de las interfaces de relogging. Esto se debe a que debe producir datos que el Analizador de rendimiento de Windows, una herramienta ETW, puede comprender. Se requiere cierto conocimiento previo de cómo funciona ETW si planea utilizar las interfaces de reregistro.

### <a name="creating-analyzer-groups"></a>Creación de grupos de analizadores

Es importante saber cómo crear grupos. Este es un ejemplo que muestra cómo crear un grupo de analizadores que imprime *Hello, world!* por cada evento de inicio de actividad que recibe.

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>Uso de eventos

### <a name="sdk-types-and-functions-related-to-events"></a>Tipos y funciones de SDK relacionados con eventos

| Funcionalidad | API de C++ | API de C | Notas |
|--|--|--|--|
| Eventos de coincidencia y filtrado | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | La API de C++ ofrece funciones que facilitan la extracción de los eventos que más le importan de sus seguimientos. Con la API de C, este filtrado debe realizarse a mano. |
| Tipos de datos de eventos | [Actividad](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[Commandline](cpp-event-data-types/command-line.md)<br />[Compilador](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Evento](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Función](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[Invocación](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Enlazador](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Hilo](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Actividades y eventos sencillos

Los eventos vienen en dos categorías: *actividades* y *eventos simples.* Las actividades son procesos continuos en el tiempo que tienen un principio y un final. Los eventos simples son ocurrencias puntuales y no tienen una duración. Al analizar los seguimientos de MSVC con el SDK de C++ Build Insights, recibirá eventos independientes cuando se inicie y se detenga una actividad. Solo recibirás un evento cuando se produzca un evento simple.

### <a name="parent-child-relationships"></a>Relaciones padre-hijo

Las actividades y los eventos simples están relacionados entre sí a través de relaciones padre-hijo. El elemento primario de una actividad o evento simple es la actividad que abarca en la que se producen. Por ejemplo, al compilar un archivo de código fuente, el compilador tiene que analizar el archivo y, a continuación, generar el código. Las actividades de análisis y generación de código son elementos secundarios de la actividad del compilador.

Los eventos simples no tienen una duración, por lo que no puede pasar nada más dentro de ellos. Como tal, nunca tienen hijos.

Las relaciones primario-secundario de cada actividad y evento simple se indican en la tabla de [eventos](event-table.md). Conocer estas relaciones es importante cuando se consumen eventos de C++ Build Insights. A menudo tendrá que confiar en ellos para comprender el contexto completo de un evento.

### <a name="properties"></a>Propiedades

Todos los eventos tienen las siguientes propiedades:

| Propiedad | Descripción |
|--|--|
| Identificador de tipo | Número que identifica de forma única el tipo de evento. |
| Identificador de instancia | Número que identifica de forma única el evento dentro del seguimiento. Si se producen dos eventos del mismo tipo en un seguimiento, ambos obtienen un identificador de instancia único. |
| Hora de inicio | La hora en que se inició una actividad o la hora en que se produjo un evento simple. |
| Identificador de proceso | Número que identifica el proceso en el que se produjo el evento. |
| Identificador de subproceso | Número que identifica el subproceso en el que se produjo el evento. |
| Indice del procesador | Un índice de base cero que indica el procesador lógico por el que se emitió el evento. |
| Nombre del evento | Cadena que describe el tipo de evento. |

Todas las actividades que no sean eventos simples también tienen estas propiedades:

| Propiedad | Descripción |
|--|--|
| Tiempo de parada | La hora en que se detuvo la actividad. |
| Duración exclusiva | El tiempo que pasa en una actividad, excluyendo el tiempo que dedica a sus actividades secundarias. |
| Tiempo de CPU | El tiempo que la CPU pasó ejecutando código en el subproceso asociado a la actividad. No incluye el tiempo en el que el subproceso conectado a la actividad estaba en suspensión. |
| Tiempo exclusivo de CPU | Igual que el tiempo de CPU, pero excluyendo el tiempo de CPU empleado por las actividades secundarias. |
| Responsabilidad del horario del reloj de pared | La contribución de la actividad al tiempo general del reloj de pared. La responsabilidad del tiempo del reloj de pared tiene en cuenta el paralelismo entre las actividades. Por ejemplo, supongamos que dos actividades no relacionadas se ejecutan en paralelo. Ambos tienen una duración de 10 segundos, y exactamente el mismo tiempo de inicio y parada. En este caso, Build Insights asigna una responsabilidad de tiempo de reloj de pared de 5 segundos. Por el contrario, si estas actividades se ejecutan una tras otra sin superposición, a ambas se les asigna una responsabilidad de tiempo de reloj de pared de 10 segundos. |
| Responsabilidad exclusiva del horario del reloj de pared | Igual que la responsabilidad del horario del reloj de pared, pero excluye la responsabilidad del horario de la hora de la pared de las actividades infantiles. |

Algunos eventos tienen sus propias propiedades más allá de las mencionadas. En este caso, estas propiedades adicionales se enumeran en la tabla de [eventos](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Consumir eventos proporcionados por el SDK de C++ Build Insights

#### <a name="the-event-stack"></a>La pila de eventos

Cada vez que el SDK de C++ Build Insights proporciona un evento, viene en forma de pila. La última entrada de la pila es el evento actual y las entradas antes de que sean su jerarquía primaria. Por ejemplo, los eventos de inicio y detención [de LTCG](event-table.md#ltcg) se producen durante el paso 1 del vinculador. En este caso, la pila que \[recibiría contiene: [LINKER](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. La jerarquía primaria es conveniente porque puede rastrear un evento hasta su raíz. Si la actividad LTCG mencionada anteriormente es lenta, puede saber inmediatamente qué invocación del vinculador estuvo involucrada.

#### <a name="matching-events-and-event-stacks"></a>Coincidencia de eventos y pilas de eventos

El SDK de C++ Build Insights le proporciona todos los eventos de un seguimiento, pero la mayoría de las veces solo le importa un subconjunto de ellos. En algunos casos, es posible que solo le importe un subconjunto de pilas de *eventos.* El SDK proporciona instalaciones para ayudarle a extraer rápidamente los eventos o la pila de eventos que necesita y rechazar los que no. Se hace a través de estas funciones de coincidencia:

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | Mantenga un evento si coincide con uno de los tipos especificados. Reenvíe los eventos coincidentes a una expresión lambda u otro tipo invocable. Esta función no tiene en cuenta la jerarquía primaria del evento. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Mantenga un evento si coincide con el tipo especificado en el parámetro de una función miembro. Reenviar eventos coincidentes a la función miembro. Esta función no tiene en cuenta la jerarquía primaria del evento. |
| [MatchEventStack](functions/match-event-stack.md) | Mantenga un evento si el evento y su jerarquía primaria coinciden con los tipos especificados. Reenvíe el evento y los eventos de jerarquía primaria coincidentes a una expresión lambda u otro tipo invocable. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Mantenga un evento si el evento y su jerarquía primaria coinciden con los tipos especificados en la lista de parámetros de una función miembro. Reenvíe el evento y los eventos de jerarquía primariocoincidentes a la función miembro. |

Las funciones de `MatchEventStack` coincidencia de la pila de eventos, como permiten que los espacios al describir la jerarquía primaria coincidan. Por ejemplo, puede decir que está \[interesado en la pila [LINKER](event-table.md#linker), [LTCG.](event-table.md#ltcg) \] También coincidiría \[con la pila LINKER, [PASS1,](event-table.md#pass1)LTCG.\] El último tipo especificado debe ser el tipo de evento que se va a coincidir y no forma parte de la jerarquía primaria.

#### <a name="capture-classes"></a>Clases de captura

El `Match*` uso de las funciones requiere que especifique los tipos que desea que coincidan. Estos tipos se seleccionan de una lista de clases de *captura.* Las clases de captura vienen en varias categorías, que se describen a continuación.

| Category | Descripción |
|--|--|
| Exact | Estas clases de captura se utilizan para hacer coincidir un tipo de evento específico y ninguno otro. Un ejemplo es la clase [Compiler,](cpp-event-data-types/compiler.md) que coincide con el evento [COMPILER.](event-table.md#compiler) |
| Wildcard (Carácter comodín) | Estas clases de captura se pueden utilizar para hacer coincidir cualquier evento de la lista de eventos que admiten. Por ejemplo, el carácter comodín [Actividad](cpp-event-data-types/activity.md) coincide con cualquier evento de actividad. Otro ejemplo es el comodín [CompilerPass,](cpp-event-data-types/compiler-pass.md) que puede coincidir con el [evento FRONT_END_PASS](event-table.md#front-end-pass) o [BACK_END_PASS.](event-table.md#back-end-pass) |
| Grupo | Los nombres de las clases de captura de grupo terminan en *Grupo*. Se usan para hacer coincidir varios eventos del mismo tipo en una fila, ignorando los huecos. Solo tienen sentido al hacer coincidir eventos recursivos, porque no sabe cuántos existen en la pila de eventos. Por ejemplo, la actividad [FRONT_END_FILE](event-table.md#front-end-file) se produce cada vez que el compilador analiza un archivo. Esta actividad es recursiva porque el compilador puede encontrar una directiva include mientras analiza el archivo. La clase [FrontEndFile](cpp-event-data-types/front-end-file.md) solo coincide con un evento FRONT_END_FILE de la pila. Utilice la clase [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) para que coincida con toda la jerarquía de inclusión. |
| Grupo de comodines | Un grupo de caracteres comodín combina las propiedades de comodines y grupos. La única clase de esta categoría es [InvocationGroup](cpp-event-data-types/invocation-group.md), que coinciden y capturan todos los eventos [LINKER](event-table.md#linker) y [COMPILER](event-table.md#compiler) en una sola pila de eventos. |

Consulte la tabla de [eventos](event-table.md) para saber qué clases de captura se pueden utilizar para hacer coincidir cada evento.

#### <a name="after-matching-using-captured-events"></a>Después de la coincidencia: utilizando los eventos capturados

Una vez que una coincidencia `Match*` se completa correctamente, las funciones construyen los objetos de clase de captura y los reenvían a la función especificada. Utilice estos objetos de clase de captura para tener acceso a las propiedades de los eventos.

#### <a name="example"></a>Ejemplo

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
