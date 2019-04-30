---
title: Crear un proyecto de archivos MAKE de C++ en Visual Studio
ms.date: 12/08/2018
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 9c2edfe35233672e8117d336ba40cfea497b1a22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272352"
---
# <a name="create-a-c-makefile-project"></a>Crear un proyecto de archivos MAKE de C++

Un *archivos Make* es un archivo de texto que contiene instrucciones sobre cómo compilar y vincular o *crear* un conjunto de archivos de código fuente en C++. Un programa *Make* lee el archivo Make e invoca un compilador, un vinculador y posiblemente otros programas para crear un archivo ejecutable. La implementación de Microsoft la *realizar* programa se denomina [NMAKE](nmake-reference.md);

Si tiene un proyecto de archivo Make existente, tiene estas opciones si desea codificarlo o depurarlo en el IDE de Visual Studio:

- Cree un proyecto de archivos MAKE de Visual Studio que usa el archivo MAKE existente para configurar un archivo .vcxproj que va a usar Visual Studio para IntelliSense. (No tendrá todas las características del IDE que obtendrá con un proyecto de MSBuild nativo). Vea [Para crear un proyecto de archivos Make](#create_a_makefile_project) a continuación.
- Use el asistente para **Crear nuevo proyecto de archivos de código fuente existentes** para crear un proyecto de MSBuild nativo a partir del código fuente. No se usará el archivo MAKE original después de esto. Para obtener más información, vea [Cómo: Crear un proyecto de C++ a partir del código existente](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 y versiones posteriores**: Use la **Abrir carpeta** característica para editar y compilar un proyecto de archivos MAKE como-sin ninguna participación del sistema MSBuild. Para más información, vea el artículo sobre los [proyectos Abrir carpeta para C++](../open-folder-projects-cpp.md).

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Para crear un proyecto de archivos MAKE con la plantilla de proyecto de archivos MAKE

En Visual Studio 2017 y versiones posteriores, la plantilla de proyecto de archivos Make está disponible cuando se instala la carga de trabajo de Desarrollo de escritorio de C++.

Siga el asistente para especificar los comandos y el entorno que el archivo Make va a usar. A continuación, puede utilizar este proyecto para compilar el código en Visual Studio.

De forma predeterminada, el proyecto de archivo Make no mostrará ningún archivo en el Explorador de soluciones. El proyecto de archivo Make especifica la configuración de compilación, que se refleja en la página de propiedades del proyecto.

El archivo de salida que especifique en el proyecto no afectará al nombre que genera el script de compilación; sólo declara una intención. Aún así, el archivo Make controla el proceso de compilación y especifica los destinos de compilación.

1. En la página de inicio de Visual Studio, escriba "archivo Make" en el cuadro de búsqueda **Nuevo proyecto**. O bien, en el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C++** > **General** (Visual Studio 2015) u **Otros** (Visual Studio 2017) y después seleccione **Proyecto de archivos Make** en el panel Plantillas para abrir el asistente para proyectos.

1. En la página **Configuración de la aplicación**, escriba la información sobre comandos, salida y limpieza, y la información de recompilación para las compilaciones de depuración y comercial.

1. Haga clic en **Finalizar** para cerrar el asistente y abrir el **Explorador de soluciones** del proyecto recién creado.

Puede ver y editar las propiedades del proyecto en la página de propiedades. Consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md) para obtener información acerca de cómo mostrar la página de propiedades.

## <a name="makefile-project-wizard"></a>Asistente para proyecto de archivos MAKE

Después de crear un proyecto de archivos MAKE, puede ver y editar cada una de las siguientes opciones en el **Nmake** página de la página de propiedades del proyecto.

- **Línea de comandos de compilación:** Especifica la línea de comandos que se ejecutará cuando el usuario selecciona la compilación en el menú compilar. Se muestra en el campo de la línea de comandos de compilación en la página de Nmake de página de propiedades del proyecto.

- **Salida:** Especifica el nombre del archivo que contendrá la salida para la línea de comandos. De forma predeterminada, esta opción se basa en el nombre del proyecto. Se muestra en el campo de salida en la página de Nmake de página de propiedades del proyecto.

- **Comandos para limpiar:** Especifica la línea de comandos que se ejecutará cuando el usuario seleccione Limpiar en el menú compilar. Se muestra en el campo de la línea de comandos de limpieza en la página de Nmake de página de propiedades del proyecto.

- **Vuelva a generar la línea de comandos:** Especifica la línea de comandos que se ejecutará cuando el usuario seleccione volver a generar en el menú compilar. Muestra en la regeneración de todos los campos de la línea de comandos en la página de Nmake de página de propiedades del proyecto.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Procedimiento Habilitar IntelliSense para proyectos de archivos Make

IntelliSense se produce un error en los proyectos de archivos MAKE cuando ciertas opciones de proyecto o las opciones del compilador se ha configurado correctamente. Siga estos pasos para configurar proyectos de archivos MAKE para que IntelliSense funcione según lo esperado:

1. Abra el cuadro de diálogo **Páginas de propiedades**. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

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
[Cómo: Crear un proyecto de C++ desde el código existente](../how-to-create-a-cpp-project-from-existing-code.md)
[caracteres especiales en un archivo MAKE](special-characters-in-a-makefile.md)<br/>
[Contenido de un archivo MAKE](contents-of-a-makefile.md)<br/>
