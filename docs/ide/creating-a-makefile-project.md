---
title: Creación de un proyecto de archivos Make en C++
ms.date: 10/19/2018
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 0c64f6df342e82e3ea5409e2b07af1e591747d7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494853"
---
# <a name="creating-a-c-makefile-project"></a>Creación de un proyecto de archivos Make en C++

Un *archivos Make* es un archivo de texto que contiene instrucciones sobre cómo compilar y vincular o *crear* un conjunto de archivos de código fuente en C++. Un programa *Make* lee el archivo Make e invoca un compilador, un vinculador y posiblemente otros programas para crear un archivo ejecutable. La implementación de Microsoft del programa *Make* se denomina **NMAKE**. (Visual Studio de forma predeterminada usa el sistema MSBuild basado en archivos .vcxproj; es decir, lo que se crea mediante **Archivo | Nuevo | Proyecto**).

Si tiene un proyecto de archivo Make existente, tiene estas opciones si desea codificarlo o depurarlo en el IDE de Visual Studio:

- Cree un proyecto de archivos Make en Visual Studio que use el archivo Make existente para compilar el código en el IDE. (No tendrá todas las características del IDE que obtendrá con un proyecto de MSBuild nativo). Vea [Para crear un proyecto de archivos Make](#create_a_makefile_project) a continuación.
- Use el asistente para **Crear nuevo proyecto de archivos de código fuente existentes** para crear un proyecto de MSBuild nativo a partir del código fuente. Para más información, vea [Cómo: Crear un proyecto de C++ a partir del código existente](how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 y versiones posteriores**: use la característica **Abrir carpeta** para abrir un proyecto de archivo Make sin convertirlo a MSBuild. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](non-msbuild-projects.md).

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Para crear un proyecto de archivos Make con la plantilla de proyecto de archivos Make

En Visual Studio 2017 y versiones posteriores, la plantilla de proyecto de archivos Make está disponible cuando se instala la carga de trabajo de Desarrollo de escritorio de C++.

Siga el asistente para especificar los comandos y el entorno que el archivo Make va a usar. Después, podrá usar este proyecto para compilar el código desde el entorno de desarrollo de Visual Studio.

De forma predeterminada, el proyecto de archivo Make no mostrará ningún archivo en el Explorador de soluciones. El proyecto de archivo Make especifica la configuración de compilación, que se refleja en la página de propiedades del proyecto.

El archivo de salida que especifique en el proyecto no afectará al nombre que genera el script de compilación; sólo declara una intención. Aún así, el archivo Make controla el proceso de compilación y especifica los destinos de compilación.

1. En la página de inicio de Visual Studio, escriba "archivo Make" en el cuadro de búsqueda **Nuevo proyecto**. O bien, en el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C++** > **General** (Visual Studio 2015) u **Otros** (Visual Studio 2017) y después seleccione **Proyecto de archivos Make** en el panel Plantillas para abrir el asistente para proyectos.

1. En la página [Configuración de la aplicación](../ide/application-settings-makefile-project-wizard.md), escriba la información sobre comandos, salida y limpieza, y la información de recompilación para las compilaciones de depuración y comercial.

1. Haga clic en **Finalizar** para cerrar el asistente y abrir el **Explorador de soluciones** del proyecto recién creado.

Puede ver y editar las propiedades del proyecto en la página de propiedades. Vea [Establecer las propiedades de un proyecto de Visual C++](../ide/working-with-project-properties.md) para obtener información sobre cómo mostrar la página de propiedades.

## <a name="see-also"></a>Vea también

[Asistente para proyectos de archivos MAKE](../ide/makefile-project-wizard.md)<br/>
[Caracteres especiales en un archivo MAKE](../build/special-characters-in-a-makefile.md)<br/>
[Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)<br/>
