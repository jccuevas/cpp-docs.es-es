---
title: Crear un proyecto de archivos MAKE | Documentos de Microsoft
ms.custom: 
ms.date: 02/28/2018
ms.technology:
- cpp-ide
ms.topic: article
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f487126b58dddc0243646ebce7faa2754ffa7053
ms.sourcegitcommit: 4e01d36ffa64ea11bacf589f79d2f1df947e2510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="creating-a-makefile-project"></a>Crear un proyecto de archivos MAKE

Si tiene un proyecto de código fuente existente que se compila desde la línea de comandos mediante el uso de un archivo MAKE, el entorno de desarrollo de Visual Studio tiene varias formas de convertir en un proyecto que puede aprovechar al máximo las características del IDE de Visual Studio. Este artículo describe cómo crear un proyecto de archivos MAKE de Visual Studio que usa el archivo MAKE existente para compilar el código en el IDE. Como alternativa, puede usar el **crear nuevo proyecto de archivos de código existentes** Asistente para crear un proyecto de MSBuild nativo desde el código fuente. Para más información, vea [Cómo: Crear un proyecto de C++ a partir del código existente](how-to-create-a-cpp-project-from-existing-code.md). A partir de 2017 de Visual Studio, también puede usar el **Abrir carpeta** característica, que puede utilizar varios sistemas de compilación existente como si fueran proyectos nativos de Visual Studio. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](non-msbuild-projects.md).

Para usar Visual Studio para abrir y compilar el código fuente con el archivo MAKE existente, primero cree un nuevo proyecto seleccionando la plantilla de proyecto de archivos MAKE. Un asistente le ayuda a especificar los comandos y el entorno que utilizará el archivo MAKE. A continuación, puede utilizar este proyecto para compilar el código en el entorno de desarrollo de Visual Studio.

De forma predeterminada, el proyecto de archivos MAKE no muestra ningún archivo en el Explorador de soluciones. El proyecto de archivos MAKE especifica la configuración de compilación, que se refleja en la página de propiedades del proyecto.

El archivo de salida que especifique en el proyecto no afectará al nombre que genera el script de compilación; sólo declara una intención. Aún así, el archivo MAKE controla el proceso de compilación y especifica los destinos de compilación.

## <a name="to-create-a-makefile-project"></a>Para crear un proyecto de archivos MAKE

1. Siga las instrucciones del tema de Ayuda [crear un proyecto con un Asistente para aplicaciones de Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).

1. En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C++** > **General** y, a continuación, seleccione **proyecto de archivos MAKE** en el Panel de plantillas para abrir al Asistente para proyectos.

1. En el [configuración de la aplicación](../ide/application-settings-makefile-project-wizard.md) , proporcione el resultado del comando, limpiar y volver a generar información de depuración y comerciales compilaciones.

1. Haga clic en **finalizar** para cerrar el asistente y abrir el proyecto recién creado en **el Explorador de soluciones**.

Puede ver y editar las propiedades del proyecto en la página de propiedades. Vea [establecer las propiedades de un proyecto de Visual C++](../ide/working-with-project-properties.md) para obtener información acerca de cómo mostrar la página de propiedades.

## <a name="see-also"></a>Vea también

[Asistente para proyectos de archivos MAKE](../ide/makefile-project-wizard.md)<br/>
[Caracteres especiales en un archivo MAKE](../build/special-characters-in-a-makefile.md)<br/>
[Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)<br/>
