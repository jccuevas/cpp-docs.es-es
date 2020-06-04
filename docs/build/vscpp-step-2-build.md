---
title: Compilación y ejecución de un proyecto de aplicación de consola de C++
description: Compilación y ejecución de una aplicación de consola "Hola mundo" en Visual C++
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749241"
---
# <a name="build-and-run-a-c-console-app-project"></a>Compilación y ejecución de un proyecto de aplicación de consola de C++

Ha creado un proyecto de aplicación de consola de C++ y ha escrito el código. Ahora puede compilarlo y ejecutarlo en Visual Studio. Después, ejecútelo como una aplicación independiente desde la línea de comandos.

## <a name="prerequisites"></a>Requisitos previos

- Instalar y ejecutar Visual Studio con la carga de trabajo Desarrollo para el escritorio con C++ en el equipo. Si todavía no está instalada, siga los pasos en [Instalación de compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md).

- Cree un proyecto de "Hola mundo" y escriba su código fuente. Si aún no ha realizado este paso, siga los pasos descritos en [Creación de un proyecto de aplicación de consola de C++](vscpp-step-1-create.md).

Si Visual Studio tiene este aspecto, está listo para compilar y ejecutar la aplicación:

   ![A punto para compilar el proyecto nuevo](media/vscpp-ready-to-build.png "A punto para compilar el proyecto nuevo")

## <a name="build-and-run-your-code-in-visual-studio"></a>Compilación y ejecución del código en Visual Studio

1. Para compilar el proyecto, seleccione **Compilar solución** en el menú **Compilar**. En la ventana **Salida** se muestran los resultados del proceso de compilación.

   ![Compilación del proyecto](media/vscpp-build-solution.gif "Compilar el proyecto")

1. Para ejecutar el código, en la barra de menús, seleccione **Depurar**, **Iniciar sin depurar**.

   ![Inicio del proyecto](media/vscpp-start-without-debugging.gif "Inicio del proyecto")

   Se abre una ventana de consola y después se ejecuta la aplicación. Al iniciar una aplicación de consola en Visual Studio, ejecuta el código y después imprime "Presione cualquier tecla para continuar . " para ofrecerle la oportunidad de ver la salida.

¡Enhorabuena! Ha creado la primera aplicación de consola "Hola mundo" en Visual Studio. Presione una tecla para cerrar la ventana de la consola y volver a Visual Studio.

[He tenido un problema.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Ejecución del código en una ventana de comandos

Normalmente, las aplicaciones de consola se ejecutan en el símbolo del sistema, no en Visual Studio. Una vez que la aplicación se compila con Visual Studio, se puede ejecutar desde cualquier ventana de comandos. Aquí se muestra cómo buscar y ejecutar la aplicación nueva en una ventana del símbolo del sistema.

1. En **Explorador de soluciones**, seleccione la solución HelloWorld (no el proyecto HelloWorld) y haga clic con el botón derecho para abrir el menú contextual. Elija **Abrir carpeta en el explorador de archivos** para abrir una ventana del **Explorador de archivos** en la carpeta de la solución HelloWorld.

1. En la ventana del **Explorador de archivos**, abra la carpeta Depuración. Esta carpeta contiene la aplicación, el archivo *HelloWorld.exe* y otro par de archivos de depuración. Mantenga presionada la tecla **Mayús** y haga clic con el botón derecho en *HelloWorld.exe* para abrir el menú contextual. Elija **Copiar como ruta de acceso** para copiar en el portapapeles la ruta de acceso a la aplicación.

1. Para abrir una ventana del símbolo del sistema, presione **Windows + R** y se abrirá el cuadro de diálogo **Ejecutar**. Escriba *cmd.exe* en el cuadro de texto **Abrir** y luego elija **Aceptar** para ejecutar una ventana del símbolo del sistema.

1. En la ventana del símbolo del sistema, haga clic con el botón derecho para pegar la ruta de acceso a la aplicación en el símbolo del sistema. Presione Entrar para ejecutar el código.

   ![Ejecución de la aplicación en el símbolo del sistema](media/vscpp-run-in-cmd.gif "Ejecución de la aplicación en el símbolo del sistema")

Enhorabuena, ha compilado y ejecutado una aplicación de consola en Visual Studio.

[He tenido un problema.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Pasos siguientes

Una vez que haya compilado y ejecutado esta aplicación sencilla, estará listo para proyectos más complejos. Para obtener más información, vea [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Tiene tutoriales más detallados que exploran las capacidades de Microsoft C++ en Visual Studio.

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Aquí puede encontrar soluciones a incidencias comunes al crear su primer proyecto de C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Compilación y ejecución del código en Visual Studio: incidencias

Si aparecen subrayados ondulados de color rojo en cualquier elemento del editor de código fuente, puede que la compilación tenga errores o advertencias. Compruebe que el código coincida con el ejemplo en ortografía, puntuación y uso de mayúsculas y minúsculas.

[Volver](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Ejecución del código en una ventana de comandos: incidencias

Si la ruta de acceso que aparece en el Explorador de archivos termina en *\\HelloWorld\\HelloWorld*, se ha abierto el *proyecto* HelloWorld en lugar de la *solución* HelloWorld. Se confundirá con una carpeta Depuración que no contiene la aplicación. Desplácese hacia arriba en el Explorador de archivos para llegar a la carpeta de la solución, la primera *HelloWorld* de la ruta de acceso. Esta carpeta también contiene una carpeta Depuración en la que se encuentra la aplicación.

También se puede ir a la carpeta Depuración de la solución en la línea de comandos para ejecutar la aplicación. La aplicación no se ejecutará desde otros directorios sin especificar la ruta de acceso a la aplicación. Sin embargo, se puede copiar la aplicación en otro directorio y ejecutarla desde allí. También es posible copiarla en un directorio que especifique la variable de entorno PATH y luego ejecutarla desde cualquier lugar.

Si no ve la opción **Copiar como ruta de acceso** en el menú contextual, descarte el menú y, después, mantenga presionada la tecla **Mayús** mientras vuelve a abrirlo. Este comando es solo para su comodidad. También se puede copiar la ruta de acceso en la carpeta desde la barra de búsqueda del Explorador de archivos, pegarla en el cuadro de diálogo **Ejecutar** y, después, escribir el nombre del ejecutable al final. Simplemente supone escribir un poco más, pero tiene el mismo resultado.

[Volver](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
