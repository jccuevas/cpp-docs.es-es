---
title: Creación de un proyecto de archivos Make de C++ en Visual Studio
ms.date: 08/05/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects [C++]
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 861cd88440a697ce5a3abc83109526227ae42f8e
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866129"
---
# <a name="create-a-c-makefile-project"></a>Creación de un proyecto de archivos Make de C++

Un *archivos Make* es un archivo de texto que contiene instrucciones sobre cómo compilar y vincular o *crear* un conjunto de archivos de código fuente en C++. Un programa *Make* lee el archivo Make e invoca un compilador, un vinculador y posiblemente otros programas para crear un archivo ejecutable. La implementación de Microsoft del programa *Make* se denomina [NMAKE](nmake-reference.md).

Si tiene un proyecto de archivo Make existente, tiene estas opciones si desea codificarlo o depurarlo en el IDE de Visual Studio:

- Cree un proyecto de archivos Make en Visual Studio en el que se use el archivo Make existente para configurar un archivo .vcxproj que Visual Studio usará para IntelliSense. (No tendrá todas las características del IDE que obtendrá con un proyecto de MSBuild nativo). Vea [Para crear un proyecto de archivos Make](#create_a_makefile_project) a continuación.
- Use el asistente para **Crear nuevo proyecto de archivos de código fuente existentes** para crear un proyecto de MSBuild nativo a partir del código fuente. Después de esto no se usará el archivo Make original. Para obtener más información, consulte [Cómo Crear un proyecto de C++ a partir del código existente](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 y versiones posteriores**: Use la característica **Abrir carpeta** para editar y compilar un proyecto de archivos Make como está, sin participación alguna del sistema MSBuild. Para más información, vea el artículo sobre los [proyectos Abrir carpeta para C++](../open-folder-projects-cpp.md).
- **Visual Studio 2019 y versiones posteriores**: Cree un proyecto de archivos Make de UNIX para Linux.

## <a name="a-namecreate_a_makefile_project-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Para crear un proyecto de archivos Make con la plantilla de proyecto de archivos Make

En Visual Studio 2017 y versiones posteriores, la plantilla de proyecto de archivos Make está disponible cuando se instala la carga de trabajo de Desarrollo de escritorio de C++.

Siga el asistente para especificar los comandos y el entorno que el archivo Make va a usar. Después, podrá usar este proyecto para compilar el código en Visual Studio.

De forma predeterminada, el proyecto de archivo Make no mostrará ningún archivo en el Explorador de soluciones. El proyecto de archivo Make especifica la configuración de compilación, que se refleja en la página de propiedades del proyecto.

El archivo de salida que especifique en el proyecto no afectará al nombre que genera el script de compilación; sólo declara una intención. Aún así, el archivo Make controla el proceso de compilación y especifica los destinos de compilación.

::: moniker range="vs-2019"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>Para crear un proyecto de archivos Make en Visual Studio 2019

1. En el menú principal de Visual Studio, seleccione **Archivo** > **Nuevo** > **Proyecto** y escriba "archivo Make" en el cuadro de búsqueda. O bien, en el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C++**  > **General** (Visual Studio 2015) u **Otros** (Visual Studio 2017) y, después, seleccione entre las dos opciones en función de si se va a destinar a Windows o Linux.

1. **Solo Windows**: En la página **Configuración de depuración**, escriba la información sobre comandos, salida, limpieza y recompilación para las compilaciones de depuración y comercial. Haga clic en **Siguiente** si quiere especificar otros valores para una configuración de versión.

1. Haga clic en **Finalizar** para cerrar el cuadro de diálogo y abrir el proyecto recién creado en el **Explorador de soluciones**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>Para crear un proyecto de archivos Make en Visual Studio 2015 o Visual Studio 2017

1. En la página de inicio de Visual Studio, escriba "archivo Make" en el cuadro de búsqueda **Nuevo proyecto**. O bien, en el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C++**  > **General** (Visual Studio 2015) u **Otros** (Visual Studio 2017) y después seleccione **Proyecto de archivos Make** en el panel Plantillas para abrir el asistente para proyectos.

1. En la página **Configuración de la aplicación**, escriba la información sobre comandos, salida y limpieza, y la información de recompilación para las compilaciones de depuración y comercial.

1. Haga clic en **Finalizar** para cerrar el asistente y abrir el **Explorador de soluciones** del proyecto recién creado.

::: moniker-end

Puede ver y editar las propiedades del proyecto en la página de propiedades. Vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md) para obtener información sobre cómo mostrar la página de propiedades.

## <a name="makefile-project-wizard"></a>Asistente para proyectos de archivos Make

Después de crear un proyecto de archivos Make, puede ver y modificar cada una de las opciones siguientes en la página **Nmake** de la página de propiedades del proyecto.

- **Línea de comandos de Compilar:** especifica la línea de comandos que se va a ejecutar cuando el usuario seleccione Compilar en el menú Compilar. Se muestra en el campo Línea de comandos de Compilar de la página Nmake de la página de propiedades del proyecto.

- **Salida:** Especifica el nombre del archivo que contendrá la salida para la línea de comandos. De forma predeterminada, esta opción se basa en el nombre del proyecto. Se muestra en el campo Salida de la página Nmake de la página de propiedades del proyecto.

- **Comandos de Limpiar:** especifica la línea de comandos que se va a ejecutar cuando el usuario seleccione Limpiar en el menú Compilar. Se muestra en el campo Línea de comandos de Limpiar de la página Nmake de la página de propiedades del proyecto.

- **Línea de comandos de regeneración:** especifica la línea de comandos que se va a ejecutar cuando el usuario seleccione Recompilar en el menú Compilar. Se muestra en el campo Línea de comandos de regeneración de la página Nmake de la página de propiedades del proyecto.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Procedimiento Habilitar IntelliSense para proyectos de archivos Make

IntelliSense no funciona en los proyectos de archivos Make cuando no se configuran de manera correcta determinados valores del proyecto u opciones del compilador. Siga estos pasos para configurar proyectos de archivos Make para que IntelliSense funcione según lo esperado:

1. Abra el cuadro de diálogo **Páginas de propiedades**. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Seleccione la página de propiedades **NMake** y, después, modifique las propiedades en **IntelliSense** según corresponda.

   - Establezca la propiedad **Definiciones de preprocesador** para definir los símbolos de preprocesador en el proyecto de archivo Make. Vea [/D (Definiciones de preprocesador)](d-preprocessor-definitions.md) para obtener más información.

   - Establezca la propiedad **Ruta de acceso de búsqueda de inclusión** para especificar la lista de directorios en los que el compilador debe buscar para resolver las referencias de archivo que se pasan a las directivas de preprocesador en el proyecto de archivo Make. Vea [/I (Directorios de inclusión adicionales)](i-additional-include-directories.md) para obtener más información.

    - Para los proyectos que se compilan mediante CL.EXE desde una ventana de comandos, establezca la variable de entorno **INCLUDE** para especificar los directorios en los que el compilador debe buscar para resolver las referencias de archivo que se pasan a las directivas de preprocesador en el proyecto de archivo Make.

   - Establezca la propiedad **Archivos de inclusión forzados** para especificar qué archivos de encabezado se van a procesar al compilar el proyecto de archivo Make. Vea [/FI (Dar nombre al archivo de inclusión obligatorio)](fi-name-forced-include-file.md) para obtener más información.

   - Establezca la propiedad **Ruta de acceso de búsqueda de ensamblado** para especificar la lista de directorios que el compilador debe buscar para resolver las referencias a los ensamblados .NET del proyecto. Vea [/AI (Especificar directorios de metadatos)](ai-specify-metadata-directories.md) para obtener más información.

   - Establezca la propiedad **Ensamblados de uso forzados** para especificar qué ensamblados .NET se van a procesar al compilar el proyecto de archivo Make. Vea [/FU (Dar nombre al archivo #using obligatorio)](fu-name-forced-hash-using-file.md) para obtener más información.

   - Establezca la propiedad **Opciones adicionales** para especificar modificadores de compilador adicionales que IntelliSense usará al analizar los archivos de C++.

1. Haga clic en **Aceptar** para cerrar las páginas de propiedades.

1. Use el comando **Guardar todo** para guardar la configuración de proyecto modificada.

La próxima vez que abra el proyecto de archivo Make en el entorno de desarrollo de Visual Studio, ejecute los comandos **Limpiar solución** y **Compilar solución**. IntelliSense debería funcionar correctamente en el IDE.

## <a name="see-also"></a>Vea también

[Usar IntelliSense](/visualstudio/ide/using-intellisense)<br>
[Referencia de NMAKE](nmake-reference.md)<br>
[Cómo: Crear un proyecto de C++ a partir del código existente](../how-to-create-a-cpp-project-from-existing-code.md)
[Caracteres especiales en un archivo Make](special-characters-in-a-makefile.md)<br/>
[Contenido de un archivo MAKE](contents-of-a-makefile.md)<br/>
