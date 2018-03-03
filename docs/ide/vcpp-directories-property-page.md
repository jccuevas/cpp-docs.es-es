---
title: "Página de propiedades de directorios de VC ++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c92a97ccd28a1bc7d1fae518cf499b45d339dae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="vc-directories-property-page-windows"></a>Página de propiedades de directorios de VC ++ (Windows)

Utilice esta página de propiedades para indicar a Visual Studio los directorios que se utilizan al compilar el proyecto seleccionado actualmente. Para establecer directorios para varios proyectos en una solución, utilice una hoja de propiedades personalizadas, como se describe en [crear configuraciones de propiedad reutilizables](working-with-project-properties.md#bkmkPropertySheets).

Para la versión de Linux de esta página, vea [directorios de VC ++ (C++ Linux)](../linux/prop-pages/directories-linux.md).   

Para tener acceso a la **directorios de VC ++** página de propiedades:

1. en el menú principal seleccione **vista | Explorador de soluciones**
1. Haga doble clic en el nodo del proyecto (no la solución de nivel superior) y elija **propiedades**
1. en el panel izquierdo de la **páginas de propiedades** cuadro de diálogo, expanda **propiedades de configuración** y seleccione **directorios de VC ++**.  

Propiedades de directorios de VC ++ se aplican a un proyecto, no el nodo de solución de nivel superior:

![Seleccione el nodo del proyecto](media/vcppdir.png "seleccione el nodo de proyecto para ver las propiedades de directorios de VC ++")

Si no ve la página de propiedades, asegúrese de que tiene el nodo del proyecto seleccionado en **el Explorador de soluciones**. Tenga en cuenta que un **directorios de VC ++** página de propiedades de los proyectos multiplataforma, parece diferente. Para los proyectos de distinta de Windows, vea [directorios de VC ++ (C++ Linux)](../linux/prop-pages/directories-linux.md) o. 
 
Si no está familiarizado con *propiedades del proyecto* en Visual Studio, le resultará útil para la primera lectura [trabajar con configuraciones de proyecto](working-with-project-properties.md). 
 
La configuración predeterminada para los directorios de VC ++ depende del tipo de proyecto. Para proyectos de escritorio incluyen las ubicaciones de herramientas de VC ++ para un determinado conjunto de herramientas de plataforma y la ubicación del SDK de Windows. Puede cambiar la **conjunto de herramientas de plataforma** y **versión del SDK de Windows** en el **propiedades de configuración: General** página. Para ver los valores de cualquiera de los directorios:

1. en el panel derecho de la **directorios de VC ++** , seleccione una fila. Por ejemplo, **directorios de bibliotecas**
1. Elija el botón de flecha abajo a la derecha
1. Elija **editar**.

![Editar directorios de bibliotecas](media/vcppdir_libdir_edit.png "cuadro de diálogo para editar las rutas de acceso de la biblioteca")

Ahora verá un cuadro de diálogo similar al siguiente: 

![Mostrar directorios de bibliotecas](media/vcppdir_libdir.png "cuadro de diálogo para agregar o quitar rutas de acceso de biblioteca")

Utilice este cuadro de diálogo para ver los directorios actuales. Sin embargo, si desea cambiar o agregar un directorio, es mejor usar **Administrador de propiedades** para crear una hoja de propiedades o modificar la hoja de propiedades de usuario de forma predeterminada. Para obtener más información, consulte [crear configuraciones de propiedad reutilizables](working-with-project-properties.md#bkmkPropertySheets).

Como se indicó anteriormente, muchas de las rutas de acceso heredadas se proporcionan como macros.  Para examinar el valor actual de una macro, elija la **Macros** botón en la esquina inferior derecha del cuadro de diálogo. Tenga en cuenta que muchas macros dependen del tipo de configuración. Una macro en una compilación de depuración puede evaluarse como una ruta de acceso diferente a la misma macro en una versión de lanzamiento. 

Puede buscar una coincidencia parcial o completa en el cuadro de edición. La ilustración siguiente muestra todas las macros que contengan la cadena "WindowsSDK" y también muestra la ruta de acceso actual que se evalúa como la macro:

![Vea los valores de la macro](media/vcppdir_libdir_macros.png "cuadro de diálogo para editar las macros")

Nota: La lista se rellena a medida que escribe. No presione **ENTRAR**.

Para obtener más información acerca de las macros y por qué se debe usar en lugar de rutas codificadas de forma rígida siempre que sea posible, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Para obtener una lista de macros utilizadas, consulte [comunes Macros para propiedades y comandos de generación](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties).

Puede definir sus propias macros de dos maneras:
-   Establecer variables de entorno en un símbolo del sistema para desarrolladores. Todas las variables de entorno se tratan como macros/propiedades de MSBuild.
-   Definir macros de usuario en un archivo .props. Para obtener más información, consulte [macros de la página de propiedades](working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Para obtener más información, vea estas entradas de blog: [directorios de VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [hereda propiedades y hojas de propiedades](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), y [guía para actualizar proyectos de Visual Studio 2010 C++](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## <a name="directory-types"></a>Tipos de directorio

También puede especificar otros directorios, de la manera siguiente.  
  
**Directorios de archivos ejecutables**  
Directorios donde buscar archivos ejecutables. Corresponde a la **ruta de acceso** variable de entorno.

**Directorios de archivos de inclusión**  
Directorios donde buscar archivos de inclusión a los que se hace referencia en el código fuente. Corresponde a la **INCLUDE** variable de entorno.

**Directorios de referencia**  
 Directorios donde buscar archivos de módulo (metadatos) que se hace referencia en el código fuente de ensamblado y la [#using](../preprocessor/hash-using-directive-cpp.md) directiva. Corresponde a la **LIBPATH** variable de entorno.

**Directorios de archivos de bibliotecas**  
Directorios donde buscar archivos de bibliotecas (.lib); esto incluye las bibliotecas en tiempo de ejecución. Corresponde a la **LIB** variable de entorno. Esta configuración no se aplica a los archivos .obj; Para vincular a un archivo .obj, en la [vinculador](../ide/linker-property-pages.md)**General** página de propiedades, seleccione **dependencias de biblioteca adicionales** y, a continuación, especifique la ruta de acceso relativa del archivo.

**Directorios de origen**  
Directorios donde buscar archivos de código fuente para utilizar con IntelliSense.

**Excluir directorios**  
Directorios en los que no se va a buscar cuando se comprueban las dependencias de compilación.

## <a name="sharing-the-settings"></a>Compartir la configuración

Puede compartir propiedades del proyecto con otros usuarios o en varios equipos. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).
