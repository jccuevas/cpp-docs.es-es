---
title: Página de propiedades NMake (ventanas de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
dev_langs:
- C++
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f156d69467f00c4c4a62ec84d3b870e2999d7115
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-property-page"></a>NMake (página de propiedades)
El **NMake** página de propiedades le permite especificar opciones de compilación para proyectos NMake.  
  
 Para obtener más información acerca de los proyectos NMake, vea [crear un proyecto de archivos MAKE](../ide/creating-a-makefile-project.md). Para proyectos de archivos MAKE non_Windows, consulte [propiedades del proyecto de archivos MAKE (C++ Linux)](../linux/prop-pages/makefile-linux.md), [propiedades del proyecto General (Android archivo MAKE de C++)](/visualstudio/cross-platform/general-makefile-android-prop-page) o [NMake propiedades (C++ Android)](/visualstudio/cross-platform/nmake-android-prop-page).
  
 El **NMake** página de propiedades contiene las siguientes propiedades.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Compilar la línea de comandos**  
 Especifica el comando que se ejecutará cuando **generar** se hace clic en el **generar** menú.  
  
 **Volver a generar todos los de línea de comandos**  
 Especifica el comando que se ejecutará cuando **volver a generar todo** se hace clic en el **generar** menú.  
  
 **Limpiar la línea de comandos**  
 Especifica el comando que se ejecutará cuando **limpiar** se hace clic en el **generar** menú.  
  
 **Salida**  
 Especifica el nombre del archivo que contendrá la salida de la línea de comandos. De forma predeterminada, este nombre de archivo se basa en el nombre del proyecto.  
  
 **Definiciones de preprocesador**  
 Especifica las definiciones del preprocesador que el origen de archivos de uso. El valor predeterminado se determina por la plataforma actual y la configuración.  
  
 **Incluir la ruta de acceso de búsqueda**  
 Especifica los directorios donde el compilador busca los archivos de inclusión.  
  
 **Fuerza incluye**  
 Especifica los archivos que el preprocesador procesa automáticamente aun cuando no se incluyen en los archivos de proyecto.  
  
 **Ruta de acceso de búsqueda de ensamblado**  
 Especifica los directorios donde .NET Framework busca cuando se intenta resolver ensamblados. NET.  
  
 **Ensamblados de uso forzados**  
 Especifica los ensamblados de .NET Framework procesa automáticamente.  
  
 **Opciones adicionales**  
 Especifica los modificadores del compilador adicionales de IntelliSense que se usará cuando analiza los archivos de C++.  
  
 Para obtener información sobre cómo obtener acceso a la **NMake** página de propiedades, vea [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
 Para obtener información acerca de cómo mediante programación el acceso a los miembros de este objeto, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)   
 [Cómo: Habilitar IntelliSense para proyectos de archivos MAKE](../ide/how-to-enable-intellisense-for-makefile-projects.md)