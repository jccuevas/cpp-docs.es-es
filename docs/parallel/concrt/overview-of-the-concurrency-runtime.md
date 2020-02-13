---
title: Información general sobre el runtime de simultaneidad
ms.date: 11/19/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: b50c943bb83c587ab4001556b1143f9d5f868a0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142936"
---
# <a name="overview-of-the-concurrency-runtime"></a>Información general sobre el runtime de simultaneidad

En este documento se proporciona información general sobre el Runtime de simultaneidad. Se describen las ventajas del Runtime de simultaneidad, cuándo usarlo, y cómo interactúan sus componentes entre sí y con el sistema operativo y las aplicaciones.

## <a name="top"></a> Secciones

Este documento contiene las siguientes secciones:

- [Runtime de simultaneidad historial de implementación](#dlls)

- [Por qué es importante un tiempo de ejecución para la simultaneidad](#runtime)

- [Architecture](#architecture)

- [C++Expresiones lambda](#lambda)

- [Requisitos](#requirements)

## <a name="dlls"></a>Runtime de simultaneidad historial de implementación

En Visual Studio 2010 a 2013, el Runtime de simultaneidad se incorporó en msvcr100. dll a través de msvcr120. dll.  Cuando se produce la refactorización UCRT en Visual Studio 2015, esa DLL se refactoriza en tres partes:

- ucrtbase. dll: API de C, incluida en Windows 10 y con servicio de nivel inferior mediante Windows Update-

- vcruntime140. dll: funciones de compatibilidad del compilador y tiempo de ejecución EH, enviadas a través de Visual Studio

- concrt140. dll: Runtime de simultaneidad, enviado a través de Visual Studio. Se requiere para los algoritmos y contenedores paralelos, como `concurrency::parallel_for`. Además, STL requiere este archivo DLL en Windows XP para potenciar los primitivos de sincronización, ya que Windows XP no tiene variables de condición.

En Visual Studio de 2015 y versiones posteriores, el programador de tareas del Runtime de simultaneidad ya no es el programador de la clase de tarea y los tipos relacionados en ppltasks.h. Esos tipos usan ahora el grupo de subprocesos de Windows para lograr un mejor rendimiento e interoperabilidad con las primitivas de sincronización de Windows.

## <a name="runtime"></a>Por qué es importante un tiempo de ejecución para la simultaneidad

Un Runtime de simultaneidad proporciona uniformidad y previsibilidad a las aplicaciones y a los componentes de aplicación que se ejecutan simultáneamente. Dos ejemplos de las ventajas de los Runtime de simultaneidad son la *programación cooperativa de tareas* y el *bloqueo cooperativo*.

El Runtime de simultaneidad usa un programador de tareas cooperativo que implementa un algoritmo de robo de trabajo para distribuir el trabajo de forma eficaz entre los recursos informáticos. Pensemos, por ejemplo, en una aplicación que tenga dos subprocesos, ambos administrados por el mismo runtime. Si un subproceso finaliza su tarea programada, puede descargar de trabajo al otro subproceso. Este mecanismo equilibra la carga de trabajo total de la aplicación.

El Runtime de simultaneidad también proporciona primitivas de sincronización que usan el bloqueo cooperativo para sincronizar el acceso a los recursos. Pensemos, por ejemplo, en una tarea que deba obtener acceso exclusivo a un recurso compartido. Mediante un bloqueo cooperativo, el runtime puede usar el cuanto restante para realizar otra tarea mientras la primera espera por el recurso. Este mecanismo promueve el uso máximo de los recursos informáticos.

[[Arriba](#top)]

## <a name="architecture"></a> Arquitectura

El Runtime de simultaneidad se divide en cuatro componentes: la Biblioteca de modelos de procesamiento paralelo (PPL), la Biblioteca de agentes asincrónicos, el Programador de tareas y el Administrador de recursos. Estos componentes se encuentran entre el sistema operativo y las aplicaciones. La siguiente ilustración muestra cómo interactúan los componentes del Runtime de simultaneidad entre el sistema operativo y las aplicaciones:

**Arquitectura de Runtime de simultaneidad**

![Arquitectura de Runtime de simultaneidad](../../parallel/concrt/media/concurrencyrun.png "La arquitectura del Runtime de simultaneidad")

> [!IMPORTANT]
> Los componentes Programador de tareas y Administrador de recursos no están disponibles en una aplicación Plataforma universal de Windows (UWP) o cuando se usa la clase de tarea u otros tipos de ppltasks. h.

La Runtime de simultaneidad es muy *ajustable*, es decir, puede combinar la funcionalidad existente para hacer más. El Runtime de simultaneidad compone muchas características —por ejemplo, algoritmos paralelos— a partir de componentes de nivel inferior.

El Runtime de simultaneidad también proporciona primitivas de sincronización que usan el bloqueo cooperativo para sincronizar el acceso a los recursos. Para obtener más información acerca de estas primitivas de sincronización, vea [Synchronization Data Structures](../../parallel/concrt/synchronization-data-structures.md).

En las secciones siguientes se proporciona una breve descripción general de lo que cada componente proporciona y cuándo usarlo.

### <a name="parallel-patterns-library"></a>Biblioteca de patrones de procesamiento paralelo

La Biblioteca de modelos de procesamiento paralelo (PPL) proporciona algoritmos y contenedores de propósito general para realizar paralelismos específicos. La biblioteca PPL permite el *paralelismo de datos imperativo* al proporcionar algoritmos paralelos que distribuyen los cálculos en colecciones o en conjuntos de datos entre los recursos informáticos. También habilita el *paralelismo de tareas* al proporcionar objetos de tarea que distribuyen varias operaciones independientes en los recursos informáticos.

Use la Biblioteca de modelos de procesamiento paralelo si cuenta con un cálculo local que se puede beneficiar de la ejecución paralela. Por ejemplo, puede usar el algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) para transformar un bucle de `for` existente para que actúe en paralelo.

Para obtener más información acerca de la biblioteca de patrones de procesamiento paralelo, vea [biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

### <a name="asynchronous-agents-library"></a>Biblioteca de agentes asincrónicos

La biblioteca de agentes asincrónicos (o simplemente *biblioteca de agentes*) proporciona un modelo de programación basado en actor y las interfaces de paso de mensajes para las tareas de canalización y transmisión de flujo de bits generales. Los agentes asincrónicos permiten realizar un uso productivo de la latencia ya que realizan el trabajo mientras otros componentes esperan datos.

Use la Biblioteca de agentes si dispone de varias entidades que se comunican entre sí de forma asincrónica. Por ejemplo, puede crear un agente que lea datos de un archivo o de una conexión de red y que, a continuación, use las interfaces de paso de mensajes para enviar esos datos a otro agente.

Para obtener más información sobre la biblioteca de agentes, vea [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).

### <a name="task-scheduler"></a>Programador de tareas

El Programador de tareas programa y coordina las tareas en tiempo de ejecución. El Programador de tareas es cooperativo y usa un algoritmo de robo de trabajo para optimizar el uso de recursos de procesamiento.

El Runtime de simultaneidad proporciona un programador predeterminado, de modo que no es necesario administrar los detalles de infraestructura. Sin embargo, para satisfacer las necesidades de calidad de la aplicación, también puede usar su propia directiva de programación o asociar programadores concretos a tareas específicas.

Para obtener más información sobre el Programador de tareas, vea [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

### <a name="resource-manager"></a>Resource Manager

El Administrador de recursos desempeña el rol de administrar los recursos informáticos, como los procesadores y la memoria. Responde a las cargas de trabajo a medida que cambian en tiempo de ejecución mediante la asignación de recursos allí donde pueden resultar más eficaces.

El Administrador de recursos actúa como una abstracción sobre los recursos e interactúa principalmente con el Programador de tareas. Si bien se puede usar el Administrador de recursos para ajustar el rendimiento de las bibliotecas y aplicaciones, por lo general se usa la funcionalidad que proporcionan la Biblioteca de modelos de procesamiento paralelo, la Biblioteca de agentes y el Programador de tareas. Estas bibliotecas usan el Administrador de recursos para volver a equilibrar de forma dinámica los recursos a medida que cambian las cargas de trabajo.

[[Arriba](#top)]

## <a name="lambda"></a>C++ Expresiones lambda

Muchos de los tipos y algoritmos que se definen en el Runtime de simultaneidad se implementan como plantillas de C++. Algunos de estos tipos y algoritmos toman como parámetro una rutina que realiza trabajo. Este parámetro puede ser una función lambda, un objeto de función o un puntero a una función. Estas entidades también se conocen como *funciones de trabajo* o *rutinas de trabajo*.

Las expresiones lambda son una característica nueva e importante del lenguaje Visual C++ porque proporcionan una manera concisa de definir funciones de trabajo para el procesamiento paralelo. Los objetos de función y los punteros a función permiten usar el Runtime de simultaneidad con el código existente. Sin embargo, se recomienda usar expresiones lambda al escribir código nuevo debido a las ventajas de seguridad y productividad que proporcionan.

En el ejemplo siguiente se compara la sintaxis de las funciones lambda, los objetos de función y los punteros de función en varias llamadas al algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) . Cada llamada a `parallel_for_each` utiliza una técnica diferente para calcular el cuadrado de cada elemento en un objeto [STD:: Array](../../standard-library/array-class-stl.md) .

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**Salida**

```Output
1
256
6561
65536
390625
```

Para obtener más información sobre las funciones C++lambda en, consulte [expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).

[[Arriba](#top)]

## <a name="requirements"></a> Requisitos

En la siguiente tabla se muestran los archivos de encabezado asociados a cada componente del Runtime de simultaneidad:

|Componente|Archivos de encabezado|
|---------------|------------------|
|Parallel Patterns Library (PPL)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|
|Biblioteca de agentes asincrónicos|agents.h|
|Programador de tareas|concrt.h|
|Resource Manager|concrtrm.h|

El Runtime de simultaneidad se declara en el espacio de nombres de [simultaneidad](../../parallel/concrt/reference/concurrency-namespace.md) . (También puede usar la [simultaneidad](../../parallel/concrt/reference/concurrency-namespace.md), que es un alias para este espacio de nombres). El espacio de nombres `concurrency::details` admite el marco de Runtime de simultaneidad y no está pensado para usarse directamente desde el código.

El Runtime de simultaneidad se proporciona como parte de la Biblioteca en tiempo de ejecución de C (CRT). Para obtener más información sobre cómo compilar una aplicación que usa CRT, vea características de la [biblioteca CRT](../../c-runtime-library/crt-library-features.md).

[[Arriba](#top)]
