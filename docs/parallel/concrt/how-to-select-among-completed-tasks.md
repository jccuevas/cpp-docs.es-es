---
title: "C&#243;mo: Seleccionar tareas completadas | Microsoft Docs"
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
  - "seleccionar tareas completadas [Runtime de simultaneidad]"
  - "tareas completadas, seleccionar [Runtime de simultaneidad]"
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
caps.latest.revision: 17
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Seleccionar tareas completadas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra cómo usar las clases [concurrency::choice](../../parallel/concrt/reference/choice-class.md) y [concurrency::join](../../parallel/concrt/reference/join-class.md) para seleccionar la primera tarea para completar un algoritmo de búsqueda.  
  
## Ejemplo  
 En el ejemplo siguiente se ejecutan dos algoritmos de búsqueda en paralelo y se selecciona el primer algoritmo para que se complete.  En este ejemplo se define el tipo `employee`, que almacena un identificador numérico y un sueldo para un empleado.  La función `find_employee` encuentra al primer empleado que tiene el identificador o el sueldo especificados.  La función `find_employee` también controla el caso en el que ningún empleado tiene el identificador o el sueldo especificados.  La función `wmain` crea una matriz de objetos `employee` y busca varios valores del identificador y del sueldo.  
  
 En el ejemplo se usa un objeto `choice` para realizar la selección entre los siguientes casos:  
  
1.  Existe un empleado que tiene el identificador especificado.  
  
2.  Existe un empleado que tiene el sueldo especificado.  
  
3.  No existe ningún empleado con el identificador o el sueldo especificados.  
  
 En el ejemplo, en los dos primeros casos se usa un objeto [concurrency::single\_assignment](../../parallel/concrt/reference/single-assignment-class.md) para almacenar el identificador y otro objeto `single_assignment` para almacenar el salario.  En el ejemplo se usa un objeto `join` para el tercer caso.  El objeto `join` se compone de dos objetos `single_assignment` adicionales, uno para el caso en el que no existe ningún empleado con el identificador especificado y otro para el caso en el que no existe ningún empleado con el sueldo especificado.  El objeto `join` envía un mensaje cuando cada uno de sus miembros recibe un mensaje.  En este ejemplo, el objeto `join` envía un mensaje cuando no existe ningún empleado con el identificador o el sueldo especificados.  
  
 En el ejemplo se usa un objeto [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) para ejecutar los dos algoritmos de búsqueda en paralelo.  Cada tarea de búsqueda escribe en uno de los objetos `single_assignment` para indicar si existe el empleado especificado.  En el ejemplo se usa la función [concurrency::receive](../Topic/receive%20Function.md) para obtener el índice del primer búfer que contiene un mensaje y un bloque `switch` para imprimir el resultado.  
  
 [!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/CPP/how-to-select-among-completed-tasks_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Employee with id 14758 has salary 27780.00.**  
**Employee with salary 29150.00 has id 84345.**  
**Employee with id 61935 has salary 29905.00.**  
**No employee has id 899 or salary 31223.00.** En este ejemplo se usa la función auxiliar [concurrency::make\_choice](../Topic/make_choice%20Function.md) para crear objetos `choice` y la función auxiliar [concurrency::make\_join](../Topic/make_join%20Function.md) para crear objetos `join`.  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `find-employee.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc find\-employee.cpp**  
  
## Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)   
 [Clase choice](../../parallel/concrt/reference/choice-class.md)   
 [join \(Clase\)](../../parallel/concrt/reference/join-class.md)