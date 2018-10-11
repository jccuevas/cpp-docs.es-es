---
title: Compilar proyectos de C++ en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0da2464684a06b62c6e22ea04bb68a01dc36f42b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382354"
---
# <a name="building-c-projects-in-visual-studio"></a>Compilar proyectos de C++ en Visual Studio

En el entorno de desarrollo integrado (IDE) de Visual Studio, hay varias formas de compilar una solución completa o solo uno de sus proyectos. También puede modificar la configuración de compilación y especificar pasos de compilación personalizada para que el proceso de desarrollo sea más eficiente.

Para compilar una solución que esté abierta en Visual Studio y seleccionada en el **Explorador de soluciones**, puede hacer lo siguiente:

- En la barra de menús, elija **Compilar**, **Compilar solución**.

- O bien, en el **Explorador de soluciones**, abra el menú contextual de la solución y, después, seleccione **Compilar solución**.

- O bien, presione F7 (es el método abreviado de teclado predeterminado de la configuración del desarrollo en C/C++).

- O bien, en la [ventana Comandos](/visualstudio/ide/reference/command-window) (en la barra de menús, seleccione **Ver**, **Otras ventanas**, **Ventana Comandos**), escriba `Build.BuildSolution`.

- O bien, en el cuadro [Inicio rápido](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box), escriba `build build solution`.

Para compilar un proyecto que esté seleccionado en el **Explorador de soluciones**, puede hacer lo siguiente:

- En la barra de menús, seleccione **Compilar**, **Compilar \<Nombre del proyecto>**.

- O bien, en el **Explorador de soluciones**, abra el menú contextual del proyecto y, después, seleccione **Compilar**.

- O bien, en la ventana Comandos (en la barra de menús, seleccione **Ver**, **Otras ventanas**, **Ventana Comandos**), escriba `Build.BuildOnlyProject`.

- O bien, en el cuadro Inicio rápido, escriba `build project only build only <project name>`.

Al compilar una aplicación de Visual C++ en Visual Studio, puede modificar gran parte de la configuración de la compilación en el cuadro de diálogo Páginas de propiedades del proyecto. Para obtener información sobre cómo establecer propiedades de proyectos, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

Para obtener un ejemplo de cómo usar el IDE con el fin de crear, compilar y depurar un proyecto de C++, vea [Tutorial: Explorar el IDE de Visual Studio con C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Para obtener un ejemplo de cómo usar el IDE para compilar un proyecto de C++/CLR, vea [Tutorial: Compilar un programa de C++ orientado a CLR en Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Para ver un ejemplo de cómo usar el IDE para crear una aplicación de Windows Runtime, vea [Create your first Windows Runtime app using C++](https://msdn.microsoft.com/library/windows/apps/hh974580.aspx) (Crear su primera aplicación de Windows Runtime con C++).

Para más información sobre cómo compilar, modificar la configuración de compilación y especificar pasos de compilación personalizada, consulte los siguientes artículos.

## <a name="in-this-section"></a>En esta sección

[Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)<br>
Describe cómo personalizar el proceso de compilación en el entorno de desarrollo integrado.

[Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)<br>
Presenta una lista de macros que puede usar donde se aceptan cadenas.

[Compilar proyectos externos](../ide/building-external-projects.md)<br>
Examina la compilación de proyectos que utilizan instalaciones de fuera del entorno de desarrollo integrado.

[Archivos de proyecto](../ide/project-files.md)<br>
Presenta la estructura XML de un archivo .vcxproj.

## <a name="related-sections"></a>Secciones relacionadas

[Directorios de VC++, Proyectos, Cuadro de diálogo Opciones](vcpp-directories-property-page.md)<br>
(Solo para proyectos de MSBuild) Se explica cómo modificar la ruta de búsqueda de los archivos ejecutables, archivos de inclusión, archivos de biblioteca y archivos de código fuente durante una compilación.

[Compilar y generar en Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio)<br>
Proporciona información sobre la compilación en Visual Studio.

[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br>
Ofrece vínculos a temas en los que se describe la compilación de programas desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.

[Referencia de compilación de C/C++](../build/reference/c-cpp-building-reference.md)<br>
Incluye vínculos a una introducción a la compilación de programas en C++, opciones del compilador y el enlazador y herramientas de compilación adicionales.

[Actualizar proyectos desde versiones anteriores de Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br>
Proporciona vínculos a temas en los que se describen los problemas de actualización del proyecto de C++ a versiones más recientes del Conjunto de herramientas del compilador.

[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md) Información detallada sobre cómo actualizar aplicaciones de C++ que se crearon en versiones anteriores de Visual Studio, y también cómo migrar las aplicaciones que se crearon con herramientas distintas a Visual Studio.

## <a name="see-also"></a>Vea también

[Aplicaciones de Windows universales (C++)](../windows/universal-windows-apps-cpp.md)