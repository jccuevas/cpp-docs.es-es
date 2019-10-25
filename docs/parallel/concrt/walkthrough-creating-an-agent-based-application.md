---
title: 'Tutorial: Creación de una aplicación basada en agente'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 4a2fabd9ab4f358d40b17e662fb64ab70d01c58e
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631660"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Tutorial: Creación de una aplicación basada en agente

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

- [Usar la clase file_reader en la aplicación](#useagentclass)

##  <a name="createapplication"></a>Creación de la aplicación de consola

En esta sección se muestra cómo crear C++ una aplicación de consola que haga referencia a los archivos de encabezado que utilizará el programa. Los pasos iniciales varían en función de la versión de Visual Studio que se use. Asegúrese de que el selector de versiones esté configurado correctamente en la parte superior izquierda de esta página.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Para crear una C++ aplicación de consola en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**. 

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la página siguiente, escriba `BasicAgent` como nombre del proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

1. Haga clic con el botón secundario en el nodo del proyecto en **Explorador de soluciones**y elija **propiedades**. En **propiedades** > de configuración > **CC++** **/encabezados**precompilados encabezado precompilado, elija crear.  > 

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Para crear una C++ aplicación de consola en Visual Studio 2017 y versiones anteriores

1. En el menú **archivo** , haga clic en **nuevo**y, a continuación, haga clic en **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** .

1. En el cuadro de diálogo **nuevo proyecto** , seleccione el nodo **Visual C++**  en el panel **tipos de proyecto** y, a continuación, seleccione aplicación de **consola Win32** en el panel **plantillas** . Escriba un nombre para el proyecto, por ejemplo, `BasicAgent`y, a continuación, haga clic en **Aceptar** para mostrar el **Asistente para aplicaciones de consola Win32**.

1. En el cuadro de diálogo **Asistente para aplicaciones de consola Win32** , haga clic en **Finalizar**.

::: moniker-end

1. En *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores), agregue el código siguiente:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   El archivo de encabezado Agents. h contiene la funcionalidad de la clase [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) .

1. Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú compilar, haga clic en compilar **solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo clic en **iniciar** depuración en el menú Depurar.

[[Arriba](#top)]

##  <a name="createagentclass"></a>Crear la clase file_reader

En esta sección se muestra cómo crear la clase `file_reader`. El runtime programa cada agente para realizar el trabajo en su propio contexto. Por tanto, puede crear un agente que realice el trabajo de forma sincrónica pero que interactúe con otros componentes de forma asincrónica. La clase `file_reader` lee los datos de un archivo de entrada determinado y los envía desde este archivo a un componente de destino determinado.

#### <a name="to-create-the-file_reader-class"></a>Para crear la clase file_reader

1. Agregue un nuevo archivo de encabezado de C++ al proyecto. Para ello, haga clic con el botón secundario en el nodo **archivos de encabezado** de **Explorador de soluciones**, haga clic en **Agregar**y, a continuación, haga clic en **nuevo elemento**. En el panel **plantillas** , seleccione **archivo de encabezado (. h)** . En el cuadro de diálogo **Agregar nuevo elemento** , `file_reader.h` escriba en el cuadro **nombre** y, a continuación, haga clic en **Agregar**.

1. En file_reader.h, agregue el siguiente código.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. En file_reader.h, cree una clase de nombre `file_reader` que derive de `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Agregue los siguientes miembros de datos a la sección `private` de la clase.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   El miembro `_file_name` es el nombre de archivo del que lee el agente. El `_target` miembro es un objeto [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) en el que el agente escribe el contenido del archivo. El miembro `_error` contiene cualquier error que se produce durante la vida del agente.

1. Agregue el código siguiente para los constructores de `file_reader` en la sección `public` de la clase `file_reader`.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Cada sobrecarga de constructor establece los miembros de datos de `file_reader`. La segunda y tercera sobrecarga de constructor permiten que la aplicación use un programador concreto con el agente. La primera sobrecarga utiliza el programador predeterminado con el agente.

1. Agregue el método `get_error` a la sección pública de la clase `file_reader`.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   El método `get_error` recupera cualquier error que se produce durante la vida del agente.

1. Implemente el método Concurrency [:: Agent:: Run](reference/agent-class.md#run) en `protected` la sección de la clase.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

El método `run` abre el archivo y lee sus datos. El método `run` utiliza el control de excepciones para capturar los errores que se produzcan durante el procesamiento del archivo.

   Cada vez que este método lee datos del archivo, llama a la función [Concurrency:: Asend](reference/concurrency-namespace-functions.md#asend) para enviar esos datos al búfer de destino. Envía la cadena vacía a su búfer de destino para indicar el fin del procesamiento.

En el ejemplo siguiente se muestra el contenido completo de file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Arriba](#top)]

##  <a name="useagentclass"></a>Usar la clase file_reader en la aplicación

En esta sección se muestra cómo utilizar la clase `file_reader` para leer el contenido de un archivo de texto. También se muestra cómo crear un objeto [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) que recibe los datos de este archivo y calcula su suma de comprobación Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Para utilizar la clase file_reader en la aplicación

1. En BasicAgent.cpp, agregue la siguiente instrucción `#include`.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. En BasicAgent.cpp, agregue las siguientes directivas `using`.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. En la `_tmain` función, cree un objeto [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) que señale el final del procesamiento.

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

Llame siempre a [Concurrency:: Agent::d un](reference/agent-class.md#done) método para pasar el agente al estado completado. Por lo general se llama a este método antes de volver del método `run`.

## <a name="next-steps"></a>Pasos siguientes

Para obtener otro ejemplo de una aplicación basada en agente, [consulte Tutorial: Usar join para evitar el](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)interbloqueo.

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[Estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Tutorial: Uso de una combinación para evitar el interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
