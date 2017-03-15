---
title: "Informaci&#243;n general sobre el runtime de simultaneidad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Runtime de simultaneidad, arquitectura"
  - "Runtime de simultaneidad, expresiones lambda"
  - "Runtime de simultaneidad, información general"
  - "Runtime de simultaneidad, requisitos"
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# Informaci&#243;n general sobre el runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se proporciona información general sobre el Runtime de simultaneidad.  Se describen las ventajas del Runtime de simultaneidad, cuándo usarlo, y cómo interactúan sus componentes entre sí y con el sistema operativo y las aplicaciones.  
  
> [!IMPORTANT]
>  En Visual Studio de 2015 y versiones posteriores, el programador de tareas del Runtime de simultaneidad ya no es el programador de la clase de tarea y los tipos relacionados en ppltasks.h.  Esos tipos usan ahora el grupo de subprocesos de Windows para lograr un mejor rendimiento e interoperabilidad con las primitivas de sincronización de Windows.  Los algoritmos paralelos, como parallel\_for, siguen usando el programador de tareas de Runtime de simultaneidad  
  
##  <a name="top"></a> Secciones  
 Este documento contiene las siguientes secciones:  
  
-   [Por qué es importante un Runtime de simultaneidad](#runtime)  
  
-   [Arquitectura](#architecture)  
  
-   [Expresiones Lambda de C\+\+](#lambda)  
  
-   [Requisitos](#requirements)  
  
##  <a name="runtime"></a> Por qué es importante un Runtime de simultaneidad  
 Un Runtime de simultaneidad proporciona uniformidad y previsibilidad a las aplicaciones y a los componentes de aplicación que se ejecutan simultáneamente.  Dos ejemplos de las ventajas del Runtime de simultaneidad son la *programación de tareas cooperativa* y el *bloqueo cooperativo*.  
  
 El Runtime de simultaneidad usa un programador de tareas cooperativo que implementa un algoritmo de robo de trabajo para distribuir el trabajo de forma eficaz entre los recursos informáticos.  Pensemos, por ejemplo, en una aplicación que tenga dos subprocesos, ambos administrados por el mismo runtime.  Si un subproceso finaliza su tarea programada, puede descargar de trabajo al otro subproceso.  Este mecanismo equilibra la carga de trabajo total de la aplicación.  
  
 El Runtime de simultaneidad también proporciona primitivas de sincronización que usan el bloqueo cooperativo para sincronizar el acceso a los recursos.  Pensemos, por ejemplo, en una tarea que deba obtener acceso exclusivo a un recurso compartido.  Mediante un bloqueo cooperativo, el runtime puede usar el cuanto restante para realizar otra tarea mientras la primera espera por el recurso.  Este mecanismo promueve el uso máximo de los recursos informáticos.  
  
 \[[Arriba](#top)\]  
  
##  <a name="architecture"></a> Arquitectura  
 El Runtime de simultaneidad se divide en cuatro componentes: la Biblioteca de modelos de procesamiento paralelo \(PPL\), la Biblioteca de agentes asincrónicos, el Programador de tareas y el Administrador de recursos.  Estos componentes se encuentran entre el sistema operativo y las aplicaciones.  La siguiente ilustración muestra cómo interactúan los componentes del Runtime de simultaneidad entre el sistema operativo y las aplicaciones:  
  
 **Arquitectura del Runtime de simultaneidad**  
  
 ![La arquitectura del Runtime de simultaneidad](../../parallel/concrt/media/concurrencyrun.png "ConcurrencyRun")  
  
> [!IMPORTANT]
>  Los componentes de programador de tareas y administrador de recursos no están disponibles en una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] ni al usar la clase de tarea u otros tipos de ppltasks.h.  
  
 El Runtime de simultaneidad *admite composición* en un alto grado, es decir, se puede combinar la funcionalidad existente para aumentar las capacidades.  El Runtime de simultaneidad compone muchas características —por ejemplo, algoritmos paralelos— a partir de componentes de nivel inferior.  
  
 El Runtime de simultaneidad también proporciona primitivas de sincronización que usan el bloqueo cooperativo para sincronizar el acceso a los recursos.  Para obtener más información sobre estas primitivas de sincronización, vea [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md).  
  
 En las secciones siguientes se proporciona una breve descripción general de lo que cada componente proporciona y cuándo usarlo.  
  
### Biblioteca de modelos de procesamiento paralelo \(PPL\)  
 La Biblioteca de modelos de procesamiento paralelo \(PPL\) proporciona algoritmos y contenedores de propósito general para realizar paralelismos específicos.  Esta biblioteca habilita el *paralelismo de datos imperativo*, ya que proporciona algoritmos paralelos que distribuyen los cálculos en colecciones o en conjuntos de datos entre los recursos informáticos.  También habilita el *paralelismo de tareas*, ya que proporciona objetos de tarea que distribuyen varias operaciones independientes entre los recursos informáticos.  
  
 Use la Biblioteca de modelos de procesamiento paralelo si cuenta con un cálculo local que se puede beneficiar de la ejecución paralela.  Por ejemplo, puede usar el algoritmo [Concurrency::parallel\_for](../Topic/parallel_for%20Function.md) para transformar un bucle `for` existente para que actúe en paralelo.  
  
 Para obtener más información sobre la biblioteca PPL, vea [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
### Biblioteca de agentes asincrónicos  
 La Biblioteca de agentes asincrónicos \(o simplemente *Biblioteca de agentes*\) proporciona un modelo de programación basado en actores e interfaces de paso de mensajes para las tareas genéricas de flujo de datos y canalización  Los agentes asincrónicos permiten realizar un uso productivo de la latencia ya que realizan el trabajo mientras otros componentes esperan datos.  
  
 Use la Biblioteca de agentes si dispone de varias entidades que se comunican entre sí de forma asincrónica.  Por ejemplo, puede crear un agente que lea datos de un archivo o de una conexión de red y que, a continuación, use las interfaces de paso de mensajes para enviar esos datos a otro agente.  
  
 Para obtener más información sobre la Biblioteca de agentes asincrónicos, vea [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).  
  
### Programador de tareas  
 El Programador de tareas programa y coordina las tareas en tiempo de ejecución.  El Programador de tareas es cooperativo y usa un algoritmo de robo de trabajo para optimizar el uso de recursos de procesamiento.  
  
 El Runtime de simultaneidad proporciona un programador predeterminado, de modo que no es necesario administrar los detalles de infraestructura.  Sin embargo, para satisfacer las necesidades de calidad de la aplicación, también puede usar su propia directiva de programación o asociar programadores concretos a tareas específicas.  
  
 Para obtener más información sobre el programador de tareas, vea [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
### Administrador de recursos  
 El Administrador de recursos desempeña el rol de administrar los recursos informáticos, como los procesadores y la memoria.  Responde a las cargas de trabajo a medida que cambian en tiempo de ejecución mediante la asignación de recursos allí donde pueden resultar más eficaces.  
  
 El Administrador de recursos actúa como una abstracción sobre los recursos e interactúa principalmente con el Programador de tareas.  Si bien se puede usar el Administrador de recursos para ajustar el rendimiento de las bibliotecas y aplicaciones, por lo general se usa la funcionalidad que proporcionan la Biblioteca de modelos de procesamiento paralelo, la Biblioteca de agentes y el Programador de tareas.  Estas bibliotecas usan el Administrador de recursos para volver a equilibrar de forma dinámica los recursos a medida que cambian las cargas de trabajo.  
  
 \[[Arriba](#top)\]  
  
##  <a name="lambda"></a> Expresiones Lambda de C\+\+  
 Muchos de los tipos y algoritmos que se definen en el Runtime de simultaneidad se implementan como plantillas de C\+\+.  Algunos de estos tipos y algoritmos toman como parámetro una rutina que realiza trabajo.  Este parámetro puede ser una función lambda, un objeto de función o un puntero a una función.  Estas entidades también se conocen como *funciones de trabajo* o *rutinas de trabajo*.  
  
 Las expresiones lambda son una característica nueva e importante del lenguaje Visual C\+\+ porque proporcionan una manera concisa de definir funciones de trabajo para el procesamiento paralelo.  Los objetos de función y los punteros a función permiten usar el Runtime de simultaneidad con el código existente.  Sin embargo, se recomienda usar expresiones lambda al escribir código nuevo debido a las ventajas de seguridad y productividad que proporcionan.  
  
 En el ejemplo siguiente se compara la sintaxis de las funciones lambda, los objetos de función y los punteros a función en varias llamadas al algoritmo [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md).  Cada llamada a `parallel_for_each` usa una técnica diferente para calcular el cuadrado de cada elemento de un objeto [std::array](../../standard-library/array-class-stl.md).  
  
 [!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/CPP/overview-of-the-concurrency-runtime_1.cpp)]  
  
 **Resultado**  
  
  **1**  
**256**  
**6561**  
**65536**  
**390625** Para más información sobre las funciones lambda en C\+\+, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="requirements"></a> Requisitos  
 En la siguiente tabla se muestran los archivos de encabezado asociados a cada componente del Runtime de simultaneidad:  
  
|Componente|Archivos de encabezado|  
|----------------|----------------------------|  
|Parallel Patterns Library \(PPL\)|ppl.h<br /><br /> concurrent\_queue.h<br /><br /> concurrent\_vector.h|  
|Biblioteca de agentes asincrónicos|agents.h|  
|Programador de tareas|concrt.h|  
|Administrador de recursos|concrtrm.h|  
  
 El Runtime de simultaneidad se declara en el espacio de nombres [Concurrency](../../parallel/concrt/reference/concurrency-namespace.md).  \(También puede usar [concurrency](../../parallel/concrt/reference/concurrency-namespace.md), que es un alias de este espacio de nombres\). El espacio de nombres `concurrency::details` es compatible con el marco de Runtime de simultaneidad y no está diseñado para usarse directamente en el código.  
  
 El Runtime de simultaneidad se proporciona como parte de la Biblioteca en tiempo de ejecución de C \(CRT\).  Para obtener más información sobre cómo compilar una aplicación que usa CRT, vea el tema sobre [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
 \[[Arriba](#top)\]