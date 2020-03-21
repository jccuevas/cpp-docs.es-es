---
title: 'Tutorial: crear un programa C++ estándar (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 381fa347a4ca2872ef0697d76a1e788c97e8a014
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075438"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Tutorial: crear un programa C++ estándar (C++)

Puede usar Visual Studio para crear programas estándar C++ . Al seguir los pasos de este tutorial, puede crear un proyecto, agregar un nuevo archivo al proyecto, modificar el archivo para agregar C++ código y, a continuación, compilar y ejecutar el programa mediante Visual Studio.

Puede escribir su propio C++ programa o usar uno de los programas de ejemplo. El programa de ejemplo de este tutorial es una aplicación de consola. Esta aplicación usa el contenedor de `set` en C++ la biblioteca estándar.

> [!NOTE]
> Si se requiere compatibilidad con una versión específica C++ del estándar del lenguaje (es decir, c++ 14 o c++ 17), use la opción del compilador `/std:c++14` o `/std:c++17`. (Visual Studio 2017 y versiones posteriores).

## <a name="prerequisites"></a>Prerequisites

Para completar este tutorial, debe comprender los conceptos básicos del lenguaje C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Para crear un proyecto y agregar un archivo de código fuente

Los siguientes pasos varían según la versión de Visual Studio que use. Asegúrese de que el selector de versión en la esquina superior izquierda de esta página está establecido correctamente.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Para crear un C++ proyecto en Visual Studio 2019

1. En el menú principal, elija **archivo** > **nuevo** > **proyecto** para abrir el cuadro de diálogo **crear un nuevo proyecto** .

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**.

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la página siguiente, escriba un nombre para el proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Para crear un C++ proyecto en Visual Studio 2017

1. Cree un proyecto seleccionando **nuevo** en el menú **archivo** y, a continuación, haga clic en **proyecto**.

1. En el panel tipos de proyecto **Visual C++**  , haga clic en **escritorio de Windows**y, a continuación, haga clic en aplicación de **consola Windows**.

1. Escriba un nombre para el proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente. También puede escribir una ubicación diferente para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Para crear un C++ proyecto en Visual Studio 2015

1. Cree un proyecto seleccionando **nuevo** en el menú **archivo** y, a continuación, haga clic en **proyecto**.

1. En el panel tipos de proyecto **Visual C++**  , haga clic en **escritorio de Windows**y, a continuación, haga clic en aplicación de **consola Windows**.

1. En el cuadro de diálogo **nuevo proyecto** , expanda **instalado** > **plantillas** > **Visual C++** y, a continuación, seleccione **Win32**. En el panel central, seleccione **Aplicación de consola Win32**.

1. Escriba un nombre para el proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente. También puede escribir una ubicación diferente para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto.

1. Complete el **Asistente para aplicaciones Win32**.

1. Haga clic en **siguiente**, asegúrese de que la opción **aplicación de consola** está seleccionada y desactive la casilla **encabezados precompilados** .

1. Haga clic en **Finalizar**

::: moniker-end

## <a name="add-a-new-source-file"></a>Agregar un nuevo archivo de código fuente

1. Si no se muestra **Explorador de soluciones** , en el menú **Ver** , haga clic en **Explorador de soluciones**.

1. Agregue un nuevo archivo de código fuente al proyecto, como se indica a continuación.

   1. En **Explorador de soluciones**, haga clic con el botón secundario en la carpeta **archivos de código fuente** , seleccione **Agregar**y, a continuación, haga clic en **nuevo elemento**.

   1. En el nodo **código** , haga clic en  **C++ archivo (. cpp)** , escriba un nombre para el archivo y, a continuación, haga clic en **Agregar**.

   El archivo. cpp aparece en la carpeta de **archivos de origen** en **Explorador de soluciones**y el archivo se abre en el editor de Visual Studio.

1. En el archivo del editor, escriba un programa válido C++ que use la C++ biblioteca estándar, o copie uno de los programas de ejemplo y péguelo en el archivo.

1. Guarde el archivo.

1. En el menú **Compilar**, haga clic en **Compilar solución**.

   La ventana de **salida** muestra información sobre el progreso de la compilación, por ejemplo, la ubicación del registro de compilación y un mensaje que indica el estado de la compilación.

1. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.

   Si usó el programa de ejemplo, se muestra una ventana de comandos que muestra si se encuentran determinados enteros en el conjunto.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [aplicaciones de consola en C++ visual](../windows/console-applications-in-visual-cpp.md)<br/>
**Siguiente:** [Tutorial: compilar C++ un programa nativo en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Consulte también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
