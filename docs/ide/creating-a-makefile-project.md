---
title: Crear un proyecto de archivos Make | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc854f96f1c41baf28a5af4ca1f253e47d9a8914
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33336783"
---
# <a name="creating-a-makefile-project"></a>Crear un proyecto de archivos MAKE

Si tiene un proyecto de código fuente existente que se compila desde la línea de comandos mediante un archivo Make, el entorno de desarrollo de Visual Studio tiene varias formas de convertirlo en un proyecto que pueda aprovechar al máximo las características del IDE de Visual Studio. En este artículo se describe cómo crear un proyecto de archivos Make en Visual Studio que use el archivo Make existente para compilar el código en el IDE. Como alternativa, se puede usar el asistente **Crear nuevo proyecto de archivos de código fuente existentes** para crear un proyecto de MSBuild nativo desde el código fuente. Para más información, vea [Cómo: Crear un proyecto de C++ a partir del código existente](how-to-create-a-cpp-project-from-existing-code.md). A partir de Visual Studio 2017, también puede usar la característica **Abrir carpeta**, que puede usar varios sistemas de compilación existentes como si fueran proyectos nativos de Visual Studio. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](non-msbuild-projects.md).

Para usar Visual Studio para abrir y compilar el código fuente con el archivo Make existente, primero cree un proyecto seleccionando la plantilla de proyecto de archivos Make. Un asistente le ayudará a especificar los comandos y el entorno que el archivo Make va a usar. Después, podrá usar este proyecto para compilar el código desde el entorno de desarrollo de Visual Studio.

De forma predeterminada, el proyecto de archivo Make no mostrará ningún archivo en el Explorador de soluciones. El proyecto de archivo Make especifica la configuración de compilación, que se refleja en la página de propiedades del proyecto.

El archivo de salida que especifique en el proyecto no afectará al nombre que genera el script de compilación; sólo declara una intención. Aún así, el archivo Make controla el proceso de compilación y especifica los destinos de compilación.

## <a name="to-create-a-makefile-project"></a>Para crear un proyecto de archivos MAKE

1. Siga las instrucciones descritas en el tema de Ayuda [Crear un proyecto con el Asistente para aplicaciones de Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).

1. En el cuadro de diálogo **Nuevo proyecto**, expanda **Visual C++** > **General** y después seleccione **Proyecto de archivos Make** en el panel Plantillas para abrir el asistente para proyectos.

1. En la página [Configuración de la aplicación](../ide/application-settings-makefile-project-wizard.md), escriba la información sobre comandos, salida y limpieza, y la información de recompilación para las compilaciones de depuración y comercial.

1. Haga clic en **Finalizar** para cerrar el asistente y abrir el **Explorador de soluciones** del proyecto recién creado.

Puede ver y editar las propiedades del proyecto en la página de propiedades. Vea [Establecer las propiedades de un proyecto de Visual C++](../ide/working-with-project-properties.md) para obtener información sobre cómo mostrar la página de propiedades.

## <a name="see-also"></a>Vea también

[Asistente para proyectos de archivos MAKE](../ide/makefile-project-wizard.md)<br/>
[Caracteres especiales en un archivo MAKE](../build/special-characters-in-a-makefile.md)<br/>
[Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)<br/>
