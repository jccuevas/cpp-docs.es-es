---
title: Procedimiento Modificación de las propiedades y los destinos de un proyecto de C++ sin cambiar el archivo del proyecto
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: 72107b572e35f222c0b03959e0edd2d23bd0130a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328463"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Procedimiento Modificación de las propiedades y los destinos de un proyecto de C++ sin cambiar el archivo del proyecto

Puede invalidar las propiedades y los destinos del proyecto desde la línea de comandos de MSBuild sin cambiar el archivo de proyecto. Esto es útil cuando se quieren aplicar algunas propiedades de manera ocasional o temporal. Se presuponen ciertos conocimientos de MSBuild. Para obtener más información, vea [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Para crear el archivo .props o .targets, puede usar el Editor XML de Visual Studio o cualquier editor de texto. No use el **Administrador de propiedades** en este escenario ya que agrega las propiedades al archivo de proyecto.

*Para reemplazar las propiedades del proyecto:*

1. Cree un archivo .props en el que se especifiquen las propiedades que se quieren invalidar.

1. Desde el símbolo del sistema: establezca ForceImportBeforeCppTargets="C:\sources\my_props.props".

*Para reemplazar los destinos del proyecto:*

1. Cree un archivo .targets con su implementación o un destino concreto.

2. Desde el símbolo del sistema: establezca ForceImportAfterCppTargets ="C:\sources\my_target.targets".

También puede establecer cualquiera de las opciones en la línea de comandos de msbuild mediante la opción /p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

El reemplazo de propiedades y destinos de esta manera equivale a agregar las importaciones siguientes a todos los archivos .vcxproj de la solución:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
