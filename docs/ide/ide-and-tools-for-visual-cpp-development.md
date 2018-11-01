---
title: IDE y herramientas para desarrollo de Visual C++ | Microsoft Docs
description: El IDE de Visual Studio admite el desarrollo de C++ en Windows, Linux, Android e iOS con un editor de código, un depurador, marcos de pruebas, analizadores estáticos y otras herramientas de programación.
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99fdb8f9c08845c5f440fc4ae1f100f8afd832e2
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136164"
---
# <a name="ide-and-compiler-tools-for-visual-c-development"></a>IDE y herramientas de compilación para el desarrollo de Visual C++

Como parte del Entorno de desarrollo integrado (IDE) de Visual Studio, Microsoft Visual C++ (MSVC) comparte muchas ventanas y herramientas con otros lenguajes. Muchas de ellas, como el **Explorador de soluciones**, el Editor de código y el depurador, están documentadas en [Introducción al IDE de Visual Studio](/visualstudio/ide/visual-studio-ide). A menudo, una herramienta o una ventana compartida tiene un conjunto de características ligeramente diferente para C++ que para los lenguajes .NET o JavaScript. Algunas ventanas o herramientas solo están disponibles en las ediciones Visual Studio Professional o Visual Studio Enterprise.

Además de las herramientas compartidas en el IDE de Visual Studio, MSVC dispone de varias herramientas específicas para el desarrollo de código nativo. Esas herramientas también se indican en este artículo. Para obtener una lista de las herramientas disponibles en cada edición de Visual Studio, vea [Herramientas de Visual C++ y características en ediciones de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="create-projects"></a>Crear proyectos

Un *proyecto* es básicamente un conjunto de archivos de código fuente y recursos como imágenes o archivos de datos que se integran en un archivo ejecutable.

Visual Studio 2015 proporciona compatibilidad con proyectos de MSBuild. Puede descargar extensiones de Visual Studio para otros sistemas de compilación, como Qt o CMake.

Visual Studio 2017 proporciona compatibilidad con cualquier sistema de compilación o herramientas de compilación personalizadas que se quieran usar, con compatibilidad total con IntelliSense, la exploración y la depuración:

- **MSBuild** es el sistema de compilación nativo de Visual Studio. Al seleccionar **Archivo** > **Nuevo** > **Proyecto** desde el menú principal, se ven muchos tipos de *plantillas de proyecto* de MSBuild para comenzar a desarrollar rápidamente diferentes tipos de aplicaciones de C++.

   ![Plantillas de proyecto](media/vs2017-new-project.png "Cuadro de diálogo Nuevo proyecto de Visual Studio 2017")

   En general, debe usar estas plantillas para los nuevos proyectos, a menos que tenga una razón concreta para usar CMake u otro sistema de proyecto. Algunos proyectos tienen un *asistente* que guía paso a paso durante el proceso de creación de un nuevo proyecto. Para obtener más información, vea [Creación y administración de proyectos de Visual C++ basados en MSBuild](creating-and-managing-visual-cpp-projects.md).

- **CMake** es un sistema de compilación multiplataforma que se integra en el IDE de Visual Studio cuando se instala la carga de trabajo Desarrollo para el escritorio con C++. Para más información, consulte el artículo sobre [proyectos CMake en Visual C++](cmake-tools-for-visual-cpp.md).
- A través de la característica **Abrir carpeta**, se admite cualquier otro sistema de compilación de C++, incluida una colección flexible de archivos. Se crean archivos JSON sencillos para invocar el programa de compilación y configurar las sesiones de depuración. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](non-msbuild-projects.md).

## <a name="add-to-source-control"></a>Agregar al control de código fuente

El control de código fuente permite coordinar el trabajo entre varios desarrolladores, aislar el trabajo en curso del código en producción y realizar copias de seguridad del código fuente. Visual Studio es compatible con Git y [Team Foundation Version Control \(TFVC\)](/azure/devops/repos/tfvc/) a través de su ventana **Team Explorer**.

![Team Explorer](media/vs2017-team-explorer.png "Visual Studio 2017 Team Explorer")

Para obtener más información sobre la integración de Git con repositorios de Azure, vea [Share your code with Visual Studio 2017 and Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017) (Compartir el código con Visual Studio 2017 y Git de Azure Repos). Para obtener información sobre la integración de Git con GitHub, vea [Extensión de GitHub para Visual Studio](https://visualstudio.github.com/).

## <a name="create-user-interfaces-with-designers"></a>Crear interfaces de usuario con diseñadores

Si el programa tiene una interfaz de usuario, puede usar un diseñador para rellenarla rápidamente con controles como botones, cuadros de lista, etc. Cuando se arrastra un control desde la ventana de cuadro de herramientas y se coloca en la superficie de diseño, Visual Studio genera los recursos y el código necesarios para que todo funcione. Luego se escribe el código para personalizar la apariencia y el comportamiento.

![Diseñador y cuadro de herramientas](media/vs2017-toolbox-designer.png "Diseñador y cuadro de herramientas de Visual Studio 2017")

Para obtener más información sobre cómo diseñar una interfaz de usuario para una aplicación para Plataforma universal de Windows, vea [Diseña y codifica aplicaciones para UWP](https://developer.microsoft.com/windows/design).

Para obtener más información sobre cómo crear una interfaz de usuario para una aplicación de MFC, vea [Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md). Para obtener información sobre los programas de Windows de Win32, vea [Aplicaciones de escritorio de Windows (C++)](../windows/windows-desktop-applications-cpp.md).

## <a name="write-code"></a>Escribir código

Después de crear un proyecto, todos los archivos del proyecto se muestran en la ventana **Explorador de soluciones**. (Una *solución* es un contenedor lógico para uno o más proyectos relacionados). Al hacer clic en un archivo .h o .cpp en el **Explorador de soluciones**, el archivo se abre en el editor de código.

![Explorador de soluciones y editor de código](media/vs2017-solution-explorer-code-editor.png "Explorador de soluciones y editor de código de Visual Studio 2017")

El editor de código es un procesador de textos especializado para código fuente en C++. Este editor codifica mediante colores las palabras clave, los nombres de los métodos y las variables del lenguaje, así como otros elementos del código para que el código sea más fácil de leer y entender.

Para obtener más información, vea [Escribir y refactorizar código](writing-and-refactoring-code-cpp.md).

## <a name="add-and-edit-resources"></a>Agregar y editar recursos

El término *recurso* incluye elementos como cuadros de diálogo, iconos, imágenes, cadenas localizables, pantallas de presentación, cadenas de conexión de base de datos o cualquier dato arbitrario que quiera incluir en el archivo ejecutable.

Para obtener más información sobre cómo agregar y editar recursos en proyectos nativos de C++ de escritorio, vea [Trabajar con archivos de recursos](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Compilación (compilación y vinculación)

Seleccione **Compilar** > **Compilar solución** en la barra de menús, o bien presione la combinación de teclas Ctrl+Mayús+B para compilar y vincular un proyecto. Los errores de compilación y las advertencias se muestran en la Lista de errores (Ctrl+\\, E). La **ventana de salida** (Alt+2) muestra información sobre el proceso de compilación.

![Ventana de salida y lista de errores](media/vs2017-output-error-list.png "Ventana de salida y lista de errores de Visual Studio 2017")Para obtener más información sobre las configuraciones de MSBuild, vea [Trabajar con configuraciones de proyecto](working-with-project-properties.md) y [Compilar proyectos de C++ en Visual Studio](building-cpp-projects-in-visual-studio.md).

También se puede usar el compilador (cl.exe) y muchas otras herramientas independientes relacionadas con la compilación, como NMAKE y LIB, directamente desde la línea de comandos. Para obtener más información, vea [Compilar el código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md) y [Referencia de compilación de C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="debug"></a>Depuración

Puede iniciar la depuración si presiona **F5**. La ejecución se detiene en cualquier punto de interrupción que se haya establecido. También puede recorrer el código de línea en línea, ver los valores de registros o variables e, incluso, en algunos casos, realizar cambios en el código y continuar la depuración sin volver a compilar. La siguiente ilustración muestra una sesión de depuración en la que se detiene la ejecución en un punto de interrupción. Los valores de los miembros de la estructura de datos son visibles en la **ventana Inspección**.

![Sesión de depuración](media/vs2017-debug-watch.png "Sesión de depuración de Visual Studio 2017")

Para obtener más información, vea [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="test"></a>Prueba

Visual Studio incluye marcos de pruebas unitarias para código C++/CLI y C++ nativo. También se admiten Boost.Test, Google Test y CTest. Ejecute las pruebas desde la ventana **Explorador de pruebas**:

![Explorador de pruebas](media/cpp-test-explorer-passed.png "Explorador de pruebas de Visual Studio 2017")

Para obtener más información, vea [Comprobar el código con pruebas unitarias](/visualstudio/test/unit-test-your-code) y [Escribir pruebas unitarias para C/C ++ en Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp).

## <a name="analyze"></a>Analizar

Visual Studio incluye herramientas de análisis de código estático que pueden detectar posibles problemas en el código fuente. Estas herramientas incluyen una implementación de los comprobadores de reglas de [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). Para obtener más información, vea [Análisis de código para obtener información general de C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="deploy-completed-applications"></a>Implementar aplicaciones completadas

Puede implementar aplicaciones de escritorio tradicionales y aplicaciones de UWP para los clientes a través de Microsoft Store. La implementación de CRT se controla automáticamente en segundo plano. Para obtener más información, vea [Publicar aplicaciones y juegos de Windows](/windows/uwp/publish/).

También puede implementar un escritorio de C++ nativo en otro equipo. Para obtener más información, vea [Implementar aplicaciones de escritorio](deploying-native-desktop-applications-visual-cpp.md).

Para obtener más información sobre la implementación de un programa de C++/CLI, vea [Guía de implementación para desarrolladores](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="related-articles"></a>Artículos relacionados

|||
|-|-|
|[Herramientas y características de Visual C++ en las ediciones de Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)|Muestra qué características están disponibles en las diferentes ediciones de Visual Studio.|
|[Creación y administración de proyectos de Visual C++ basados en MSBuild](creating-and-managing-visual-cpp-projects.md)|Proporciona información general sobre los proyectos de C++ basados en MSBuild en Visual Studio y vínculos a otros artículos en los que se explica cómo crearlos y administrarlos.|
|[Proyectos CMake en Visual C++](cmake-tools-for-visual-cpp.md)|Se describe cómo crear proyectos de CMake u otros proyectos que no sean de MSBuild en Visual C++.|
|[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)|Describe cómo compilar proyectos de C++.|
|[Implementar aplicaciones de escritorio](deploying-native-desktop-applications-visual-cpp.md)|Proporciona información general sobre la implementación de aplicaciones de C++ y vínculos a otros artículos que describen de forma detallada la implementación.|
|[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Información detallada sobre cómo actualizar aplicaciones de C++ que se crearon en versiones anteriores de Visual Studio, y también cómo migrar las aplicaciones que se crearon con herramientas distintas a Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Describe las principales características de Visual C++ en Visual Studio y vínculos al resto de la documentación sobre Visual C++.|
