---
title: Directorios de VC++ (Página de propiedades) | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
dev_langs:
- C++
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 238f26e8955d4be676c3bf37f7cc8b2d842b3de9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394457"
---
# <a name="vc-directories-property-page-windows"></a>Directorios de VC++ (Página de propiedades) (Windows)

Use esta página de propiedades para indicar a Visual Studio los directorios que se van a usar al compilar el proyecto seleccionado actualmente. Para establecer directorios para varios proyectos de una solución, use una hoja de propiedades personalizadas, como se describe en [Crear configuraciones de propiedad reutilizables](working-with-project-properties.md#bkmkPropertySheets).

Para la versión de Linux de esta página, vea [Directorios de VC++ (C++ para Linux)](../linux/prop-pages/directories-linux.md).

Para acceder a la página de propiedades **Directorios de VC++**:

1. Si la ventana **Explorador de soluciones** no es visible, seleccione **Ver** > **Explorador de soluciones** en el menú principal.
1. Haga clic con el botón derecho en un nodo de proyecto (no en la solución de nivel superior) y seleccione **Propiedades**.
1. En el panel de la izquierda del cuadro de diálogo **Páginas de propiedades**, seleccione **Propiedades de configuración** > **Directorios de VC++**.

Las propiedades de los directorios de VC++ se aplican a un proyecto, no al nodo de solución de nivel superior. Si no ve **Directorios de VC++** en **Propiedades de configuración**, seleccione un nodo de proyecto de C++ en la ventana **Explorador de soluciones**:

![Seleccionar el nodo de proyecto](media/vcppdir.png "Seleccionar el nodo de proyecto para ver las propiedades de los directorios de VC++")

Tenga en cuenta que la página de propiedades **Directorios de VC++** de los proyectos multiplataforma tiene otro aspecto. Para obtener información específica de los proyectos de C++ para Linux, vea [Directorios de VC++ (C++ para Linux)](../linux/prop-pages/directories-linux.md).

Si no está familiarizado con las *propiedades del proyecto* en Visual Studio, es posible que le resulte útil leer primero [Trabajar con propiedades de proyecto](working-with-project-properties.md).

La configuración predeterminada de las propiedades **Directorios de VC++** depende del tipo de proyecto. Para los proyectos de escritorio incluyen las ubicaciones de herramientas de C++ para un conjunto de herramientas de plataforma determinado y la ubicación del SDK de Windows. Puede cambiar **Conjunto de herramientas de plataforma** y **Versión de Windows SDK** en la página **Propiedades de configuración** > **General**.

Para ver los valores de cualquiera de los directorios:

1. Seleccione una de las propiedades de la página **Directorios de VC++**. Por ejemplo, seleccione **Directorios de bibliotecas**.
1. Haga clic el botón de flecha hacia abajo al final del campo de valor de propiedad.
1. En el menú desplegable, seleccione **Editar**.

![Editar directorios de bibliotecas](media/vcppdir_libdir_edit.png "Cuadro de diálogo para editar las rutas de acceso de bibliotecas")

Ahora verá un cuadro de diálogo similar al siguiente:

![Mostrar directorios de bibliotecas](media/vcppdir_libdir.png "Cuadro de diálogo para agregar o quitar rutas de acceso de bibliotecas")

Use este cuadro de diálogo para ver los directorios actuales. Pero si quiere cambiar o agregar un directorio, es mejor usar el **Administrador de propiedades** para crear una hoja de propiedades o modificar la hoja de propiedades de usuario predeterminada. Para obtener más información, vea [Crear configuraciones de propiedad reutilizables](working-with-project-properties.md#bkmkPropertySheets).

Como se indicó anteriormente, muchas de las rutas de acceso heredadas se proporcionan como macros.  Para examinar el valor actual de una macro, haga clic en el botón **Macros** en la esquina inferior derecha del cuadro de diálogo. Tenga en cuenta que muchas macros dependen del tipo de configuración. Es posible que una macro en una compilación de depuración se evalúe como otra ruta de acceso que la misma macro en una compilación de versión.

Puede buscar una coincidencia parcial o completa en el cuadro de edición. En la ilustración siguiente se muestran todas las macros que contienen la cadena "WindowsSDK" y también la ruta de acceso actual a la que se evalúa la macro:

![Ver los valores de la macro](media/vcppdir_libdir_macros.png "Cuadro de diálogo para editar las macros")

Nota: Esta lista se rellena a medida que se escribe. No presione **Entrar**.

Para obtener más información sobre las macros y por qué se deben usar en lugar de rutas de acceso codificadas de forma rígida siempre que sea posible, vea [Trabajar con propiedades del proyecto](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros).

Para obtener una lista de las macros usadas con frecuencia, vea [Macros comunes para propiedades y comandos de compilación](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties).

Hay dos maneras de definir macros propias:
-   Establecer variables de entorno en un símbolo del sistema para desarrolladores. Todas las variables de entorno se tratan como propiedades o macros de MSBuild.
-   Definir macros de usuario en un archivo .props. Para obtener más información, vea [Macros de la página de propiedades](working-with-project-properties.md#bkmkPropertiesVersusMacros).

Para obtener más información, vea estas entradas de blog: [VC++ Directories](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx) (Directorios de VC++), [Inherited Properties and Property Sheets](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx) (Propiedades y hojas de propiedades heredadas) y [Visual Studio 2010 C++ Project Upgrade Guide](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) (Guía de actualización de proyectos de C++ de Visual Studio 2010).

## <a name="directory-types"></a>Tipos de directorio

También puede especificar otros directorios, de la manera siguiente.

**Directorios de archivos ejecutables**<br/>
Directorios donde buscar archivos ejecutables. Se corresponde a la variable de entorno **PATH**.

**Directorios de archivos de inclusión**<br/>
Directorios donde buscar archivos de inclusión a los que se hace referencia en el código fuente. Se corresponde a la variable de entorno **INCLUDE**.

**Directorios de referencia**<br/>
Directorios donde buscar archivos de ensamblado y módulo (metadatos) a los que la directiva [#using](../preprocessor/hash-using-directive-cpp.md) hace referencia en el código fuente. Se corresponde a la variable de entorno **LIBPATH**.

**Directorios de archivos de bibliotecas**<br/>
Directorios donde buscar archivos de bibliotecas (.lib); esto incluye las bibliotecas en tiempo de ejecución. Se corresponde a la variable de entorno **LIB**. Este valor no se aplica a los archivos .obj; para crear vínculos a un archivo .obj, en la página de propiedades **Configuración de propiedades** > **Vinculador** > **General**, seleccione **Dependencias de biblioteca adicionales** y después especifique la ruta de acceso relativa del archivo. Para obtener más información, vea [Páginas de propiedades del vinculador](../ide/linker-property-pages.md).

**Directorios de biblioteca WinRT**<br/>
Directorios donde buscar los archivos de biblioteca de WinRT para usar en aplicaciones para la Plataforma universal de Windows (UWP).

**Directorios de archivos de código fuente**<br/>
Directorios donde buscar archivos de código fuente para utilizar con IntelliSense.

**Directorios de archivos de inclusión**<br/>
Antes de cada compilación, Visual Studio consulta la marca de tiempo de todos los archivos para determinar si alguno se ha modificado desde la compilación anterior. Si el proyecto tiene bibliotecas estables grandes, se pueden acelerar los tiempos de compilación si esos directorios se excluyen de la comprobación de marca de tiempo.

## <a name="sharing-the-settings"></a>Compartir la configuración

Puede compartir propiedades del proyecto con otros usuarios o en varios equipos. Para obtener más información, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).
