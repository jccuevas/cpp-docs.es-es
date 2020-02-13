---
title: 'Cómo: Seleccionar tareas completadas'
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 75ecac8dd0e8845401e3e287e8c95ea614055970
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142472"
---
# <a name="how-to-select-among-completed-tasks"></a>Cómo: Seleccionar tareas completadas

En este ejemplo se muestra cómo usar las clases [Concurrency:: Choice](../../parallel/concrt/reference/choice-class.md) y [Concurrency:: join](../../parallel/concrt/reference/join-class.md) para seleccionar la primera tarea para completar un algoritmo de búsqueda.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se ejecutan dos algoritmos de búsqueda en paralelo y se selecciona el primer algoritmo para que se complete. En este ejemplo se define el tipo `employee`, que almacena un identificador numérico y un sueldo para un empleado. La función `find_employee` encuentra al primer empleado que tiene el identificador o el sueldo especificados. La función `find_employee` también controla el caso en el que ningún empleado tiene el identificador o el sueldo especificados. La función `wmain` crea una matriz de objetos `employee` y busca varios valores del identificador y del sueldo.

En el ejemplo se usa un objeto `choice` para realizar la selección entre los siguientes casos:

1. Existe un empleado que tiene el identificador especificado.

1. Existe un empleado que tiene el sueldo especificado.

1. No existe ningún empleado con el identificador o el sueldo especificados.

En los dos primeros casos, en el ejemplo se usa un objeto [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) para contener el identificador y otro objeto `single_assignment` que contenga el salario. En el ejemplo se usa un objeto `join` para el tercer caso. El objeto `join` se compone de dos objetos `single_assignment` adicionales, uno para el caso en el que no existe ningún empleado con el identificador especificado y otro para el caso en el que no existe ningún empleado con el sueldo especificado. El objeto `join` envía un mensaje cuando cada uno de sus miembros recibe un mensaje. En este ejemplo, el objeto `join` envía un mensaje cuando no existe ningún empleado con el identificador o el sueldo especificados.

En el ejemplo se usa un objeto [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) para ejecutar los dos algoritmos de búsqueda en paralelo. Cada tarea de búsqueda escribe en uno de los objetos `single_assignment` para indicar si existe el empleado especificado. En el ejemplo se usa la función [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) para obtener el índice del primer búfer que contiene un mensaje y un bloque `switch` para imprimir el resultado.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

En este ejemplo se usa la función auxiliar [Concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) para crear objetos `choice` y la función auxiliar [Concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) para crear objetos `join`.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `find-employee.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Find-Employee. cpp**

## <a name="see-also"></a>Consulte también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[choice (clase)](../../parallel/concrt/reference/choice-class.md)<br/>
[join (clase)](../../parallel/concrt/reference/join-class.md)
