---
title: 'Tutorial: Crear una aplicación basada en agente | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68c4b389bdd8f1121a59bce1a0ca8942f077e062
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377178"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Tutorial: Crear una aplicación basada en agente

En este tema se describe cómo crear una aplicación basada en agente básica. En este tutorial, puede crear un agente que lee datos de un archivo de texto de forma asincrónica. La aplicación utiliza el algoritmo de suma de comprobación Adler-32 para calcular la suma de comprobación del contenido de ese archivo.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe comprender los siguientes temas:

- [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)

- [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> Secciones

En este tutorial se muestra cómo realizar las tareas siguientes:

- [Crear la aplicación de consola](#createapplication)

- [Crear la clase file_reader](#createagentclass)

- [Uso de la clase file_reader en la aplicación](#useagentclass)

##  <a name="createapplication"></a> Creación de la aplicación de consola

En esta sección se muestra cómo crear una aplicación de consola de Visual C++ que hace referencia a los archivos de encabezado que el programa usará.

#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>Para crear una aplicación Visual C++ utilizando el Asistente para aplicación de consola Win32

1. En el **archivo** menú, haga clic en **New**y, a continuación, haga clic en **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.

1. En el **nuevo proyecto** cuadro de diálogo, seleccione el **Visual C++** nodo en el **tipos de proyecto** panel y, a continuación, seleccione **aplicación de consola Win32** en el **plantillas** panel. Escriba un nombre para el proyecto, por ejemplo, `BasicAgent`y, a continuación, haga clic en **Aceptar** para mostrar el **Asistente para aplicaciones de consola Win32**.

1. En el **Asistente para aplicaciones de consola Win32** cuadro de diálogo, haga clic en **finalizar**.

1. En stdafx.h, agregue el código siguiente.

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

     The header file agents.h contains the functionality of the [concurrency::agent](../../parallel/concrt/reference/agent-class.md) class.

1. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el **compilar** menú, haga clic en **compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo **Iniciar depuración** en el **depurar** menú.

[[Arriba](#top)]

##  <a name="createagentclass"></a> Crear la clase file_reader

En esta sección se muestra cómo crear la clase `file_reader`. El runtime programa cada agente para realizar el trabajo en su propio contexto. Por tanto, puede crear un agente que realice el trabajo de forma sincrónica pero que interactúe con otros componentes de forma asincrónica. La clase `file_reader` lee los datos de un archivo de entrada determinado y los envía desde este archivo a un componente de destino determinado.

#### <a name="to-create-the-filereader-class"></a>Para crear la clase file_reader

1. Agregue un nuevo archivo de encabezado de C++ al proyecto. Para ello, haga clic en el **archivos de encabezado** nodo **el Explorador de soluciones**, haga clic en **agregar**y, a continuación, haga clic en **nuevo elemento**. En el **plantillas** panel, seleccione **archivo de encabezado (. h)**. En el **Agregar nuevo elemento** cuadro de diálogo, escriba `file_reader.h` en el **nombre** cuadro y, a continuación, haga clic en **agregar**.

1. En file_reader.h, agregue el siguiente código.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. En file_reader.h, cree una clase de nombre `file_reader` que derive de `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Agregue los siguientes miembros de datos a la sección `private` de la clase.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

     The `_file_name` member is the file name that the agent reads from. The `_target` member is a [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) object that the agent writes the contents of the file to. The `_error` member holds any error that occurs during the life of the agent.

1. Agregue el código siguiente para los constructores de `file_reader` en la sección `public` de la clase `file_reader`.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

     Each constructor overload sets the `file_reader` data members. The second and third constructor overload enables your application to use a specific scheduler with your agent. The first overload uses the default scheduler with your agent.

1. Agregue el método `get_error` a la sección pública de la clase `file_reader`.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

     The `get_error` method retrieves any error that occurs during the life of the agent.

1. Implemente el [concurrency::agent::run](reference/agent-class.md#run) método en la `protected` sección de la clase.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

El método `run` abre el archivo y lee sus datos. El método `run` utiliza el control de excepciones para capturar los errores que se produzcan durante el procesamiento del archivo.

   Cada vez que este método lee datos desde el archivo, lo llama el [Concurrency:: asend ](reference/concurrency-namespace-functions.md#asend) /función para enviar datos al búfer de destino. Envía la cadena vacía a su búfer de destino para indicar el fin del procesamiento.

En el ejemplo siguiente se muestra el contenido completo de file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Arriba](#top)]

##  <a name="useagentclass"></a> Uso de la clase file_reader en la aplicación

En esta sección se muestra cómo utilizar la clase `file_reader` para leer el contenido de un archivo de texto. También muestra cómo crear un [Concurrency:: call](../../parallel/concrt/reference/call-class.md) objeto que recibe datos de este archivo y calcula su suma de comprobación Adler-32.

#### <a name="to-use-the-filereader-class-in-your-application"></a>Para utilizar la clase file_reader en la aplicación

1. En BasicAgent.cpp, agregue la siguiente instrucción `#include`.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. En BasicAgent.cpp, agregue las siguientes directivas `using`.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. En el `_tmain` función, cree un [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) objeto al que señala el final del procesamiento.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Cree un objeto `call` que actualice la suma de comprobación cuando reciba datos.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

     This `call` object also sets the `event` object when it receives the empty string to signal the end of processing.

1. Cree un objeto `file_reader` que lea del archivo test.txt y escriba el contenido de este archivo en el objeto `call`.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Inicie el agente y espere a que finalice.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Espere a que el objeto `call` reciba todos los datos y finalice.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Compruebe los errores del lector del archivo. Si no se ha producido ningún error, calcule la suma Adler-32 final e imprímala en la consola.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

En el ejemplo siguiente se muestra el archivo BasicAgent.cpp completo.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Arriba](#top)]

## <a name="sample-input"></a>Entrada de ejemplo

Este es el contenido de ejemplo del archivo de entrada text.txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Resultados del ejemplo

Cuando se utiliza con la entrada de ejemplo, este programa produce el siguiente resultado:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Programación sólida

Para evitar el acceso simultáneo a los miembros de datos, se recomienda agregar métodos que realicen el trabajo en las secciones `protected` o `private` de la clase. Agregue únicamente los métodos que envían o reciben mensajes del agente en la sección `public` de la clase.

Llame siempre a la [Concurrency:: Agent:: realiza](reference/agent-class.md#done) método para mover el agente al estado completado. Por lo general se llama a este método antes de volver del método `run`.

## <a name="next-steps"></a>Pasos siguientes

Para obtener otro ejemplo de una aplicación basada en agente, vea [Tutorial: usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Tutorial: Usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)

