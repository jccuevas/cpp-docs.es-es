---
title: página de propiedades Recursos administrados
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 14802996e63392bfb5fcc22096ef5f3d9db197c2
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177525"
---
# <a name="managed-resources-property-page"></a>página de propiedades Recursos administrados

La página de propiedades **recursos administrados** expone las siguientes propiedades para el compilador de recursos administrados [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) cuando se usan recursos de .net en C++los programas/CLI:

- **Nombre lógico del recurso**

   Especifica el *nombre lógico* del archivo .resources intermedio que se genera. El nombre lógico es el que se usa para cargar el recurso. Si no se especifica ningún nombre lógico, se usa el nombre de archivo de recursos (.resx) como el nombre lógico.

- **Nombre del archivo de salida**

   Especifica el nombre del archivo de salida final al que contribuye este archivo de recursos (.resx).

- **Recursos adaptados predeterminados**

   Especifica si el archivo .resx indicado contribuye a los recursos predeterminados o a un archivo .dll satélite.

Para obtener información sobre cómo obtener acceso a la página de propiedades **recursos administrados** , vea [establecer C++ las propiedades del compilador y compilación en Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Vea también

[Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) [Uso de RC (la línea de comandos de RC)]<br>
[C++referencia de la página de propiedades del proyecto](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (Insertar un recurso administrado)](assemblyresource-embed-a-managed-resource.md)
