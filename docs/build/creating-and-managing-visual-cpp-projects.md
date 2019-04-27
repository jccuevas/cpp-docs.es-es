---
title: Proyectos de Visual Studio - C++
ms.date: 12/12/2018
f1_keywords:
- vcprojects
- creatingmanagingVC
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: b4772b9bd625a542a18039386fefe42840ab65b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195728"
---
# <a name="visual-studio-projects---c"></a>Proyectos de Visual Studio - C++

Un *proyecto de Visual Studio* es un proyecto basado en el sistema de compilación de MSBuild. MSBuild es el sistema de compilación nativa para Visual Studio y suele ser que el mejor sistema que se usará para las aplicaciones para UWP, así como aplicaciones de escritorio que usan las bibliotecas MFC o ATL, componentes COM y otros programas de Windows específicos de compilación. MSBuild está estrechamente integrado con Visual Studio, pero también puede usar la línea de comandos. 

## <a name="create-a-project"></a>Crear un proyecto

Puede crear proyectos de C++ eligiendo **archivo &#124; New &#124; proyecto**, a continuación, elija Visual C++ en el panel izquierdo. En el panel central, verá una lista de plantillas de proyecto: 

   ![Plantillas de proyecto](../overview/media/vs2017-new-project.png "Cuadro de diálogo Nuevo proyecto de Visual Studio 2017")

Para obtener más información acerca de todas las plantillas de proyecto predeterminada que se incluyen en Visual Studio, consulte [plantillas de proyecto de C++ en Visual Studio](reference/visual-cpp-project-types.md). Puede crear sus propias plantillas de proyecto. Para obtener más información, vea [Cómo: Crear plantillas de proyecto](/visualstudio/ide/how-to-create-project-templates).

Después de crear un proyecto, aparece en el [el Explorador de soluciones](/visualstudio/ide/solutions-and-projects-in-visual-studio) ventana:

   ![Explorador de soluciones](media/mathlibrary-solution-explorer-153.png)

Cuando crea un nuevo proyecto, también se crea un archivo de solución (.sln). Puede agregar proyectos adicionales a la solución con el botón secundario en él en **el Explorador de soluciones**. El archivo de solución se usa para coordinar las dependencias de compilación cuando tiene varios proyectos relacionados, pero no hace mucho más. Todas las opciones del compilador se establecen en el nivel de proyecto.

## <a name="add-items"></a>Agregar elementos

Agregar archivos de código fuente, iconos o cualquier otro elemento al proyecto con el botón secundario en el proyecto en **el Explorador de soluciones** y eligiendo **Agregar > nuevo** o **Add > Existing**.

## <a name="add-third-party-libraries"></a>Agregar bibliotecas de terceros

Para agregar las bibliotecas de terceros, use el [vcpkg](vcpkg.md) Administrador de paquetes. Ejecute el paso de integración de Visual Studio para configurar las rutas de acceso a esa biblioteca cuando se hace referencia desde cualquier proyecto de Visual Studio. 

## <a name="set-compiler-options-and-other-build-properties"></a>Establecer las opciones del compilador y otras propiedades de compilación

Para configurar las opciones de compilación para un proyecto, haga doble clic en el proyecto en **el Explorador de soluciones** y elija **propiedades**. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Compilar y ejecutar

Para compilar y ejecutar el nuevo proyecto, presione **F5** o haga clic en el *depurar desplegable* con la flecha verde en la barra de herramientas principal. El *lista desplegable configuración* es donde elegir si desea realizar un *depurar* o *versión* compilación (u otra configuración personalizada).

Un nuevo proyecto se compila sin errores. Al agregar su propio código, en ocasiones puede introducir un error o desencadenar una advertencia. Un error impide que la compilación se complete; no es una advertencia. Todos los errores y advertencias aparecerá en la ventana de salida y en la lista de errores al compilar el proyecto. 

   ![Lista de error y la ventana de salida](../overview/media/vs2017-output-error-list.png)

En la lista de errores, puede presionar **F1** en un error resaltado para ir a su tema de documentación.

## <a name="in-this-section"></a>En esta sección

[Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](working-with-project-properties.md)<br/>
Aprenda a utilizar hojas de propiedades y páginas de propiedades para especificar la configuración del proyecto.

[Bibliotecas de referencia y los componentes en tiempo de compilación](adding-references-in-visual-cpp-projects.md)<br/>
Cómo incluir los componentes COM y .NET en bibliotecas, archivos DLL, en un proyecto.
 
[Organización de archivos de salida del proyecto](how-to-organize-project-output-files-for-builds.md)<br/>
Cómo personalizar la ubicación de los archivos ejecutables que se creó en el proceso de compilación.

[Pasos de compilación personalizada y eventos de compilación](understanding-custom-build-steps-and-build-events.md)<br/>
Cómo agregar un comando arbitrario al proceso de compilación en los puntos especificados.

[Creación de un proyecto a partir del código existente](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Cómo crear un nuevo proyecto de Visual Studio de una colección de archivos de origen no estricta.

## <a name="see-also"></a>Vea también

[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br>
