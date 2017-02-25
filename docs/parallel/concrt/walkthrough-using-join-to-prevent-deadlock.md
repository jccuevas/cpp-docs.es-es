---
title: "Tutorial: Usar la clase join para evitar un interbloqueo | Microsoft Docs"
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
  - "impedir el interbloqueo con combinaciones [Runtime de simultaneidad]"
  - "interbloqueo, impedir [Runtime de simultaneidad]"
  - "combinaciones no expansivas, ejemplo"
  - "join (clase), ejemplo"
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Tutorial: Usar la clase join para evitar un interbloqueo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se usa el problema de la cena de los filósofos para ilustrar cómo se usa la clase [concurrency::join](../../parallel/concrt/reference/join-class.md) para evitar el interbloqueo en la aplicación.  En una aplicación de software, el *interbloqueo* se produce cuando dos o más procesos mantienen un recurso y esperan mutuamente a que el otro proceso libere algún otro recurso.  
  
 El problema de la cena de los filósofos es un ejemplo concreto del conjunto general de problemas que se pueden producir cuando se comparte un conjunto de recursos entre varios procesos simultáneos.  
  
## Requisitos previos  
 Lea los siguientes temas antes de iniciar este tutorial:  
  
-   [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)  
  
-   [Tutorial: Crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
  
-   [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)  
  
-   [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> Secciones  
 Este tutorial contiene las siguientes secciones:  
  
-   [El problema de la cena de los filósofos](#problem)  
  
-   [Una implementación sencilla](#deadlock)  
  
-   [Usar una combinación para evitar el interbloqueo](#solution)  
  
##  <a name="problem"></a> El problema de la cena de los filósofos  
 El problema de la cena de los filósofos ilustra cómo se produce el interbloqueo en una aplicación.  En este problema, cinco filósofos están sentados a una mesa redonda.  Cada filósofo alterna entre pensar y comer.  Cada filósofo debe compartir un palillo con el vecino sentado a la izquierda y otro palillo con el vecino sentado a la derecha.  En la siguiente ilustración se muestra este diseño.  
  
 ![El problema de la cena de los filósofos](../../parallel/concrt/media/dining_philosophersproblem.png "Dining\_PhilosophersProblem")  
  
 Para comer, un filósofo debe tener en la mano dos palillos.  Si cada filósofo tiene un solo palillo y está esperando a que le den otro, ninguno puede comer y todos se quedan sin comer.  
  
 \[[Arriba](#top)\]  
  
##  <a name="deadlock"></a> Una implementación sencilla  
 En el siguiente ejemplo se muestra una implementación sencilla del problema de la cena de los filósofos.  La clase `philosopher`, que se deriva de [concurrency::agent](../../parallel/concrt/reference/agent-class.md), permite que cada filósofo actúe de forma independiente.  En el ejemplo se usa una matriz compartida de objetos [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) para dar a cada objeto `philosopher` acceso exclusivo a un par de palillos.  
  
 Para relacionar la implementación con la ilustración, la clase `philosopher` representa a un filósofo.  Una variable `int` representa cada palillo.  Los objetos `critical_section` sirven como contenedores en los que se encuentran los palillos.  El método `run` simula la vida del filósofo.  El método `think` simula el acto de pensar y el método `eat` simula el acto de comer.  
  
 Un objeto `philosopher` bloquea ambos objetos `critical_section` para simular la retirada de los palillos de los contenedores antes de llamar al método `eat`.  Después de la llamada a `eat`, el objeto `philosopher` devuelve los palillos a los contenedores, y los objetos `critical_section` vuelven a establecerse en el estado desbloqueado.  
  
 El método `pickup_chopsticks` ilustra dónde se puede producir el interbloqueo.  Si cada objeto `philosopher` obtiene acceso a uno de los bloqueos, ningún objeto `philosopher` puede continuar porque otro objeto `philosopher` controla el otro bloqueo.  
  
## Ejemplo  
  
### Descripción  
  
### Código  
 [!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_1.cpp)]  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `philosophers-deadlock.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc philosophers\-deadlock.cpp**  
  
 \[[Arriba](#top)\]  
  
##  <a name="solution"></a> Usar una combinación para evitar el interbloqueo  
 En esta sección se muestra cómo usar los búferes de mensajes y las funciones de paso de mensajes para eliminar la oportunidad de que se produzcan interbloqueos.  
  
 Para relacionar este ejemplo con el anterior, la clase `philosopher` reemplaza cada objeto `critical_section` con un objeto [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) y un objeto `join`.  El objeto `join` sirve como un árbitro que proporciona los palillos al filósofo.  
  
 En este ejemplo se usa la clase `unbounded_buffer` porque cuando un destino recibe un mensaje de un objeto `unbounded_buffer`, el mensaje se quita de la cola de mensajes.  Esto permite que un objeto `unbounded_buffer` contenga un mensaje para indicar que el palillo está disponible.  Un objeto `unbounded_buffer` que no contiene ningún mensaje indica que el palillo se está usando.  
  
 Este ejemplo usa un objeto `join` no expansivo porque una combinación no expansiva solo da cada acceso a ambos palillos al objeto `philosopher` cuando ambos objetos `unbounded_buffer` contienen un mensaje.  Una combinación expansiva no evitaría el interbloqueo porque aceptaría los mensajes en cuanto estuvieran disponibles.  Se puede producir el interbloqueo si todos los objetos `join` expansivos reciben uno de los mensajes pero esperan para siempre a que el otro esté disponible.  
  
 Para obtener más información sobre las combinaciones expansivas y no expansivas, y las diferencias entre los diversos tipos de búfer de mensajes, vea [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).  
  
#### Para evitar el interbloqueo en este ejemplo  
  
1.  Quite el siguiente código del ejemplo.  
  
     [!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_2.cpp)]  
  
2.  Cambie el tipo de los miembros de datos `_right` y `_left` de la clase `philosopher` a `unbounded_buffer`.  
  
     [!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_3.cpp)]  
  
3.  Modifique el constructor `philosopher` de forma que tome los objetos `unbounded_buffer` como parámetros.  
  
     [!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_4.cpp)]  
  
4.  Modifique el método `pickup_chopsticks` para usar un objeto `join` no expansivo para recibir los mensajes de los búferes de mensajes para ambos palillos.  
  
     [!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_5.cpp)]  
  
5.  Modifique el método `putdown_chopsticks` para liberar el acceso a los palillos enviando un mensaje a los búferes de mensajes para ambos palillos.  
  
     [!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_6.cpp)]  
  
6.  Modifique el método `run` de forma que retenga los resultados del método `pickup_chopsticks` y pase esos resultados al método `putdown_chopsticks`.  
  
     [!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_7.cpp)]  
  
7.  Modifique la declaración de la variable `chopsticks` en la función `wmain` para que sea una matriz de objetos `unbounded_buffer`, cada uno de los cuales contiene un mensaje.  
  
     [!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_8.cpp)]  
  
## Ejemplo  
  
### Descripción  
 A continuación se muestra el ejemplo completo que usa los objetos `join` no expansivos para eliminar el riesgo de interbloqueo.  
  
### Código  
 [!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_9.cpp)]  
  
### Comentarios  
 Este ejemplo produce el siguiente resultado:  
  
  **aristotle ate 50 times.**  
**descartes ate 50 times.**  
**hobbes ate 50 times.**  
**socrates ate 50 times.**  
**plato ate 50 times.**   
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `philosophers-join.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc philosophers\-join.cpp**  
  
 \[[Arriba](#top)\]  
  
## Vea también  
 [Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)   
 [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)