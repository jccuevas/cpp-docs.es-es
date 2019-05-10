---
title: 'Tutorial: Creación de un programa estándar de C++ (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: ed9c19dad029f8fc9495d38ab6e5c0ba8ad6d529
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877419"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Tutorial: Creación de un programa estándar de C++ (C++)

Puede usar Visual Studio para crear estándar C++ programas. Siguiendo los pasos descritos en este tutorial, puede crear un proyecto, agregue un nuevo archivo al proyecto, modificar el archivo para agregar código de C++ y, a continuación, compilar y ejecutar el programa mediante el uso de Visual Studio.

Puede escribir su propio programa de C++ o utilizar uno de los programas de ejemplo. El programa de ejemplo en este tutorial es una aplicación de consola. Esta aplicación usa el `set` contenedor en la biblioteca estándar de C++.

> [!NOTE]
> Si el cumplimiento con una versión específica de la C++ estándar del lenguaje (es decir, C ++ 14 o C ++ 17) es necesario, utilice el `/std:C++14` o `/std:c++17` opción del compilador. (Visual Studio 2017 y versiones posterior.)

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe comprender los conceptos básicos del lenguaje C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Para crear un proyecto y agregar un archivo de origen

Los pasos siguientes varían dependiendo de qué versión de Visual Studio que esté usando. Asegúrese de que el selector de versión en la esquina superior izquierda de esta página se ha establecido correctamente.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Para crear un C++ proyecto en Visual Studio de 2019

1. En el menú principal, elija **archivo** > **New** > **proyecto** para abrir el **crear un nuevo proyecto** cuadro de diálogo cuadro.

1. En la parte superior del cuadro de diálogo, establezca **lenguaje** a **C++**, establezca **plataforma** a **Windows**y establezca **deltipodeproyecto** a **consola**. 

1. En la lista filtrada de tipos de proyecto, elija **aplicación de consola** , a continuación, elija **siguiente**. En la siguiente página, escriba un nombre para el proyecto y, si lo desea, especifique la ubicación del proyecto.

1. Elija la **crear** botón para crear el proyecto.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Para crear un C++ proyecto en Visual Studio 2017

1. Cree un proyecto que apunta a **New** en el **archivo** menú y, a continuación, haga clic en **proyecto**.

1. En el **Visual C++** panel tipos de proyecto, haga clic en **Windows Desktop**y, a continuación, haga clic en **aplicación de consola Windows**.

1. Escriba un nombre para el proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente. También puede escribir una ubicación diferente para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Para crear un C++ proyecto en Visual Studio 2015

1. Cree un proyecto que apunta a **New** en el **archivo** menú y, a continuación, haga clic en **proyecto**.

1. En el **Visual C++** panel tipos de proyecto, haga clic en **Windows Desktop**y, a continuación, haga clic en **aplicación de consola Windows**.

1. En el **nuevo proyecto** cuadro de diálogo, expanda **instalado** > **plantillas** > **Visual C++** , y a continuación, seleccione **Win32**. En el panel central, seleccione **Aplicación de consola Win32**.

1. Escriba un nombre para el proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente. También puede escribir una ubicación diferente para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto.

1. Completar la **Asistente para aplicaciones Win32**. 

1. Haga clic en **siguiente**, a continuación, asegúrese de que **aplicación de consola** está seleccionada y desactive el **encabezados precompilados** cuadro. 

1. Haga clic en **Finalizar**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Agregue un nuevo archivo de origen

1. Si **el Explorador de soluciones** no se muestra, en el **vista** menú, haga clic en **el Explorador de soluciones**.

1. Agregue un nuevo archivo de origen al proyecto, como sigue.

   1. En **el Explorador de soluciones**, haga clic en el **archivos de código fuente** carpeta, seleccione **agregar**y, a continuación, haga clic en **nuevo elemento**.

   1. En el **código** nodo, haga clic en **archivo C++ (.cpp)**, escriba un nombre para el archivo y, a continuación, haga clic en **agregar**.

   El archivo .cpp aparece en la **archivos de código fuente** carpeta **el Explorador de soluciones**, y el archivo se abre en el editor de Visual Studio.

1. En el archivo en el editor, escriba un programa de C++ válido que usa la biblioteca estándar de C++ o copie uno de los programas de ejemplo y péguelo en el archivo.

1. Guarde el archivo.

1. En el menú **Compilar** , haga clic en **Compilar solución**.

   El **salida** ventana muestra información sobre el progreso de la compilación, por ejemplo, la ubicación del registro de compilación y un mensaje que indica el estado de compilación.

1. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.

   Si usa el programa de ejemplo, una ventana de comandos se muestra y se muestra si hay determinados enteros en el conjunto.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [Aplicaciones de consola en Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Siguiente:** [Tutorial: Compilación de un programa nativo de C++ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
