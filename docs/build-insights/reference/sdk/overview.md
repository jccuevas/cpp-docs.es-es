---
title: C++SDK de Build Insights
description: Información general sobre el SDK de C++ Visual Studio Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aafcc65bc30de77131d1945c9f4e78361db14ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334035"
---
# <a name="c-build-insights-sdk"></a>C++SDK de Build Insights

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

El C++ SDK de Build Insights es una colección de API que le permiten crear herramientas personalizadas sobre la C++ plataforma de información de compilación. En esta página se proporciona información general de alto nivel para ayudarle a empezar.

## <a name="obtaining-the-sdk"></a>Obtención del SDK

Puede descargar el C++ SDK de Build Insights como un paquete NuGet siguiendo estos pasos:

1. En Visual Studio 2017 y versiones posteriores, cree un C++ nuevo proyecto.
1. En el panel **Explorador de soluciones** , haga clic con el botón derecho en el proyecto.
1. Seleccione **administrar paquetes NuGet** en el menú contextual.
1. En la parte superior derecha, seleccione el origen del paquete **Nuget.org** .
1. Busque la versión más reciente del paquete Microsoft. cpp. BuildInsights.
1. Elija **instalar**.
1. Acepte la licencia.

Siga leyendo para obtener información sobre los conceptos generales relacionados con el SDK. También puede acceder al repositorio de [ C++ GitHub de ejemplos de Build Insights](https://github.com/microsoft/cpp-build-insights-samples) para ver ejemplos de aplicaciones C++ reales que usan el SDK.

## <a name="collecting-a-trace"></a>Recopilar un seguimiento

El uso C++ del SDK de Build Insights para analizar los eventos que salen de la cadena de herramientas de MSVC requiere que primero se recopile un seguimiento. El SDK hace uso del seguimiento de eventos para Windows (ETW) como la tecnología de seguimiento subyacente. La recopilación de un seguimiento se puede realizar de dos maneras:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>Método 1: uso de vcperf en Visual Studio 2019 y versiones posteriores

1. Abra una símbolo del sistema de las herramientas nativas x64 con privilegios elevados para VS 2019.
1. Ejecute el siguiente comando: `vcperf /start MySessionName`
1. Compile el proyecto.
1. Ejecute el siguiente comando: `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Use el comando `/stopnoanalyze` al detener el seguimiento con vcperf. No se puede usar C++ el SDK de Build Insights para analizar los seguimientos detenidas por el comando normal de `/stop`.

### <a name="method-2-programmatically"></a>Método 2: mediante programación

Use cualquiera de estas C++ funciones de colección de seguimiento del SDK de Build Insights para iniciar y detener los seguimientos mediante programación. **El programa que ejecuta estas llamadas de función debe tener privilegios administrativos.** Solo las funciones de seguimiento de inicio y detención requieren privilegios administrativos. Todas las demás funciones del C++ SDK de Build Insights se pueden ejecutar sin ellas.

### <a name="sdk-functions-related-to-trace-collection"></a>Funciones de SDK relacionadas con la recopilación de seguimiento

| Funcionalidad | API de C++ | API de C |
|--|--|--|
| Iniciar un seguimiento | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| Detener un seguimiento | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| Detener un seguimiento y<br />analizar inmediatamente el resultado | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| Detener un seguimiento y<br />reregistro inmediato del resultado | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

En las secciones siguientes se muestra cómo configurar un análisis o una sesión de registro. Se requiere para las funciones de funcionalidad combinada, como [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md).

## <a name="consuming-a-trace"></a>Consumir un seguimiento

Una vez que tenga un seguimiento de ETW, C++ use el SDK de Build Insights para desempaquetarlo. El SDK proporciona los eventos en un formato que le permite desarrollar sus herramientas rápidamente. No se recomienda utilizar el seguimiento de ETW sin procesar sin usar el SDK. El formato de evento usado por MSVC no está documentado, optimizado para escalar a grandes compilaciones y difícil de tener sentido. Además, la C++ API del SDK de Build Insights es estable, mientras que el formato de seguimiento de ETW sin formato está sujeto a cambios sin previo aviso.

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>Tipos y funciones de SDK relacionados con el consumo de seguimiento

| Funcionalidad | API de C++ | API de C | Notas |
|--|--|--|--|
| Configurar devoluciones de llamada de eventos | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | El C++ SDK de Build Insights proporciona eventos a través de funciones de devolución de llamada. En C++, implemente las funciones de devolución de llamada mediante la creación de una clase de analizador o de reregistrador que herede la interfaz IAnalyzer o IRelogger. En C, implemente las devoluciones de llamada en las funciones globales y proporcione punteros a ellas en la estructura ANALYSIS_CALLBACKS o RELOG_CALLBACKS. |
| Crear grupos | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | La C++ API proporciona funciones y tipos auxiliares para agrupar varios objetos de analizador y de registro. Los grupos son una forma cómoda de dividir un análisis complejo en pasos más sencillos. [vcperf](https://github.com/microsoft/vcperf) se organiza de esta manera. |
| Analizar o reregistrar | [Análisis](functions/analyze.md)<br />[Registrar](functions/relog.md) | [Analizara](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>Analizar y reregistrar

El consumo de un seguimiento se realiza a través de una sesión de análisis o una sesión de reinicio.

El uso de un análisis normal es adecuado para la mayoría de los escenarios. Este método ofrece la flexibilidad de elegir el formato de salida: `printf` texto, XML, JSON, base de datos, llamadas REST, etc.

El reinicio de sesión es para los análisis de uso especial que necesitan generar un archivo de salida de ETW. Mediante el reinicio de sesión, puede C++ traducir los eventos de Build Insights en su propio formato de evento ETW. Un uso apropiado del reinicio de sesión sería enlazar C++ datos de la información de compilación a la infraestructura y las herramientas de ETW existentes. Por ejemplo, [vcperf](https://github.com/microsoft/vcperf) hace uso de las interfaces de reregistro. Esto se debe a que debe generar datos que el analizador de rendimiento de Windows, una herramienta ETW, puede entender. Algunos conocimientos previos de cómo funciona ETW es necesario si planea usar las interfaces de reregistro.

### <a name="creating-analyzer-groups"></a>Crear grupos de Analyzer

Es importante saber cómo crear grupos. Este es un ejemplo que muestra cómo crear un grupo de Analyzer que imprime *Hello, World!* para cada evento de inicio de actividad que recibe.

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

## <a name="using-events"></a>Usar eventos

### <a name="sdk-types-and-functions-related-to-events"></a>Tipos y funciones de SDK relacionados con eventos

| Funcionalidad | API de C++ | API de C | Notas |
|--|--|--|--|
| Coincidencia y filtrado de eventos | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | La C++ API ofrece funciones que facilitan la extracción de los eventos que le interesan de los seguimientos. Con la API de C, este filtrado debe realizarse manualmente. |
| Tipos de datos de eventos | [Actividad](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[CommandLine](cpp-event-data-types/command-line.md)<br />[Compilación](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[Evento](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Function](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[Invocación](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[Linker](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Subproceso](cpp-event-data-types/thread.md)<br />[Desactivación](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>Actividades y eventos simples

Los eventos tienen dos categorías: *actividades* y *eventos simples*. Las actividades son procesos continuos en el tiempo que tienen un principio y un fin. Los eventos simples son Punctual repeticiones y no tienen una duración. Al analizar los seguimientos de C++ MSVC con el SDK de Build Insights, recibirá eventos independientes cuando se inicie y se detenga una actividad. Solo recibirá un evento cuando se produzca un evento simple.

### <a name="parent-child-relationships"></a>Relaciones de elementos primarios y secundarios

Las actividades y los eventos simples se relacionan entre sí mediante relaciones de elementos primarios y secundarios. El elemento primario de una actividad o un evento simple es la actividad englobada en la que se producen. Por ejemplo, al compilar un archivo de código fuente, el compilador tiene que analizar el archivo y, a continuación, generar el código. Las actividades de análisis y generación de código son elementos secundarios de la actividad del compilador.

Los eventos simples no tienen una duración, por lo que no se puede producir nada más en ellos. Como tal, nunca tienen elementos secundarios.

Las relaciones de elementos primarios y secundarios de cada actividad y evento simple se indican en la [tabla de eventos](event-table.md). Conocer estas relaciones es importante al consumir eventos C++ de información de compilación. A menudo tendrá que confiar en ellos para comprender el contexto completo de un evento.

### <a name="properties"></a>Propiedades

Todos los eventos tienen las siguientes propiedades:

| Propiedad | Descripción |
|--|--|
| Identificador de tipo | Número que identifica de forma única el tipo de evento. |
| Identificador de instancia | Número que identifica de forma única el evento dentro del seguimiento. Si dos eventos del mismo tipo se producen en un seguimiento, ambos obtienen un identificador de instancia único. |
| Start time | La hora a la que se inició una actividad o la hora a la que se produjo un evento simple. |
| Identificador de proceso | Número que identifica el proceso en el que se produjo el evento. |
| Identificador de subproceso | Número que identifica el subproceso en el que se produjo el evento. |
| Índice del procesador | Índice de base cero que indica en qué procesador lógico se emitió el evento. |
| Nombre del evento. | Cadena que describe el tipo de evento. |

Todas las actividades distintas de los eventos simples también tienen estas propiedades:

| Propiedad | Descripción |
|--|--|
| Hora de detención | La hora a la que se detuvo la actividad. |
| Duración exclusiva | El tiempo invertido en una actividad, excluido el tiempo invertido en sus actividades secundarias. |
| Tiempo de CPU | El tiempo que la CPU invierte en ejecutar código en el subproceso asociado a la actividad. No incluye el tiempo en el que el subproceso asociado a la actividad estaba en suspensión. |
| Tiempo de CPU exclusivo | Igual que el tiempo de CPU, pero excluyendo el tiempo de CPU empleado por las actividades secundarias. |
| Responsabilidad de la hora de reloj | La contribución de la actividad a la hora general del reloj de la pared. La responsabilidad del reloj en la pared tiene en cuenta el paralelismo entre las actividades. Por ejemplo, supongamos que dos actividades no relacionadas se ejecutan en paralelo. Ambos tienen una duración de 10 segundos y exactamente la misma hora de inicio y de finalización. En este caso, Build Insights asigna una responsabilidad de tiempo de reloj de 5 segundos. Por el contrario, si estas actividades se ejecutan una tras otra sin superposición, se les asigna una responsabilidad de tiempo de reloj de 10 segundos. |
| Responsabilidad exclusiva del tiempo de reloj | Igual que la responsabilidad de la hora de la pared, pero excluye la responsabilidad de la hora de reloj de las actividades secundarias. |

Algunos eventos tienen sus propias propiedades más allá de las mencionadas. En este caso, estas propiedades adicionales se enumeran en la [tabla de eventos](event-table.md).

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Consumo de eventos proporcionados por C++ el SDK de Build Insights

#### <a name="the-event-stack"></a>Pila de eventos

Cada vez C++ que el SDK de Build Insights le proporciona un evento, se incluye en forma de una pila. La última entrada de la pila es el evento actual y las entradas antes de ser su jerarquía primaria. Por ejemplo, los eventos de inicio y detención de [LTCG](event-table.md#ltcg) se producen durante el paso 1 del enlazador. En este caso, la pila que se recibiría contiene: \[[enlazador](event-table.md#linker), [PASS1](event-table.md#pass1), LTCG\]. La jerarquía primaria es útil porque puede realizar un seguimiento de un evento hasta su raíz. Si la actividad LTCG mencionada anteriormente es lenta, puede saber inmediatamente qué invocación del enlazador estaba implicada.

#### <a name="matching-events-and-event-stacks"></a>Eventos y pilas de eventos coincidentes

El C++ SDK de Build Insights le proporciona todos los eventos de un seguimiento, pero la mayor parte del tiempo solo le interesa un subconjunto de ellos. En algunos casos, es posible que solo tenga cuidado con un subconjunto de *pilas de eventos*. El SDK proporciona los recursos para ayudarle a extraer rápidamente los eventos o la pila de eventos que necesita y a rechazar los que no. Se realiza a través de estas funciones coincidentes:

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | Mantenga un evento si coincide con uno de los tipos especificados. Reenviar eventos coincidentes a una expresión lambda u otro tipo al que se puede llamar. Esta función no tiene en cuenta la jerarquía primaria del evento. |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | Mantenga un evento si coincide con el tipo especificado en el parámetro de una función miembro. Reenviar los eventos coincidentes a la función miembro. Esta función no tiene en cuenta la jerarquía primaria del evento. |
| [MatchEventStack](functions/match-event-stack.md) | Mantenga un evento si el evento y su jerarquía primaria coinciden con los tipos especificados. Reenvíe el evento y los eventos de jerarquía primario coincidentes a una expresión lambda u otro tipo al que se puede llamar. |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | Mantenga un evento si el evento y su jerarquía primaria coinciden con los tipos especificados en la lista de parámetros de una función miembro. Reenvíe el evento y los eventos de la jerarquía primaria coincidentes a la función miembro. |

Las funciones de coincidencia de pila de eventos como `MatchEventStack` permiten intervalos al describir la jerarquía primaria para que coincidan. Por ejemplo, puede decir que está interesado en el [enlazador](event-table.md#linker)\[, [LTCG](event-table.md#ltcg)\] Stack. También coincidirá con el \[VINCULAdor, [PASS1](event-table.md#pass1), LTCG\] pila. El último tipo especificado debe ser el tipo de evento para que coincida y no forma parte de la jerarquía primaria.

#### <a name="capture-classes"></a>Clases de captura

El uso de las funciones `Match*` requiere que especifique los tipos que desea buscar. Estos tipos se seleccionan de una lista de *clases de captura*. Las clases de captura se incluyen en varias categorías, que se describen a continuación.

| Categoría | Descripción |
|--|--|
| Exacto | Estas clases de captura se usan para buscar coincidencias con un tipo de evento específico y ninguna otra. Un ejemplo es la clase [del compilador](cpp-event-data-types/compiler.md) , que coincide con el evento [del compilador](event-table.md#compiler) . |
| Comodín | Estas clases de captura se pueden usar para buscar coincidencias con cualquier evento de la lista de eventos que admiten. Por ejemplo, el carácter comodín de [actividad](cpp-event-data-types/activity.md) coincide con cualquier evento de actividad. Otro ejemplo es el carácter comodín [CompilerPass](cpp-event-data-types/compiler-pass.md) , que puede coincidir con el [FRONT_END_PASS](event-table.md#front-end-pass) o el evento [BACK_END_PASS](event-table.md#back-end-pass) . |
| Grupo | Los nombres de las clases de captura de grupo terminan en el *Grupo*. Se usan para buscar coincidencias con varios eventos del mismo tipo en una fila, omitiendo los huecos. Solo tienen sentido al hacer coincidir eventos recursivos, ya que no sabe cuántos existen en la pila de eventos. Por ejemplo, la actividad [FRONT_END_FILE](event-table.md#front-end-file) se produce cada vez que el compilador analiza un archivo. Esta actividad es recursiva porque el compilador puede encontrar una directiva Include mientras analiza el archivo. La clase [FrontEndFile](cpp-event-data-types/front-end-file.md) solo coincide con un evento FRONT_END_FILE de la pila. Use la clase [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) para buscar coincidencias con toda la jerarquía de inclusión. |
| Grupo de caracteres comodín | Un grupo de caracteres comodín combina las propiedades de los caracteres comodín y los grupos. La única clase de esta categoría es [InvocationGroup](cpp-event-data-types/invocation-group.md), que coincide y captura todos los eventos del [enlazador](event-table.md#linker) y [del compilador](event-table.md#compiler) en una sola pila de eventos. |

Consulte la [tabla de eventos](event-table.md) para saber qué clases de captura se pueden usar para coincidir con cada evento.

#### <a name="after-matching-using-captured-events"></a>Después de la coincidencia: usar eventos capturados

Una vez que se completa correctamente una coincidencia, las funciones de `Match*` construyen los objetos de la clase Capture y los reenvían a la función especificada. Utilice estos objetos de clase de captura para tener acceso a las propiedades de los eventos.

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
