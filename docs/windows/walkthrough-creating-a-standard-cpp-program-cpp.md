---
title: 'Tutorial: Crear un programa de C++ estándar (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 105ac62131b45afdea2a445b5888a344f1e4d46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370221"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Tutorial: Crear un programa de C++ estándar (C++)

Puede usar Visual Studio para crear programas C++ estándar. Siguiendo los pasos de este tutorial, puede crear un proyecto, agregar un nuevo archivo al proyecto, modificar el archivo para agregar código C++ y, a continuación, compilar y ejecutar el programa mediante Visual Studio.

Puede escribir su propio programa C++ o utilizar uno de los programas de ejemplo. El programa de ejemplo de este tutorial es una aplicación de consola. Esta aplicación `set` utiliza el contenedor de la biblioteca estándar C++.

> [!NOTE]
> Si se requiere el cumplimiento de una versión específica del estándar de lenguaje C++ (es decir, C++14 o C++17), utilice la `/std:c++14` opción o `/std:c++17` compilador. (Visual Studio 2017 y versiones posteriores.)

## <a name="prerequisites"></a>Prerrequisitos

Para completar este tutorial, debe comprender los conceptos básicos del lenguaje C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Para crear un proyecto y agregar un archivo de origen

Los siguientes pasos varían según la versión de Visual Studio que use. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Para crear un proyecto De+ en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++ **, establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**.

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la página siguiente, escriba un nombre para el proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Para crear un proyecto de C++ en Visual Studio 2017

1. Cree un proyecto apuntando a **Nuevo** en el menú **Archivo** y, a continuación, haga clic en **Proyecto**.

1. En el panel Tipos de proyecto de **Visual C++,** haga clic en Escritorio de **Windows**y, a continuación, haga clic en Aplicación de consola de **Windows**.

1. Escriba un nombre para el proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente. También puede escribir una ubicación diferente para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Para crear un proyecto de C++ en Visual Studio 2015

1. Cree un proyecto apuntando a **Nuevo** en el menú **Archivo** y, a continuación, haga clic en **Proyecto**.

1. En el panel Tipos de proyecto de **Visual C++,** haga clic en Escritorio de **Windows**y, a continuación, haga clic en Aplicación de consola de **Windows**.

1. En el cuadro de diálogo **Nuevo proyecto** , expanda**Plantillas** >  **instaladas** > **Visual C++** y, a continuación, seleccione **Win32**. En el panel central, seleccione **Aplicación de consola Win32**.

1. Escriba un nombre para el proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto, pero puede escribir un nombre diferente. También puede escribir una ubicación diferente para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto.

1. Complete el **Asistente para aplicaciones Win32**.

1. Haga clic en **Siguiente**y, a continuación, asegúrese de que **Aplicación** de consola está seleccionada y desactive la casilla **Encabezados precompilados.**

1. Haga clic en **Finalizar**

::: moniker-end

## <a name="add-a-new-source-file"></a>Agregar un nuevo archivo de origen

1. Si no se muestra **el Explorador** de soluciones, en el menú **Ver,** haga clic en **Explorador de soluciones**.

1. Agregue un nuevo archivo de origen al proyecto, como se indica a continuación.

   1. En **el Explorador**de soluciones , haga clic con el botón secundario en la carpeta Archivos de **origen,** seleccione **Agregar**y, a continuación, haga clic en **Nuevo elemento**.

   1. En el nodo **Código** , haga clic en **Archivo C++ (.cpp),** escriba un nombre para el archivo y, a continuación, haga clic en **Agregar**.

   El archivo .cpp aparece en la carpeta Archivos de **origen** del **Explorador**de soluciones y el archivo se abre en el editor de Visual Studio.

1. En el archivo del editor, escriba un programa C++ válido que utilice la biblioteca estándar C++, o copie uno de los programas de ejemplo y péguelo en el archivo.

1. Guarde el archivo.

1. En el menú **Compilar**, haga clic en **Compilar solución**.

   La ventana **Salida** muestra información sobre el progreso de la compilación, por ejemplo, la ubicación del registro de compilación y un mensaje que indica el estado de compilación.

1. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.

   Si ha utilizado el programa de ejemplo, se muestra una ventana de comandos que muestra si se encuentran determinados enteros en el conjunto.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** Aplicaciones de [consola en Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Siguiente:** [Tutorial: Compilación de un programa C++ nativo en la línea](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) de comandos

## <a name="see-also"></a>Consulte también

[Referencia del idioma C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
