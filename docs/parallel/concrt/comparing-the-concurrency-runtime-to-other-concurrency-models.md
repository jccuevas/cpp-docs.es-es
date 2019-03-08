---
title: Comparar el runtime de simultaneidad con otros modelos de simultaneidad
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
ms.openlocfilehash: 885cce09707e1c067efdeb0bdc8b7d8a40841c02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285105"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Comparar el runtime de simultaneidad con otros modelos de simultaneidad

En este documento se describen las diferencias entre las características y los modelos de programación del Runtime de simultaneidad y otras tecnologías. Si compara las ventajas del Runtime de simultaneidad con las ventajas de otros modelos de programación, podrá seleccionar la tecnología que mejor satisfaga los requisitos de sus aplicaciones.

Si actualmente usa otro modelo de programación, como el grupo de subprocesos de Windows u OpenMP, hay casos en los que puede ser adecuado migrar al Runtime de simultaneidad. Por ejemplo, en el tema [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) se describe cuál podría ser el momento adecuado para migrar de OpenMP al Runtime de simultaneidad, aunque si está satisfecho con el rendimiento de la aplicación y con la compatibilidad de depuración actual, no es necesario llevar a cabo la migración.

Puede usar las características y las ventajas de productividad del Runtime de simultaneidad para complementar su aplicación que usa otro modelo de simultaneidad. El Runtime de simultaneidad no puede garantizar el equilibrio de carga si hay varios programadores de tareas que compiten por los mismos recursos informáticos, aunque este efecto es mínimo si las cargas de trabajo no se superponen.

##  <a name="top"></a> Secciones

- [Comparación de la programación preferente y la programación cooperativa](#models)

- [Comparación del Runtime de simultaneidad y la API de Windows](#winapi)

- [Comparación del Runtime de simultaneidad y OpenMP](#openmp)

##  <a name="models"></a> Comparación de la programación preferente y la programación cooperativa

Los modelos de programación preferente y cooperativa son dos métodos comunes para que varias tareas compartan recursos informáticos (por ejemplo, procesadores o subprocesos de hardware).

### <a name="preemptive-and-cooperative-scheduling"></a>Programación preferente y cooperativa

La*programación preferente* es un mecanismo round robin basado en la prioridad que proporciona a todas las tareas acceso exclusivo a un recurso informático durante un período determinado y, luego, pasa a otra tarea. Este tipo de programación es habitual en los sistemas operativos de multitarea, como Windows. *La programación cooperativa* es un mecanismo que proporciona todas las tareas acceso exclusivo a un recurso informático hasta que la tarea finaliza o cede su acceso al recurso. El Runtime de simultaneidad usa la programación cooperativa junto con el programador preferente del sistema operativo. De este modo, consigue el mayor uso posible de los recursos de procesamiento.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Diferencias entre los programadores preferente y cooperativo

Los programadores preferentes buscan dar a varios subprocesos el mismo acceso a los recursos informáticos para garantizar que cada subproceso progrese. En los equipos que tienen muchos recursos informáticos, el hecho de garantizar un acceso equitativo es menos problemático que garantizar que los recursos se usen de forma eficaz.

Los programadores preferentes en modo kernel necesitan que el código de la aplicación se base en el sistema operativo para tomar decisiones relacionadas con la programación. Por el contrario, los programadores cooperativos en modo usuario permiten que el código de la aplicación tome sus propias decisiones relativas a la programación. Dado que en la programación cooperativa la aplicación puede tomar muchas decisiones de programación, reduce en gran medida la sobrecarga asociada con la sincronización en modo kernel. Los programadores cooperativos suelen ceder las decisiones de programación al kernel del sistema operativo si no tienen nada más que programar. Un programador cooperativo también cede las decisiones al programador del sistema operativo cuando hay una operación de bloqueo que se ha comunicado al kernel, pero no al programador en modo de usuario.

### <a name="cooperative-scheduling-and-efficiency"></a>Programación cooperativa y eficacia

Para un programador preferente, todos los trabajos que tienen el mismo nivel de prioridad son iguales. Los programadores preferentes suelen programar los subprocesos en el orden en el que se crean. Además, asignan a todos los subprocesos un intervalo de tiempo con el método round robin, según la prioridad del subproceso. Aunque este mecanismo aporta equidad (todos los subprocesos progresan), esto va en detrimento de la eficacia. Por ejemplo, hay muchos algoritmos de cálculo intensivo que no requieren equidad. En su lugar, es importante que las tareas relacionadas finalicen en la mayor brevedad posible. La programación cooperativa permite que una aplicación programe el trabajo de forma más eficaz. Por ejemplo, imagínese una aplicación que tiene muchos subprocesos. La programación de subprocesos que no comparten recursos para ejecutarse simultáneamente puede reducir la sobrecarga de sincronización y, por lo tanto, aumentar la eficacia. Otra manera eficaz de programar tareas consiste en ejecutar canalizaciones de tareas (en las que cada tarea actúa sobre el resultado de la anterior) en el mismo procesador, de modo que la entrada de cada fase de canalización ya esté cargada en la memoria caché.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Usar conjuntamente la programación preferente y la cooperativa

La programación cooperativa no resuelve todos los problemas de programación. Por ejemplo, las tareas que no ceden de forma equitativa a otras tareas pueden consumir todos los recursos informáticos disponibles e impedir que otras tareas progresen. El Runtime de simultaneidad aprovecha las ventajas de la eficacia de la programación cooperativa para complementar las garantías de equidad de la programación preferente. De forma predeterminada, el Runtime de simultaneidad proporciona un programador cooperativo que usa un algoritmo de robo de trabajo para distribuir el trabajo de forma eficaz entre los recursos informáticos. No obstante, el programador del Runtime de simultaneidad también se basa en el programador preferente del sistema operativo para distribuir los recursos por las aplicaciones de forma equitativa. También puede crear programadores personalizados y directivas de programador en las aplicaciones para obtener un control específico de la ejecución de los subprocesos.

[[Arriba](#top)]

##  <a name="winapi"></a> Comparación del Runtime de simultaneidad y la API de Windows

La interfaz de programación de aplicaciones de Microsoft Windows, más conocida como la API de Windows (y anteriormente denominada Win32), proporciona un modelo de programación que permite la simultaneidad en las aplicaciones. El Runtime de simultaneidad se basa en la API de Windows para proporcionar unos modelos de programación que no están disponibles en el sistema operativo subyacente.

El Runtime de simultaneidad se basa en el modelo de subprocesos de la API de Windows para llevar a cabo trabajos paralelos. También usa la administración de memoria de la API de Windows y los mecanismos de almacenamiento local de subprocesos. En Windows 7 y Windows Server 2008 R2, usa la compatibilidad de la API de Windows para los subprocesos programables por los usuarios y los equipos que tienen más de 64 subprocesos de hardware. El Runtime de simultaneidad amplía el modelo de la API de Windows proporcionando un programador de tareas cooperativo y un algoritmo de robo de trabajo para maximizar el uso de los recursos informáticos; también permite varias instancias simultáneas del programador.

### <a name="programming-languages"></a>Lenguajes de programación

La API de Windows usa el lenguaje de programación C para exponer el modelo de programación. El Runtime de simultaneidad proporciona una interfaz de programación de C++ que aprovecha las nuevas características del lenguaje C++. Por ejemplo, las funciones lambda proporcionan un mecanismo conciso con seguridad de tipos para definir funciones de trabajo paralelo. Para obtener más información sobre las nuevas características de C++ que usa el Runtime de simultaneidad, consulte [Información general](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Subprocesos y grupos de subprocesos

El mecanismo de simultaneidad central en la API de Windows es el subproceso. Normalmente se usa la función [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) para crear subprocesos. Aunque los subprocesos son relativamente fáciles de crear y de usar, el sistema operativo asigna una cantidad significativa de tiempo y otros recursos para administrarlos. Además, aunque se garantiza que todos los subprocesos reciben el mismo tiempo de ejecución que cualquier otro subproceso que esté en el mismo nivel de prioridad, la sobrecarga asociada hace que deba crear tareas suficientemente grandes. Para las tareas pequeñas o más específicas, la sobrecarga asociada a la simultaneidad puede pesar más que la ventaja de ejecutar las tareas en paralelo.

Los grupos de subprocesos son una forma de reducir el coste de la administración de subprocesos. Los grupos de subprocesos personalizados y la implementación de grupos de subprocesos proporcionada con la API de Windows permiten que los elementos de trabajo pequeños se ejecuten en paralelo de forma eficaz. El grupo de subprocesos de Windows mantiene los elementos de trabajo en una cola «primero en entrar, primero en salir» (FIFO). Todos los elementos de trabajo se inician en el orden en que se agregaron al grupo.

El Runtime de simultaneidad implementa un algoritmo de robo de trabajo para extender el mecanismo de programación FIFO. El algoritmo mueve las tareas que todavía no se han iniciado a los subprocesos que se ejecutan fuera de los elementos de trabajo. Aunque el algoritmo de robo de trabajo puede equilibrar las cargas de trabajo, también puede hacer que los elementos de trabajo se vuelvan a ordenar. Este proceso de reordenación puede hacer que un elemento de trabajo se inicie en un orden diferente del orden en el que se envió. Esto resulta útil con los algoritmos recursivos, en los que es más fácil que los datos se compartan entre las tareas más recientes y no entre las más antiguas. El hecho de que los elementos nuevos se ejecuten primero implica menos errores de caché y, posiblemente, menos errores de página.

Desde la perspectiva del sistema operativo, el robo de trabajo no es equitativo, aunque cuando una aplicación implementa un algoritmo o una tarea para ejecutarlos en paralelo, la equidad entre las subtareas no siempre importa. Lo que sí importa es la rapidez con la que finaliza la tarea. En cuanto a otros algoritmos, FIFO es la estrategia de programación adecuada.

### <a name="behavior-on-various-operating-systems"></a>Comportamiento en varios sistemas operativos

En Windows XP y Windows Vista, las aplicaciones que usan el Runtime de simultaneidad se comportan de forma similar, salvo que en Windows Vista se ha mejorado el rendimiento de montón.

En Windows 7 y Windows Server 2008 R2, el sistema operativo admite la simultaneidad y la escalabilidad. Por ejemplo, estos sistemas operativos admiten los equipos que tienen más de 64 subprocesos de hardware. Las aplicaciones que usan la API de Windows deben modificarse para poder aprovechar estas nuevas características, aunque las aplicaciones que usan el Runtime de simultaneidad usan automáticamente estas características, por lo que no es necesario hacer modificaciones.

[base.user-mode_scheduling](https://msdn.microsoft.com/library/windows/desktop/dd627187)

[[Arriba](#top)]

##  <a name="openmp"></a> Comparación del Runtime de simultaneidad y OpenMP

El Runtime de simultaneidad ofrece una variedad de modelos de programación. Estos modelos pueden superponerse o complementar los modelos de otras bibliotecas. En esta sección se compara el Runtime de simultaneidad con [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).

El modelo de programación de OpenMP se define con un estándar abierto y tiene enlaces bien definidos con los lenguajes de programación Fortran y C/C++. Las versiones 2.0 y 2.5 de OpenMP son apropiadas para los algoritmos paralelos que son iterativos; es decir, efectúan una iteración paralela en una matriz de datos. OpenMP es más eficaz cuando el grado de paralelismo se determina previamente y coincide con los recursos disponibles en el sistema. El modelo de OpenMP es una muy buena opción para la informática de alto rendimiento, en la que los problemas de cálculo considerables se distribuyen por los recursos de procesamiento de un único equipo. En este escenario, el entorno de hardware es conocido y el desarrollador puede suponer, con razón, que tendrá acceso exclusivo a los recursos informáticos en el momento en que se ejecute el algoritmo.

También puede haber otros entornos informáticos con menos restricciones que no sean tan idóneos para OpenMP. Por ejemplo, los problemas recursivos (como el algoritmo quicksort o la búsqueda de un árbol de datos) son más difíciles de implementar con OpenMP. El Runtime de simultaneidad complementa la funcionalidad de OpenMP proporcionando la [biblioteca de patrones de procesamiento paralelo](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) y la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md). A diferencia de OpenMP, el Runtime de simultaneidad proporciona un programador dinámico que se adapta a los recursos disponibles y ajusta el grado de paralelismo a medida que las cargas de trabajo varían.

Muchas de las características del Runtime de simultaneidad se pueden extender. También puede combinar características existentes para crear nuevas características. Dado que OpenMP se basa en las directivas de compilador, no se puede ampliar fácilmente.

Para obtener más información sobre la comparación del Runtime de simultaneidad y OpenMP y sobre cómo migrar el código existente de OpenMP para usar el Runtime de simultaneidad, consulte [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Arriba](#top)]

## <a name="see-also"></a>Vea también

[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)<br/>
[Información general](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
