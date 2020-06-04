---
title: 'Tutorial: Crear una aplicación basada en agente'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 20197786e3d3c2d34d29af748c1cc073902cf70d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377457"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Tutorial: Crear una aplicación basada en agente

En este tema se describe cómo crear una aplicación basada en agente básica. En este tutorial, puede crear un agente que lee datos de un archivo de texto de forma asincrónica. La aplicación utiliza el algoritmo de suma de comprobación Adler-32 para calcular la suma de comprobación del contenido de ese archivo.

## <a name="prerequisites"></a>Prerrequisitos

Para completar este tutorial, debe comprender los siguientes temas:

- [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funciones de paso de mensajes](../../parallel/concrt/message-passing-functions.md)

- [Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Secciones

En este tutorial se muestra cómo realizar las tareas siguientes:

- [Crear la aplicación de consola](#createapplication)

- [Crear la clase file_reader](#createagentclass)

- [Usar la clase file_reader en la aplicación](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Creación de la aplicación de consola

En esta sección se muestra cómo crear una aplicación de consola C++ que hace referencia a los archivos de encabezado que utilizará el programa. Los pasos iniciales varían en función de la versión de Visual Studio que esté utilizando. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Para crear una aplicación de consola C++ en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++ **, establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**.

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la página `BasicAgent` siguiente, escriba como nombre para el proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

1. Haga clic con el botón secundario en el nodo del proyecto en el **Explorador**de soluciones y elija **Propiedades**. En **Propiedades** > de configuración**C/C++** > **Encabezados precompilados encabezadopres,** > **Precompiled header** elija **Crear**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Para crear una aplicación de consola C++ en Visual Studio 2017 y versiones anteriores

1. En **el** archivo menú, haga clic en **nuevo**y, a continuación, haga clic en **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.

1. En el cuadro de diálogo **Nuevo proyecto,** seleccione el nodo **Visual C++** en el panel **Tipos** de proyecto y, a continuación, seleccione Aplicación de **consola Win32** en el panel **Plantillas.** Escriba un nombre para el `BasicAgent`proyecto, por ejemplo , y, a continuación, haga clic en **Aceptar** para mostrar el Asistente para aplicaciones de **consola Win32**.

1. En el cuadro de diálogo Asistente para aplicaciones de **consola Win32** , haga clic en **Finalizar**.

::: moniker-end

1. En *pch.h* (*stdafx.h* en Visual Studio 2017 y versiones anteriores), agregue el código siguiente:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   El archivo de encabezado agents.h contiene la funcionalidad de la clase [concurrency::agent.](../../parallel/concrt/reference/agent-class.md)

1. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú **Compilar,** haga clic en **Compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo clic en **Iniciar depuración** en el menú **Depurar.**

[[Superior](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Creación de la clase file_reader

En esta sección se muestra cómo crear la clase `file_reader`. El runtime programa cada agente para realizar el trabajo en su propio contexto. Por tanto, puede crear un agente que realice el trabajo de forma sincrónica pero que interactúe con otros componentes de forma asincrónica. La clase `file_reader` lee los datos de un archivo de entrada determinado y los envía desde este archivo a un componente de destino determinado.

#### <a name="to-create-the-file_reader-class"></a>Para crear la clase file_reader

1. Agregue un nuevo archivo de encabezado de C++ al proyecto. Para ello, haga clic con el botón secundario en el nodo Archivos de **encabezado** del **Explorador**de soluciones , haga clic en **Agregar**y, a continuación, haga clic en **Nuevo elemento**. En el panel **Plantillas,** seleccione **Archivo de encabezado (.h).** En el cuadro de diálogo `file_reader.h` Agregar nuevo **elemento,** escriba el cuadro **Nombre** y, a continuación, haga clic en **Agregar**.

1. En file_reader.h, agregue el siguiente código.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. En file_reader.h, cree una clase de nombre `file_reader` que derive de `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Agregue los siguientes miembros de datos a la sección `private` de la clase.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   El miembro `_file_name` es el nombre de archivo del que lee el agente. El `_target` miembro es un objeto [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) en el que el agente escribe el contenido del archivo. El miembro `_error` contiene cualquier error que se produce durante la vida del agente.

1. Agregue el código siguiente para los constructores de `file_reader` en la sección `public` de la clase `file_reader`.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Cada sobrecarga de constructor establece los miembros de datos de `file_reader`. La segunda y tercera sobrecarga de constructor permiten que la aplicación use un programador concreto con el agente. La primera sobrecarga utiliza el programador predeterminado con el agente.

1. Agregue el método `get_error` a la sección pública de la clase `file_reader`.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   El método `get_error` recupera cualquier error que se produce durante la vida del agente.

1. Implemente el método [concurrency::agent::run](reference/agent-class.md#run) en la sección de la `protected` clase.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

El método `run` abre el archivo y lee sus datos. El método `run` utiliza el control de excepciones para capturar los errores que se produzcan durante el procesamiento del archivo.

   Cada vez que este método lee los datos del archivo, llama a la función [concurrency::asend](reference/concurrency-namespace-functions.md#asend) para enviar esos datos al búfer de destino. Envía la cadena vacía a su búfer de destino para indicar el fin del procesamiento.

En el ejemplo siguiente se muestra el contenido completo de file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Superior](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Uso de la clase file_reader en la aplicación

En esta sección se muestra cómo utilizar la clase `file_reader` para leer el contenido de un archivo de texto. También muestra cómo crear un objeto [concurrency::call](../../parallel/concrt/reference/call-class.md) que recibe estos datos de archivo y calcula su suma de comprobación Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Para utilizar la clase file_reader en la aplicación

1. En BasicAgent.cpp, agregue la siguiente instrucción `#include`.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. En BasicAgent.cpp, agregue las siguientes directivas `using`.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. En `_tmain` la función, cree un objeto [concurrency::event](../../parallel/concrt/reference/event-class.md) que señale el final del procesamiento.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Cree un objeto `call` que actualice la suma de comprobación cuando reciba datos.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Este objeto `call` también establece el objeto `event` cuando recibe la cadena vacía para señalar el fin del procesamiento.

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

[[Superior](#top)]

## <a name="sample-input"></a>Entrada de ejemplo

Este es el contenido de ejemplo del archivo de entrada text.txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Salida de ejemplo

Cuando se utiliza con la entrada de ejemplo, este programa produce el siguiente resultado:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Programación sólida

Para evitar el acceso simultáneo a los miembros de datos, se recomienda agregar métodos que realicen el trabajo en las secciones `protected` o `private` de la clase. Agregue únicamente los métodos que envían o reciben mensajes del agente en la sección `public` de la clase.

Llame siempre al método [concurrency::agent::dun](reference/agent-class.md#done) método para mover el agente al estado completado. Por lo general se llama a este método antes de volver del método `run`.

## <a name="next-steps"></a>Pasos siguientes

Para obtener otro ejemplo de una aplicación basada en agente, vea Tutorial: Uso de [la combinación para evitar el interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Consulte también

[biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones de paso de mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Tutorial: Usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
