---
title: Página de propiedades de directorios de VC ++ | Documentos de Microsoft
ms.custom: ''
ms.date: 04/26/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8931ecd34acfa1aba0287274acb45d362bdec2cf
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="vc-directories-property-page-windows"></a>Página de propiedades de directorios de VC ++ (Windows)

Utilice esta página de propiedades para indicar a Visual Studio los directorios que se utilizan al compilar el proyecto seleccionado actualmente. Para establecer directorios para varios proyectos en una solución, utilice una hoja de propiedades personalizadas, como se describe en [crear configuraciones de propiedad reutilizables](working-with-project-properties.md#bkmkPropertySheets).

Para la versión de Linux de esta página, vea [directorios de VC ++ (C++ Linux)](../linux/prop-pages/directories-linux.md).   

Para tener acceso a la **directorios de VC ++** página de propiedades:

1. Si el **el Explorador de soluciones** ventana no está visible, a continuación, en el menú principal, elija **vista** > **el Explorador de soluciones**.
1. Haga doble clic en un nodo de proyecto (no la solución de nivel superior) y elija **propiedades**.
1. En el panel izquierdo de la **páginas de propiedades** cuadro de diálogo, seleccione **propiedades de configuración** > **directorios de VC ++**.  

Propiedades de directorios de VC ++ se aplican a un proyecto, no el nodo de solución de nivel superior. Si no ve **directorios de VC ++** en **propiedades de configuración**, seleccione un nodo de proyecto de C++ en el **el Explorador de soluciones** ventana: 

![Seleccione el nodo del proyecto](media/vcppdir.png "seleccione el nodo de proyecto para ver las propiedades de directorios de VC ++")

Tenga en cuenta que la **directorios de VC ++** página de propiedades de los proyectos multiplataforma, parece diferente. Para obtener información específica de proyectos de C++ de Linux, consulte [directorios de VC ++ (C++ Linux)](../linux/prop-pages/directories-linux.md). 
 
Si no está familiarizado con *propiedades del proyecto* en Visual Studio, le resultará útil para la primera lectura [trabajar con configuraciones de proyecto](working-with-project-properties.md). 
 
La configuración predeterminada de **directorios de VC ++** propiedades dependen del tipo de proyecto. Para proyectos de escritorio incluyen las ubicaciones de herramientas de C++ para un determinado conjunto de herramientas de plataforma y la ubicación del SDK de Windows. Puede cambiar la **conjunto de herramientas de plataforma** y **versión del SDK de Windows** en el **propiedades de configuración** > **General** página. 

Para ver los valores de cualquiera de los directorios:

1. Seleccione una de las propiedades de la **directorios de VC ++** página. Por ejemplo, elegir **directorios de bibliotecas**.
1. Elija el botón de flecha hacia abajo al final del campo de valor de propiedad.
1. En el menú desplegable, elija **editar**.

![Editar directorios de bibliotecas](media/vcppdir_libdir_edit.png "cuadro de diálogo para editar las rutas de acceso de la biblioteca")

Ahora verá un cuadro de diálogo similar al siguiente: 

![Mostrar directorios de bibliotecas](media/vcppdir_libdir.png "cuadro de diálogo para agregar o quitar rutas de acceso de biblioteca")

Utilice este cuadro de diálogo para ver los directorios actuales. Sin embargo, si desea cambiar o agregar un directorio, es mejor usar **Administrador de propiedades** para crear una hoja de propiedades o modificar la hoja de propiedades de usuario de forma predeterminada. Para obtener más información, consulte [crear configuraciones de propiedad reutilizables](working-with-project-properties.md#bkmkPropertySheets).

Como se indicó anteriormente, muchas de las rutas de acceso heredadas se proporcionan como macros.  Para examinar el valor actual de una macro, elija la **Macros** botón en la esquina inferior derecha del cuadro de diálogo. Tenga en cuenta que muchas macros dependen del tipo de configuración. Una macro en una compilación de depuración puede evaluarse como una ruta de acceso diferente a la misma macro en una versión de lanzamiento. 

Puede buscar una coincidencia parcial o completa en el cuadro de edición. La ilustración siguiente muestra todas las macros que contengan la cadena "WindowsSDK" y también muestra la ruta de acceso actual que se evalúa como la macro:

![Vea los valores de la macro](media/vcppdir_libdir_macros.png "cuadro de diálogo para editar las macros")

Nota: Esta lista se rellena a medida que escribe. No presione **ENTRAR**.

Para obtener más información acerca de las macros y por qué se debe usar en lugar de rutas codificadas de forma rígida siempre que sea posible, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Para obtener una lista de macros utilizadas, consulte [comunes Macros para propiedades y comandos de generación](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties).

Puede definir sus propias macros de dos maneras:
-   Establecer variables de entorno en un símbolo del sistema para desarrolladores. Todas las variables de entorno se tratan como macros/propiedades de MSBuild.
-   Definir macros de usuario en un archivo .props. Para obtener más información, consulte [macros de la página de propiedades](working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Para obtener más información, vea estas entradas de blog: [directorios de VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [hereda propiedades y hojas de propiedades](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), y [guía para actualizar proyectos de Visual Studio 2010 C++](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## <a name="directory-types"></a>Tipos de directorio

También puede especificar otros directorios, de la manera siguiente.  
  
**Directorios de archivos ejecutables**<br/>
Directorios donde buscar archivos ejecutables. Corresponde a la **ruta de acceso** variable de entorno.

**Directorios de archivos de inclusión**<br/>
Directorios donde buscar archivos de inclusión a los que se hace referencia en el código fuente. Corresponde a la **INCLUDE** variable de entorno.

**Directorios de referencia**<br/>
 Directorios donde buscar archivos de módulo (metadatos) que se hace referencia en el código fuente de ensamblado y la [#using](../preprocessor/hash-using-directive-cpp.md) directiva. Corresponde a la **LIBPATH** variable de entorno.

**Directorios de archivos de bibliotecas**<br/>
Directorios donde buscar archivos de bibliotecas (.lib); esto incluye las bibliotecas en tiempo de ejecución. Corresponde a la **LIB** variable de entorno. Esta configuración no se aplica a los archivos .obj; Para vincular a un archivo .obj, en la **propiedades de configuración** > **vinculador** > **General** página de propiedades, seleccione  **Dependencias de biblioteca adicionales** y, a continuación, especifique la ruta de acceso relativa del archivo. Para obtener más información, consulte [páginas de propiedades vinculador](../ide/linker-property-pages.md).

**Directorios de bibliotecas WinRT**<br/>
Directorios donde buscar archivos de biblioteca de WinRT para usar en aplicaciones de la plataforma Universal de Windows (UWP). 

**Directorios de origen**<br/>
Directorios donde buscar archivos de código fuente para utilizar con IntelliSense.

**Excluir directorios**<br/>
Antes de cada compilación, Visual Studio realiza una consulta la marca de tiempo en todos los archivos para determinar si alguno ha modificado desde la compilación anterior. Si el proyecto tiene grandes bibliotecas estables, potencialmente puede acelerar los tiempos de compilación excluyendo los directorios de la comprobación de marca de tiempo.

## <a name="sharing-the-settings"></a>Compartir la configuración

Puede compartir propiedades del proyecto con otros usuarios o en varios equipos. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).
