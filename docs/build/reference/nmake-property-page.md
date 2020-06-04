---
title: NMake (página de propiedades) (Windows C++)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
ms.openlocfilehash: c0dbe537635fe6698f814f3d8456f0caa9c8c796
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320609"
---
# <a name="nmake-property-page"></a>NMake (página de propiedades)

La página de propiedades **NMake** permite especificar opciones de compilación para los proyectos NMake. (NMAKE es la implementación de Microsoft [realizar](https://wikipedia.org/wiki/Make_(software)).)

Para obtener más información sobre los proyectos NMake, vea [Crear un proyecto de archivo Make](creating-a-makefile-project.md). Para los proyectos que no sean Windows MakeFile, consulte [las propiedades del proyecto de archivos MAKE (Linux C++)](../../linux/prop-pages/makefile-linux.md), [propiedades de proyectos generales (Android archivos MAKE de C++)](/visualstudio/cross-platform/general-makefile-android-prop-page) o [propiedades de NMake (C++ para Android)](/visualstudio/cross-platform/nmake-android-prop-page).

La página de propiedades **NMake** contiene las propiedades siguientes:

## <a name="uielement-list"></a>Lista de UIElement

- **Línea de comandos de Compilar**

   Especifica el comando que se va a ejecutar cuando se hace clic en **Compilar** en el menú **Compilar**.

- **Línea de comandos de Recompilar todo**

   Especifica el comando que se va a ejecutar cuando se hace clic en **Recompilar todo** en el menú **Compilar**.

- **Línea de comandos de limpieza**

   Especifica el comando que se va a ejecutar cuando se hace clic en **Limpiar** en el menú **Compilar**.

- **Salida**

   Especifica el nombre del archivo que contendrá la salida para la línea de comandos. De forma predeterminada, este nombre de archivo se basa en el nombre del proyecto.

- **Definiciones de preprocesador**

   Especifica las definiciones de preprocesador que usan los archivos de código fuente. El valor predeterminado se determina por la plataforma y la configuración actuales.

- **Ruta de acceso de búsqueda de inclusión**

   Especifica los directorios donde el compilador busca los archivos de inclusión.

- **Archivos de inclusión forzados**

   Especifica los archivos que el preprocesador procesa de manera automática incluso si no se incluyen en los archivos de proyecto.

- **Ruta de acceso de búsqueda de ensamblado**

   Especifica los directorios donde .NET Framework busca cuando intenta resolver los ensamblados .NET.

- **Ensamblados de uso forzados**

   Especifica los ensamblados que .NET Framework procesa de manera automática.

- **Opciones adicionales**

   Especifica los modificadores del compilador adicionales que va a usar IntelliSense cuando analiza los archivos de C++.

Para obtener información acerca de cómo obtener acceso a la **NMake** página de propiedades, vea [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

Para obtener información sobre cómo acceder mediante programación a los miembros de este objeto, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.

## <a name="see-also"></a>Vea también

[Referencia de página de propiedades de proyecto de C++](property-pages-visual-cpp.md)<br>
