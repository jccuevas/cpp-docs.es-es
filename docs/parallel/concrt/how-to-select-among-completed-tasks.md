---
title: Procedimiento Seleccionar tareas completadas
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 0d31f9bd16aaa70cc773e60e4f1193e66ec520f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205647"
---
# <a name="how-to-select-among-completed-tasks"></a>Procedimiento Seleccionar tareas completadas

En este ejemplo se muestra cómo usar el [Concurrency:: choice](../../parallel/concrt/reference/choice-class.md) y [Concurrency:: join](../../parallel/concrt/reference/join-class.md) clases para seleccionar la primera tarea para completar un algoritmo de búsqueda.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se ejecutan dos algoritmos de búsqueda en paralelo y se selecciona el primer algoritmo para que se complete. En este ejemplo se define el tipo `employee`, que almacena un identificador numérico y un sueldo para un empleado. La función `find_employee` encuentra al primer empleado que tiene el identificador o el sueldo especificados. La función `find_employee` también controla el caso en el que ningún empleado tiene el identificador o el sueldo especificados. La función `wmain` crea una matriz de objetos `employee` y busca varios valores del identificador y del sueldo.

En el ejemplo se usa un objeto `choice` para realizar la selección entre los siguientes casos:

1. Existe un empleado que tiene el identificador especificado.

1. Existe un empleado que tiene el sueldo especificado.

1. No existe ningún empleado con el identificador o el sueldo especificados.

Para los dos primeros casos, el ejemplo se usa un [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) objeto para contener el identificador y otro `single_assignment` objeto para almacenar el salario. En el ejemplo se usa un objeto `join` para el tercer caso. El objeto `join` se compone de dos objetos `single_assignment` adicionales, uno para el caso en el que no existe ningún empleado con el identificador especificado y otro para el caso en el que no existe ningún empleado con el sueldo especificado. El objeto `join` envía un mensaje cuando cada uno de sus miembros recibe un mensaje. En este ejemplo, el objeto `join` envía un mensaje cuando no existe ningún empleado con el identificador o el sueldo especificados.

El ejemplo se usa un [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objeto que se va a ejecutar los dos algoritmos de búsqueda en paralelo. Cada tarea de búsqueda escribe en uno de los objetos `single_assignment` para indicar si existe el empleado especificado. El ejemplo se usa el [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) función para obtener el índice del primer búfer que contiene un mensaje y un `switch` bloque para imprimir el resultado.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

Este ejemplo se usa el [Concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) función auxiliar para crear `choice` objetos y el [Concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) función auxiliar para crear `join` objetos.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `find-employee.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe /EHsc find-employee.cpp**

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[choice (clase)](../../parallel/concrt/reference/choice-class.md)<br/>
[join (clase)](../../parallel/concrt/reference/join-class.md)
