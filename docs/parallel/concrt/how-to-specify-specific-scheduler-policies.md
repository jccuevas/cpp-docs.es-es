---
title: "C&#243;mo: Especificar directivas de Scheduler concretas | Microsoft Docs"
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
  - "especificar directivas del programador [Runtime de simultaneidad]"
  - "directivas del programador, especificar [Runtime de simultaneidad]"
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: Especificar directivas de Scheduler concretas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las directivas de Scheduler permiten controlar la estrategia que el programador utiliza cuando administra tareas. En este tema se muestra cómo utilizar una directiva de programador para aumentar la prioridad del subproceso de una tarea que imprime un indicador de progreso en la consola.  
  
 Para obtener un ejemplo que utiliza directivas de programador personalizadas junto con los agentes asincrónicos, vea [Cómo: crear agentes que directivas de programador específicas de uso](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se llevan a cabo dos tareas en paralelo. La primera tarea calcula el<sup>th</sup> número de Fibonacci. La segunda imprime un indicador de progreso en la consola.  
  
 La primera tarea utiliza la descomposición recursiva para calcular el número de Fibonacci. Es decir, cada tarea crea de forma recursiva subtareas para calcular el resultado total. Una tarea que utiliza la descomposición recursiva podría utilizar todos los recursos disponibles y dejar otras tareas sin alimentar. En este ejemplo, la tarea que imprime el indicador de progreso tal vez no reciba el acceso oportuno a los recursos de cálculo.  
  
 Para proporcionar la tarea que imprime un acceso equitativo de mensaje de progreso a los recursos informáticos, este ejemplo utiliza los pasos que se describen en [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) para crear una instancia del programador que tiene una directiva personalizada. La directiva personalizada especifica la prioridad del subproceso como la clase de prioridad máxima.  
  
 Este ejemplo se utiliza la [Concurrency:: call](../../parallel/concrt/reference/call-class.md) y [Concurrency:: Timer](../../parallel/concrt/reference/timer-class.md) clases para imprimir el indicador de progreso. Estas clases tienen versiones de sus constructores que toman una referencia a un [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) objeto que las programa. En el ejemplo se utiliza el programador predeterminado para programar la tarea que calcula el número de Fibonacci y la instancia del programador para programar la tarea que imprime el indicador de progreso.  
  
 Para mostrar las ventajas de utilizar un programador que tiene una directiva personalizada, en el ejemplo se realiza la tarea dos veces. Primero se usa el programador predeterminado para programar ambas tareas. A continuación, se utiliza el programador predeterminado para programar la primera tarea y un programador que tiene una directiva personalizada para programar la segunda tarea.  
  
 [!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/CPP/how-to-specify-specific-scheduler-policies_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
Default scheduler:  
...........................................................................done  
Scheduler that has a custom policy:  
...........................................................................done  
```  
  
 Aunque ambos conjuntos de tareas generan el mismo resultado, la versión que utiliza una directiva personalizada habilita la tarea que imprime el indicador de progreso para ejecutarse con una prioridad elevada de forma que responda con prontitud.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `scheduler-policy.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc scheduler-policy.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Directivas del programador](../../parallel/concrt/scheduler-policies.md)   
 [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Cómo: crear agentes que usen directivas de programador específicas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

