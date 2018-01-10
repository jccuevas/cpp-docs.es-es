---
title: "Compilar y ejecutar un proyecto de aplicación de consola de C++ | Documentos de Microsoft"
description: Instalar la compatibilidad de Visual Studio para Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology: devlang-C++
ms.devlang: C++
dev_langs: C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5b9c250b102b7d8847e99b87139136bc7df808b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="build-and-run-a-c-console-app-project"></a>Compilar y ejecutar un proyecto de aplicación de consola de C++

Cuando se crea un proyecto de aplicación de consola de C++ y se especificó el código, puede compilar y ejecutar en Visual Studio y, a continuación, ejecutarlo como una aplicación independiente desde la línea de comandos.

## <a name="prerequisites"></a>Requisitos previos

- Hacer que Visual Studio con el desarrollo de escritorio con cargas de trabajo de C++ instalados y ejecutándose en el equipo. Si aún no está instalado, siga los pasos de [compatibilidad instalar C++ en Visual Studio](../build/vscpp-step-0-installation.md).

- Crear un "Hello, World!" proyecto y escriba su código fuente. Si aún no lo ha hecho aún, siga los pasos de [crear un proyecto de aplicación de consola de C++](../build/vscpp-step-1-create.md).

Si Visual Studio tiene un aspecto similar al siguiente, está listo para compilar y ejecutar la aplicación:

   ![Listo para generar el nuevo proyecto](../build/media/vscpp-ready-to-build.png "listo para generar el nuevo proyecto")

## <a name="build-and-run-your-code-in-visual-studio"></a>Compilar y ejecutar el código en Visual Studio

1. Para compilar el proyecto, elija **generar solución** desde el **generar** menú. El **salida** ventana muestra los resultados del proceso de compilación.

   ![Compile el proyecto](../build/media/vscpp-build-solution.gif "compilar el proyecto")

1. Para ejecutar el código, en la barra de menús, elija **depurar**, **iniciar sin depurar**.

   ![Inicie el proyecto](../build/media/vscpp-start-without-debugging.gif "el proyecto de inicio")

    Abrirá una ventana de consola y, a continuación, ejecuta la aplicación. Cuando se inicia una aplicación de consola en Visual Studio, se ejecuta el código, a continuación, se imprime "Presione cualquier tecla para continuar. . ." para ofrecerle una oportunidad para ver el resultado.

¡Enhorabuena! Ha creado su primer "Hello, world!" aplicación de consola en Visual Studio. Presione una tecla para cerrar la ventana de consola y vuelva a Visual Studio.

[Produjo un problema.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Ejecutar el código en una ventana de comandos

Normalmente, las aplicaciones de consola se ejecutan en el símbolo del sistema, no en Visual Studio. Una vez que la aplicación se compila en Visual Studio, puede ejecutar desde cualquier ventana de comandos. Aquí se muestra cómo buscar y ejecutar la aplicación nuevo en una ventana del símbolo del sistema.

1. En **el Explorador de soluciones**, seleccione la solución HelloWorld y haga clic en para abrir el menú contextual. Elija **Abrir carpeta en el Explorador de archivos** para abrir un **Explorador de archivos** ventana en la carpeta de solución HelloWorld.

1. En el **Explorador de archivos** ventana, abra la carpeta de depuración. Contiene la aplicación, HelloWorld.exe y un par de otros archivos de depuración. Seleccione HelloWorld.exe, mantenga presionada la tecla MAYÚS y haga clic en para abrir el menú contextual. Elija **copiar como ruta de acceso** para copiar la ruta de acceso a la aplicación en el Portapapeles.

1. Para abrir una ventana del símbolo del sistema, presione R de Windows para abrir el **ejecutar** cuadro de diálogo. Escriba *cmd.exe* en el **abiertos** cuadro de texto, a continuación, elija **Aceptar** para ejecutar una ventana del símbolo del sistema.

1. En la ventana de símbolo del sistema, haga clic en para pegar la ruta de acceso a la aplicación en el símbolo del sistema. Presione ENTRAR para ejecutar la aplicación.

   ![Ejecutar la aplicación en la línea de comandos](../build/media/vscpp-run-in-cmd.gif "ejecutar la aplicación en el símbolo del sistema")

Enhorabuena, ha compilado y ejecutar una aplicación de consola en Visual Studio.

[Produjo un problema.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Pasos siguientes

Una vez que ha compilado y ejecutar esta aplicación simple, está listo para proyectos más complejos. Vea [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md) para obtener más tutoriales que explican las capacidades de Visual C++ en Visual Studio.

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Venir aquí para las soluciones a problemas comunes al crear su primer proyecto de C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Compilar y ejecutar el código con problemas de Visual Studio

Si aparece un subrayado ondulado rojo en nada en el editor de código fuente, la compilación puede tener errores o advertencias. Compruebe que el código coincide con el ejemplo de ortografía y mayúsculas y signos de puntuación.

[Volver.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Ejecutar el código en una ventana de comandos de problemas

También puede navegar hasta la carpeta de depuración de la solución en la línea de comandos para ejecutar la aplicación. No se puede ejecutar la aplicación de otros directorios sin especificar la ruta de acceso a la aplicación. Sin embargo, puede copiar la aplicación a otro directorio y ejecútelo desde allí.

[Volver.](#run-your-code-in-a-command-window)


<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
