---
title: páginas de propiedades Vinculador
ms.date: 11/21/2017
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 1412531ae0ca9c0f5270df6df7b79ddc9be425ad
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826855"
---
# <a name="linker-property-pages"></a>páginas de propiedades Vinculador

En este tema se describen las propiedades siguientes de la página de propiedades **General** del enlazador. Para la versión de Linux de esta página, vea [Propiedades del enlazador (C++ para Linux)](../../linux/prop-pages/linker-linux.md).

## <a name="general-page-properties"></a>Página de propiedades General

### <a name="ignore-import-library"></a>Omitir biblioteca de importación

Esta propiedad indica al enlazador que no intente vincular ningún archivo .lib generado en esta compilación a ningún proyecto dependiente. Esto permite al sistema de proyectos controlar los archivos .dll que no producen un archivo .lib cuando se compilan. Si un proyecto depende de otro que genera un archivo DLL, el sistema de proyectos vincula automáticamente el archivo .lib generado por ese proyecto secundario. Esto puede no ser necesario en el caso de proyectos que generan archivos DLL COM o archivos DLL solo de recursos; estos archivos DLL no tienen exportaciones significativas. Si un archivo DLL no tiene exportaciones, el enlazador no genera un archivo .lib. Si no hay ningún archivo de exportación .lib en el disco y el sistema de proyectos indica al enlazador que establezca un vínculo con este archivo DLL (que falta), se produce un error en el vínculo. Use la propiedad **Omitir biblioteca de importación** para resolver este problema. Cuando se establece en **Sí**, el sistema de proyectos ignora la presencia o ausencia de ese archivo .lib y evita que cualquier proyecto que dependa de este se vincule al archivo .lib inexistente.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Registrar resultados

Ejecuta `regsvr32.exe /s $(TargetPath)` en la salida de compilación, que solo es válida en los proyectos de archivo .dll. En los proyectos de archivo .exe se omite esta propiedad. Para registrar un resultado de tipo .exe, establezca un evento posterior a la compilación en la configuración para que realice el registro personalizado que siempre se necesita para los archivos .exe registrados.

Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Redirección por usuario

En Visual Studio, el registro se ha realizado tradicionalmente en HKEY_CLASSES_ROOT (HKCR). Con Windows Vista y sistemas operativos posteriores, para acceder a HKCR se debe ejecutar Visual Studio en modo elevado. Los desarrolladores no siempre desean trabajar en modo elevado, pero aun así deben trabajar con el registro. La redirección por usuario le permite registrar sin tener que trabajar en este modo.

La redirección por usuario fuerza la redirección a HKEY\_CURRENT\_USER (HKCU) de todas las operaciones de escritura en HKCR. Si la redirección por usuario está desactivada, puede producir [Error PRJ0050 al compilar el proyecto](../../error-messages/tool-errors/project-build-error-prj0050.md) cuando el programa intenta escribir en HKCR.

### <a name="link-library-dependencies"></a>Dependencias de la biblioteca de vínculos

Especifica si se vinculan los archivos .lib generados por los proyectos dependientes. Normalmente, le interesará vincular en los archivos .lib, pero puede que ese no sea el caso de determinados archivos DLL.

También puede especificar un archivo .obj si proporciona el nombre de archivo y la ruta de acceso relativa, por ejemplo "..\\..\MyLibProject\MyObjFile.obj". Si el código fuente del archivo .obj incluye un encabezado precompilado, por ejemplo pch.h, el archivo pch.obj se encuentra en la misma carpeta que MyObjFile.obj y también debe agregar pch.ob como una dependencia adicional.

### <a name="use-library-dependency-inputs"></a>Usar entradas de dependencia de biblioteca

En un proyecto grande, cuando un proyecto dependiente genera un archivo .lib, se deshabilita la vinculación incremental. Si hay muchos proyectos dependientes que generan archivos .lib, puede llevar bastante tiempo compilar la aplicación. Cuando esta propiedad se establece en **Sí**, el sistema de proyectos vincula en los archivos .obj para los archivos .lib generados por los proyectos dependientes, con lo que se habilita la vinculación incremental.

Para obtener información acerca de cómo obtener acceso a la **General** página de propiedades del vinculador, vea [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Vea también

[Configuración de proyecto de VC++, Proyectos y soluciones, Opciones (Cuadro de diálogo)](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)<br>
[Referencia de página de propiedades de proyecto de C++](property-pages-visual-cpp.md)