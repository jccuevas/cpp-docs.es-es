---
title: "Páginas de propiedades vinculador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs:
- C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b8a1d0d4775955ee55aa0f40ac10a75cda54379
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-property-pages"></a>páginas de propiedades Vinculador

En este tema se describe las propiedades siguientes en el **General** página de propiedades del vinculador. Para la versión de Linux de esta página, vea [propiedades del vinculador (C++ Linux)](../linux/prop-pages/linker-linux.md).

## <a name="general-page-properties"></a>Propiedades de la página general

### <a name="ignore-import-library"></a>Omitir biblioteca de importación

Esta propiedad indica al vinculador que no vincular ningún resultado .lib generado a partir de esta compilación a ningún proyecto dependiente. Esto permite al sistema de proyectos controlar los archivos .dll que no producen un archivo .lib cuando se compilan. Si un proyecto depende de otro proyecto que genera un archivo DLL, el sistema de proyectos vinculará automáticamente el archivo .lib generado por el proyecto secundario. Esto puede no ser necesario en el caso de proyectos que generan archivos DLL COM o archivos DLL solo de recursos; estos archivos DLL no tienen exportaciones significativas. Si un archivo DLL no tiene exportaciones, el vinculador no genera un archivo .lib. Si ningún archivo de exportación .lib está presente en el disco y el sistema de proyectos indica al vinculador para vincular con este archivo DLL (que falta), se produce un error en el vínculo. Use la **Omitir biblioteca de importación** propiedad para resolver este problema. Cuando se establece en **Sí**, el sistema del proyecto pasa por alto la presencia o ausencia del archivo .lib y hace que cualquier proyecto que dependa de este proyecto se vincule al archivo .lib inexistente.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Registrar resultados

Se ejecuta `regsvr32.exe /s $(TargetPath)` en la salida de compilación, que es válida sólo en proyectos de DLL. En los proyectos de archivo .exe se omite esta propiedad. Para registrar un resultado de tipo .exe, establezca un evento posterior en la configuración para que realice el registro personalizado que siempre es necesario para los archivos .exe registrados.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Redirección por usuario

Registro en Visual Studio se ha realizado tradicionalmente en HKEY_CLASSES_ROOT (HKCR). Con [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]para tener acceso a HKCR se debe ejecutar Visual Studio en modo elevado. Los desarrolladores no siempre desean trabajar en modo elevado, pero aun así deben trabajar con el registro. La redirección por usuario le permite registrar sin tener que trabajar en este modo.

Redirección por usuario fuerza las escrituras en HKCR se redirija a HKEY\_actual\_usuario (HKCU). Si se desactiva la redirección por usuario, es posible que [Project Build Error PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md) cuando el programa intenta escribir en HKCR.

### <a name="link-library-dependencies"></a>Dependencias de la biblioteca de vínculos

Especifica si se debe vincular los archivos .lib generados por proyectos dependientes. Normalmente, debe vincular en los archivos .lib, pero esto puede no ser el caso de determinados archivos DLL.

También puede especificar un archivo .obj proporcionando el nombre de archivo y ruta de acceso relativa, por ejemplo ".. \\.. \MyLibProject\MyObjFile.obj". Si el código fuente del archivo .obj #includes un encabezado precompilado, por ejemplo pch.h, el archivo pch.obj se encuentra en la misma carpeta que MyObjFile.obj, y también deben agregar pch.obj como una dependencia adicional.

### <a name="use-library-dependency-inputs"></a>Usar entradas de dependencia de biblioteca

En un proyecto grande, cuando un proyecto dependiente genera un archivo .lib, se deshabilita la vinculación incremental. Si hay muchos proyectos dependientes que generan archivos .lib, puede llevar bastante tiempo compilar la aplicación. Cuando esta propiedad se establece en **Sí**, el sistema de proyectos vincula en los archivos .obj para los archivos .lib generados por proyectos dependientes, lo que permite la vinculación incremental.

Para obtener información sobre cómo obtener acceso a la **General** página de propiedades del vinculador, vea [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Vea también

[Configuración de proyecto de VC++, Proyectos y soluciones, Opciones (Cuadro de diálogo)](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)  
[Páginas de propiedades](../ide/property-pages-visual-cpp.md)  