---
title: "C&#243;mo: Crear agentes que usen directivas de programador espec&#237;ficas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "directivas del programador, agentes [Runtime de simultaneidad]"
  - "crear agentes que usen directivas específicas [Runtime de simultaneidad]"
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear agentes que usen directivas de programador espec&#237;ficas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un agente es un componente de aplicación que funciona de forma asincrónica con otros componentes para resolver tareas de computación mayores.  Normalmente, un agente tiene un ciclo de vida establecido y mantiene el estado.  
  
 Cada agente puede tener requisitos de aplicación únicos.  Por ejemplo, un agente que permite la interacción con el usuario \(ya sea al recuperar la entrada o al mostrar la salida\) puede requerir un acceso más prioritario a los recursos informáticos.  Las directivas de programador permiten controlar la estrategia que el programador utiliza cuando administra tareas.  En este tema se muestra cómo crear agentes que usen directivas de programador específicas.  
  
 Para obtener un ejemplo básico donde se usan directivas de programador personalizadas junto con bloques de mensaje asincrónicos, vea [Cómo: Especificar directivas de programador concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
 En este tema se usa la funcionalidad de la Biblioteca de agentes asincrónicos, como agentes, bloques de mensaje y funciones para pasar mensajes, para realizar el trabajo.  Para obtener más información sobre la Biblioteca de agentes asincrónicos, vea [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).  
  
## Ejemplo  
 En el siguiente ejemplo, se definen dos clases que se derivan de [concurrency::agent](../../parallel/concrt/reference/agent-class.md): `permutor` y `printer`.  La clase `permutor` calcula todas las permutaciones de una cadena de entrada determinada.  La clase `printer` imprime los mensajes de progreso en la consola.  La clase `permutor` realiza una operación que requiere gran cantidad de recursos de computación y que podría usar todos los recursos disponibles.  Para ser útil, la clase `printer` debe imprimir cada mensaje de progreso de una manera puntual.  
  
 Con el fin de que la clase `printer` disponga del acceso necesario a los recursos de computación, en este ejemplo se usan los pasos que se describen en [Cómo: Administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) para crear una instancia de programador con una directiva personalizada.  La directiva personalizada especifica la prioridad del subproceso como la clase de prioridad máxima.  
  
 Para mostrar las ventajas de utilizar un programador que tiene una directiva personalizada, en el ejemplo se realiza la tarea dos veces.  Primero se usa el programador predeterminado para programar ambas tareas.  A continuación, se usa el programador predeterminado para programar el objeto `permutor` y un programador con una directiva personalizada para programar el objeto `printer`.  
  
 [!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/CPP/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **With default scheduler:**  
**Computing all permutations of 'Grapefruit'...**  
**100% complete...**  
**With higher context priority:**  
**Computing all permutations of 'Grapefruit'...**  
**100% complete...** Aunque ambos conjuntos de tareas generan el mismo resultado, la versión que usa la directiva personalizada permite que el objeto `printer` se ejecute con una prioridad elevada y, por tanto, con una mayor capacidad de respuesta.  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `permute-strings.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc permute\-strings.cpp**  
  
## Vea también  
 [Directivas del programador](../../parallel/concrt/scheduler-policies.md)   
 [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)   
 