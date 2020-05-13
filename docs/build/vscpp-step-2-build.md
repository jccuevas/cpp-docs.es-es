---
title: Compilación y ejecución de un proyecto de aplicación de consola de C++
description: Compile y ejecute una aplicación de consola Hello World en Visual C++
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749241"
---
# <a name="build-and-run-a-c-console-app-project"></a>Compilación y ejecución de un proyecto de aplicación de consola de C++

Ha creado un proyecto de aplicación de consola De+ C+ e introducido el código. Ahora puede compilarlo y ejecutarlo en Visual Studio. A continuación, ejecútelo como una aplicación independiente desde la línea de comandos.

## <a name="prerequisites"></a>Prerrequisitos

- Instalar y ejecutar Visual Studio con la carga de trabajo Desarrollo para el escritorio con C++ en el equipo. Si aún no está instalado, siga los pasos descritos en [Instalar compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md).

- Crea un "¡Hola, mundo!" proyecto e introduzca su código fuente. Si aún no ha realizado este paso, siga los pasos descritos en Crear un proyecto de aplicación de [consola C++.](vscpp-step-1-create.md)

Si Visual Studio tiene este aspecto, está listo para compilar y ejecutar la aplicación:

   ![Listo para construir el nuevo proyecto](media/vscpp-ready-to-build.png "Listo para construir el nuevo proyecto")

## <a name="build-and-run-your-code-in-visual-studio"></a>Compile y ejecute el código en Visual Studio

1. Para compilar el proyecto, seleccione **Compilar solución** en el menú **Compilar**. En la ventana **Salida** se muestran los resultados del proceso de compilación.

   ![Construir el proyecto](media/vscpp-build-solution.gif "Compilación del proyecto")

1. Para ejecutar el código, en la barra de menús, seleccione **Depurar**, **Iniciar sin depurar**.

   ![Inicio del proyecto](media/vscpp-start-without-debugging.gif "Inicio del proyecto")

   Se abre una ventana de consola y después se ejecuta la aplicación. Al iniciar una aplicación de consola en Visual Studio, ejecuta el código y después imprime "Presione cualquier tecla para continuar . ." para ofrecerle la oportunidad de ver la salida.

¡Enhorabuena! Ha creado la primera aplicación de consola "Hola mundo" en Visual Studio. Presione una tecla para cerrar la ventana de la consola y volver a Visual Studio.

[He tenido un problema.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Ejecute el código en una ventana de comandos

Normalmente, se ejecutan aplicaciones de consola en el símbolo del sistema, no en Visual Studio. Una vez que Visual Studio compila la aplicación, puede ejecutarla desde cualquier ventana de comandos. A continuación se muestra cómo buscar y ejecutar la nueva aplicación en una ventana del símbolo del sistema.

1. En el Explorador de **soluciones**, seleccione la solución HelloWorld (no el proyecto HelloWorld) y haga clic con el botón derecho para abrir el menú contextual. Elija **Abrir carpeta en** el Explorador de archivos para abrir una ventana del **Explorador** de archivos en la carpeta de la solución HelloWorld.

1. En la ventana **Explorador** de archivos, abra la carpeta Depurar. Esta carpeta contiene la aplicación, *HelloWorld.exe*y un par de otros archivos de depuración. Mantenga pulsada la **tecla Mayús** y haga clic con el botón derecho en *HelloWorld.exe* para abrir el menú contextual. Elija **Copiar como ruta** de acceso para copiar la ruta de acceso a la aplicación en el portapapeles.

1. Para abrir una ventana del símbolo del sistema, presione **Windows+R** para abrir el cuadro de diálogo **Ejecutar.** Escriba *cmd.exe* en el cuadro de texto **Abrir** y, a continuación, elija **Aceptar** para ejecutar una ventana del símbolo del sistema.

1. En la ventana del símbolo del sistema, haga clic con el botón derecho para pegar la ruta de acceso a la aplicación en el símbolo del sistema. Presione Intro para ejecutar la aplicación.

   ![Ejecute la aplicación en el símbolo del sistema](media/vscpp-run-in-cmd.gif "Ejecute la aplicación en el símbolo del sistema")

¡Felicitaciones, ha creado y ejecutado una aplicación de consola en Visual Studio!

[He tenido un problema.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Pasos siguientes

Una vez que haya creado y ejecutado esta sencilla aplicación, estará listo para proyectos más complejos. Para obtener más información, vea Uso del IDE de Visual Studio para el desarrollo de [escritorios de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Tiene tutoriales más detallados que exploran las capacidades de Microsoft C++ en Visual Studio.

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Venga aquí para encontrar soluciones a problemas comunes cuando cree su primer proyecto C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Compile y ejecute el código en Visual Studio: problemas

Si las ondulaciones rojas aparecen debajo de cualquier cosa en el editor de código fuente, la compilación puede tener errores o advertencias. Compruebe que el código coincide con el ejemplo de ortografía, puntuación y mayúsculas y minúsculas.

[Volver.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Ejecute el código en una ventana de comandos: problemas

Si la ruta de acceso que se muestra en el Explorador de archivos finaliza en * \\\\HelloWorld HelloWorld*, ha abierto el *proyecto* HelloWorld en lugar de la *solución*HelloWorld . Se confundirá con una carpeta de depuración que no contiene la aplicación. Navegue un nivel en el Explorador de archivos para llegar a la carpeta de la solución, el primer *HelloWorld* en la ruta de acceso. Esta carpeta también contiene una carpeta De depuración y encontrará la aplicación allí.

También puede navegar a la carpeta de depuración de la solución en la línea de comandos para ejecutar la aplicación. La aplicación no se ejecutará desde otros directorios sin especificar la ruta de acceso a la aplicación. Sin embargo, puede copiar la aplicación en otro directorio y ejecutarla desde allí. También es posible copiarlo en un directorio especificado por la variable de entorno PATH y, a continuación, ejecutarlo desde cualquier lugar.

Si no ve **Copiar como ruta** en el menú contextual, descarte el menú y, a continuación, mantenga pulsada la tecla **Mayús** mientras vuelve a abrirla. Este comando es sólo por conveniencia. También puede copiar la ruta de acceso a la carpeta desde la barra de búsqueda del Explorador de archivos y pegarla en el cuadro de diálogo **Ejecutar** y, a continuación, escribir el nombre del ejecutable al final. Es sólo un poco más de mecanografía, pero tiene el mismo resultado.

[Volver.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
