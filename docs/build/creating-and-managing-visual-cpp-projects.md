---
title: 'Proyectos de Visual Studio: C++'
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 3694478e22bfd2a3c58a72ba0c3ad2d15351bc9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078693"
---
# <a name="visual-studio-projects---c"></a>Proyectos de Visual Studio: C++

Un *proyecto de Visual Studio* es un proyecto basado en el sistema de compilación MSBuild. MSBuild es el sistema de compilación nativo para Visual Studio y, generalmente, es el mejor para los programas específicos de Windows. MSBuild está totalmente integrado con Visual Studio, pero también se puede usar desde la línea de comandos. En el caso de los proyectos multiplataforma o los proyectos que usan bibliotecas de código abierto, se recomienda usar [proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md) en Visual Studio 2017 y versiones posteriores. Para obtener información sobre cómo actualizar proyectos de MSBuild desde versiones anteriores de Visual Studio, vea la [Guía de migración y actualización de Microsoft C++](../porting/visual-cpp-porting-and-upgrading-guide.md).

## <a name="create-a-project"></a>Crear un proyecto

::: moniker range="vs-2019"

Puede crear proyectos de C++ si selecciona **Archivo** > **Nuevo** > **Proyecto** y, después, establece el **Lenguaje** en C++. En la lista de resultados, verá una lista de plantillas de proyecto que puede filtrar si establece **Plataforma** o **Tipo de proyecto**, y escribe palabras clave en el cuadro de búsqueda.

   ![Plantillas de proyecto de Visual Studio 2019](../build/media/vs2019-choose-console-app.png "Cuadro de diálogo Nuevo proyecto de Visual Studio 2019")

::: moniker-end

::: moniker range="vs-2017"

Puede crear proyectos de C++ si selecciona **Archivo** > **Nuevo** > **Proyecto** y después Visual C++ en el panel de la izquierda. En el panel central, verá una lista de plantillas de proyecto:

   ![Plantillas de proyecto](../overview/media/vs2017-new-project.png "Cuadro de diálogo Nuevo proyecto de Visual Studio 2017")

::: moniker-end

Para más información sobre las plantillas de proyecto predeterminadas que se incluyen con Visual Studio, vea [Plantillas de proyecto de C++ en Visual Studio](reference/visual-cpp-project-types.md). Puede crear plantillas de proyecto propias. Para obtener más información, vea [Cómo: crear plantillas de proyecto](/visualstudio/ide/how-to-create-project-templates).

Después de crear un proyecto, aparece en la ventana [Explorador de soluciones](/visualstudio/ide/solutions-and-projects-in-visual-studio):

   ![Explorador de soluciones](media/mathlibrary-solution-explorer-153.png)

Cuando crea un proyecto, también se crea un archivo de solución (.sln). Puede agregar proyectos adicionales a la solución si hace clic con el botón derecho en ella en el **Explorador de soluciones**. El archivo de solución se usa para coordinar las dependencias de compilación cuando tiene varios proyectos relacionados, pero no hace mucho más. Todas las opciones del compilador se establecen en el nivel de proyecto.

## <a name="add-items"></a>Adición de elementos

Para agregar archivos de código fuente, iconos o cualquier otro elemento al proyecto, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione **Agregar > Nuevo** o **Agregar > Elemento existente**.

## <a name="add-third-party-libraries"></a>Adición de bibliotecas de terceros

Para agregar bibliotecas de terceros, use el administrador de paquetes [vcpkg](vcpkg.md). Ejecute el paso de integración de Visual Studio para configurar las rutas de acceso a esa biblioteca cuando haga referencia a la misma desde cualquier proyecto de Visual Studio.

## <a name="set-compiler-options-and-other-build-properties"></a>Configuración de opciones del compilador y otras propiedades de compilación

Para configurar opciones de compilación para un proyecto, haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y elija **Propiedades**. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Compilación y ejecución

Para compilar y ejecutar el proyecto nuevo, presione **F5** o haga clic en el *menú desplegable de depuración* con la flecha de color verde en la barra de herramientas principal. En la *lista desplegable de configuración* puede elegir si quiere realizar una compilación de *Depuración* o *Versión* (u otra configuración personalizada).

Un proyecto nuevo se compila sin errores. Al agregar código propio, en ocasiones se puede introducir un error o desencadenar una advertencia. Un error impide que la compilación se complete; una advertencia no. Todos los errores y advertencias aparecerán en la ventana Salida y en la lista de errores al compilar el proyecto.

   ![Ventana Salida y Lista de errores](../overview/media/vs2017-output-error-list.png)

En la Lista de errores, puede presionar **F1** en un error resaltado para ir a su tema en la documentación.

## <a name="in-this-section"></a>En esta sección

[Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](working-with-project-properties.md)<br/>
Procedimientos para usar páginas de propiedades y hojas de propiedades para especificar la configuración del proyecto.

[Bibliotecas de referencia y los componentes en tiempo de compilación](adding-references-in-visual-cpp-projects.md)<br/>
Procedimientos para incluir bibliotecas, archivos DLL y componentes COM y .NET en un proyecto.

[Organización de archivos de salida del proyecto](how-to-organize-project-output-files-for-builds.md)<br/>
Procedimientos para personalizar la ubicación de los archivos ejecutables creados en el proceso de compilación.

[Pasos de compilación personalizada y eventos de compilación](understanding-custom-build-steps-and-build-events.md)<br/>
Procedimientos para agregar un comando arbitrario al proceso de compilación en los puntos especificados.

[Creación de un proyecto a partir del código existente](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Procedimientos para crear un proyecto de Visual Studio a partir de una colección flexible de archivos de código fuente.

## <a name="see-also"></a>Vea también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br>
[Guía de migración y actualización de Microsoft C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
