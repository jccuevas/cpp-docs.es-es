---
title: IDE y herramientas para desarrollo de Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2018
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
ms.openlocfilehash: d4e7742afd3fecc4dd115624da0c1650dc662004
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412527"
---
# <a name="ide-and-tools-for-visual-c-development"></a>IDE y herramientas para desarrollo de Visual C++

Como parte del Entorno de desarrollo integrado (IDE) de Visual Studio, Microsoft Visual C++ (MSVC) comparte muchas ventanas y herramientas con otros lenguajes. Muchas de ellas, como el **Explorador de soluciones**, el Editor de código y el depurador, están documentadas en [Introducción al IDE de Visual Studio](/visualstudio/ide/visual-studio-ide). A menudo, una herramienta o una ventana compartida tiene un conjunto de características ligeramente diferentes para C++ que para los lenguajes .NET o Javascript. Algunas ventanas o herramientas solo están disponibles en Visual Studio Pro o Visual Studio Enterprise.

Además de las herramientas compartidas en el IDE de Visual Studio, MSVC dispone de varias herramientas específicas para el desarrollo de código nativo. Esas herramientas también se indican en este artículo. Para obtener una lista de las herramientas disponibles en cada edición de Visual Studio, vea [Herramientas de Visual C++ y características en ediciones de Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).

## <a name="creating-a-solution-and-projects"></a>Crear una solución y uno o varios proyectos

Un *proyecto* es básicamente un conjunto de archivos de código fuente y recursos como imágenes o archivos de datos que se integran en un archivo ejecutable.

Visual Studio 2015 proporciona compatibilidad con proyectos de MSBuild. Puede descargar extensiones de Visual Studio para otros sistemas de compilación, como Qt o CMake.

Visual Studio 2017 proporciona compatibilidad con cualquier sistema de compilación o herramientas de compilación personalizadas que se quieran usar, con compatibilidad total con IntelliSense, la exploración y la depuración:

- MSBuild es el sistema de compilación nativo para Visual Studio y suele ser la mejor opción para las aplicaciones de la Plataforma universal de Windows (UWP) o las aplicaciones de escritorio de Windows heredadas en las que se usa MFC o ATL. Para obtener más información sobre los proyectos de C++ basados en MSBuild, vea [Crear y administrar proyectos basados en MSBuild](creating-and-managing-visual-cpp-projects.md).
- CMake es un sistema de compilación multiplataforma que se integra en el IDE de Visual Studio cuando se instala la carga de trabajo Desarrollo para el escritorio con C++. Para más información, consulte el artículo sobre [proyectos CMake en Visual C++](cmake-tools-for-visual-cpp.md).
- A través de la característica Abrir carpeta, se admite cualquier otro sistema de compilación de C++, incluida una colección flexible de archivos. Se crean archivos JSON sencillos para invocar el programa de compilación y configurar las sesiones de depuración. Para obtener más información, vea [Bring your C++ codebase to Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/) (Llevar el código base de C++ a Visual Studio).

### <a name="project-templates-msbuild"></a>Plantillas de proyecto (MSBuild)

Visual Studio incluye varias plantillas para proyectos basados en MSBuild, que contienen código de inicio y la configuración necesaria para diversos tipos de programas básicos. Normalmente, se empieza seleccionando **Archivo** > **Nuevo proyecto** para crear un proyecto a partir de una plantilla de proyecto y luego se agregan archivos de código fuente nuevos a ese proyecto, o bien se comienza a escribir código en los archivos proporcionados. Para obtener información específica de los proyectos de C++ y los asistentes para proyectos, vea [Crear y administrar proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

### <a name="application-wizards-msbuild"></a>Asistentes para aplicaciones (MSBuild)

Visual Studio proporciona asistentes para algunos tipos de proyecto de MSBuild cuando se selecciona **Archivo** > **Nuevo proyecto**. Un asistente le guía paso a paso durante el proceso de creación de un nuevo proyecto. Esto es útil para los tipos de proyectos que tienen muchas opciones y configuración. Para obtener más información, vea [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md).

## <a name="creating-user-interfaces-with-designers-msbuild"></a>Creación de interfaces de usuario con diseñadores (MSBuild)

Si el programa tiene interfaz de usuario, una de las primeras tareas que se deben realizar consiste en rellenar la interfaz de controles, como botones, cuadros de lista, etc. Visual Studio incluye una superficie de diseño visual y un cuadro de herramientas para cada tipo de aplicación de C++. Independientemente del tipo de aplicación que quiera crear, la idea básica es siempre la misma: arrastrar un control desde la ventana del cuadro de herramientas y colocarlo en el lugar que se desee de la superficie de diseño. Visual Studio genera en segundo plano los recursos y el código necesario para que todo funcione. Después, se escribe el código para rellenar los controles con datos o personalizar su apariencia y comportamiento.

Para obtener más información sobre cómo diseñar una interfaz de usuario para una aplicación para Plataforma universal de Windows, vea [Diseña y codifica aplicaciones para UWP](https://developer.microsoft.com/en-us/windows/design).

Para obtener más información sobre cómo crear una interfaz de usuario para una aplicación de MFC, vea [Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md). Para obtener información sobre los programas de Windows de Win32, vea [Aplicaciones de escritorio de Windows (C++)](../windows/windows-desktop-applications-cpp.md).

## <a name="writing-and-editing-code"></a>Escribir y editar código

### <a name="semantic-colorization"></a>Coloración semántica

Después de crear un proyecto, todos los archivos del proyecto se muestran en la ventana **Explorador de soluciones**. Al hacer clic en un archivo .h o .cpp en el **Explorador de soluciones**, el archivo se abre en el editor de código. El editor de código es un procesador de textos especializado para código fuente en C++. Este editor codifica mediante colores las palabras clave, los nombres de los métodos y las variables del lenguaje, así como otros elementos del código para que el código sea más fácil de leer y entender.

### <a name="intellisense"></a>IntelliSense

El editor de código también admite varias características que, juntas, se conocen como IntelliSense. Puede mantener el mouse sobre un método y ver su documentación básica. Después de escribir el nombre de una variable de clase y un . o ->, aparecerá una lista de miembros de instancia de esa clase. Si escribe el nombre de una clase y, luego, un ::, se mostrará una lista de miembros estáticos. Cuando empieza a escribir un nombre de clase o método, el editor de código le ofrece sugerencias para completar la instrucción. Para obtener más información, vea [Usar IntelliSense](/visualstudio/ide/using-intellisense).

### <a name="code-snippets"></a>Fragmentos de código

Puede usar fragmentos de código de IntelliSense para generar construcciones de código de uso frecuente o complicadas con solo presionar un método abreviado de teclado. Para obtener más información, vea [Fragmentos de código](/visualstudio/ide/code-snippets).

## <a name="navigating-code"></a>Navegar por el código

El menú **Ver** proporciona acceso a muchas ventanas y herramientas que permiten navegar por los archivos de código. Para obtener información detallada sobre estas ventanas, vea [Visualización de la estructura del código](/visualstudio/ide/viewing-the-structure-of-code).

### <a name="solution-explorer"></a>Explorador de soluciones

En todas las ediciones de Visual Studio, use el panel **Explorador de soluciones** para navegar por los archivos de un proyecto. Expanda un icono de archivo .h o .cpp para ver las clases que hay en el archivo. Expanda una clase para ver sus miembros. Haga doble clic en un miembro para ir hasta su definición o implementación en el archivo.

### <a name="class-view-and-code-definition-window"></a>Vista de clases y ventana Definición de código

Use el panel **Vista de clases** para ver los espacios de nombres y las clases de todos los archivos, incluidas las clases parciales. Puede expandir cada espacio de nombres o clase para ver sus miembros y hacer doble clic en el miembro para ir hasta ese lugar del archivo de origen. Si abre la ventana **Definición de código**, puede ver la definición o implementación del tipo al elegirlo en la **Vista de clases**.

### <a name="object-browser"></a>Examinador de objetos

Use el **Examinador de objetos** para examinar la información de tipos en los componentes de Windows Runtime (archivos .winmd), los ensamblados .NET y las bibliotecas de tipos COM. No se utiliza con archivos DLL de Win32.

### <a name="go-to-definitiondeclaration"></a>Ir a definición/declaración

Presione F12 en cualquier variable de miembro o nombre de API para ir a su definición. Si la definición se encuentra en un archivo .winmd (para una aplicación para UWP o Windows 8.x Store), se muestra la información de tipos en el Examinador de objetos. También puede seleccionar **Ir a definición** o **Ir a declaración** si hace clic con el botón derecho en el nombre de variable o de tipo, y elige la opción correspondiente en el menú contextual.

### <a name="find-all-references"></a>Buscar todas las referencias

En un archivo de código fuente, haga clic con el botón derecho con el cursor del mouse sobre el nombre de un tipo, método o variable, y seleccione **Buscar todas las referencias** para obtener una lista de todas las ubicaciones del archivo, proyecto o solución donde se usa el tipo. **Buscar todas las referencias** es inteligente y solo devuelve las instancias de la misma variable idéntica, aunque otras variables de otro ámbito tengan el mismo nombre.

## <a name="add-and-edit-resources--msbuild"></a>Agregar y editar recursos (MSBuild)

El término *recurso* en el contexto de un proyecto de escritorio de Visual Studio incluye elementos como cuadros de diálogo, iconos, cadenas localizables, pantallas de presentación, cadenas de conexión de base de datos o cualquier dato arbitrario que quiera incluir en el archivo ejecutable.

Para obtener más información sobre cómo agregar y editar recursos en proyectos nativos de C++ de escritorio, vea [Trabajar con archivos de recursos](../windows/working-with-resource-files.md).

## <a name="build-compile-and-link"></a>Compilación (compilación y vinculación)

Seleccione **Compilar** > **Compilar solución** en la barra de menús, o bien presione la combinación de teclas Ctrl+Mayús+B para compilar y vincular un proyecto. Para crear código ejecutable, Visual Studio usa [MSBuild](/visualstudio/msbuild/msbuild1) o CMake, o el entorno de compilación que se establezca mediante **Abrir carpeta**. Para los proyectos de MSBuild, las opciones de compilación generales se establecen en **Herramientas** > **Opciones** > **Proyectos y soluciones**, y en **Proyecto** > **Propiedades** se pueden establecer propiedades para proyectos específicos. Los errores de compilación y las advertencias se muestran en la Lista de errores (Ctrl+\\, E). Los proyectos que no son de MSBuild se configuran con archivos JSON que se crean en el Explorador de soluciones. Con independencia del sistema de compilación que se use, en la ventana **Salida** (Alt+2) se muestra información sobre el proceso de compilación. Para obtener más información sobre las configuraciones de MSBuild, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md) y [Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).

También se puede usar el compilador (cl.exe) y muchas otras herramientas independientes relacionadas con la compilación, como NMAKE y LIB, directamente desde la línea de comandos. Para obtener más información, vea [Compilar el código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md) y [Referencia de compilación de C/C++](../build/reference/c-cpp-building-reference.md).

## <a name="test"></a>Prueba

Visual Studio incluye un marco de pruebas unitarias para código C++/CLI y C++ nativo. Para obtener más información, vea [Pruebas unitarias en Visual Studio](/visualstudio/test/unit-test-your-code) y [Escribir pruebas unitarias para C/C++ en Visual Studio](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp).

## <a name="analyze"></a>Analizar

Visual Studio incluye herramientas de análisis de código estático de C++, incluida una implementación de los comprobadores de reglas de [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md). Para obtener más información, vea [Análisis de código para obtener información general de C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

## <a name="debug"></a>Depuración

Puede depurar el programa si presiona **F5** cuando la configuración del proyecto esté establecida en Debug. Durante la depuración se pueden establecer puntos de interrupción presionando **F9**, recorrer el código presionando **F10**, ver los valores de registros o variables especificados e, incluso, en algunos casos, realizar cambios en el código y continuar la depuración sin tener que volver a compilar. Para obtener más información, vea [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).

## <a name="deploy-completed-applications"></a>Implementar aplicaciones completadas

Una aplicación para UWP se implementa para los clientes a través de Microsoft Store mediante la opción de menú **Proyecto** > **Store**. La implementación de CRT se controla automáticamente en segundo plano. Para obtener más información, vea [Publicar aplicaciones y juegos de Windows](/windows/uwp/publish/).

Al implementar una aplicación de escritorio de C++ nativo en otro equipo, debe instalar tanto la aplicación como todos los archivos de biblioteca de los que dependa la aplicación. Hay tres maneras de implementar el runtime de C++ Universal (UCRT) con una aplicación: implementación central, implementación local o vinculación estática. Para obtener más información, vea [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md).

Para obtener más información sobre la implementación de un programa de C++/CLI, vea [Guía de implementación para desarrolladores](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="related-articles"></a>Artículos relacionados

|||
|-|-|
|[Herramientas y características de Visual C++ en las ediciones de Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|Muestra qué características están disponibles en las diferentes ediciones de Visual Studio.|
|[Creación y administración de proyectos de Visual C++ basados en MSBuild](../ide/creating-and-managing-visual-cpp-projects.md)|Proporciona información general sobre los proyectos de C++ basados en MSBuild en Visual Studio y vínculos a otros artículos en los que se explica cómo crearlos y administrarlos.|
|[Proyectos CMake en Visual C++](cmake-tools-for-visual-cpp.md)|Se describe cómo crear proyectos de CMake u otros proyectos que no sean de MSBuild en Visual C++.|
|[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)|Describe cómo compilar proyectos de C++.|
|[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)|Proporciona información general sobre la implementación de aplicaciones de C++ y vínculos a otros artículos que describen de forma detallada la implementación.|
|[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Información detallada sobre cómo actualizar aplicaciones de C++ que se crearon en versiones anteriores de Visual Studio, y también cómo migrar las aplicaciones que se crearon con herramientas distintas a Visual Studio.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Describe las principales características de Visual C++ en Visual Studio y vínculos al resto de la documentación sobre Visual C++.|
