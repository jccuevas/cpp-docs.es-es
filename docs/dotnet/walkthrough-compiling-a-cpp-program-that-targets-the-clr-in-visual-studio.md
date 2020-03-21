---
title: Compilar un programa/CLI destinado a C++CLR
description: Use Microsoft C++ para crear programas y bibliotecas que pueden conectar código C++ nativo y programas .net.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 36c41856dfcdb5c5f50ba59205b4c73c5fde5963
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080015"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Tutorial: compilar un programa/CLI destinado a C++CLR en Visual Studio

El uso C++de/CLI le permite C++ crear programas que usan clases de .net, así C++ como tipos nativos. C++/CLI está pensado para su uso en aplicaciones de consola y en archivos dll C++ que encapsulan código nativo y lo hacen accesible desde programas .net. Para crear una interfaz de usuario de Windows basada en .NET C# , use o Visual Basic.

Para este procedimiento, puede escribir su propio C++ programa o usar uno de los programas de ejemplo. En el programa de ejemplo que se usa en este procedimiento se crea un archivo de texto denominado textfile.txt y se guarda en el directorio del proyecto.

## <a name="prerequisites"></a>Prerequisites

- Descripción de los fundamentos del lenguaje C++.
- En Visual Studio 2017 y versiones posteriores C++, la compatibilidad con/CLI es un componente opcional. Para instalarlo, abra el **instalador de Visual Studio** desde el menú Inicio de Windows. Asegúrese de que esté activada la casilla **desarrollo de escritorio con C++**  icono y, en la sección componentes **opcionales** , consulte  **C++también compatibilidad con/CLI**.

## <a name="create-a-new-project"></a>Creación de un nuevo proyecto

Los siguientes pasos varían según la versión de Visual Studio que use. Asegúrese de que el selector de versión en la esquina superior izquierda de esta página está establecido correctamente.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Para crear un C++proyecto/CLI en Visual Studio 2019

1. En **Explorador de soluciones**, haga clic con el botón secundario en la parte superior para abrir el cuadro de diálogo **crear nuevo proyecto** .

1. En la parte superior del cuadro de diálogo, escriba **CLR** en el cuadro de búsqueda y, a continuación, elija **proyecto vacío de CLR** en la lista de resultados.

1. Elija el botón **Crear** para crear el proyecto.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Para crear un C++proyecto/CLI en Visual Studio 2017

1. Cree un nuevo proyecto. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

1. En los tipos de proyecto de Visual C++, haga clic en **CLR** y después en **Proyecto vacío de CLR**.

1. Escriba un nombre de proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto nuevo, pero puede escribir otro nombre. Si quiere, puede escribir otra ubicación para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto nuevo.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Para crear un C++proyecto/CLI en Visual Studio 2015

1. Cree un nuevo proyecto. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

1. En los tipos de proyecto de Visual C++, haga clic en **CLR** y después en **Proyecto vacío de CLR**.

1. Escriba un nombre de proyecto. De forma predeterminada, la solución que contiene el proyecto tiene el mismo nombre que el proyecto nuevo, pero puede escribir otro nombre. Si quiere, puede escribir otra ubicación para el proyecto.

1. Haga clic en **Aceptar** para crear el proyecto nuevo.

::: moniker-end

## <a name="add-a-source-file"></a>Agregar un archivo de código fuente

1. Si el **Explorador de soluciones** no está visible, haga clic en **Explorador de soluciones** en el menú **Ver**.

1. Agregue un archivo de código fuente nuevo al proyecto:

   - Haga clic con el botón derecho en la carpeta **Archivos de código fuente** en el **Explorador de soluciones**, seleccione **Agregar** y haga clic en **Nuevo elemento**.

   - Haga clic en **Archivo C++ (.cpp)** , escriba un nombre de archivo y, después, haga clic en **Agregar**.

   El archivo **.cpp** aparece en la carpeta **Archivos de código fuente** en el **Explorador de soluciones** y se muestra una ventana con pestañas donde puede escribir el código que quiera en ese archivo.

1. Haga clic en la pestaña recién creada en Visual Studio y escriba un programa de Visual C++ válido, o copie y pegue uno de los programas de ejemplo.

   Por ejemplo, puede usar el programa de ejemplo [Cómo: Escribir un archivo de texto (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) (en el nodo **Control y E/S de archivos** de la Guía de programación).

   Si usa el programa de ejemplo, observe que se usa la palabra clave `gcnew` en lugar de `new` al crear un objeto .NET y que `gcnew` devuelve un identificador (`^`) en lugar de un puntero (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Para obtener más información C++sobre la sintaxis de/CLI, vea [extensiones de componentes para plataformas en tiempo de ejecución](../extensions/component-extensions-for-runtime-platforms.md).

1. En el menú **Compilar**, haga clic en **Compilar solución**.

   En la ventana **Salida** se muestra información sobre el progreso de la compilación, como la ubicación del registro de compilación y un mensaje que indica el estado de la compilación.

   Si realiza cambios y ejecuta el programa sin realizar una compilación, es posible que se indique que el proyecto no está actualizado en un cuadro de diálogo. Active la casilla de este cuadro de diálogo antes de hacer clic en **Aceptar** si quiere que Visual Studio use siempre las versiones actuales de los archivos en lugar de solicitárselo cada vez que se compile la aplicación.

1. En el menú **Depurar**, haga clic en **Iniciar sin depurar**.

1. Si usó el programa de ejemplo, al ejecutar el programa se muestra una ventana de comandos en la que se indica que se ha creado el archivo de texto.

   El archivo de texto **textfile.txt** se encuentra ahora en el directorio del proyecto. Puede abrir este archivo mediante el Bloc de notas.

   > [!NOTE]
   > Al elegir la plantilla de proyecto vacío de CLR se establece automáticamente la opción del compilador `/clr`. Para comprobarlo, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones**, seleccione **Propiedades** y, después, active la opción **Compatible con Common Language Runtime** en el nodo  **General** de **Propiedades de configuración**.

## <a name="see-also"></a>Consulte también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](../build/projects-and-build-systems-cpp.md)<br/>
