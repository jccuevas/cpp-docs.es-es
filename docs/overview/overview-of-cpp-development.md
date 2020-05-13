---
title: Introducción al desarrollo de C++ en Visual Studio
description: El IDE de Visual Studio admite el desarrollo de C++ en Windows, Linux, Android e iOS con un editor de código, un depurador, marcos de pruebas, analizadores estáticos y otras herramientas de programación.
ms.date: 12/02/2019
helpviewer_keywords:
- Visual C++, development tools
author: corob-msft
ms.author: corob
ms.openlocfilehash: 4e04e189b44fe61759a9422139d856ab8a09f201
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "77415708"
---
# <a name="overview-of-c-development-in-visual-studio"></a>Introducción al desarrollo de C++ en Visual Studio

Como parte del Entorno de desarrollo integrado (IDE) de Visual Studio, Microsoft C++ (MSVC) comparte muchas ventanas y herramientas con otros lenguajes. Muchas de ellas, como el **Explorador de soluciones**, el Editor de código y el depurador, están documentadas en [Introducción al IDE de Visual Studio](/visualstudio/get-started/visual-studio-ide). A menudo, una herramienta o una ventana compartida tienen un conjunto de características ligeramente diferente para C++ que para otros lenguajes. Algunas ventanas o herramientas solo están disponibles en las ediciones Visual Studio Professional o Visual Studio Enterprise.

Además de las herramientas compartidas en el IDE de Visual Studio, MSVC dispone de varias herramientas específicas para el desarrollo de código nativo. Esas herramientas también se indican en este artículo. Para obtener una lista de las herramientas disponibles en cada edición de Visual Studio, vea [Herramientas de C++ y características en ediciones de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Crear proyectos

Un *proyecto* es básicamente un conjunto de archivos de código fuente y recursos como imágenes o archivos de datos que se integran en una biblioteca o un programa ejecutable.

Visual Studio proporciona compatibilidad con cualquier sistema de proyectos o herramientas de compilación personalizadas que se quieran usar, con compatibilidad total con IntelliSense, la exploración y la depuración:

- **MSBuild** es el sistema de proyectos nativo de Visual Studio. Al seleccionar **Archivo** > **Nuevo** > **Proyecto** desde el menú principal, se ven muchos tipos de *plantillas de proyecto* de MSBuild para comenzar a desarrollar rápidamente diferentes tipos de aplicaciones de C++.

   ::: moniker range="vs-2019"

   ![Nuevas plantillas de proyecto](../build/media/mathclient-project-name-2019.png "Cuadro de diálogo Nuevo proyecto de Visual Studio 2019")

   ::: moniker-end

   ::: moniker range="<=vs-2017"

   ![Plantillas de proyecto](media/vs2017-new-project.png "Cuadro de diálogo Nuevo proyecto de Visual Studio 2017")

   ::: moniker-end

   En general, debe usar estas plantillas con los nuevos proyectos, a menos que esté usando proyectos CMake existentes u otro sistema de proyectos. Para obtener más información, vea [Creación y administración de proyectos de Visual C++ basados en MSBuild](../build/creating-and-managing-visual-cpp-projects.md).

- **CMake** es un sistema de compilación multiplataforma que se integra en el IDE de Visual Studio cuando se instala la carga de trabajo Desarrollo para el escritorio con C++. Puede usar la plantilla de proyecto de CMake con los proyectos nuevos, o simplemente abrir una carpeta con un archivo CMakeLists.txt. Para más información, vea el artículo sobre [proyectos de CMake en Visual Studio](../build/cmake-projects-in-visual-studio.md).

- A través de la característica **Abrir carpeta**, se admite cualquier otro sistema de compilación de C++, incluida una colección flexible de archivos. Se crean archivos JSON sencillos para invocar el programa de compilación y configurar las sesiones de depuración. Para más información, vea el artículo sobre los [proyectos Abrir carpeta para C++](../build/open-folder-projects-cpp.md).

## <a name="add-to-source-control"></a>Agregar al control de código fuente

El control de código fuente permite coordinar el trabajo entre varios desarrolladores, aislar el trabajo en curso del código en producción y realizar copias de seguridad del código fuente. Visual Studio es compatible con Git y [Team Foundation Version Control \(TFVC\)](/azure/devops/repos/tfvc/) a través de su ventana **Team Explorer**.

::: moniker range="vs-2019"

![Team Explorer](media/vs2019-team-explorer.png "Team Explorer de Visual Studio 2017")

::: moniker-end

::: moniker range="<=vs-2017"

![Team Explorer](media/vs2017-team-explorer.png "Team Explorer de Visual Studio 2017")

::: moniker-end

Para obtener más información sobre la integración de Git con repositorios de Azure, vea [Share your code with Visual Studio 2017 and Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017) (Compartir el código con Visual Studio 2017 y Git de Azure Repos). Para obtener información sobre la integración de Git con GitHub, vea [Extensión de GitHub para Visual Studio](https://visualstudio.github.com/).

## <a name="obtain-libraries"></a>Obtener bibliotecas

Use el administrador de paquetes [vcpkg](../build/vcpkg.md) para obtener e instalar bibliotecas de terceros. Actualmente hay disponibles más de 900 bibliotecas de código abierto en el catálogo.

## <a name="create-user-interfaces-with-designers"></a>Crear interfaces de usuario con diseñadores

Si el programa tiene una interfaz de usuario, puede usar un diseñador para rellenarla rápidamente con controles como botones, cuadros de lista, etc. Cuando se arrastra un control desde la ventana de cuadro de herramientas y se coloca en la superficie de diseño, Visual Studio genera los recursos y el código necesarios para que todo funcione. Luego se escribe el código para personalizar la apariencia y el comportamiento.

![Diseñador y cuadro de herramientas](media/vs2017-toolbox-designer.png "Diseñador y cuadro de herramientas de Visual Studio 2017")

Para obtener más información sobre cómo diseñar una interfaz de usuario para una aplicación para Plataforma universal de Windows, consulte [Diseño e interfaz de usuario](https://developer.microsoft.com/windows/design).

Para obtener más información sobre cómo crear una interfaz de usuario para una aplicación de MFC, vea [Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md). Para obtener información sobre los programas de Windows de Win32, vea [Aplicaciones de escritorio de Windows (C++)](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Escribir código

Después de crear un proyecto, todos los archivos del proyecto se muestran en la ventana **Explorador de soluciones**. (Una *solución* es un contenedor lógico para uno o más proyectos relacionados). Al hacer clic en un archivo .h o .cpp en el **Explorador de soluciones**, el archivo se abre en el editor de código.

![Explorador de soluciones y editor de código](media/vs2017-solution-explorer-code-editor.png "Explorador de soluciones y editor de código de Visual Studio 2017")

El editor de código es un procesador de textos especializado para código fuente en C++. Este editor codifica mediante colores las palabras clave, los nombres de los métodos y las variables del lenguaje, así como otros elementos del código para que el código sea más fácil de leer y entender. También proporciona herramientas para refactorizar código, navegar entre los distintos archivos y saber cómo se estructura el código. Para obtener más información, vea [Escribir y refactorizar código](../ide/writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Agregar y editar recursos

Un programa de Windows o DLL por lo general incluye algunos *recursos* como cuadros de diálogo, iconos, imágenes, cadenas localizables, pantallas de presentación, cadenas de conexión de base de datos o cualquier dato arbitrario. Visual Studio incluye herramientas para agregar y editar recursos. Para más información, consulte [Trabajar con archivos de recursos](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Compilación (compilación y vinculación)

Seleccione **Compilar** > **Compilar solución** en la barra de menús, o bien presione la combinación de teclas **Ctrl+Mayús+B** para compilar y vincular un proyecto. Los errores de compilación y las advertencias se muestran en la lista de errores (**Ctrl+\\, E**). La ventana de **salida** (**Alt+2**) muestra información sobre el proceso de compilación.

![Ventana de salida y Lista de errores](media/vs2017-output-error-list.png "Ventana de salida y Lista de errores de Visual Studio 2017")

Para más información sobre cómo configurar compilaciones, vea [Trabajar con propiedades de proyecto](../build/working-with-project-properties.md) y [Proyectos y sistemas de compilación](../build/projects-and-build-systems-cpp.md).

También se puede usar el compilador (cl.exe) y muchas otras herramientas independientes relacionadas con la compilación, como NMAKE y LIB, directamente desde la línea de comandos. Para obtener más información, vea [Compilar el código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md) y [Referencia de compilación de C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Depuración

Puede iniciar la depuración si presiona **F5**. La ejecución se detiene en cualquier punto de interrupción que se haya establecido (presionando **F9**). También puede recorrer el código de línea en línea (**F10**), ver los valores de registros o variables e, incluso, en algunos casos, realizar cambios en el código y continuar la depuración sin volver a compilar. La siguiente ilustración muestra una sesión de depuración en la que se detiene la ejecución en un punto de interrupción. Los valores de los miembros de la estructura de datos son visibles en la **ventana Inspección**.

![Sesión de depuración](media/vs2017-debug-watch.png "Sesión de depuración de Visual Studio 2017")

Para obtener más información, vea [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Prueba

Visual Studio incluye el marco de pruebas unitarias de Microsoft para C++, así como compatibilidad con Boost.Test, Google Test y CTest. Ejecute las pruebas desde la ventana **Explorador de pruebas**:

![Explorador de pruebas](media/cpp-test-explorer-passed.png "Explorador de pruebas de Visual Studio 2017")

Para obtener más información, vea [Comprobar el código con pruebas unitarias](/visualstudio/test/unit-test-your-code) y [Escribir pruebas unitarias para C/C ++ en Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analizar

Visual Studio incluye herramientas de análisis de código estático que pueden detectar posibles problemas en el código fuente. Estas herramientas incluyen una implementación de los comprobadores de reglas de [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). Para obtener más información, vea [Análisis de código para obtener información general de C/C++](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Implementar aplicaciones completadas

Puede implementar aplicaciones de escritorio tradicionales y aplicaciones de UWP para los clientes a través de Microsoft Store. La implementación de CRT se controla automáticamente en segundo plano. Para obtener más información, vea [Publicar aplicaciones y juegos de Windows](/windows/uwp/publish/).

También puede implementar un escritorio nativo C++ en otro equipo. Para obtener más información, vea [Implementar aplicaciones de escritorio](../windows/deploying-native-desktop-applications-visual-cpp.md).

Para obtener más información sobre la implementación de un programa de C++/CLI, vea [Guía de implementación para desarrolladores](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="next-steps"></a>Pasos siguientes

Profundice aún más en Visual Studio con alguno de estos artículos introductorios:

> [!div class="nextstepaction"]
> [Aprender a usar el editor de código](/visualstudio/get-started/tutorial-editor)

> [!div class="nextstepaction"]
> [Información sobre proyectos y soluciones](/visualstudio/get-started/tutorial-projects-solutions)
